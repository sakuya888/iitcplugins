// ==UserScript==
// @id             iitc-plugin-virus@taskjp
// @name           IITC plugin: Virus
// @category       Layer
// @version        0.0.1
// @namespace      iitc-plugin-virus
// @description    Show virus information
// @updateURL      https://dl.dropboxusercontent.com/s/ohh8m1k67xxslqd/iitc-plugin-virus.meta.js
// @downloadURL    https://dl.dropboxusercontent.com/s/vbdhwpvb1onmuyn/iitc-plugin-virus.user.js
// @author         taskjp
// @include        https://*.ingress.com/intel*
// @match          https://*.ingress.com/intel*
// @grant          none
// ==/UserScript==

function wrapper(plugin_info) {
    // ensure plugin framework is there, even if iitc is not yet loaded
    if(typeof window.plugin !== 'function') window.plugin = function() {};

    // PLUGIN START ////////////////////////////////////////////////////////

    // use own namespace for plugin
    window.plugin.virus = function() {};

    var self = window.plugin.virus;
    self.layerGroup = null;
    self.layers = {};

    self.db = function() {};
    var db = self.db;
    db.indexedDB = null;
    db.init = function() {
        var indexedDB = window.indexedDB || window.webkitIndexedDB || window.mozIndexedDB || window.msIndexedDB;
        var idbRequest = indexedDB.open('iitc-plugin-virus', 1);
        idbRequest.onupgradeneeded = function (event) {
            var db = event.target.result;
            var store = db.createObjectStore('virus', { keyPath: ['latE6', 'lngE6', 'timestamp'] });
            store.createIndex('latlng', ['latE6', 'lngE6']);
            store.createIndex('timestamp', 'timestamp');
       };
        idbRequest.onerror = function (event) {
            alert("virus: indexedDB.open() failed");
        };

        idbRequest.onsuccess = function (event) {
            db.indexedDB = idbRequest.result;
            db.cleanupExpiered();
        };
    }

    db.add = function(data) {
        if (!db.indexedDB) return;
        var transaction = db.indexedDB.transaction(['virus'], 'readwrite');
        var store = transaction.objectStore('virus');
        var request = store.put({
                                    latE6: data.portal.latE6,
                                    lngE6: data.portal.lngE6,
                                    timestamp: data.timestamp,
                                    portal: data.portal.name,
                                    agent: data.agent.plain,
                                    faction: data.agent.team,
                                    virus: data.virus
                                });
        request.onsuccess = function(event) {
            console.debug('virus', event);
        }
    }

    db.latest = function(callback) {
        if (!db.indexedDB) return {};
        var transaction = db.indexedDB.transaction(['virus'], 'readonly');
        var store = transaction.objectStore('virus');
        var index = store.index('timestamp');
        var range = IDBKeyRange.lowerBound(Date.now() - 2 * 60 * 60 * 1000);
        var request = index.openCursor(range, 'next');
        request.onsuccess = function(event) {
            var cursor = event.target.result;
            callback(cursor);
        }
    }

    db.find = function(latE6, lngE6, callback) {
        if (!db.indexedDB) return {};
        var transaction = db.indexedDB.transaction(['virus'], 'readonly');
        var store = transaction.objectStore('virus');
        var index = store.index('latlng');
        var range = IDBKeyRange.only([latE6, lngE6]);
        var request = index.openCursor(range, 'next');
        request.onsuccess = function(event) {
            var cursor = event.target.result;
            callback(cursor);
        }
    }
    db.cleanupExpiered = function() {
        var transaction = db.indexedDB.transaction(['virus'], 'readwrite');
        var store = transaction.objectStore('virus');
        var index = store.index('timestamp');
        var range = IDBKeyRange.upperBound(Date.now() - 5 * 24 * 60 * 60 * 1000);
        var request = index.openCursor(range, 'next');
        request.onsuccess = function(event) {
            var cursor = event.target.result;
            if (cursor) {
                cursor.delete();
                cursor.continue();
            }
        }
    }

    self.detect = function(data) {
        var cache = {};
        var result = data.result;
        var previous = [];
        for (var i = 0; i < result.length; i++) {
            var p = previous;
            previous = [];
            var log = result[i];
            if (log.length !== 3) continue;
            var timestamp = log[1];
            var plext = log[2].plext;
            if (!plext) continue;
            var markup = plext.markup;
            if (!markup) continue;
            if (markup.length !== 3) continue;

            if (markup[0][0] !== "PLAYER") continue;
            var player = markup[0][1];

            if (markup[1][0] !== "TEXT") continue;
            var action = markup[1][1].plain;
            if (action !== " destroyed a Resonator on ") continue;

            if (markup[2][0] !== "PORTAL") continue;
            var portal = markup[2][1];

            var cacheKey = portal.latE6 + ',' + portal.lngE6;
            if (player.team === portal.team) {
                if (cache[cacheKey] === timestamp) return;
                cache[cacheKey] = timestamp;
                window.runHooks('virusDetected', {
                                    timestamp: timestamp,
                                    agent: player,
                                    virus: player.team === "RESISTANCE" ? "ADA" : "JARVIS",
                                    portal: portal
                                });
            } else {
                if (p.length === 3 && timestamp === p[1] && plext.text === p[2].plext.text) {
                    if (cache[cacheKey] === timestamp) return;
                    cache[cacheKey] = timestamp;
                    window.runHooks('virusDetected', {
                                        timestamp: timestamp,
                                        agent: player,
                                        virus: player.team === "RESISTANCE" ? "JARVIS" : "ADA",
                                        portal: portal
                                    });
                }
            }
            previous = log;
        }
    };

    self.detected = function(data) {
        db.add(data);
        self.updateLater(500);
    };

    self.timer = null;
    self.updateLater = function(msecs) {
        if (self.timer)
            clearTimeout(self.timer);
        self.timer = setTimeout(self.update, msecs);
    }

    self.update = function(data) {
        self.timer = null;
        var keys = Object.keys(self.layers);
        var now = (new Date).getTime();
        db.latest(function(cursor) {
            if (!cursor) {
                self.updateLater(1000);
                return;
            }
            var data = cursor.value;
            var age = (now - cursor.value.timestamp) / 60 / 1000;
            var className = 'iitc-plugin-virus-layer iitc-plugin-virus-layer-';
            if (age > 60) {
                className += 'expired';
            } else if (age > 55) {
                className += '5min';
            } else if (age > 50) {
                className += '10min';
            } else {
                className += '60min';
            }
            var key = data.latE6 + ',' + data.lngE6;
            var index = keys.indexOf(key);
            if (index !== -1) {
                keys.splice(index);
                var marker = self.layers[key];
                self.layerGroup.removeLayer(marker);
            }
            var icon = L.divIcon({
                className: className,
                iconSize: [ 14, 14 ],
                iconAnchor: [ 9, 6 ],
                html: ('0' + (new Date(cursor.value.timestamp)).getMinutes()).slice(-2),
            });
            var latLng = L.latLng(data.latE6 / 1e6, data.lngE6 / 1e6);
            var label = L.marker(latLng, {
                                     icon: icon,
                                     opacity: 1.0,
                                     clickable: false,
                                     keyboard: false
                                 });
            label.addTo(self.layerGroup);
            self.layers[key] = label;

            cursor.continue();
        });
    };

    self.formatTime = function(timestamp) {
        var date = new Date(timestamp);
        var hh = ('0' + date.getHours()).slice(-2);
        var mm = ('0' + date.getMinutes()).slice(-2);
        var ss = ('0' + date.getSeconds()).slice(-2);
        var zzz = ('00' + date.getMilliseconds()).slice(-3);
        return hh + ':' + mm + ':' + ss + '.' + zzz;
    }

    self.showDetails = function(data) {
        var latE6 = data.portalData.latE6;
        var lngE6 = data.portalData.lngE6;
        var virus = null;
        $('#virus-details').remove();
        db.find(latE6, lngE6, function(cursor) {
            if (cursor) {
                if (!virus || virus.timestamp < cursor.value.timestamp) {
                    virus = cursor.value;
                }
                cursor.continue();
            } else if (virus){
                var now = (new Date).getTime();
                var age = (now - virus.timestamp) / 60 / 1000;
                var className = 'virus-details-';
                if (age > 60) {
                    className += 'expired';
                } else if (age > 55) {
                    className += '5min';
                } else if (age > 50) {
                    className += '10min';
                } else {
                    className += '60min';
                }

                $('#randdetails').before('<div id="virus-details" class="' + className + '"><span class="' + virus.faction.slice(0, 3).toLowerCase() +'">' + virus.agent + '</span> <span class="' + (virus.virus === 'ADA' ? 'res' : 'enl') +'">' + virus.virus + 'ed</span> at ' + self.formatTime(virus.timestamp) + '</div>');
            }
        });
    }

    var setup = function() {
        window.addHook('publicChatDataAvailable', self.detect);
        window.addHook('portalDetailsUpdated', self.showDetails);
        window.pluginCreateHook('virusDetected')
        window.addHook('virusDetected', self.detected);

        db.init();

        self.layerGroup = new L.LayerGroup();
        window.addLayerGroup('Virus', self.layerGroup, true);
        self.updateLater(500);

        var style = (function () {/*
#virus-details {
    text-align: center;
    padding: 5px;
    margin: 5px;
    text-shadow:black 1px 1px 0, black -1px -1px 0, black -1px 1px 0, black 1px -1px 0, black 0px 1px 0, black  0-1px 0, black -1px 0 0, black 1px 0 0;
}
.virus-details-5min {
    background-color: red;
}
.virus-details-10min {
    background-color: orange;
}
.virus-details-60min {
    background-color: yellow;
}
.virus-details-expired {
    background-color: gray;
}

.iitc-plugin-virus-layer {
    text-align: center;
    font-family: monospace;
    font-size:10px;line-height:10px;
    text-align:center;padding: 2px;
    overflow:visible;
    pointer-events:none;
    text-shadow:black 1px 1px 0, black -1px -1px 0, black -1px 1px 0, black 1px -1px 0, black 0px 1px 0, black  0-1px 0, black -1px 0 0, black 1px 0 0;
}
.iitc-plugin-virus-layer-5min {
    color:red;
}
.iitc-plugin-virus-layer-10min {
    color:orange;
}
.iitc-plugin-virus-layer-60min {
    color:yellow;
}
.iitc-plugin-virus-layer-expired {
    opacity: 0.50;
    color:gray;
}
        */}).toString().match(/(?:\/\*(?:[\s\S]*?)\*\/)/).pop().replace(/^\/\*/, "").replace(/\*\/$/, "");

        $('<style>').prop('type', 'text/css').html(style).appendTo('head');
    };

    // PLUGIN END //////////////////////////////////////////////////////////

    setup.info = plugin_info; //add the script info data to the function as a property
    if(!window.bootPlugins) window.bootPlugins = [];
    window.bootPlugins.push(setup);
    // if IITC has already booted, immediately run the 'setup' function
    if(window.iitcLoaded && typeof setup === 'function') setup();
} // wrapper end
// inject code into site context
var script = document.createElement('script');
var info = {};
if (typeof GM_info !== 'undefined' && GM_info && GM_info.script) info.script = { version: GM_info.script.version, name: GM_info.script.name, description: GM_info.script.description };
script.appendChild(document.createTextNode('('+ wrapper +')('+JSON.stringify(info)+');'));
(document.body || document.head || document.documentElement).appendChild(script);
