// ==UserScript==
// @id             iitc-plugin-drawlayer-launcher@mocching
// @name           IITC plugin: Draw Layer Launcher
// @namespace      https://plus.google.com/u/0/103682011707526462879/#1
// @description    DrawTools LayerLauncher
// @version        0.20171207.4
// @category       Layer
// @updateURL      https://dl.dropbox.com/s/przl5tjf8hx353m/IITC_plugin_Draw_Layer_Launcher.user.js
// @downloadURL    https://dl.dropbox.com/s/przl5tjf8hx353m/IITC_plugin_Draw_Layer_Launcher.user.js
// @include        https://*.ingress.com/intel*
// @include        http://*.ingress.com/intel*
// @match          https://*.ingress.com/intel*
// @match          http://*.ingress.com/intel*
// @grant          none
// ==/UserScript==

function wrapper(plugin_info) {
// in case IITC is not available yet, define the base plugin object
// ensure plugin framework is there, even if iitc is not yet loaded
  plugin_info.buildName = 'drawlayer-launcher';
  plugin_info.dateTimeVersion = '0.20171207.1';
  plugin_info.pluginId = 'Draw-Layer-Launcher';
if(typeof window.plugin !== 'function') window.plugin = function() {};
// PLUGIN START ///////////////////////////////////////////////////////////////

window.plugin.drawlayerLauncher = function() {};
window.plugin.drawlayerLauncher.setup = function() {

  if(!localStorage['iitc-drawlayerLauncher-data']){
    localStorage['iitc-drawlayerLauncher-data'] = JSON.stringify({
      "select": 1,
      "data":{ "n1": "","n2": "","n3": "", "n4": "", "n5": "","n6": "" }
    });
  }
  window.plugin.drawlayerLauncher.svg = {
    'marker': '<svg viewBox="-60 0 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M192.921,0C86.272,0,0,86.272,0,192.921C0,248.413,27.746,298.7,55.06,345.089c33.38,57.659,73.266,111.418,119.652,159.106 c9.973,10.406,26.448,10.406,36.85,0c40.754-40.317,76.736-85.838,107.083-134.395c32.515-52.455,67.629-113.152,67.629-176.879 C385.842,86.707,299.568,0,192.921,0z M192.921,271.719c-46.358,0-84-37.642-84-84s37.642-84,84-84c46.353,0,84,37.337,84,84 C276.921,234.381,239.274,271.719,192.921,271.719z"/></svg>',
    'polyline': '<svg viewBox="-4 0 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M76.2,512C34.2,512,0,477.8,0,435.8c0-42,34.2-76.2,76.2-76.2c9.7,0,19.1,1.8,27.7,5.3l255-255c-5-10.1-7.8-21.5-7.8-33.6 c0-42,34.2-76.2,76.2-76.2c42,0,76.2,34.2,76.2,76.2c0,42-34.2,76.2-76.2,76.2c-10.5,0-20.4-2.2-29.5-5.9L144,400.5 c5.5,10.5,8.6,22.5,8.6,35.2C152.6,477.8,118.4,512,76.2,512L76.2,512z M76.2,391.4c-24.3,0-44.2,19.9-44.2,44.2 c0,24.3,19.9,44.2,44.2,44.2c24.3,0,44.2-19.9,44.2-44.2C120.6,411.3,100.7,391.4,76.2,391.4L76.2,391.4z M427.4,31.9 c-24.3,0-44.2,19.9-44.2,44.2c0,24.3,19.9,44.2,44.2,44.2c24.3,0,44.2-19.9,44.2-44.2C471.8,51.8,451.9,31.9,427.4,31.9L427.4,31.9z "/></svg>',
    'polygon': '<svg viewBox="-44 -46 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M126.8,423.2L0,192L180.8,0l238.5,112.5L386,374L126.8,423.2z"/></svg>',
    'circle': '<svg viewBox="-54 -54 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M403.5,201.795c0,111.473-90.322,201.795-201.795,201.795C90.322,403.5,0,313.178,0,201.795C0,90.322,90.322,0,201.795,0 C313.178,0,403.5,90.322,403.5,201.795z"/></svg>',
    'multiline': '<svg viewBox="-10 0 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M426.9,268.9c-35.9,0-65.1,29.2-65.3,65.1l-206.1,67.2l249.9-272.4c4.8,1.1,9.7,1.7,14.8,1.7c36,0,65.3-29.2,65.3-65.3 c0-36.1-29.2-65.2-65.3-65.2S355,29.2,355,65.3c0,13.2,3.9,25.7,10.9,35.9l-245,267.3c-0.1-0.1-0.4-0.2-0.5-0.4l53.9-237.4 c33.6-2.6,60.1-30.8,60.1-65c0-36-29.2-65.3-65.3-65.3c-36,0-65.1,29.2-65.1,65.3c0,20.6,9.7,39,24.6,51l-54.4,239 C32.9,357.7,0,392,0,433.8C0,476.9,35.1,512,78.2,512c36.9,0,67.9-25.7,76-60.1l224.9-73.3c11.9,12.9,29,20.9,47.8,20.9 c36,0,65.3-29.2,65.3-65.3C492.2,298.2,463,268.9,426.9,268.9z M420.2,35.8c16.2,0,29.5,13.2,29.5,29.5c0,16.2-13.2,29.5-29.5,29.5 c-16.3,0-29.5-13.2-29.5-29.5C390.8,49,404,35.8,420.2,35.8z M169.3,36.2c16.2,0,29.5,13.2,29.5,29.5c0,16.2-13.2,29.5-29.5,29.5 c-16.2,0-29.5-13.2-29.5-29.5C139.8,49.4,153.1,36.2,169.3,36.2z M78.2,464.3c-16.8,0-30.4-13.6-30.4-30.4 c0-16.8,13.6-30.5,30.4-30.5c16.8,0,30.4,13.6,30.4,30.4S95,464.3,78.2,464.3z M426.9,363.6c-16.2,0-29.5-13.2-29.5-29.5 c0-16.2,13.2-29.5,29.5-29.5c16.3,0,29.5,13.2,29.5,29.5C456.4,350.3,443.2,363.6,426.9,363.6z"/></svg>',
    'eraser': '<svg viewBox="0 -28 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M466.9,427.6H325.4l-30.3,28.3h191.8c13.9,0,25.1-2.2,25.1-16.1C512,425.8,480.8,427.6,466.9,427.6z M486.9,212.5 c11.7-11.7,11.7-30.7,0-42.4L325.6,8.8C319.8,2.9,312.1,0,304.4,0c-7.7,0-15.4,3-21.2,8.8L89.7,202.3L293.4,406L486.9,212.5z M130.1,447c5.7,5.7,13.4,8.9,21.4,8.9h75.8h3.8c8,0,15.7-3.2,21.4-8.9l6.3-6.3l5.3-5.3L60.3,231.7L8.8,283.2 c-11.7,11.7-11.7,30.7,0,42.4L130.1,447z"/></svg>',
    'copy': '<svg viewBox="0 -47 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M89.3,53.7h328.5c28.5,0,52.9,21.9,52.9,50.4v217.4c0,4.5,3.3,8.7,8.3,8.7c18.6,0,33.1-15.3,33.1-34.3V35.5 C512,16.9,496.7,0,478.1,0H115.3c-19,0-33.1,16.9-33.1,36v7.9C82.2,48.3,84.7,53.3,89.3,53.7z M433.5,117.4 c0-16.9-12-30.6-28.5-30.6H98.4h-69C13.2,86.8,0,100,0,116.1v271.5C0,402.9,12.4,417,27.7,417h379.8c15.3,0,26-14.1,26-29.3v-74.8 L433.5,117.4L433.5,117.4z"/></svg>',
    'mix': '<svg viewBox="0 -47 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M89.3,53.7h328.5c28.5,0,52.9,21.9,52.9,50.4v217.4c0,4.5,3.3,8.7,8.3,8.7c18.6,0,33.1-15.3,33.1-34.3V35.5 C512,16.9,496.7,0,478.1,0H115.3c-19,0-33.1,16.9-33.1,36v7.9C82.2,48.3,84.7,53.3,89.3,53.7z M433.5,117.4 c0-16.9-12-30.6-28.5-30.6H98.4h-69C13.2,86.8,0,100,0,116.1v271.5C0,402.9,12.4,417,27.7,417h379.8c15.3,0,26-14.1,26-29.3v-74.8 V117.4L433.5,117.4z M213.563,143.084h3.471c18.326,0,31.727,13.401,31.727,31.727v35.199c0,1.453,2.986,2.502,4.925,2.502h34.229 c19.294,0,35.683,16.388,35.683,35.198v2.503c0,18.891-16.389,36.248-35.197,36.248h-34.23c-2.019,0-5.006-0.97-5.006,1.049v32.696 v2.503c0,18.325-13.4,33.261-31.727,33.261h-3.956c-18.81,0-33.745-15.42-33.745-34.229v-1.453v-32.695 c0-1.453-1.938-1.05-3.956-1.05h-35.199c-18.811,0-35.683-17.357-35.683-35.684v-2.502c0-19.375,17.841-36.249,37.702-36.249h32.695 c2.019,0,4.037-0.484,4.037-2.502v-33.746c0-19.375,14.854-33.261,34.23-33.261V143.084L213.563,143.084z"/></svg>',
    'import': '<svg viewBox="0 0 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M512,305.089c0-24.389-19.813-44.2-44.201-44.2c-24.388,0-44.2,19.813-44.2,44.2v120.954c0,0.313-0.26,0.572-0.571,0.572 H88.973c-0.312,0-0.572-0.261-0.572-0.572V305.089c0-24.389-19.813-44.2-44.201-44.2c-24.388,0-44.2,19.812-44.2,44.2v120.954 c0.052,49.037,39.937,88.974,88.973,88.974h334.053c49.036,0,88.974-39.885,88.974-88.974V305.089L512,305.089z M246.484,347.99 c17.264,17.264,45.241,17.264,62.504,0l99.166-99.167c8.632-8.632,12.947-19.969,12.947-31.252c0-11.284-4.315-22.621-12.947-31.253 c-17.266-17.265-45.24-17.265-62.505,0l-23.35,23.349v-55.59c0-17.42,6.864-33.852,19.345-46.332 c12.479-12.48,28.912-19.344,46.333-19.344h55.642c24.388,0,44.2-19.813,44.2-44.201c0-24.388-19.813-44.2-44.2-44.2h-55.693 c-20.695,0-40.872,4.107-59.903,12.168c-18.306,7.8-34.737,18.876-48.882,33.021c-14.145,14.144-25.22,30.576-33.021,48.881 c-8.06,19.084-12.168,39.208-12.168,59.957v56.266l-24.024-24.024c-17.264-17.265-45.241-17.265-62.505,0 c-17.264,17.264-17.264,45.24,0,62.505L246.484,347.99z"/></svg>',
    'export': '<svg viewBox="0 0 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M512,301.293c0-24.389-19.813-44.201-44.201-44.201c-24.388,0-44.2,19.813-44.2,44.201v120.954 c0,0.312-0.26,0.572-0.571,0.572H88.973c-0.312,0-0.572-0.262-0.572-0.572V301.293c0-24.389-19.813-44.201-44.201-44.201 c-24.388,0-44.2,19.813-44.2,44.201v120.954c0.052,49.037,39.937,88.974,88.973,88.974h334.053 c49.036,0,88.974-39.885,88.974-88.974V301.293L512,301.293z M379.45,12.948c-17.266-17.264-45.241-17.264-62.505,0 c-17.266,17.264-17.266,45.241,0,62.505l24.023,24.024h-56.266c-20.748,0-40.873,4.108-59.957,12.168 c-18.304,7.8-34.737,18.876-48.881,33.021c-14.144,14.145-25.22,30.577-33.021,48.881c-8.06,19.032-12.168,39.208-12.168,59.905 v55.692c0,24.389,19.812,44.201,44.201,44.201c24.388,0,44.201-19.813,44.201-44.201v-55.641c0-17.42,6.864-33.853,19.344-46.333 s28.912-19.344,46.332-19.344h55.59l-23.349,23.348c-17.265,17.265-17.265,45.241,0,62.505c8.632,8.633,19.969,12.948,31.253,12.948 c11.283,0,22.62-4.315,31.252-12.948l99.166-99.166c17.264-17.264,17.264-45.24,0-62.504L379.45,12.948z"/></svg>',
    'change': '<svg viewBox="0 -5 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M55.9,170.1l35.7-35.7c-5.7-20.7,1.5-46.2,20.3-65c14.1-14.1,32.5-22.1,50.5-22.1c4.2,0,9.2,0.5,14.5,1.8l32.5-32.5l3.3-3.3 C197.8,4.6,180.6,0,162.4,0c-30.5,0-61.1,13.1-84,36c-21.1,21.1-33.8,48.2-35.7,76.4c-1,14.2,0.8,27.8,5.2,40.7 C50.1,159,52.7,164.7,55.9,170.1z M185.1,482c6.2,6.2,14.4,9.3,22.5,9.3c8.1,0,16.3-3.1,22.5-9.3l143.8-143.8 c3.6-3.6,8.1-6.3,13-7.9l65.9-20.8c17.1-5.4,22.4-27.1,9.7-39.7l-10.1-10.1l-18.8-18.8L251.8,58.9l-20.2-20.2l-28.5,28.5l-93.2,93.2 l-33.6,33.6l-67,67c-12.4,12.4-12.4,32.6,0,45L185.1,482z M56.4,285.6h339.5c3.3,0,3.9,4.7,0.7,5.6l-33.8,8.6 c-1.4,0.4-2.6,1-3.7,2.1l-147.5,147c-3.1,3.1-8.1,3.1-11.3,0L50.7,299.2C45.7,294.2,49.3,285.6,56.4,285.6z M457.9,340.9 c-2.4-2.3-5.5-3.5-8.7-3.6c-4.8,0.2-9.5,2.8-11.8,8c-0.3,0.8-0.7,1.5-1,2.3c-8,18.6-16.7,36.8-24,55.6c-11.2,29.3-27.2,69.2-0.5,95 c10.3,10,23.8,14.2,37.2,13.6c13.4,0.6,27-3.6,37.2-13.6c26.7-25.9,10.8-65.8-0.5-95c-7.6-19.7-16.7-38.6-24.9-57.9 C460.2,343.6,459.2,342.1,457.9,340.9z"/></svg>',
    'color': '<svg viewBox="0 -28 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M256.262,0C114.751-0.157,0,114.542,0,256c0,141.406,114.594,256,256,256c0.053,0,0.105,0,0.158,0 c4.46,0,6.034-5.93,2.203-8.186c-9.812-5.824-19.151-12.487-27.704-20.41c-12.487-11.491-22.509-25.868-29.068-41.714 c-8.605-20.673-11.229-43.707-5.667-65.64c8.868-34.787,39.667-61.232,75.977-62.02c68.053-1.416,86.994,74.402,116.692,120.628 c3.096,4.827,6.349,9.497,9.969,13.957c0.053,0.053,0.053,0.105,0.105,0.105c5.823,7.188,16.423,8.027,23.401,2.046 C477.107,403.912,512,334.022,512,256C512,114.594,397.616,0.105,256.262,0z M89.094,345.982c-27.606,0-50-22.387-50-50 c0-27.615,22.394-50,50-50s50,22.385,50,50C139.094,323.596,116.7,345.982,89.094,345.982z M136.579,192.666 c-27.61,0-50-22.39-50-50c0-27.61,22.39-50,50-50c27.611,0,50,22.326,50,50C186.579,170.338,164.189,192.666,136.579,192.666z M294.775,146.02c-27.61,0-50-22.39-50-50c0-27.61,22.39-50,50-50c27.609,0,50,22.39,50,50 C344.775,123.63,322.384,146.02,294.775,146.02z M460.734,205.629c0,27.61-22.39,50-50.001,50c-27.61,0-49.999-22.327-49.999-50 c0-27.673,22.389-50,49.999-50C438.344,155.629,460.734,178.019,460.734,205.629z"/></svg>',
    'layer': '<svg viewBox="0 0 512 512" y="0px" x="0px" version="1.1" style="fill: #464646;"><path d="M504.887,314.293l-42.918,21.755l-190.704,96.666c-10.263,5.202-28.707,3.57-42.25-3.11L72.336,352.33l-59.944-29.564 c-12.181-6.009-16.826-14.955-7.309-19.778l18.635-9.445l48.618,23.979l156.679,77.274c13.543,6.681,31.987,8.312,42.25,3.11 l190.704-96.668l26.399-13.38l11.322,5.584C512.592,299.807,514.96,309.185,504.887,314.293z M499.691,363.368l-11.322-5.584 l-26.399,13.38l-190.704,96.667c-10.263,5.2-28.707,3.569-42.25-3.11L72.336,387.446l-48.618-23.979l-18.635,9.444 c-9.518,4.826-4.872,13.771,7.309,19.78l59.944,29.563l156.679,77.275c13.543,6.681,31.987,8.313,42.25,3.11l190.704-96.669 l42.918-21.753C514.96,379.111,512.592,369.731,499.691,363.368z M235.027,147.556v75.314c0,11.345,9.197,20.542,20.542,20.542 c11.343,0,20.542-9.197,20.542-20.542v-75.314c34.782-7.744,60.449-46.539,60.449-78.585C336.56,30.88,300.299,0,255.569,0 s-80.992,30.88-80.992,68.97C174.577,101.017,200.245,139.812,235.027,147.556z M12.392,253.04l59.944,29.564l156.679,77.273 c13.543,6.681,31.987,8.312,42.25,3.11l190.704-96.667l42.918-21.753c10.073-5.108,7.705-14.487-5.196-20.851l-153.578-75.746 l-33.22,34.563l-13.32,42.919c0,24.302-19.702,44.003-44.004,44.003c-24.304,0-44.004-19.701-44.004-44.003l-11.273-41.49 l-33.033-32.908L5.083,233.261C-4.434,238.085,0.211,247.03,12.392,253.04z"/></svg>'
  }
  window.plugin.drawlayerLauncher.palette = [
    ['#000000','#434343','#666666','#999999','#b7b7b7','#cccccc','#d9d9d9','#efefef','#f3f3f3','#ffffff'],
    ['#980000','#ff0000','#ff9900','#ffff00','#00ff00','#00ffff','#4a86e8','#0000ff','#9900ff','#ff00ff'],
    ['#e6b8af','#f4cccc','#fce5cd','#fff2cc','#d9ead3','#d0e0e3','#c9daf8','#cfe2f3','#d9d2e9','#ead1dc'],
    ['#dd7e6b','#ea9999','#f9cb9c','#ffe599','#b6d7a8','#a2c4c9','#a4c2f4','#9fc5e8','#b4a7d6','#d5a6bd'],
    ['#cc4125','#e06666','#f6b26b','#ffd966','#93c47d','#76a5af','#6d9eeb','#6fa8dc','#8e7cc3','#c27ba0'],
    ['#a61c00','#cc0000','#e69138','#f1c232','#6aa84f','#45818e','#3c78d8','#3d85c6','#674ea7','#a64d79'],
    ['#85200c','#990000','#b45f06','#bf9000','#38761d','#134f5c','#1155cc','#0b5394','#351c75','#741b47'],
    ['#5b0f00','#660000','#783f04','#7f6000','#274e13','#0c343d','#1c4587','#073763','#20124d','#4c1130']
  ];
  window.plugin.drawlayerLauncher.addControlButton();
  window.addHook('portalDetailsUpdated', window.plugin.drawlayerLauncher.portalDetailsUpdated );

  const title = (!isSmartphone()) ? "Drawlayer Launcher Setup" : "";
  $("#toolbox").append('<a onclick="window.plugin.drawlayerLauncher.sendDialog();return false;" title="'+ title +'">DLauncher</a>');
  $("#drawLauncher-number").on( 'click', function(){
    if(!window.plugin.drawTools){
      alert('DrawToolsプラグインを有効にして下さい！！');
      return;
    }
    if(!$("#drawLauncher-bar").hasClass("_onclick")){
      $("#drawLauncher-bar").addClass('_onclick');
      $(".drawlayerLauncher_drawIcon svg").css("fill", window.plugin.drawTools.currentColor);
      window.plugin.drawlayerLauncher.SortDrawtype();
    }else{
      $("#drawLauncher-bar").removeClass('_onclick');
      $(".drawlayerLauncher_activeDraw").removeClass("drawlayerLauncher_activeDraw");
    }
    window.plugin.drawlayerLauncher.setPalette_color();
  });
  $("._onclick-switch").on('click', function(){
    if(!$(this).parent().hasClass("_onclick")){
      $(this).parent().addClass("_onclick");
      window.plugin.drawlayerLauncher.SortDrawtype();
    }else{
      $(this).parent().removeClass("_onclick");
      $(".drawlayerLauncher_activeDraw").removeClass("drawlayerLauncher_activeDraw");
    }
  })
  $("#drawLauncher-bar-close").on('click', function(){
    $("#drawLauncher-bar").removeClass("_onclick");
  })
  const layers = window.plugin.drawlayerLauncher.loadDraw();
  if(layers.layersState){
    for(const l in layers.layersState){
      if(layers.layersState[l] && l !== "l0"){
        $('#drawLauncher-no .'+ l.replace("l","n") +' i').css("opacity",1);
      }
    }
    if(layers.layersState["l"+ layers.select]) $('#drawLauncher-layer-del').show();
  }
}//setup
////////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.portalDetailsUpdated = function(data) {
  const latlng = [data.portalData.latE6/1E6 ,data.portalData.lngE6/1E6 ];
  window.plugin.drawlayerLauncher.portalDetailsUpdated.latlng = latlng;
  $(".drawlayerLauncher_drawIcon svg").css("opacity", 1);
  if(window.plugin.drawlayerLauncher.portalDetailsUpdated.lastLatlng && $(".drawlayerLauncher_activeDraw").length){
    window.plugin.drawlayerLauncher.drawingPortal("line");
  }
}
////////////////////////////////////////////////////////////////////////////////
  window.plugin.drawlayerLauncher.changer = function(no) {
    const layers = window.plugin.drawlayerLauncher.loadDraw();
    $("#drawLauncher-number").html(no);
    if(!layers.data["n"+ no]){
      layers.data["n"+ no] = "";
    }
    layers.data["n"+ layers.select] = (localStorage['plugin-draw-tools-layer']) ? JSON.parse(localStorage['plugin-draw-tools-layer']) : [];
    layers.select = no;
    window.plugin.drawlayerLauncher.saveDraw();
    window.plugin.drawTools.drawnItems.clearLayers();
    window.plugin.drawTools.import(layers.data["n"+ no]);
    window.plugin.drawTools.save();
    $(".drawLauncher-select-hide > a").removeClass("_hide");
    $(".drawLauncher-select-hide > a.n"+ no ).addClass("_hide");
    window.plugin.drawlayerLauncher.SortDrawtype();

    window.plugin.drawlayerLauncher.setLayersStates();
  }
////////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.writeDraw = function (no) {
  const layers = window.plugin.drawlayerLauncher.loadDraw();
  const promptAction = confirm(layers.select +' のデータを '+ no +' のデータに上書きします', '');
  if(promptAction) {
    const drawData = (localStorage['plugin-draw-tools-layer']) ? JSON.parse(localStorage['plugin-draw-tools-layer']) : [];
      layers.data["n"+ no] = drawData;
    window.plugin.drawlayerLauncher.saveDraw();
  }
}
////////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.margeDraw = function (no) {
  const layers = window.plugin.drawlayerLauncher.loadDraw();
  const promptAction = confirm(layers.select +' のデータを '+ no +' のデータに追加して合成します', '');
  if(promptAction) {
    const drawData = (localStorage['plugin-draw-tools-layer']) ? JSON.parse(localStorage['plugin-draw-tools-layer']) : [];
    for(const a in drawData){
      layers.data["n"+ no].push(drawData[a]);
    }
    window.plugin.drawlayerLauncher.saveDraw();
  }
}
////////////////////////////////////////////////////////////////////////////////
  window.plugin.drawlayerLauncher.allDelete = function () {
    const layers = window.plugin.drawlayerLauncher.loadDraw();
    const promptAction = confirm(layers.select +' に登録されているデータを消去します', '');
    if(promptAction) {
      layers.data["n"+ layers.select] = "";
      window.plugin.drawlayerLauncher.saveDraw();
      localStorage['plugin-draw-tools-layer'] = JSON.stringify([]);
      window.plugin.drawTools.drawnItems.clearLayers();
      window.plugin.drawTools.load();
      runHooks('pluginDrawTools', {event: 'clear'});
      window.plugin.drawlayerLauncher.SortDrawtype();
    }
  }
///////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.drawingPortal = function (type) {
  const drawData = (localStorage['plugin-draw-tools-layer']) ? JSON.parse(localStorage['plugin-draw-tools-layer']) : [];
  if(!window.plugin.drawlayerLauncher.portalDetailsUpdated.latlng) return;
  const portalDetailsUpdated = window.plugin.drawlayerLauncher.portalDetailsUpdated;
  const latlng = portalDetailsUpdated.latlng;
  if(type === "maker"){
    let dd = 0;
    let count =0;
    const makerd = JSON.parse('{"type":"marker","latLng":{"lat":' + latlng[0] + ',"lng":'+ latlng[1] +'},"color":"' + window.plugin.drawTools.currentColor + '"}');
    for(const key of drawData){
      if(key.type === makerd.type &&
        JSON.stringify(key.latLng) === JSON.stringify(makerd.latLng) &&
        key.color === makerd.color){
          drawData.splice(count,1);
          dd = 1;
          break;
        }
        count++;
      }
      if(dd === 0) drawData.push(makerd);
    }else if(type === "line" && portalDetailsUpdated.lastLatlng){
      const lastLatlng = portalDetailsUpdated.lastLatlng;
      const makerd = JSON.parse('{"type":"polyline","latLngs":[{"lat":'
      + lastLatlng[0] + ',"lng":'+ lastLatlng[1] +'},{"lat":' + latlng[0] + ',"lng":'+ latlng[1] +'}],"color":"'
      + window.plugin.drawTools.currentColor + '"}');
      drawData.push(makerd);
      if($("#drawLauncher-drawLine").hasClass("drawlayerLauncher_activeDraw")){
        window.plugin.drawlayerLauncher.portalDetailsUpdated.lastLatlng = null;
        $("#drawLauncher-drawLine").removeClass("drawlayerLauncher_activeDraw");
      }
    }else{
      return;
    }
    window.plugin.drawTools.drawnItems.clearLayers();
    window.plugin.drawTools.import(drawData);
    window.plugin.drawTools.save();
    window.plugin.drawlayerLauncher.SortDrawtype();
  }
///////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.setlinePortal = function (ele) {
  if(!$(ele).hasClass("drawlayerLauncher_activeDraw")){
    if(!window.plugin.drawlayerLauncher.portalDetailsUpdated.latlng) return;
    const latlng = window.plugin.drawlayerLauncher.portalDetailsUpdated.latlng;
    window.plugin.drawlayerLauncher.portalDetailsUpdated['lastLatlng'] = latlng;
    $(".drawlayerLauncher_activeDraw").removeClass("drawlayerLauncher_activeDraw");
    $(ele).addClass("drawlayerLauncher_activeDraw");
  }else{
    $(ele).removeClass("drawlayerLauncher_activeDraw");
    window.plugin.drawlayerLauncher.portalDetailsUpdated.lastLatlng = null;
  }
}
////////////////////////////////////////////////////////////////////////////////
  window.plugin.drawlayerLauncher.loadDraw = function () {
    const layers = (localStorage['iitc-drawlayerLauncher-data']) ?
    JSON.parse(localStorage['iitc-drawlayerLauncher-data']) :
    JSON.stringify({
      "select": 1,
      "data":{ "n1": "","n2": "","n3": "", "n4": "", "n5": "","n6": "" }
    });
    window.plugin.drawlayerLauncher.layers = layers;
    return layers;
  }
////////////////////////////////////////////////////////////////////////////////
  window.plugin.drawlayerLauncher.saveDraw = function () {
    const layers = window.plugin.drawlayerLauncher.layers
    localStorage['iitc-drawlayerLauncher-data'] = JSON.stringify(layers);
  }
////////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.setPalette_change = function () {
let svg = "";
let colorSet = {
  flat: false,
  preferredFormat: "hex",
  showInput: true,
  showButtons: true,
  showPalette: true,
  showSelectionPalette: false,
  allowEmpty:true,
  chooseText: "適用",
  cancelText: "キャンセル",
  palette: window.plugin.drawlayerLauncher.palette,
  color: window.plugin.drawTools.currentColor,
  show: function(color) {
    const dataColor = $(this).attr('data-color');
    $(this).spectrum("set", dataColor)
    if(isSmartphone()){
      $(".sp-container.sp-light").css({"top": "0","left": "0"});
    }
  },
  change: function(color) {
    const dataType = $(this).attr('data-type');
    const dataColor = $(this).attr('data-color');
    window.plugin.drawlayerLauncher.changeDrawcolor(dataType, dataColor, color.toHexString());
  },
}
$('.drawLauncher-color-input').spectrum(colorSet);
}
////////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.removeLayersStates = function (n) {
  const layers = window.plugin.drawlayerLauncher.loadDraw();
  const no = (n !== undefined) ? 'l'+ n : 'l'+ layers.select;
  if(!layers.layersState) layers['layersState'] = {};
  layers.layersState[no] = false;
  window.plugin.drawlayerLauncher.saveDraw();
  if(n !== 0){
    window.plugin.drawlayerLauncher.loadLayersState(0);
    $('#drawLauncher-no .'+ no.replace("l","n") +' i').css("opacity",0);
  }
  $('#drawLauncher-layer-del').hide();
}
////////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.setLayersStates = function () {
  const layers = window.plugin.drawlayerLauncher.loadDraw();
  const lkey = 'l'+ layers.select;
  if((typeof layers.layersState === 'object') && layers.layersState.hasOwnProperty(lkey) && layers.layersState[lkey]){
    if(!layers.layersState['l0']) window.plugin.drawlayerLauncher.saveLayersStates(0);
    window.plugin.drawlayerLauncher.loadLayersState();
    $('#drawLauncher-layer-del').show();
  }else{
    window.plugin.drawlayerLauncher.loadLayersState(0);
    window.plugin.drawlayerLauncher.removeLayersStates(0);
  }
}
////////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.saveLayersStates = function (n) {
  const layers = window.plugin.drawlayerLauncher.loadDraw();
  const layersState = JSON.parse(localStorage['ingress.intelmap.layergroupdisplayed']);
  if(!layers.layersState) layers['layersState'] = {};
  const no = (n !== undefined) ? 'l'+ n : 'l'+ layers.select;
  layers.layersState[no] = layersState;
  window.plugin.drawlayerLauncher.saveDraw();
  if(n !== 0) $('#drawLauncher-no .'+ no.replace("l","n") +' i').css("opacity",1);
  $('#drawLauncher-layer-del').show();
}
////////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.loadLayersState = function (n) {
  const layers = window.plugin.drawlayerLauncher.loadDraw();
  const no = (n !== undefined) ? 'l'+ n : 'l'+ layers.select;
  if(!layers.layersState || !layers.layersState[no]) return;
  const layersState = layers.layersState[no];
  for (i in window.layerChooser._layers) {
    const layer = window.layerChooser._layers[i];
    if (!window.map.hasLayer(layer.layer) && layersState[layer.name] === true) {
      window.map.addLayer(layer.layer);
    }else if(window.map.hasLayer(layer.layer) && layersState[layer.name] === false) {
      window.map.removeLayer(layer.layer);
    }
  }
}
////////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.setPalette_color = function () {
  let colorSet = {
    flat: false,
    preferredFormat: "hex",
    showInput: true,
    showButtons: true,
    showPalette: true,
    showSelectionPalette: false,
    allowEmpty:true,
    chooseText: "適用",
    cancelText: "キャンセル",
    palette: window.plugin.drawlayerLauncher.palette,
    color: window.plugin.drawTools.currentColor,
    change: function(color) {
      window.plugin.drawTools.setDrawColor(color.toHexString());
      $(".drawlayerLauncher_drawIcon svg").css('fill',window.plugin.drawTools.currentColor);
    },
  }
  $('#drawLauncher-color').spectrum(colorSet);
}
///////////////////////////////////////////////////////////////////////////////
window.plugin.drawlayerLauncher.SortDrawtype = function () {
  const svg = window.plugin.drawlayerLauncher.svg;
  const drawData = (localStorage['plugin-draw-tools-layer']) ? JSON.parse(localStorage['plugin-draw-tools-layer']) : [];
  let eraser = '<a class="drawLauncher-span-hide remove-type" onclick="window.plugin.drawlayerLauncher.allDelete();return false;">ALL</a>';
  let change = '';
  const list = {};
  for(const key of drawData){
    if(!list[key.type]){
      list[key.type] = [];
      list[key.type].push(key.color);
    }else{
      if(list[key.type].indexOf(key.color) === -1){
        list[key.type].push(key.color);
      }
    }
  }
  for(const key of Object.keys(list)){
    for(const i of list[key]){
      eraser += '<a class="drawLauncher-span-hide remove-type" onclick="window.plugin.drawlayerLauncher.delDrawtype(\''+ key +'\' ,\''+ i + '\');return false;">'+ svg[key].replace(/fill: #[0-9A-F]{3,6}/i, 'fill: '+ i) +'</a>';

      change += '<a class="drawLauncher-span-hide remove-type input-palet">'+ svg[key].replace(/fill: #[0-9A-F]{3,6}/i, 'fill: '+ i) +'<input type="color" name="drawLauncher-color" data-type="'+ key +'" data-color="'+ i +'" class="drawLauncher-color-input" /></a>';
    }
  }
  $("#drawLauncher-dele > a.remove-type").remove();
  $("#drawLauncher-dele").append(eraser);
  $("#drawLauncher-change > a.remove-type").remove();
  $("#drawLauncher-change").append(change);
  window.plugin.drawlayerLauncher.setPalette_change();
}
////////////////////////////////////////////////////////////////////////////////
  window.plugin.drawlayerLauncher.changeDrawcolor = function (type,color,attcolor) {
    const drawData = (localStorage['plugin-draw-tools-layer']) ? JSON.parse(localStorage['plugin-draw-tools-layer']) : [];
    const change = [];
    $.each(drawData, function(i, ele){
      if(ele.type === type && ele.color === color){
        ele.color = attcolor;
        change.push(ele);
      }else{
        change.push(ele);
      }
    });
    window.plugin.drawTools.drawnItems.clearLayers();
    window.plugin.drawTools.import(change);
    window.plugin.drawTools.save();
    window.plugin.drawlayerLauncher.SortDrawtype();
  }
////////////////////////////////////////////////////////////////////////////////
  window.plugin.drawlayerLauncher.delDrawtype = function (type,color) {
    const drawData = (localStorage['plugin-draw-tools-layer']) ? JSON.parse(localStorage['plugin-draw-tools-layer']) : [];
    const delmaker = [];
    $.each(drawData, function(i, ele){
      if(ele.type !== type || ele.color !== color){
        delmaker.push(ele);
      }
    });
    window.plugin.drawTools.drawnItems.clearLayers();
    window.plugin.drawTools.import(delmaker);
    window.plugin.drawTools.save();
    window.plugin.drawlayerLauncher.SortDrawtype();
  }
  /////////////////////////////////////////////////////////////////////////////
  window.plugin.drawlayerLauncher.sendDialog = function() {
    const layers = window.plugin.drawlayerLauncher.loadDraw();
    //Object.keys(layers.data).length;

    let html = '<div class="">'
    + '<div style="margin-bottom: 8px; user-select: none; -moz-user-select: none;">List quantity : <b id="drawlayerLauncher_quantity" style="font-size: 1.1em; margin-right: 5px;">'
    + Object.keys(layers.data).length +'</b>'
    + ' <a onclick="window.plugin.drawlayerLauncher.layerdataControl(1);" style="margin-left: -1px;"><svg viewBox="0 0 20 20" style="width: 15px; height: 15px;"><polygon points="1,18 10,3 19,18" fill="rgb(250, 200, 0)"/></svg> 増やす</a>'
    + ' <a onclick="window.plugin.drawlayerLauncher.layerdataControl(0);" style="margin-left: -1px;"><svg viewBox="0 0 20 20" style="width: 15px; height: 15px;"><polygon points="1,5 10,19 19,5" fill="rgb(250, 200, 0)"/></svg> 減らす</a></div>'
    + '<div style="margin-bottom: 5px;">※ 4 ~ 20 まで<br>※削除する番号に入っているデータは消滅します</div>'
    + '<div><input class="drawlayerLauncher-checkbox" name="forcedtoTOP" id="drawlayerLauncher-totop" type="checkbox" />ボタンを一番上に移動する（リロード後に反映）</div>'
    + '<div><input class="drawlayerLauncher-checkbox" name="shortcut_snap" id="drawlayerLauncher-snap" type="checkbox" />Snap to Portal のショートカットを追加</div>'
    + '<div><input class="drawlayerLauncher-checkbox" name="shortcut_layer" id="drawlayerLauncher-layer" type="checkbox" />IITC Layer設定記憶のショートカットを追加</div>'
    + '<div><input class="drawlayerLauncher-checkbox" name="text_vertical" id="drawlayerLauncher-vertical" type="checkbox" />数字を縦方向に伸ばす</div>'
    + '</div>'
    dialog({
      html: html,
      id: 'dialog-drawlayer-Launcher',
      dialogClass: 'ui-dialog-drawlayer-Launcher',
      title: 'Drawlayer Launcher Setup'
    });
    if(layers.text_vertical) $("#drawlayerLauncher-vertical").prop('checked',true);
    if(layers.shortcut_snap) $("#drawlayerLauncher-snap").prop('checked',true);
    if(layers.shortcut_layer) $("#drawlayerLauncher-layer").prop('checked',true);
    if(layers.forcedtoTOP) $("#drawlayerLauncher-totop").prop('checked',true);
    $("input.drawlayerLauncher-checkbox").click(function() {
      const id = $(this).attr("name");
      if(this.checked) {
        layers[id] = true;
        if(id === "text_vertical") $("#drawLauncher-no").addClass("style_vertical");
        if(id === "shortcut_snap") $("#drawLauncher-snap").removeClass("_hide");
        if(id === "shortcut_layer") $("#drawLauncher-layer").removeClass("_hide");
      } else {
        layers[id] = false;
        if(id === "text_vertical") $("#drawLauncher-no").removeClass("style_vertical");
        if(id === "shortcut_snap") $("#drawLauncher-snap").addClass("_hide");
        if(id === "shortcut_layer") $("#drawLauncher-layer").addClass("_hide");
      }
      window.plugin.drawlayerLauncher.saveDraw();

    });
  }
    /////////////////////////////////////////////////////////////////////////////
    window.plugin.drawlayerLauncher.layerdataControl = function(c) {
      const layers = window.plugin.drawlayerLauncher.loadDraw();
      const keys = [];
      for(const key of Object.keys(layers.data)){
        keys.push(key.replace("n", ""));
      }
      keys.sort(function(a,b){return a - b;});
      let no = keys[keys.length - 1];
      if(c === 1 && keys.length < 20){
        no++;
        layers.data["n"+ no] = "";
        window.plugin.drawlayerLauncher.saveDraw();
        $("#drawLauncher-no > a:last").before('<a onclick="window.plugin.drawlayerLauncher.changer(\''+ no +'\');return false;">'+ no +'</a>');
        $("#drawLauncher-mix").append('<a class="n'+ no +' drawLauncher-span-hide" onclick="window.plugin.drawlayerLauncher.margeDraw('+ no +');return false;">+ '+ no +'</a>');
        $("#drawLauncher-write").append('<a class="n'+ no +' drawLauncher-span-hide" onclick="window.plugin.drawlayerLauncher.writeDraw('+ no +');return false;">>> '+ no +'</a>');
      }else if(c === 0 && keys.length > 4){
        if(layers.select == no){
          alert("開いている番号は削除できません")
        }else{
          delete layers.data["n"+ no];
          window.plugin.drawlayerLauncher.saveDraw();
          $("#drawLauncher-no > a:eq(-2)").remove();
          $("#drawLauncher-mix > a:last").remove();
          $("#drawLauncher-write > a:last").remove();
        }
      }
    $("#drawlayerLauncher_quantity").html(Object.keys(layers.data).length);
    }
///////////////////////////////////////////////////////////////////////////////
  window.plugin.drawlayerLauncher.addControlButton = function() {
    const layers = window.plugin.drawlayerLauncher.loadDraw();
    const svg = window.plugin.drawlayerLauncher.svg;
    window.plugin.drawlayerLauncher.viewMembersBtn = L.Control.extend({
      options:{
        position: 'topleft'
      },
      onAdd: function (map) {
        const keys = [];
        for(const key of Object.keys(layers.data)){
          keys.push(key.replace("n", ""));
        }
        keys.sort(function(a,b){return a - b;});
        let noList = "";
        let writeList = "";
        let mixList = "";
        let titleList = ["選択して消去","選択した番号にコピー","選択した番号のデータに合成","Import Draw Data","Export Draw Data","選択中のポータルにmakerを打つ","選択中のポータルから次に選択したポータルにlineを引く","選択中のポータルを中心に連続でlineを引く","Change&nbsp;Draw&nbsp;Color","Snap&nbsp;to&nbsp;Portals", "タイプ別に色変更","IITCレイヤー設定を記憶","レイヤー設定を消去"]
        let style_vertical = (layers.text_vertical) ? ' style_vertical' : "";
        const snap = (!layers.shortcut_snap) ? ' _hide' : "";
        const laye = (!layers.shortcut_layer) ? ' _hide' : "";
        for(const key of keys) {
          const hide = (key == layers.select) ? " _hide" : "";
          noList += '<a class="n'+ key + hide +'" onclick="window.plugin.drawlayerLauncher.changer('+ key +');return false;">'+ key +'<i>.</i></a>';
          writeList += '<a class="n'+ key +' drawLauncher-span-hide'+ hide +'" onclick="window.plugin.drawlayerLauncher.writeDraw('+ key +');return false;">> '+ key +'</a>';
          mixList += '<a class="n'+ key +' drawLauncher-span-hide'+ hide +'" onclick="window.plugin.drawlayerLauncher.margeDraw('+ key +');return false;">+ '+ key +'</a>';
        }
        let smartphon = "";
        if(isSmartphone()){
          titleList = ["","","","","","","","","","",""];
          smartphon = '#drawLauncher-anker #drawLauncher-set {left: 31px; top: -30px;} #drawLauncher-anker #drawLauncher-no {top: -30px; left: 62px;}'
            + '.style_vertical #drawLauncher-bar-close {bottom: -22px; left: 8px;}';
        }
        const container = L.DomUtil.create('div', 'leaflet-drawLauncher');

        $(container).append('<div class="leaflet-bar" id="drawLauncher-bar">'
        + '<a id="drawLauncher-number">'+ layers.select +'</a><b id="drawLauncher-anker">'
        + '<span id="drawLauncher-set" class="text-small">'
        + '<a class="_onclick-switch"><i id="menu_icon">　</i></a>'
        + '<span id="drawLauncher-dele" class="drawLauncher-delete drawLauncher-set-hide last-radius">'
        + '<a class="margehide _onclick-switch" title='+ titleList[0] +'>'+ svg.eraser +'</a>'
        + '</span>'
        + '<span id="drawLauncher-write" class="drawLauncher-select-hide drawLauncher-set-hide last-radius">'
        + '<a class="_onclick-switch" title='+ titleList[1] +'>'+ svg.copy +'</a>'
        + writeList
        + '</span>'
        + '<span id="drawLauncher-mix" class="drawLauncher-select-hide drawLauncher-set-hide last-radius">'
        + '<a class="_onclick-switch" title='+ titleList[2] +'>'+ svg.mix +'</a>'
        + mixList
        + '</span>'
        + '<a class="drawLauncher-set-hide" onclick="window.plugin.drawTools.optPaste();return false;" title='+ titleList[3] +'>'+ svg.import +'</a>'
        + '<a class="drawLauncher-set-hide" onclick="window.plugin.drawTools.optCopy();return false;" title='+ titleList[4] +'>'+ svg.export +'</a>'
        +'<span id="drawLauncher-layer" class="drawLauncher-select-hide drawLauncher-set-hide '+ laye +' last-radius">'
        + '<a onclick="window.plugin.drawlayerLauncher.saveLayersStates();return false;" title='
        + titleList[11] +'>'+ svg.layer + '</a>'
        + '<a id="drawLauncher-layer-del" onclick="window.plugin.drawlayerLauncher.removeLayersStates(); return false;" title='+ titleList[12] +'>Del</a>'
        + '</span>'
        + '<a class="drawLauncher-set-hide drawlayerLauncher_drawIcon" onclick="window.plugin.drawlayerLauncher.drawingPortal(\'maker\'); return false;" title='+ titleList[5] +'>'+ svg.marker + '</a>'
        + '<a class="drawLauncher-set-hide drawlayerLauncher_drawIcon" id="drawLauncher-drawLine" onclick="window.plugin.drawlayerLauncher.setlinePortal(this); return false;" title='+ titleList[6] +'>'+ svg.polyline +'</a>'
        + '<a class="drawLauncher-set-hide drawlayerLauncher_drawIcon" id="drawLauncher-multiLine" onclick="window.plugin.drawlayerLauncher.setlinePortal(this); return false;" title='+ titleList[7] +'>'+ svg.multiline +'</a>'
        + '<a id="drawLauncher-snap" class="drawLauncher-set-hide'+ snap +'" onclick="window.plugin.drawTools.snapToPortals();return false;" title='+ titleList[9] +'>Snap</a>'

        + '<span id="drawLauncher-change" class="drawLauncher-delete drawLauncher-set-hide last-radius">'
        + '<a class="margehide _onclick-switch" title='+ titleList[10] +'>'+ svg.change +'</a>'
        + '</span>'

        + '<span class="drawLauncher-set-hide input-palet" ><a id="drawLauncher_color" class="drawlayerLauncher_drawIcon" title='+ titleList[8] +'>'+ svg.color
        + '<input type="color" name="drawLauncher-color" id="drawLauncher-color" /></a></span>'
        + '</span>'

        + '<span id="drawLauncher-no" class="drawLauncher-select-hide'+ style_vertical +'">'
        + noList
        + '<a id="drawLauncher-bar-close"><svg viewBox="0 0 20 20" style="width: 12px; height: 12px; margin: 0 0 -1px 0;"><polygon points="3,11 16,20 16,2" fill="#fff"/></svg></a>'
        + '</span></b></div>');

        $('head').append('<style>'
        + 'a#margeid.margehide {border-top-right-radius: 4px; border-bottom-right-radius: 4px; border-right: 1px solid rgba(0, 0, 0, 0.2);}'
        + '#drawLauncher-bar {font-size: 14px; font-weight: 900;}'
        + '#drawLauncher-bar a {color: #444;}'
        + '#drawLauncher-bar svg {margin: 6px auto -5px; height: 16px; width: 16px;}'
        + '#drawLauncher-number { border-radius: 4px;}'
        + '#drawLauncher-anker {display: block; position: relative;}'
        + '#drawLauncher-no,#drawLauncher-set {display: none;}'
        + '#drawLauncher-layer #drawLauncher-layer-del {display: none;}'
        + '#drawLauncher-no i {font-size: 15px; color: #f00; position: relative; bottom: -5px; right: -5px; opacity: 0;}'
        + '#drawLauncher-bar._onclick #drawLauncher-no {display: inline-flex;}'
        + '#drawLauncher-bar._onclick #drawLauncher-no.style_vertical {display: block;}'
        + '#drawLauncher-bar._onclick #drawLauncher-set {display: block;}'
        + '#drawLauncher-set {border-radius: 0; left: 27px; position: absolute; top: -27px;width: 27px;}'
        + '#drawLauncher-set a {border-bottom: 1px solid #ccc;}'
        + '#drawLauncher-no {border-radius: 0;left: 54px; position: absolute; top: -27px; z-index: 100;}'
        + '#drawLauncher-no a, #drawLauncher-set a{border-radius: 0; display: inline-block; border-left: 1px solid #eee;}'
        + '#drawLauncher-set .last-radius a:last-child {border-top-right-radius: 4px; border-bottom-right-radius: 4px;}'
        + '#drawLauncher-no a:last-child {border-bottom: medium none; border-top-right-radius: 4px; border-bottom-right-radius: 4px;}'
        + 'a:last-child#drawLauncher_color {border-top-right-radius: 0; border-bottom-left-radius: 4px; border-bottom-right-radius: 4px;}'
        + '#drawLauncher-bar-close {background-color: #666; width: 15px;}'
        + '.style_vertical #drawLauncher-bar-close {bottom: -20px; left: 5px; position: absolute; transform: rotate(90deg);}'
        + '.text-small {font-size: 10px; font-weight: normal;}'
        + '.drawLauncher-delete {display: inline-flex;}'
        + '#drawLauncher-dele, #drawLauncher-change, #drawLauncher-write, #drawLauncher-mix, .input-palet {position: relative; z-index: 101;}'
        + '#menu_icon, #menu_icon::after, #menu_icon::before {background-color: #444; display: block; height: 2px; width: 12px;}'
        + '#menu_icon {position: relative; left: 7px; top: 12px;}'
        + '#menu_icon::after {top: 0; content: ""; margin: 5px auto auto; position: absolute;}'
        + '#menu_icon::before {bottom: 0; content: ""; margin: auto auto 5px; position: absolute;}'
        + '#drawLauncher-set .drawLauncher-set-hide {display: none;}'
        + '#drawLauncher-set._onclick a.drawLauncher-set-hide {display: inline-block;}'
        + '#drawLauncher-set._onclick span.drawLauncher-set-hide {display: inline-flex;}'
        + '#drawLauncher-set .drawLauncher-span-hide {display: none;} '
        + '#drawLauncher-set #drawLauncher-snap._hide {display: none;}'
        + '#drawLauncher-set #drawLauncher-layer._hide {display: none;}'
        + '#drawLauncher-set ._onclick .drawLauncher-span-hide {display: inline-block} '
        + '#drawLauncher-set ._onclick .drawLauncher-span-hide._hide {display: none;}'
        + '#drawLauncher-no a._hide {background-color: #ddd;}'
        + '#drawLauncher-anker .drawlayerLauncher_activeDraw {background-color: #eee; border: solid 1px #aaa;}'
        + '.drawlayerLauncher_drawIcon svg {opacity: 0.4;}'
        + '.drawlayerLauncher_drawIcon#drawLauncher_color svg {opacity: 1;}'
        + '.input-palet .sp-replacer {opacity: 0; padding: 0; margin: 0; height:27px; width: 27px; display: block; position: absolute; top: 0; left: 0;}'
        + '.sp-picker-container input[type="text"] {color: #000;}'
        + smartphon
        + '</style>');
        return container;

      }
    });
    map.addControl(new window.plugin.drawlayerLauncher.viewMembersBtn);
    if(layers.forcedtoTOP){
      $(".leaflet-drawLauncher").prependTo($("div.leaflet-control-container div.leaflet-top.leaflet-left"));
    }
//    window.plugin.drawlayerLauncher.setPalette_color();
  }

  var setup = window.plugin.drawlayerLauncher.setup;


// PLUGIN END //////////////////////////////////////////////////////////

  setup.info = plugin_info;
  // add the script info data to the function as a property
  if (!window.bootPlugins) window.bootPlugins = [
  ];
  window.bootPlugins.push(setup);
  // if IITC has already booted, immediately run the 'setup' function
  if (window.iitcLoaded && typeof setup === 'function') setup();
}
// wrapper end
// inject code into site context

var script = document.createElement('script');
var info = {
};
if (typeof GM_info !== 'undefined' && GM_info && GM_info.script) info.script = {
  version: GM_info.script.version,
  name: GM_info.script.name,
  description: GM_info.script.description
};
script.appendChild(document.createTextNode('(' + wrapper + ')(' + JSON.stringify(info) + ');'));
(document.body || document.head || document.documentElement) .appendChild(script);
