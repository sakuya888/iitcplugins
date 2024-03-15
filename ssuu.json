// ==UserScript==
// @id             iitc-plugin-scanner-link
// @name           IITC plugin: Dynamiclink
// @category       Portal Info
// @version        0.0.2.5
// @namespace      scanner-link
// @description    Add Dynamiclink to iitc
// @updateURL      https://dl.dropboxusercontent.com/s/jtlh5qsdm7mp86d/iitc-plugin-scanner-link.meta.js
// @downloadURL    https://dl.dropboxusercontent.com/s/vintmvytk2qwe8v/iitc-plugin-scanner-link.user.js
// @include        https://*.ingress.com/intel*
// @include        http://*.ingress.com/intel*
// @match          https://*.ingress.com/intel*
// @match          http://*.ingress.com/intel*
// @include        https://*.ingress.com/mission/*
// @include        http://*.ingress.com/mission/*
// @match          https://*.ingress.com/mission/*
// @match          http://*.ingress.com/mission/*
// @author         Made by taskjp. Modified by TNG01.
// @grant          none
// ==/UserScript==

function wrapper(plugin_info) {
	// ensure plugin framework is there, even if iitc is not yet loaded
	if (typeof window.plugin !== 'function') window.plugin = function() {};
	// plugin_info
	plugin_info.buildName = 'ingress-enl-jp-harima-unofficial';
	plugin_info.dateTimeVersion = '20220313.000000';
	plugin_info.pluginId = 'scannerLink';
	// PLUGIN START ////////////////////////////////////////////////////////
	// use own namespace for plugin
	window.plugin.scannerLink = function() {};
	window.plugin.scannerLink.setupCallback = function() {
		addHook('portalDetailsUpdated', window.plugin.scannerLink.addLink);
	};
	window.plugin.scannerLink.addLink = function(d) {
        $('.linkdetails').append('<aside><a href="https://link.ingress.com/?link=https%3a%2f%2fintel.ingress.com%2fportal%2f' + window.selectedPortal + '&apn=com.nianticproject.ingress&isi=576505181&ibi=com.google.ingress&ifl=https://apps.apple.com/app/ingress/id576505181ofl=https://intel.ingress.com/intel?pll=' + d.portal._latlng.lat.toFixed(6) + ',' + d.portal._latlng.lng.toFixed(6) + '" title="Scanner" target="_blank"><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAMAAAAoLQ9TAAAACXBIWXMAAAsTAAALEwEAmpwYAAADAFBMVEUhAGwiAGwqAG87AHQ9CIA+CYE+CoBACoBAC4FFDoNHFIdHFYZJF4dJGIhNHYpPH4pRG4tRHItRIY1SIoxVHotWHYtYKpFZH4tZIItaLZJaLZNaLpJbL5NcL5NcL5RcMJNdIo5dI45dJY5dMJNdMZNdMZReH41fJ49fNJVgHI1gMZRgMZVgNJZhJI1hJI5hNJVhNZVjM5ZkNJZmJJBoKpJoKpNoNpdqOJhrOJdsMpVsMpZtL5VtL5ZtMpZuMpZuOpluOppwM5hwSZ5xSZ9yPJtzPpxzP5x1P5t1P5x1TKF2O5x3QJ14T6F5QJ55QZ56SqB7Qp97Q6B7RJ97UqJ8TaJ9WqiAS6KAS6OCUaOCUaSKXqmKXqqLaq+La6+MZq2NZ6+NaK+ObLGPabCParCQarCQbbKQbrKRabGRarGSZLCSb7STZLCVa7GWcbSXcbSXfriYfrmbfLmcfbqdfbmdgbqdgrudg7udg7yef7qgg7yghLughbyhgLuhhr2igLykhr2kiL+liL+liMClir+lisCnh72piL6pjsGpj8OrjMCrjsGrj8KrkcKsjsGsj8KslcStkMKtl8WtmMaukcKulsWxkcSxksSxnci0lsW0lsa0msm1msm4n8q6ocrDsNLDsdHEtdPEttTGudTKt9XPvdjSxdzUyeDd0uTe0uTu7O/v7vD08vP18vP///8dAwEAAAAATattAQAAAJjA0ZQBgHgKyPvC6gEAAADA+8LqAQAAAL/x5t4BAAAAAPDC6gEAAAAwTattAQAAAGDX9AAAYAAAAD4JAgBgAAAwTqttAQAAACBNq20BAAAACHzTlAEAOx0APgkCAGAAADBOq20BAAAAIE6rbQEAAADw+9KUAQAoPgA/CQIAYAAAgD8JAgBgAAAAfLgBAGAAAIDCCQIAYAAAAMMJAgBgAACAwwkCAGAAAADECQIAYAAAAMIJAgBgAACAxAkCAGAAAADFCQIAYAAAAMYJAgBgAACAxgkCAGAAAAAAugEAYAAAfwAAAAAAAAAEXDEoAAABCklEQVR4nGLwBQG/AGubAD8wkwFEBDoaZ2caOwZCBQK8NMNmLl8xI1zTKwAo4B1kYjdtSU5rW86SqbamQd4MHlaRiyfrMUdFM+tOWBxh6c7gojan0y09t64mL8O1d66aC4O9Ypf/7LVLk1KWrp0V0qfgwGAu0Z6gPr++pqZxnlJyt7gFg5lIRypTcXxDU1wFU1aPqBmDkWBpYlFwS0lVs09hWqWAIYM2Z//qWHbPVSs9OWLWTOHUYlAWdl5Yrc+4bBmDQe0CJ2EVBhkdHq7yRfn8/AWLyrh5NWQYpKRkxFhUp0+cNF2FRUxOUpJBEgjkhVhDQ9mE5EFssICktCwfn6w0mAkAAAD//wMAhLdOXM2/Gu0AAAAASUVORK5CYII=" /></a></aside>');
	};
	var setup = function() {
			window.plugin.scannerLink.setupCallback();
		};
	// PLUGIN END //////////////////////////////////////////////////////////
	setup.info = plugin_info; //add the script info data to the function as a property
	if (!window.bootPlugins) window.bootPlugins = [];
	window.bootPlugins.push(setup);
	// if IITC has already booted, immediately run the 'setup' function
	if (window.iitcLoaded && typeof setup === 'function') setup();
}
// wrapper end
// inject code into site context
var script = document.createElement('script');
var info = {};
if (typeof GM_info !== 'undefined' && GM_info && GM_info.script) info.script = {
	version: GM_info.script.version,
	name: GM_info.script.name,
	description: GM_info.script.description
};
script.appendChild(document.createTextNode('(' + wrapper + ')(' + JSON.stringify(info) + ');'));
(document.body || document.head || document.documentElement).appendChild(script);
