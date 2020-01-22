---
title: House Price Prediction"
collection: projects
type: "Projects"
permalink: /projects/house_pice_prediction
date: 2020-01-19
year: 2020
location: "Jinan, China"
image: "/images/kaggle1.png"
language: "Jupyter Notebook"
tool: "/images/jupyter.png"
---

This is the practice for machine learning and for **Kaggle competition**: [House Prices: Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques).<br>Using Ridge, Lasso, LGBM, XGB, and Stacking CV Regressor, etc, to reach Score: 11977.59807; ***13<sup>th</sup> place*** out of 19,465 teams***(0.06%)*** For more information, please visit my [Github Repository](https://github.com/zcczhang/House_Price_Prediction_Model) or download the [HTML file](https://github.com/zcczhang/House_Price_Prediction_Model/blob/master/house_price_prediction_v2.html).




<br>

![](https://raw.githubusercontent.com/zcczhang/House_Price_Prediction_Model/master/output/rank.png)

<br>

[version 1:]() 
Simple Prediction(with ridge regression, random forest, bagging, XGBoost) [View PDF](https://zcczhang.github.io/files/House_Price_Prediction_v1.pdf)
<br>
[version 2:](https://github.com/zcczhang/House_Price_Prediction_Model/blob/master/house_price_prediction_v2.ipynb) Score(root mean squared logarithmic error): 0.10643; ***Rank: top 2%***. score: 0.10643;  
<br>
version3: Score(mean absolute error): 11977.59807; ***Rank: 13 out of 19,465 teams(0.06%)***





<head><meta charset="utf-8" />
<title>A Detailed Regression Guide with House-pricing (1)</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>

<style type="text/css">
    /*!
*
* Twitter Bootstrap
*
*/
/*!
 * Bootstrap v3.3.7 (http://getbootstrap.com)
 * Copyright 2011-2016 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */
/*! normalize.css v3.0.3 | MIT License | github.com/necolas/normalize.css */
html {
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
article,
aside,
details,
figcaption,
figure,

header,
hgroup,
main,
menu,
nav,
section,
summary {
  display: block;
}
audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline;
}
audio:not([controls]) {
  display: none;
  height: 0;
}
[hidden],
template {
  display: none;
}
a {
  background-color: transparent;
}
a:active,
a:hover {
  outline: 0;
}
abbr[title] {
  border-bottom: 1px dotted;
}
b,
strong {
  font-weight: bold;
}
dfn {
  font-style: italic;
}
h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
mark {
  background: #ff0;
  color: #000;
}
small {
  font-size: 80%;
}
sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}
sup {
  top: -0.5em;
}
sub {
  bottom: -0.25em;
}
img {
  border: 0;
}
svg:not(:root) {
  overflow: hidden;
}
figure {
  margin: 1em 40px;
}
hr {
  box-sizing: content-box;
  height: 0;
}
pre {
  overflow: auto;
}
code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em;
}
button,
input,
optgroup,
select,
textarea {
  color: inherit;
  font: inherit;
  margin: 0;
}
button {
  overflow: visible;
}
button,
select {
  text-transform: none;
}
button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer;
}
button[disabled],
html input[disabled] {
  cursor: default;
}
button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}
input {
  line-height: normal;
}
input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: textfield;
  box-sizing: content-box;
}
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
fieldset {
  border: 1px solid #c0c0c0;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em;
}
legend {
  border: 0;
  padding: 0;
}
textarea {
  overflow: auto;
}
optgroup {
  font-weight: bold;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
td,
th {
  padding: 0;
}
/*! Source: https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css */
@media print {
  *,
  *:before,
  *:after {
    background: transparent !important;
    color: #000 !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }
  a,
  a:visited {
    text-decoration: underline;
  }
  a[href]:after {
    content: " (" attr(href) ")";
  }
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  a[href^="#"]:after,
  a[href^="javascript:"]:after {
    content: "";
  }
  pre,
  blockquote {
    border: 1px solid #999;
    page-break-inside: avoid;
  }
  thead {
    display: table-header-group;
  }
  tr,
  img {
    page-break-inside: avoid;
  }
  img {
    max-width: 100% !important;
  }
  p,
  h2,
  h3 {
    orphans: 3;
    widows: 3;
  }
  h2,
  h3 {
    page-break-after: avoid;
  }
  .navbar {
    display: none;
  }
  .btn > .caret,
  .dropup > .btn > .caret {
    border-top-color: #000 !important;
  }
  .label {
    border: 1px solid #000;
  }
  .table {
    border-collapse: collapse !important;
  }
  .table td,
  .table th {
    background-color: #fff !important;
  }
  .table-bordered th,
  .table-bordered td {
    border: 1px solid #ddd !important;
  }
}
@font-face {
  font-family: 'Glyphicons Halflings';
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot');
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot?#iefix') format('embedded-opentype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff2') format('woff2'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff') format('woff'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.ttf') format('truetype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular') format('svg');
}
.glyphicon {
  position: relative;
  top: 1px;
  display: inline-block;
  font-family: 'Glyphicons Halflings';
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.glyphicon-asterisk:before {
  content: "\002a";
}
.glyphicon-plus:before {
  content: "\002b";
}
.glyphicon-euro:before,
.glyphicon-eur:before {
  content: "\20ac";
}
.glyphicon-minus:before {
  content: "\2212";
}
.glyphicon-cloud:before {
  content: "\2601";
}
.glyphicon-envelope:before {
  content: "\2709";
}
.glyphicon-pencil:before {
  content: "\270f";
}
.glyphicon-glass:before {
  content: "\e001";
}
.glyphicon-music:before {
  content: "\e002";
}
.glyphicon-search:before {
  content: "\e003";
}
.glyphicon-heart:before {
  content: "\e005";
}
.glyphicon-star:before {
  content: "\e006";
}
.glyphicon-star-empty:before {
  content: "\e007";
}
.glyphicon-user:before {
  content: "\e008";
}
.glyphicon-film:before {
  content: "\e009";
}
.glyphicon-th-large:before {
  content: "\e010";
}
.glyphicon-th:before {
  content: "\e011";
}
.glyphicon-th-list:before {
  content: "\e012";
}
.glyphicon-ok:before {
  content: "\e013";
}
.glyphicon-remove:before {
  content: "\e014";
}
.glyphicon-zoom-in:before {
  content: "\e015";
}
.glyphicon-zoom-out:before {
  content: "\e016";
}
.glyphicon-off:before {
  content: "\e017";
}
.glyphicon-signal:before {
  content: "\e018";
}
.glyphicon-cog:before {
  content: "\e019";
}
.glyphicon-trash:before {
  content: "\e020";
}
.glyphicon-home:before {
  content: "\e021";
}
.glyphicon-file:before {
  content: "\e022";
}
.glyphicon-time:before {
  content: "\e023";
}
.glyphicon-road:before {
  content: "\e024";
}
.glyphicon-download-alt:before {
  content: "\e025";
}
.glyphicon-download:before {
  content: "\e026";
}
.glyphicon-upload:before {
  content: "\e027";
}
.glyphicon-inbox:before {
  content: "\e028";
}
.glyphicon-play-circle:before {
  content: "\e029";
}
.glyphicon-repeat:before {
  content: "\e030";
}
.glyphicon-refresh:before {
  content: "\e031";
}
.glyphicon-list-alt:before {
  content: "\e032";
}
.glyphicon-lock:before {
  content: "\e033";
}
.glyphicon-flag:before {
  content: "\e034";
}
.glyphicon-headphones:before {
  content: "\e035";
}
.glyphicon-volume-off:before {
  content: "\e036";
}
.glyphicon-volume-down:before {
  content: "\e037";
}
.glyphicon-volume-up:before {
  content: "\e038";
}
.glyphicon-qrcode:before {
  content: "\e039";
}
.glyphicon-barcode:before {
  content: "\e040";
}
.glyphicon-tag:before {
  content: "\e041";
}
.glyphicon-tags:before {
  content: "\e042";
}
.glyphicon-book:before {
  content: "\e043";
}
.glyphicon-bookmark:before {
  content: "\e044";
}
.glyphicon-print:before {
  content: "\e045";
}
.glyphicon-camera:before {
  content: "\e046";
}
.glyphicon-font:before {
  content: "\e047";
}
.glyphicon-bold:before {
  content: "\e048";
}
.glyphicon-italic:before {
  content: "\e049";
}
.glyphicon-text-height:before {
  content: "\e050";
}
.glyphicon-text-width:before {
  content: "\e051";
}
.glyphicon-align-left:before {
  content: "\e052";
}
.glyphicon-align-center:before {
  content: "\e053";
}
.glyphicon-align-right:before {
  content: "\e054";
}
.glyphicon-align-justify:before {
  content: "\e055";
}
.glyphicon-list:before {
  content: "\e056";
}
.glyphicon-indent-left:before {
  content: "\e057";
}
.glyphicon-indent-right:before {
  content: "\e058";
}
.glyphicon-facetime-video:before {
  content: "\e059";
}
.glyphicon-picture:before {
  content: "\e060";
}
.glyphicon-map-marker:before {
  content: "\e062";
}
.glyphicon-adjust:before {
  content: "\e063";
}
.glyphicon-tint:before {
  content: "\e064";
}
.glyphicon-edit:before {
  content: "\e065";
}
.glyphicon-share:before {
  content: "\e066";
}
.glyphicon-check:before {
  content: "\e067";
}
.glyphicon-move:before {
  content: "\e068";
}
.glyphicon-step-backward:before {
  content: "\e069";
}
.glyphicon-fast-backward:before {
  content: "\e070";
}
.glyphicon-backward:before {
  content: "\e071";
}
.glyphicon-play:before {
  content: "\e072";
}
.glyphicon-pause:before {
  content: "\e073";
}
.glyphicon-stop:before {
  content: "\e074";
}
.glyphicon-forward:before {
  content: "\e075";
}
.glyphicon-fast-forward:before {
  content: "\e076";
}
.glyphicon-step-forward:before {
  content: "\e077";
}
.glyphicon-eject:before {
  content: "\e078";
}
.glyphicon-chevron-left:before {
  content: "\e079";
}
.glyphicon-chevron-right:before {
  content: "\e080";
}
.glyphicon-plus-sign:before {
  content: "\e081";
}
.glyphicon-minus-sign:before {
  content: "\e082";
}
.glyphicon-remove-sign:before {
  content: "\e083";
}
.glyphicon-ok-sign:before {
  content: "\e084";
}
.glyphicon-question-sign:before {
  content: "\e085";
}
.glyphicon-info-sign:before {
  content: "\e086";
}
.glyphicon-screenshot:before {
  content: "\e087";
}
.glyphicon-remove-circle:before {
  content: "\e088";
}
.glyphicon-ok-circle:before {
  content: "\e089";
}
.glyphicon-ban-circle:before {
  content: "\e090";
}
.glyphicon-arrow-left:before {
  content: "\e091";
}
.glyphicon-arrow-right:before {
  content: "\e092";
}
.glyphicon-arrow-up:before {
  content: "\e093";
}
.glyphicon-arrow-down:before {
  content: "\e094";
}
.glyphicon-share-alt:before {
  content: "\e095";
}
.glyphicon-resize-full:before {
  content: "\e096";
}
.glyphicon-resize-small:before {
  content: "\e097";
}
.glyphicon-exclamation-sign:before {
  content: "\e101";
}
.glyphicon-gift:before {
  content: "\e102";
}
.glyphicon-leaf:before {
  content: "\e103";
}
.glyphicon-fire:before {
  content: "\e104";
}
.glyphicon-eye-open:before {
  content: "\e105";
}
.glyphicon-eye-close:before {
  content: "\e106";
}
.glyphicon-warning-sign:before {
  content: "\e107";
}
.glyphicon-plane:before {
  content: "\e108";
}
.glyphicon-calendar:before {
  content: "\e109";
}
.glyphicon-random:before {
  content: "\e110";
}
.glyphicon-comment:before {
  content: "\e111";
}
.glyphicon-magnet:before {
  content: "\e112";
}
.glyphicon-chevron-up:before {
  content: "\e113";
}
.glyphicon-chevron-down:before {
  content: "\e114";
}
.glyphicon-retweet:before {
  content: "\e115";
}
.glyphicon-shopping-cart:before {
  content: "\e116";
}
.glyphicon-folder-close:before {
  content: "\e117";
}
.glyphicon-folder-open:before {
  content: "\e118";
}
.glyphicon-resize-vertical:before {
  content: "\e119";
}
.glyphicon-resize-horizontal:before {
  content: "\e120";
}
.glyphicon-hdd:before {
  content: "\e121";
}
.glyphicon-bullhorn:before {
  content: "\e122";
}
.glyphicon-bell:before {
  content: "\e123";
}
.glyphicon-certificate:before {
  content: "\e124";
}
.glyphicon-thumbs-up:before {
  content: "\e125";
}
.glyphicon-thumbs-down:before {
  content: "\e126";
}
.glyphicon-hand-right:before {
  content: "\e127";
}
.glyphicon-hand-left:before {
  content: "\e128";
}
.glyphicon-hand-up:before {
  content: "\e129";
}
.glyphicon-hand-down:before {
  content: "\e130";
}
.glyphicon-circle-arrow-right:before {
  content: "\e131";
}
.glyphicon-circle-arrow-left:before {
  content: "\e132";
}
.glyphicon-circle-arrow-up:before {
  content: "\e133";
}
.glyphicon-circle-arrow-down:before {
  content: "\e134";
}
.glyphicon-globe:before {
  content: "\e135";
}
.glyphicon-wrench:before {
  content: "\e136";
}
.glyphicon-tasks:before {
  content: "\e137";
}
.glyphicon-filter:before {
  content: "\e138";
}
.glyphicon-briefcase:before {
  content: "\e139";
}
.glyphicon-fullscreen:before {
  content: "\e140";
}
.glyphicon-dashboard:before {
  content: "\e141";
}
.glyphicon-paperclip:before {
  content: "\e142";
}
.glyphicon-heart-empty:before {
  content: "\e143";
}
.glyphicon-link:before {
  content: "\e144";
}
.glyphicon-phone:before {
  content: "\e145";
}
.glyphicon-pushpin:before {
  content: "\e146";
}
.glyphicon-usd:before {
  content: "\e148";
}
.glyphicon-gbp:before {
  content: "\e149";
}
.glyphicon-sort:before {
  content: "\e150";
}
.glyphicon-sort-by-alphabet:before {
  content: "\e151";
}
.glyphicon-sort-by-alphabet-alt:before {
  content: "\e152";
}
.glyphicon-sort-by-order:before {
  content: "\e153";
}
.glyphicon-sort-by-order-alt:before {
  content: "\e154";
}
.glyphicon-sort-by-attributes:before {
  content: "\e155";
}
.glyphicon-sort-by-attributes-alt:before {
  content: "\e156";
}
.glyphicon-unchecked:before {
  content: "\e157";
}
.glyphicon-expand:before {
  content: "\e158";
}
.glyphicon-collapse-down:before {
  content: "\e159";
}
.glyphicon-collapse-up:before {
  content: "\e160";
}
.glyphicon-log-in:before {
  content: "\e161";
}
.glyphicon-flash:before {
  content: "\e162";
}
.glyphicon-log-out:before {
  content: "\e163";
}
.glyphicon-new-window:before {
  content: "\e164";
}
.glyphicon-record:before {
  content: "\e165";
}
.glyphicon-save:before {
  content: "\e166";
}
.glyphicon-open:before {
  content: "\e167";
}
.glyphicon-saved:before {
  content: "\e168";
}
.glyphicon-import:before {
  content: "\e169";
}
.glyphicon-export:before {
  content: "\e170";
}
.glyphicon-send:before {
  content: "\e171";
}
.glyphicon-floppy-disk:before {
  content: "\e172";
}
.glyphicon-floppy-saved:before {
  content: "\e173";
}
.glyphicon-floppy-remove:before {
  content: "\e174";
}
.glyphicon-floppy-save:before {
  content: "\e175";
}
.glyphicon-floppy-open:before {
  content: "\e176";
}
.glyphicon-credit-card:before {
  content: "\e177";
}
.glyphicon-transfer:before {
  content: "\e178";
}
.glyphicon-cutlery:before {
  content: "\e179";
}
.glyphicon-header:before {
  content: "\e180";
}
.glyphicon-compressed:before {
  content: "\e181";
}
.glyphicon-earphone:before {
  content: "\e182";
}
.glyphicon-phone-alt:before {
  content: "\e183";
}
.glyphicon-tower:before {
  content: "\e184";
}
.glyphicon-stats:before {
  content: "\e185";
}
.glyphicon-sd-video:before {
  content: "\e186";
}
.glyphicon-hd-video:before {
  content: "\e187";
}
.glyphicon-subtitles:before {
  content: "\e188";
}
.glyphicon-sound-stereo:before {
  content: "\e189";
}
.glyphicon-sound-dolby:before {
  content: "\e190";
}
.glyphicon-sound-5-1:before {
  content: "\e191";
}
.glyphicon-sound-6-1:before {
  content: "\e192";
}
.glyphicon-sound-7-1:before {
  content: "\e193";
}
.glyphicon-copyright-mark:before {
  content: "\e194";
}
.glyphicon-registration-mark:before {
  content: "\e195";
}
.glyphicon-cloud-download:before {
  content: "\e197";
}
.glyphicon-cloud-upload:before {
  content: "\e198";
}
.glyphicon-tree-conifer:before {
  content: "\e199";
}
.glyphicon-tree-deciduous:before {
  content: "\e200";
}
.glyphicon-cd:before {
  content: "\e201";
}
.glyphicon-save-file:before {
  content: "\e202";
}
.glyphicon-open-file:before {
  content: "\e203";
}
.glyphicon-level-up:before {
  content: "\e204";
}
.glyphicon-copy:before {
  content: "\e205";
}
.glyphicon-paste:before {
  content: "\e206";
}
.glyphicon-alert:before {
  content: "\e209";
}
.glyphicon-equalizer:before {
  content: "\e210";
}
.glyphicon-king:before {
  content: "\e211";
}
.glyphicon-queen:before {
  content: "\e212";
}
.glyphicon-pawn:before {
  content: "\e213";
}
.glyphicon-bishop:before {
  content: "\e214";
}
.glyphicon-knight:before {
  content: "\e215";
}
.glyphicon-baby-formula:before {
  content: "\e216";
}
.glyphicon-tent:before {
  content: "\26fa";
}
.glyphicon-blackboard:before {
  content: "\e218";
}
.glyphicon-bed:before {
  content: "\e219";
}
.glyphicon-apple:before {
  content: "\f8ff";
}
.glyphicon-erase:before {
  content: "\e221";
}
.glyphicon-hourglass:before {
  content: "\231b";
}
.glyphicon-lamp:before {
  content: "\e223";
}
.glyphicon-duplicate:before {
  content: "\e224";
}
.glyphicon-piggy-bank:before {
  content: "\e225";
}
.glyphicon-scissors:before {
  content: "\e226";
}
.glyphicon-bitcoin:before {
  content: "\e227";
}
.glyphicon-btc:before {
  content: "\e227";
}
.glyphicon-xbt:before {
  content: "\e227";
}
.glyphicon-yen:before {
  content: "\00a5";
}
.glyphicon-jpy:before {
  content: "\00a5";
}
.glyphicon-ruble:before {
  content: "\20bd";
}
.glyphicon-rub:before {
  content: "\20bd";
}
.glyphicon-scale:before {
  content: "\e230";
}
.glyphicon-ice-lolly:before {
  content: "\e231";
}
.glyphicon-ice-lolly-tasted:before {
  content: "\e232";
}
.glyphicon-education:before {
  content: "\e233";
}
.glyphicon-option-horizontal:before {
  content: "\e234";
}
.glyphicon-option-vertical:before {
  content: "\e235";
}
.glyphicon-menu-hamburger:before {
  content: "\e236";
}
.glyphicon-modal-window:before {
  content: "\e237";
}
.glyphicon-oil:before {
  content: "\e238";
}
.glyphicon-grain:before {
  content: "\e239";
}
.glyphicon-sunglasses:before {
  content: "\e240";
}
.glyphicon-text-size:before {
  content: "\e241";
}
.glyphicon-text-color:before {
  content: "\e242";
}
.glyphicon-text-background:before {
  content: "\e243";
}
.glyphicon-object-align-top:before {
  content: "\e244";
}
.glyphicon-object-align-bottom:before {
  content: "\e245";
}
.glyphicon-object-align-horizontal:before {
  content: "\e246";
}
.glyphicon-object-align-left:before {
  content: "\e247";
}
.glyphicon-object-align-vertical:before {
  content: "\e248";
}
.glyphicon-object-align-right:before {
  content: "\e249";
}
.glyphicon-triangle-right:before {
  content: "\e250";
}
.glyphicon-triangle-left:before {
  content: "\e251";
}
.glyphicon-triangle-bottom:before {
  content: "\e252";
}
.glyphicon-triangle-top:before {
  content: "\e253";
}
.glyphicon-console:before {
  content: "\e254";
}
.glyphicon-superscript:before {
  content: "\e255";
}
.glyphicon-subscript:before {
  content: "\e256";
}
.glyphicon-menu-left:before {
  content: "\e257";
}
.glyphicon-menu-right:before {
  content: "\e258";
}
.glyphicon-menu-down:before {
  content: "\e259";
}
.glyphicon-menu-up:before {
  content: "\e260";
}
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
*:before,
*:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
html {
  font-size: 10px;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  line-height: 1.42857143;
  color: #000;
  background-color: #fff;
}
input,
button,
select,
textarea {
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
}
a {
  color: #337ab7;
  text-decoration: none;
}
a:hover,
a:focus {
  color: #23527c;
  text-decoration: underline;
}
a:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
figure {
  margin: 0;
}
img {
  vertical-align: middle;
}
.img-responsive,
.thumbnail > img,
.thumbnail a > img,
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  display: block;
  max-width: 100%;
  height: auto;
}
.img-rounded {
  border-radius: 3px;
}
.img-thumbnail {
  padding: 4px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: all 0.2s ease-in-out;
  -o-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
  display: inline-block;
  max-width: 100%;
  height: auto;
}
.img-circle {
  border-radius: 50%;
}
hr {
  margin-top: 18px;
  margin-bottom: 18px;
  border: 0;
  border-top: 1px solid #eeeeee;
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
[role="button"] {
  cursor: pointer;
}
h1,
h2,
h3,
h4,
h5,
h6,
.h1,
.h2,
.h3,
.h4,
.h5,
.h6 {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  color: inherit;
}
h1 small,
h2 small,
h3 small,
h4 small,
h5 small,
h6 small,
.h1 small,
.h2 small,
.h3 small,
.h4 small,
.h5 small,
.h6 small,
h1 .small,
h2 .small,
h3 .small,
h4 .small,
h5 .small,
h6 .small,
.h1 .small,
.h2 .small,
.h3 .small,
.h4 .small,
.h5 .small,
.h6 .small {
  font-weight: normal;
  line-height: 1;
  color: #777777;
}
h1,
.h1,
h2,
.h2,
h3,
.h3 {
  margin-top: 18px;
  margin-bottom: 9px;
}
h1 small,
.h1 small,
h2 small,
.h2 small,
h3 small,
.h3 small,
h1 .small,
.h1 .small,
h2 .small,
.h2 .small,
h3 .small,
.h3 .small {
  font-size: 65%;
}
h4,
.h4,
h5,
.h5,
h6,
.h6 {
  margin-top: 9px;
  margin-bottom: 9px;
}
h4 small,
.h4 small,
h5 small,
.h5 small,
h6 small,
.h6 small,
h4 .small,
.h4 .small,
h5 .small,
.h5 .small,
h6 .small,
.h6 .small {
  font-size: 75%;
}
h1,
.h1 {
  font-size: 33px;
}
h2,
.h2 {
  font-size: 27px;
}
h3,
.h3 {
  font-size: 23px;
}
h4,
.h4 {
  font-size: 17px;
}
h5,
.h5 {
  font-size: 13px;
}
h6,
.h6 {
  font-size: 12px;
}
p {
  margin: 0 0 9px;
}
.lead {
  margin-bottom: 18px;
  font-size: 14px;
  font-weight: 300;
  line-height: 1.4;
}
@media (min-width: 768px) {
  .lead {
    font-size: 19.5px;
  }
}
small,
.small {
  font-size: 92%;
}
mark,
.mark {
  background-color: #fcf8e3;
  padding: .2em;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}
.text-center {
  text-align: center;
}
.text-justify {
  text-align: justify;
}
.text-nowrap {
  white-space: nowrap;
}
.text-lowercase {
  text-transform: lowercase;
}
.text-uppercase {
  text-transform: uppercase;
}
.text-capitalize {
  text-transform: capitalize;
}
.text-muted {
  color: #777777;
}
.text-primary {
  color: #337ab7;
}
a.text-primary:hover,
a.text-primary:focus {
  color: #286090;
}
.text-success {
  color: #3c763d;
}
a.text-success:hover,
a.text-success:focus {
  color: #2b542c;
}
.text-info {
  color: #31708f;
}
a.text-info:hover,
a.text-info:focus {
  color: #245269;
}
.text-warning {
  color: #8a6d3b;
}
a.text-warning:hover,
a.text-warning:focus {
  color: #66512c;
}
.text-danger {
  color: #a94442;
}
a.text-danger:hover,
a.text-danger:focus {
  color: #843534;
}
.bg-primary {
  color: #fff;
  background-color: #337ab7;
}
a.bg-primary:hover,
a.bg-primary:focus {
  background-color: #286090;
}
.bg-success {
  background-color: #dff0d8;
}
a.bg-success:hover,
a.bg-success:focus {
  background-color: #c1e2b3;
}
.bg-info {
  background-color: #d9edf7;
}
a.bg-info:hover,
a.bg-info:focus {
  background-color: #afd9ee;
}
.bg-warning {
  background-color: #fcf8e3;
}
a.bg-warning:hover,
a.bg-warning:focus {
  background-color: #f7ecb5;
}
.bg-danger {
  background-color: #f2dede;
}
a.bg-danger:hover,
a.bg-danger:focus {
  background-color: #e4b9b9;
}
.page-header {
  padding-bottom: 8px;
  margin: 36px 0 18px;
  border-bottom: 1px solid #eeeeee;
}
ul,
ol {
  margin-top: 0;
  margin-bottom: 9px;
}
ul ul,
ol ul,
ul ol,
ol ol {
  margin-bottom: 0;
}
.list-unstyled {
  padding-left: 0;
  list-style: none;
}
.list-inline {
  padding-left: 0;
  list-style: none;
  margin-left: -5px;
}
.list-inline > li {
  display: inline-block;
  padding-left: 5px;
  padding-right: 5px;
}
dl {
  margin-top: 0;
  margin-bottom: 18px;
}
dt,
dd {
  line-height: 1.42857143;
}
dt {
  font-weight: bold;
}
dd {
  margin-left: 0;
}
@media (min-width: 541px) {
  .dl-horizontal dt {
    float: left;
    width: 160px;
    clear: left;
    text-align: right;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .dl-horizontal dd {
    margin-left: 180px;
  }
}
abbr[title],
abbr[data-original-title] {
  cursor: help;
  border-bottom: 1px dotted #777777;
}
.initialism {
  font-size: 90%;
  text-transform: uppercase;
}
blockquote {
  padding: 9px 18px;
  margin: 0 0 18px;
  font-size: inherit;
  border-left: 5px solid #eeeeee;
}
blockquote p:last-child,
blockquote ul:last-child,
blockquote ol:last-child {
  margin-bottom: 0;
}
blockquote footer,
blockquote small,
blockquote .small {
  display: block;
  font-size: 80%;
  line-height: 1.42857143;
  color: #777777;
}
blockquote footer:before,
blockquote small:before,
blockquote .small:before {
  content: '\2014 \00A0';
}
.blockquote-reverse,
blockquote.pull-right {
  padding-right: 15px;
  padding-left: 0;
  border-right: 5px solid #eeeeee;
  border-left: 0;
  text-align: right;
}
.blockquote-reverse footer:before,
blockquote.pull-right footer:before,
.blockquote-reverse small:before,
blockquote.pull-right small:before,
.blockquote-reverse .small:before,
blockquote.pull-right .small:before {
  content: '';
}
.blockquote-reverse footer:after,
blockquote.pull-right footer:after,
.blockquote-reverse small:after,
blockquote.pull-right small:after,
.blockquote-reverse .small:after,
blockquote.pull-right .small:after {
  content: '\00A0 \2014';
}
address {
  margin-bottom: 18px;
  font-style: normal;
  line-height: 1.42857143;
}
code,
kbd,
pre,
samp {
  font-family: monospace;
}
code {
  padding: 2px 4px;
  font-size: 90%;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 2px;
}
kbd {
  padding: 2px 4px;
  font-size: 90%;
  color: #888;
  background-color: transparent;
  border-radius: 1px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
}
kbd kbd {
  padding: 0;
  font-size: 100%;
  font-weight: bold;
  box-shadow: none;
}
pre {
  display: block;
  padding: 8.5px;
  margin: 0 0 9px;
  font-size: 12px;
  line-height: 1.42857143;
  word-break: break-all;
  word-wrap: break-word;
  color: #333333;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 2px;
}
pre code {
  padding: 0;
  font-size: inherit;
  color: inherit;
  white-space: pre-wrap;
  background-color: transparent;
  border-radius: 0;
}
.pre-scrollable {
  max-height: 340px;
  overflow-y: scroll;
}
.container {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
@media (min-width: 768px) {
  .container {
    width: 768px;
  }
}
@media (min-width: 992px) {
  .container {
    width: 940px;
  }
}
@media (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}
.container-fluid {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
.row {
  margin-left: 0px;
  margin-right: 0px;
}
.col-xs-1, .col-sm-1, .col-md-1, .col-lg-1, .col-xs-2, .col-sm-2, .col-md-2, .col-lg-2, .col-xs-3, .col-sm-3, .col-md-3, .col-lg-3, .col-xs-4, .col-sm-4, .col-md-4, .col-lg-4, .col-xs-5, .col-sm-5, .col-md-5, .col-lg-5, .col-xs-6, .col-sm-6, .col-md-6, .col-lg-6, .col-xs-7, .col-sm-7, .col-md-7, .col-lg-7, .col-xs-8, .col-sm-8, .col-md-8, .col-lg-8, .col-xs-9, .col-sm-9, .col-md-9, .col-lg-9, .col-xs-10, .col-sm-10, .col-md-10, .col-lg-10, .col-xs-11, .col-sm-11, .col-md-11, .col-lg-11, .col-xs-12, .col-sm-12, .col-md-12, .col-lg-12 {
  position: relative;
  min-height: 1px;
  padding-left: 0px;
  padding-right: 0px;
}
.col-xs-1, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9, .col-xs-10, .col-xs-11, .col-xs-12 {
  float: left;
}
.col-xs-12 {
  width: 100%;
}
.col-xs-11 {
  width: 91.66666667%;
}
.col-xs-10 {
  width: 83.33333333%;
}
.col-xs-9 {
  width: 75%;
}
.col-xs-8 {
  width: 66.66666667%;
}
.col-xs-7 {
  width: 58.33333333%;
}
.col-xs-6 {
  width: 50%;
}
.col-xs-5 {
  width: 41.66666667%;
}
.col-xs-4 {
  width: 33.33333333%;
}
.col-xs-3 {
  width: 25%;
}
.col-xs-2 {
  width: 16.66666667%;
}
.col-xs-1 {
  width: 8.33333333%;
}
.col-xs-pull-12 {
  right: 100%;
}
.col-xs-pull-11 {
  right: 91.66666667%;
}
.col-xs-pull-10 {
  right: 83.33333333%;
}
.col-xs-pull-9 {
  right: 75%;
}
.col-xs-pull-8 {
  right: 66.66666667%;
}
.col-xs-pull-7 {
  right: 58.33333333%;
}
.col-xs-pull-6 {
  right: 50%;
}
.col-xs-pull-5 {
  right: 41.66666667%;
}
.col-xs-pull-4 {
  right: 33.33333333%;
}
.col-xs-pull-3 {
  right: 25%;
}
.col-xs-pull-2 {
  right: 16.66666667%;
}
.col-xs-pull-1 {
  right: 8.33333333%;
}
.col-xs-pull-0 {
  right: auto;
}
.col-xs-push-12 {
  left: 100%;
}
.col-xs-push-11 {
  left: 91.66666667%;
}
.col-xs-push-10 {
  left: 83.33333333%;
}
.col-xs-push-9 {
  left: 75%;
}
.col-xs-push-8 {
  left: 66.66666667%;
}
.col-xs-push-7 {
  left: 58.33333333%;
}
.col-xs-push-6 {
  left: 50%;
}
.col-xs-push-5 {
  left: 41.66666667%;
}
.col-xs-push-4 {
  left: 33.33333333%;
}
.col-xs-push-3 {
  left: 25%;
}
.col-xs-push-2 {
  left: 16.66666667%;
}
.col-xs-push-1 {
  left: 8.33333333%;
}
.col-xs-push-0 {
  left: auto;
}
.col-xs-offset-12 {
  margin-left: 100%;
}
.col-xs-offset-11 {
  margin-left: 91.66666667%;
}
.col-xs-offset-10 {
  margin-left: 83.33333333%;
}
.col-xs-offset-9 {
  margin-left: 75%;
}
.col-xs-offset-8 {
  margin-left: 66.66666667%;
}
.col-xs-offset-7 {
  margin-left: 58.33333333%;
}
.col-xs-offset-6 {
  margin-left: 50%;
}
.col-xs-offset-5 {
  margin-left: 41.66666667%;
}
.col-xs-offset-4 {
  margin-left: 33.33333333%;
}
.col-xs-offset-3 {
  margin-left: 25%;
}
.col-xs-offset-2 {
  margin-left: 16.66666667%;
}
.col-xs-offset-1 {
  margin-left: 8.33333333%;
}
.col-xs-offset-0 {
  margin-left: 0%;
}
@media (min-width: 768px) {
  .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
    float: left;
  }
  .col-sm-12 {
    width: 100%;
  }
  .col-sm-11 {
    width: 91.66666667%;
  }
  .col-sm-10 {
    width: 83.33333333%;
  }
  .col-sm-9 {
    width: 75%;
  }
  .col-sm-8 {
    width: 66.66666667%;
  }
  .col-sm-7 {
    width: 58.33333333%;
  }
  .col-sm-6 {
    width: 50%;
  }
  .col-sm-5 {
    width: 41.66666667%;
  }
  .col-sm-4 {
    width: 33.33333333%;
  }
  .col-sm-3 {
    width: 25%;
  }
  .col-sm-2 {
    width: 16.66666667%;
  }
  .col-sm-1 {
    width: 8.33333333%;
  }
  .col-sm-pull-12 {
    right: 100%;
  }
  .col-sm-pull-11 {
    right: 91.66666667%;
  }
  .col-sm-pull-10 {
    right: 83.33333333%;
  }
  .col-sm-pull-9 {
    right: 75%;
  }
  .col-sm-pull-8 {
    right: 66.66666667%;
  }
  .col-sm-pull-7 {
    right: 58.33333333%;
  }
  .col-sm-pull-6 {
    right: 50%;
  }
  .col-sm-pull-5 {
    right: 41.66666667%;
  }
  .col-sm-pull-4 {
    right: 33.33333333%;
  }
  .col-sm-pull-3 {
    right: 25%;
  }
  .col-sm-pull-2 {
    right: 16.66666667%;
  }
  .col-sm-pull-1 {
    right: 8.33333333%;
  }
  .col-sm-pull-0 {
    right: auto;
  }
  .col-sm-push-12 {
    left: 100%;
  }
  .col-sm-push-11 {
    left: 91.66666667%;
  }
  .col-sm-push-10 {
    left: 83.33333333%;
  }
  .col-sm-push-9 {
    left: 75%;
  }
  .col-sm-push-8 {
    left: 66.66666667%;
  }
  .col-sm-push-7 {
    left: 58.33333333%;
  }
  .col-sm-push-6 {
    left: 50%;
  }
  .col-sm-push-5 {
    left: 41.66666667%;
  }
  .col-sm-push-4 {
    left: 33.33333333%;
  }
  .col-sm-push-3 {
    left: 25%;
  }
  .col-sm-push-2 {
    left: 16.66666667%;
  }
  .col-sm-push-1 {
    left: 8.33333333%;
  }
  .col-sm-push-0 {
    left: auto;
  }
  .col-sm-offset-12 {
    margin-left: 100%;
  }
  .col-sm-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-sm-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-sm-offset-9 {
    margin-left: 75%;
  }
  .col-sm-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-sm-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-sm-offset-6 {
    margin-left: 50%;
  }
  .col-sm-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-sm-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-sm-offset-3 {
    margin-left: 25%;
  }
  .col-sm-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-sm-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-sm-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 992px) {
  .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
    float: left;
  }
  .col-md-12 {
    width: 100%;
  }
  .col-md-11 {
    width: 91.66666667%;
  }
  .col-md-10 {
    width: 83.33333333%;
  }
  .col-md-9 {
    width: 75%;
  }
  .col-md-8 {
    width: 66.66666667%;
  }
  .col-md-7 {
    width: 58.33333333%;
  }
  .col-md-6 {
    width: 50%;
  }
  .col-md-5 {
    width: 41.66666667%;
  }
  .col-md-4 {
    width: 33.33333333%;
  }
  .col-md-3 {
    width: 25%;
  }
  .col-md-2 {
    width: 16.66666667%;
  }
  .col-md-1 {
    width: 8.33333333%;
  }
  .col-md-pull-12 {
    right: 100%;
  }
  .col-md-pull-11 {
    right: 91.66666667%;
  }
  .col-md-pull-10 {
    right: 83.33333333%;
  }
  .col-md-pull-9 {
    right: 75%;
  }
  .col-md-pull-8 {
    right: 66.66666667%;
  }
  .col-md-pull-7 {
    right: 58.33333333%;
  }
  .col-md-pull-6 {
    right: 50%;
  }
  .col-md-pull-5 {
    right: 41.66666667%;
  }
  .col-md-pull-4 {
    right: 33.33333333%;
  }
  .col-md-pull-3 {
    right: 25%;
  }
  .col-md-pull-2 {
    right: 16.66666667%;
  }
  .col-md-pull-1 {
    right: 8.33333333%;
  }
  .col-md-pull-0 {
    right: auto;
  }
  .col-md-push-12 {
    left: 100%;
  }
  .col-md-push-11 {
    left: 91.66666667%;
  }
  .col-md-push-10 {
    left: 83.33333333%;
  }
  .col-md-push-9 {
    left: 75%;
  }
  .col-md-push-8 {
    left: 66.66666667%;
  }
  .col-md-push-7 {
    left: 58.33333333%;
  }
  .col-md-push-6 {
    left: 50%;
  }
  .col-md-push-5 {
    left: 41.66666667%;
  }
  .col-md-push-4 {
    left: 33.33333333%;
  }
  .col-md-push-3 {
    left: 25%;
  }
  .col-md-push-2 {
    left: 16.66666667%;
  }
  .col-md-push-1 {
    left: 8.33333333%;
  }
  .col-md-push-0 {
    left: auto;
  }
  .col-md-offset-12 {
    margin-left: 100%;
  }
  .col-md-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-md-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-md-offset-9 {
    margin-left: 75%;
  }
  .col-md-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-md-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-md-offset-6 {
    margin-left: 50%;
  }
  .col-md-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-md-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-md-offset-3 {
    margin-left: 25%;
  }
  .col-md-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-md-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-md-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 1200px) {
  .col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12 {
    float: left;
  }
  .col-lg-12 {
    width: 100%;
  }
  .col-lg-11 {
    width: 91.66666667%;
  }
  .col-lg-10 {
    width: 83.33333333%;
  }
  .col-lg-9 {
    width: 75%;
  }
  .col-lg-8 {
    width: 66.66666667%;
  }
  .col-lg-7 {
    width: 58.33333333%;
  }
  .col-lg-6 {
    width: 50%;
  }
  .col-lg-5 {
    width: 41.66666667%;
  }
  .col-lg-4 {
    width: 33.33333333%;
  }
  .col-lg-3 {
    width: 25%;
  }
  .col-lg-2 {
    width: 16.66666667%;
  }
  .col-lg-1 {
    width: 8.33333333%;
  }
  .col-lg-pull-12 {
    right: 100%;
  }
  .col-lg-pull-11 {
    right: 91.66666667%;
  }
  .col-lg-pull-10 {
    right: 83.33333333%;
  }
  .col-lg-pull-9 {
    right: 75%;
  }
  .col-lg-pull-8 {
    right: 66.66666667%;
  }
  .col-lg-pull-7 {
    right: 58.33333333%;
  }
  .col-lg-pull-6 {
    right: 50%;
  }
  .col-lg-pull-5 {
    right: 41.66666667%;
  }
  .col-lg-pull-4 {
    right: 33.33333333%;
  }
  .col-lg-pull-3 {
    right: 25%;
  }
  .col-lg-pull-2 {
    right: 16.66666667%;
  }
  .col-lg-pull-1 {
    right: 8.33333333%;
  }
  .col-lg-pull-0 {
    right: auto;
  }
  .col-lg-push-12 {
    left: 100%;
  }
  .col-lg-push-11 {
    left: 91.66666667%;
  }
  .col-lg-push-10 {
    left: 83.33333333%;
  }
  .col-lg-push-9 {
    left: 75%;
  }
  .col-lg-push-8 {
    left: 66.66666667%;
  }
  .col-lg-push-7 {
    left: 58.33333333%;
  }
  .col-lg-push-6 {
    left: 50%;
  }
  .col-lg-push-5 {
    left: 41.66666667%;
  }
  .col-lg-push-4 {
    left: 33.33333333%;
  }
  .col-lg-push-3 {
    left: 25%;
  }
  .col-lg-push-2 {
    left: 16.66666667%;
  }
  .col-lg-push-1 {
    left: 8.33333333%;
  }
  .col-lg-push-0 {
    left: auto;
  }
  .col-lg-offset-12 {
    margin-left: 100%;
  }
  .col-lg-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-lg-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-lg-offset-9 {
    margin-left: 75%;
  }
  .col-lg-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-lg-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-lg-offset-6 {
    margin-left: 50%;
  }
  .col-lg-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-lg-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-lg-offset-3 {
    margin-left: 25%;
  }
  .col-lg-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-lg-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-lg-offset-0 {
    margin-left: 0%;
  }
}
table {
  background-color: transparent;
}
caption {
  padding-top: 8px;
  padding-bottom: 8px;
  color: #777777;
  text-align: left;
}
th {
  text-align: left;
}
.table {
  width: 100%;
  max-width: 100%;
  margin-bottom: 18px;
}
.table > thead > tr > th,
.table > tbody > tr > th,
.table > tfoot > tr > th,
.table > thead > tr > td,
.table > tbody > tr > td,
.table > tfoot > tr > td {
  padding: 8px;
  line-height: 1.42857143;
  vertical-align: top;
  border-top: 1px solid #ddd;
}
.table > thead > tr > th {
  vertical-align: bottom;
  border-bottom: 2px solid #ddd;
}
.table > caption + thead > tr:first-child > th,
.table > colgroup + thead > tr:first-child > th,
.table > thead:first-child > tr:first-child > th,
.table > caption + thead > tr:first-child > td,
.table > colgroup + thead > tr:first-child > td,
.table > thead:first-child > tr:first-child > td {
  border-top: 0;
}
.table > tbody + tbody {
  border-top: 2px solid #ddd;
}
.table .table {
  background-color: #fff;
}
.table-condensed > thead > tr > th,
.table-condensed > tbody > tr > th,
.table-condensed > tfoot > tr > th,
.table-condensed > thead > tr > td,
.table-condensed > tbody > tr > td,
.table-condensed > tfoot > tr > td {
  padding: 5px;
}
.table-bordered {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > tbody > tr > th,
.table-bordered > tfoot > tr > th,
.table-bordered > thead > tr > td,
.table-bordered > tbody > tr > td,
.table-bordered > tfoot > tr > td {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > thead > tr > td {
  border-bottom-width: 2px;
}
.table-striped > tbody > tr:nth-of-type(odd) {
  background-color: #f9f9f9;
}
.table-hover > tbody > tr:hover {
  background-color: #f5f5f5;
}
table col[class*="col-"] {
  position: static;
  float: none;
  display: table-column;
}
table td[class*="col-"],
table th[class*="col-"] {
  position: static;
  float: none;
  display: table-cell;
}
.table > thead > tr > td.active,
.table > tbody > tr > td.active,
.table > tfoot > tr > td.active,
.table > thead > tr > th.active,
.table > tbody > tr > th.active,
.table > tfoot > tr > th.active,
.table > thead > tr.active > td,
.table > tbody > tr.active > td,
.table > tfoot > tr.active > td,
.table > thead > tr.active > th,
.table > tbody > tr.active > th,
.table > tfoot > tr.active > th {
  background-color: #f5f5f5;
}
.table-hover > tbody > tr > td.active:hover,
.table-hover > tbody > tr > th.active:hover,
.table-hover > tbody > tr.active:hover > td,
.table-hover > tbody > tr:hover > .active,
.table-hover > tbody > tr.active:hover > th {
  background-color: #e8e8e8;
}
.table > thead > tr > td.success,
.table > tbody > tr > td.success,
.table > tfoot > tr > td.success,
.table > thead > tr > th.success,
.table > tbody > tr > th.success,
.table > tfoot > tr > th.success,
.table > thead > tr.success > td,
.table > tbody > tr.success > td,
.table > tfoot > tr.success > td,
.table > thead > tr.success > th,
.table > tbody > tr.success > th,
.table > tfoot > tr.success > th {
  background-color: #dff0d8;
}
.table-hover > tbody > tr > td.success:hover,
.table-hover > tbody > tr > th.success:hover,
.table-hover > tbody > tr.success:hover > td,
.table-hover > tbody > tr:hover > .success,
.table-hover > tbody > tr.success:hover > th {
  background-color: #d0e9c6;
}
.table > thead > tr > td.info,
.table > tbody > tr > td.info,
.table > tfoot > tr > td.info,
.table > thead > tr > th.info,
.table > tbody > tr > th.info,
.table > tfoot > tr > th.info,
.table > thead > tr.info > td,
.table > tbody > tr.info > td,
.table > tfoot > tr.info > td,
.table > thead > tr.info > th,
.table > tbody > tr.info > th,
.table > tfoot > tr.info > th {
  background-color: #d9edf7;
}
.table-hover > tbody > tr > td.info:hover,
.table-hover > tbody > tr > th.info:hover,
.table-hover > tbody > tr.info:hover > td,
.table-hover > tbody > tr:hover > .info,
.table-hover > tbody > tr.info:hover > th {
  background-color: #c4e3f3;
}
.table > thead > tr > td.warning,
.table > tbody > tr > td.warning,
.table > tfoot > tr > td.warning,
.table > thead > tr > th.warning,
.table > tbody > tr > th.warning,
.table > tfoot > tr > th.warning,
.table > thead > tr.warning > td,
.table > tbody > tr.warning > td,
.table > tfoot > tr.warning > td,
.table > thead > tr.warning > th,
.table > tbody > tr.warning > th,
.table > tfoot > tr.warning > th {
  background-color: #fcf8e3;
}
.table-hover > tbody > tr > td.warning:hover,
.table-hover > tbody > tr > th.warning:hover,
.table-hover > tbody > tr.warning:hover > td,
.table-hover > tbody > tr:hover > .warning,
.table-hover > tbody > tr.warning:hover > th {
  background-color: #faf2cc;
}
.table > thead > tr > td.danger,
.table > tbody > tr > td.danger,
.table > tfoot > tr > td.danger,
.table > thead > tr > th.danger,
.table > tbody > tr > th.danger,
.table > tfoot > tr > th.danger,
.table > thead > tr.danger > td,
.table > tbody > tr.danger > td,
.table > tfoot > tr.danger > td,
.table > thead > tr.danger > th,
.table > tbody > tr.danger > th,
.table > tfoot > tr.danger > th {
  background-color: #f2dede;
}
.table-hover > tbody > tr > td.danger:hover,
.table-hover > tbody > tr > th.danger:hover,
.table-hover > tbody > tr.danger:hover > td,
.table-hover > tbody > tr:hover > .danger,
.table-hover > tbody > tr.danger:hover > th {
  background-color: #ebcccc;
}
.table-responsive {
  overflow-x: auto;
  min-height: 0.01%;
}
@media screen and (max-width: 767px) {
  .table-responsive {
    width: 100%;
    margin-bottom: 13.5px;
    overflow-y: hidden;
    -ms-overflow-style: -ms-autohiding-scrollbar;
    border: 1px solid #ddd;
  }
  .table-responsive > .table {
    margin-bottom: 0;
  }
  .table-responsive > .table > thead > tr > th,
  .table-responsive > .table > tbody > tr > th,
  .table-responsive > .table > tfoot > tr > th,
  .table-responsive > .table > thead > tr > td,
  .table-responsive > .table > tbody > tr > td,
  .table-responsive > .table > tfoot > tr > td {
    white-space: nowrap;
  }
  .table-responsive > .table-bordered {
    border: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:first-child,
  .table-responsive > .table-bordered > tbody > tr > th:first-child,
  .table-responsive > .table-bordered > tfoot > tr > th:first-child,
  .table-responsive > .table-bordered > thead > tr > td:first-child,
  .table-responsive > .table-bordered > tbody > tr > td:first-child,
  .table-responsive > .table-bordered > tfoot > tr > td:first-child {
    border-left: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:last-child,
  .table-responsive > .table-bordered > tbody > tr > th:last-child,
  .table-responsive > .table-bordered > tfoot > tr > th:last-child,
  .table-responsive > .table-bordered > thead > tr > td:last-child,
  .table-responsive > .table-bordered > tbody > tr > td:last-child,
  .table-responsive > .table-bordered > tfoot > tr > td:last-child {
    border-right: 0;
  }
  .table-responsive > .table-bordered > tbody > tr:last-child > th,
  .table-responsive > .table-bordered > tfoot > tr:last-child > th,
  .table-responsive > .table-bordered > tbody > tr:last-child > td,
  .table-responsive > .table-bordered > tfoot > tr:last-child > td {
    border-bottom: 0;
  }
}
fieldset {
  padding: 0;
  margin: 0;
  border: 0;
  min-width: 0;
}
legend {
  display: block;
  width: 100%;
  padding: 0;
  margin-bottom: 18px;
  font-size: 19.5px;
  line-height: inherit;
  color: #333333;
  border: 0;
  border-bottom: 1px solid #e5e5e5;
}
label {
  display: inline-block;
  max-width: 100%;
  margin-bottom: 5px;
  font-weight: bold;
}
input[type="search"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
input[type="radio"],
input[type="checkbox"] {
  margin: 4px 0 0;
  margin-top: 1px \9;
  line-height: normal;
}
input[type="file"] {
  display: block;
}
input[type="range"] {
  display: block;
  width: 100%;
}
select[multiple],
select[size] {
  height: auto;
}
input[type="file"]:focus,
input[type="radio"]:focus,
input[type="checkbox"]:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
output {
  display: block;
  padding-top: 7px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
}
.form-control {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
}
.form-control:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.form-control::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.form-control:-ms-input-placeholder {
  color: #999;
}
.form-control::-webkit-input-placeholder {
  color: #999;
}
.form-control::-ms-expand {
  border: 0;
  background-color: transparent;
}
.form-control[disabled],
.form-control[readonly],
fieldset[disabled] .form-control {
  background-color: #eeeeee;
  opacity: 1;
}
.form-control[disabled],
fieldset[disabled] .form-control {
  cursor: not-allowed;
}
textarea.form-control {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: none;
}
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  input[type="date"].form-control,
  input[type="time"].form-control,
  input[type="datetime-local"].form-control,
  input[type="month"].form-control {
    line-height: 32px;
  }
  input[type="date"].input-sm,
  input[type="time"].input-sm,
  input[type="datetime-local"].input-sm,
  input[type="month"].input-sm,
  .input-group-sm input[type="date"],
  .input-group-sm input[type="time"],
  .input-group-sm input[type="datetime-local"],
  .input-group-sm input[type="month"] {
    line-height: 30px;
  }
  input[type="date"].input-lg,
  input[type="time"].input-lg,
  input[type="datetime-local"].input-lg,
  input[type="month"].input-lg,
  .input-group-lg input[type="date"],
  .input-group-lg input[type="time"],
  .input-group-lg input[type="datetime-local"],
  .input-group-lg input[type="month"] {
    line-height: 45px;
  }
}
.form-group {
  margin-bottom: 15px;
}
.radio,
.checkbox {
  position: relative;
  display: block;
  margin-top: 10px;
  margin-bottom: 10px;
}
.radio label,
.checkbox label {
  min-height: 18px;
  padding-left: 20px;
  margin-bottom: 0;
  font-weight: normal;
  cursor: pointer;
}
.radio input[type="radio"],
.radio-inline input[type="radio"],
.checkbox input[type="checkbox"],
.checkbox-inline input[type="checkbox"] {
  position: absolute;
  margin-left: -20px;
  margin-top: 4px \9;
}
.radio + .radio,
.checkbox + .checkbox {
  margin-top: -5px;
}
.radio-inline,
.checkbox-inline {
  position: relative;
  display: inline-block;
  padding-left: 20px;
  margin-bottom: 0;
  vertical-align: middle;
  font-weight: normal;
  cursor: pointer;
}
.radio-inline + .radio-inline,
.checkbox-inline + .checkbox-inline {
  margin-top: 0;
  margin-left: 10px;
}
input[type="radio"][disabled],
input[type="checkbox"][disabled],
input[type="radio"].disabled,
input[type="checkbox"].disabled,
fieldset[disabled] input[type="radio"],
fieldset[disabled] input[type="checkbox"] {
  cursor: not-allowed;
}
.radio-inline.disabled,
.checkbox-inline.disabled,
fieldset[disabled] .radio-inline,
fieldset[disabled] .checkbox-inline {
  cursor: not-allowed;
}
.radio.disabled label,
.checkbox.disabled label,
fieldset[disabled] .radio label,
fieldset[disabled] .checkbox label {
  cursor: not-allowed;
}
.form-control-static {
  padding-top: 7px;
  padding-bottom: 7px;
  margin-bottom: 0;
  min-height: 31px;
}
.form-control-static.input-lg,
.form-control-static.input-sm {
  padding-left: 0;
  padding-right: 0;
}
.input-sm {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-sm {
  height: 30px;
  line-height: 30px;
}
textarea.input-sm,
select[multiple].input-sm {
  height: auto;
}
.form-group-sm .form-control {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.form-group-sm select.form-control {
  height: 30px;
  line-height: 30px;
}
.form-group-sm textarea.form-control,
.form-group-sm select[multiple].form-control {
  height: auto;
}
.form-group-sm .form-control-static {
  height: 30px;
  min-height: 30px;
  padding: 6px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.input-lg {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-lg {
  height: 45px;
  line-height: 45px;
}
textarea.input-lg,
select[multiple].input-lg {
  height: auto;
}
.form-group-lg .form-control {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.form-group-lg select.form-control {
  height: 45px;
  line-height: 45px;
}
.form-group-lg textarea.form-control,
.form-group-lg select[multiple].form-control {
  height: auto;
}
.form-group-lg .form-control-static {
  height: 45px;
  min-height: 35px;
  padding: 11px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.has-feedback {
  position: relative;
}
.has-feedback .form-control {
  padding-right: 40px;
}
.form-control-feedback {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 2;
  display: block;
  width: 32px;
  height: 32px;
  line-height: 32px;
  text-align: center;
  pointer-events: none;
}
.input-lg + .form-control-feedback,
.input-group-lg + .form-control-feedback,
.form-group-lg .form-control + .form-control-feedback {
  width: 45px;
  height: 45px;
  line-height: 45px;
}
.input-sm + .form-control-feedback,
.input-group-sm + .form-control-feedback,
.form-group-sm .form-control + .form-control-feedback {
  width: 30px;
  height: 30px;
  line-height: 30px;
}
.has-success .help-block,
.has-success .control-label,
.has-success .radio,
.has-success .checkbox,
.has-success .radio-inline,
.has-success .checkbox-inline,
.has-success.radio label,
.has-success.checkbox label,
.has-success.radio-inline label,
.has-success.checkbox-inline label {
  color: #3c763d;
}
.has-success .form-control {
  border-color: #3c763d;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-success .form-control:focus {
  border-color: #2b542c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
}
.has-success .input-group-addon {
  color: #3c763d;
  border-color: #3c763d;
  background-color: #dff0d8;
}
.has-success .form-control-feedback {
  color: #3c763d;
}
.has-warning .help-block,
.has-warning .control-label,
.has-warning .radio,
.has-warning .checkbox,
.has-warning .radio-inline,
.has-warning .checkbox-inline,
.has-warning.radio label,
.has-warning.checkbox label,
.has-warning.radio-inline label,
.has-warning.checkbox-inline label {
  color: #8a6d3b;
}
.has-warning .form-control {
  border-color: #8a6d3b;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-warning .form-control:focus {
  border-color: #66512c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
}
.has-warning .input-group-addon {
  color: #8a6d3b;
  border-color: #8a6d3b;
  background-color: #fcf8e3;
}
.has-warning .form-control-feedback {
  color: #8a6d3b;
}
.has-error .help-block,
.has-error .control-label,
.has-error .radio,
.has-error .checkbox,
.has-error .radio-inline,
.has-error .checkbox-inline,
.has-error.radio label,
.has-error.checkbox label,
.has-error.radio-inline label,
.has-error.checkbox-inline label {
  color: #a94442;
}
.has-error .form-control {
  border-color: #a94442;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-error .form-control:focus {
  border-color: #843534;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
}
.has-error .input-group-addon {
  color: #a94442;
  border-color: #a94442;
  background-color: #f2dede;
}
.has-error .form-control-feedback {
  color: #a94442;
}
.has-feedback label ~ .form-control-feedback {
  top: 23px;
}
.has-feedback label.sr-only ~ .form-control-feedback {
  top: 0;
}
.help-block {
  display: block;
  margin-top: 5px;
  margin-bottom: 10px;
  color: #404040;
}
@media (min-width: 768px) {
  .form-inline .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .form-inline .form-control-static {
    display: inline-block;
  }
  .form-inline .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .form-inline .input-group .input-group-addon,
  .form-inline .input-group .input-group-btn,
  .form-inline .input-group .form-control {
    width: auto;
  }
  .form-inline .input-group > .form-control {
    width: 100%;
  }
  .form-inline .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio,
  .form-inline .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio label,
  .form-inline .checkbox label {
    padding-left: 0;
  }
  .form-inline .radio input[type="radio"],
  .form-inline .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .form-inline .has-feedback .form-control-feedback {
    top: 0;
  }
}
.form-horizontal .radio,
.form-horizontal .checkbox,
.form-horizontal .radio-inline,
.form-horizontal .checkbox-inline {
  margin-top: 0;
  margin-bottom: 0;
  padding-top: 7px;
}
.form-horizontal .radio,
.form-horizontal .checkbox {
  min-height: 25px;
}
.form-horizontal .form-group {
  margin-left: 0px;
  margin-right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .control-label {
    text-align: right;
    margin-bottom: 0;
    padding-top: 7px;
  }
}
.form-horizontal .has-feedback .form-control-feedback {
  right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .form-group-lg .control-label {
    padding-top: 11px;
    font-size: 17px;
  }
}
@media (min-width: 768px) {
  .form-horizontal .form-group-sm .control-label {
    padding-top: 6px;
    font-size: 12px;
  }
}
.btn {
  display: inline-block;
  margin-bottom: 0;
  font-weight: normal;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  white-space: nowrap;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  border-radius: 2px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.btn:focus,
.btn:active:focus,
.btn.active:focus,
.btn.focus,
.btn:active.focus,
.btn.active.focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
.btn:hover,
.btn:focus,
.btn.focus {
  color: #333;
  text-decoration: none;
}
.btn:active,
.btn.active {
  outline: 0;
  background-image: none;
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn.disabled,
.btn[disabled],
fieldset[disabled] .btn {
  cursor: not-allowed;
  opacity: 0.65;
  filter: alpha(opacity=65);
  -webkit-box-shadow: none;
  box-shadow: none;
}
a.btn.disabled,
fieldset[disabled] a.btn {
  pointer-events: none;
}
.btn-default {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.btn-default:focus,
.btn-default.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.btn-default:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active:hover,
.btn-default.active:hover,
.open > .dropdown-toggle.btn-default:hover,
.btn-default:active:focus,
.btn-default.active:focus,
.open > .dropdown-toggle.btn-default:focus,
.btn-default:active.focus,
.btn-default.active.focus,
.open > .dropdown-toggle.btn-default.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  background-image: none;
}
.btn-default.disabled:hover,
.btn-default[disabled]:hover,
fieldset[disabled] .btn-default:hover,
.btn-default.disabled:focus,
.btn-default[disabled]:focus,
fieldset[disabled] .btn-default:focus,
.btn-default.disabled.focus,
.btn-default[disabled].focus,
fieldset[disabled] .btn-default.focus {
  background-color: #fff;
  border-color: #ccc;
}
.btn-default .badge {
  color: #fff;
  background-color: #333;
}
.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary:focus,
.btn-primary.focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active:hover,
.btn-primary.active:hover,
.open > .dropdown-toggle.btn-primary:hover,
.btn-primary:active:focus,
.btn-primary.active:focus,
.open > .dropdown-toggle.btn-primary:focus,
.btn-primary:active.focus,
.btn-primary.active.focus,
.open > .dropdown-toggle.btn-primary.focus {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.btn-primary.disabled:hover,
.btn-primary[disabled]:hover,
fieldset[disabled] .btn-primary:hover,
.btn-primary.disabled:focus,
.btn-primary[disabled]:focus,
fieldset[disabled] .btn-primary:focus,
.btn-primary.disabled.focus,
.btn-primary[disabled].focus,
fieldset[disabled] .btn-primary.focus {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary .badge {
  color: #337ab7;
  background-color: #fff;
}
.btn-success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success:focus,
.btn-success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.btn-success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active:hover,
.btn-success.active:hover,
.open > .dropdown-toggle.btn-success:hover,
.btn-success:active:focus,
.btn-success.active:focus,
.open > .dropdown-toggle.btn-success:focus,
.btn-success:active.focus,
.btn-success.active.focus,
.open > .dropdown-toggle.btn-success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  background-image: none;
}
.btn-success.disabled:hover,
.btn-success[disabled]:hover,
fieldset[disabled] .btn-success:hover,
.btn-success.disabled:focus,
.btn-success[disabled]:focus,
fieldset[disabled] .btn-success:focus,
.btn-success.disabled.focus,
.btn-success[disabled].focus,
fieldset[disabled] .btn-success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.btn-info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info:focus,
.btn-info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.btn-info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active:hover,
.btn-info.active:hover,
.open > .dropdown-toggle.btn-info:hover,
.btn-info:active:focus,
.btn-info.active:focus,
.open > .dropdown-toggle.btn-info:focus,
.btn-info:active.focus,
.btn-info.active.focus,
.open > .dropdown-toggle.btn-info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  background-image: none;
}
.btn-info.disabled:hover,
.btn-info[disabled]:hover,
fieldset[disabled] .btn-info:hover,
.btn-info.disabled:focus,
.btn-info[disabled]:focus,
fieldset[disabled] .btn-info:focus,
.btn-info.disabled.focus,
.btn-info[disabled].focus,
fieldset[disabled] .btn-info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.btn-warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning:focus,
.btn-warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.btn-warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active:hover,
.btn-warning.active:hover,
.open > .dropdown-toggle.btn-warning:hover,
.btn-warning:active:focus,
.btn-warning.active:focus,
.open > .dropdown-toggle.btn-warning:focus,
.btn-warning:active.focus,
.btn-warning.active.focus,
.open > .dropdown-toggle.btn-warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  background-image: none;
}
.btn-warning.disabled:hover,
.btn-warning[disabled]:hover,
fieldset[disabled] .btn-warning:hover,
.btn-warning.disabled:focus,
.btn-warning[disabled]:focus,
fieldset[disabled] .btn-warning:focus,
.btn-warning.disabled.focus,
.btn-warning[disabled].focus,
fieldset[disabled] .btn-warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.btn-danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger:focus,
.btn-danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.btn-danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active:hover,
.btn-danger.active:hover,
.open > .dropdown-toggle.btn-danger:hover,
.btn-danger:active:focus,
.btn-danger.active:focus,
.open > .dropdown-toggle.btn-danger:focus,
.btn-danger:active.focus,
.btn-danger.active.focus,
.open > .dropdown-toggle.btn-danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  background-image: none;
}
.btn-danger.disabled:hover,
.btn-danger[disabled]:hover,
fieldset[disabled] .btn-danger:hover,
.btn-danger.disabled:focus,
.btn-danger[disabled]:focus,
fieldset[disabled] .btn-danger:focus,
.btn-danger.disabled.focus,
.btn-danger[disabled].focus,
fieldset[disabled] .btn-danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger .badge {
  color: #d9534f;
  background-color: #fff;
}
.btn-link {
  color: #337ab7;
  font-weight: normal;
  border-radius: 0;
}
.btn-link,
.btn-link:active,
.btn-link.active,
.btn-link[disabled],
fieldset[disabled] .btn-link {
  background-color: transparent;
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn-link,
.btn-link:hover,
.btn-link:focus,
.btn-link:active {
  border-color: transparent;
}
.btn-link:hover,
.btn-link:focus {
  color: #23527c;
  text-decoration: underline;
  background-color: transparent;
}
.btn-link[disabled]:hover,
fieldset[disabled] .btn-link:hover,
.btn-link[disabled]:focus,
fieldset[disabled] .btn-link:focus {
  color: #777777;
  text-decoration: none;
}
.btn-lg,
.btn-group-lg > .btn {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.btn-sm,
.btn-group-sm > .btn {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-xs,
.btn-group-xs > .btn {
  padding: 1px 5px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-block {
  display: block;
  width: 100%;
}
.btn-block + .btn-block {
  margin-top: 5px;
}
input[type="submit"].btn-block,
input[type="reset"].btn-block,
input[type="button"].btn-block {
  width: 100%;
}
.fade {
  opacity: 0;
  -webkit-transition: opacity 0.15s linear;
  -o-transition: opacity 0.15s linear;
  transition: opacity 0.15s linear;
}
.fade.in {
  opacity: 1;
}
.collapse {
  display: none;
}
.collapse.in {
  display: block;
}
tr.collapse.in {
  display: table-row;
}
tbody.collapse.in {
  display: table-row-group;
}
.collapsing {
  position: relative;
  height: 0;
  overflow: hidden;
  -webkit-transition-property: height, visibility;
  transition-property: height, visibility;
  -webkit-transition-duration: 0.35s;
  transition-duration: 0.35s;
  -webkit-transition-timing-function: ease;
  transition-timing-function: ease;
}
.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px dashed;
  border-top: 4px solid \9;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}
.dropup,
.dropdown {
  position: relative;
}
.dropdown-toggle:focus {
  outline: 0;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1000;
  display: none;
  float: left;
  min-width: 160px;
  padding: 5px 0;
  margin: 2px 0 0;
  list-style: none;
  font-size: 13px;
  text-align: left;
  background-color: #fff;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.15);
  border-radius: 2px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  background-clip: padding-box;
}
.dropdown-menu.pull-right {
  right: 0;
  left: auto;
}
.dropdown-menu .divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.dropdown-menu > li > a {
  display: block;
  padding: 3px 20px;
  clear: both;
  font-weight: normal;
  line-height: 1.42857143;
  color: #333333;
  white-space: nowrap;
}
.dropdown-menu > li > a:hover,
.dropdown-menu > li > a:focus {
  text-decoration: none;
  color: #262626;
  background-color: #f5f5f5;
}
.dropdown-menu > .active > a,
.dropdown-menu > .active > a:hover,
.dropdown-menu > .active > a:focus {
  color: #fff;
  text-decoration: none;
  outline: 0;
  background-color: #337ab7;
}
.dropdown-menu > .disabled > a,
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  color: #777777;
}
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  text-decoration: none;
  background-color: transparent;
  background-image: none;
  filter: progid:DXImageTransform.Microsoft.gradient(enabled = false);
  cursor: not-allowed;
}
.open > .dropdown-menu {
  display: block;
}
.open > a {
  outline: 0;
}
.dropdown-menu-right {
  left: auto;
  right: 0;
}
.dropdown-menu-left {
  left: 0;
  right: auto;
}
.dropdown-header {
  display: block;
  padding: 3px 20px;
  font-size: 12px;
  line-height: 1.42857143;
  color: #777777;
  white-space: nowrap;
}
.dropdown-backdrop {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 990;
}
.pull-right > .dropdown-menu {
  right: 0;
  left: auto;
}
.dropup .caret,
.navbar-fixed-bottom .dropdown .caret {
  border-top: 0;
  border-bottom: 4px dashed;
  border-bottom: 4px solid \9;
  content: "";
}
.dropup .dropdown-menu,
.navbar-fixed-bottom .dropdown .dropdown-menu {
  top: auto;
  bottom: 100%;
  margin-bottom: 2px;
}
@media (min-width: 541px) {
  .navbar-right .dropdown-menu {
    left: auto;
    right: 0;
  }
  .navbar-right .dropdown-menu-left {
    left: 0;
    right: auto;
  }
}
.btn-group,
.btn-group-vertical {
  position: relative;
  display: inline-block;
  vertical-align: middle;
}
.btn-group > .btn,
.btn-group-vertical > .btn {
  position: relative;
  float: left;
}
.btn-group > .btn:hover,
.btn-group-vertical > .btn:hover,
.btn-group > .btn:focus,
.btn-group-vertical > .btn:focus,
.btn-group > .btn:active,
.btn-group-vertical > .btn:active,
.btn-group > .btn.active,
.btn-group-vertical > .btn.active {
  z-index: 2;
}
.btn-group .btn + .btn,
.btn-group .btn + .btn-group,
.btn-group .btn-group + .btn,
.btn-group .btn-group + .btn-group {
  margin-left: -1px;
}
.btn-toolbar {
  margin-left: -5px;
}
.btn-toolbar .btn,
.btn-toolbar .btn-group,
.btn-toolbar .input-group {
  float: left;
}
.btn-toolbar > .btn,
.btn-toolbar > .btn-group,
.btn-toolbar > .input-group {
  margin-left: 5px;
}
.btn-group > .btn:not(:first-child):not(:last-child):not(.dropdown-toggle) {
  border-radius: 0;
}
.btn-group > .btn:first-child {
  margin-left: 0;
}
.btn-group > .btn:first-child:not(:last-child):not(.dropdown-toggle) {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn:last-child:not(:first-child),
.btn-group > .dropdown-toggle:not(:first-child) {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group > .btn-group {
  float: left;
}
.btn-group > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group .dropdown-toggle:active,
.btn-group.open .dropdown-toggle {
  outline: 0;
}
.btn-group > .btn + .dropdown-toggle {
  padding-left: 8px;
  padding-right: 8px;
}
.btn-group > .btn-lg + .dropdown-toggle {
  padding-left: 12px;
  padding-right: 12px;
}
.btn-group.open .dropdown-toggle {
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn-group.open .dropdown-toggle.btn-link {
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn .caret {
  margin-left: 0;
}
.btn-lg .caret {
  border-width: 5px 5px 0;
  border-bottom-width: 0;
}
.dropup .btn-lg .caret {
  border-width: 0 5px 5px;
}
.btn-group-vertical > .btn,
.btn-group-vertical > .btn-group,
.btn-group-vertical > .btn-group > .btn {
  display: block;
  float: none;
  width: 100%;
  max-width: 100%;
}
.btn-group-vertical > .btn-group > .btn {
  float: none;
}
.btn-group-vertical > .btn + .btn,
.btn-group-vertical > .btn + .btn-group,
.btn-group-vertical > .btn-group + .btn,
.btn-group-vertical > .btn-group + .btn-group {
  margin-top: -1px;
  margin-left: 0;
}
.btn-group-vertical > .btn:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.btn-group-vertical > .btn:first-child:not(:last-child) {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn:last-child:not(:first-child) {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
.btn-group-vertical > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.btn-group-justified {
  display: table;
  width: 100%;
  table-layout: fixed;
  border-collapse: separate;
}
.btn-group-justified > .btn,
.btn-group-justified > .btn-group {
  float: none;
  display: table-cell;
  width: 1%;
}
.btn-group-justified > .btn-group .btn {
  width: 100%;
}
.btn-group-justified > .btn-group .dropdown-menu {
  left: auto;
}
[data-toggle="buttons"] > .btn input[type="radio"],
[data-toggle="buttons"] > .btn-group > .btn input[type="radio"],
[data-toggle="buttons"] > .btn input[type="checkbox"],
[data-toggle="buttons"] > .btn-group > .btn input[type="checkbox"] {
  position: absolute;
  clip: rect(0, 0, 0, 0);
  pointer-events: none;
}
.input-group {
  position: relative;
  display: table;
  border-collapse: separate;
}
.input-group[class*="col-"] {
  float: none;
  padding-left: 0;
  padding-right: 0;
}
.input-group .form-control {
  position: relative;
  z-index: 2;
  float: left;
  width: 100%;
  margin-bottom: 0;
}
.input-group .form-control:focus {
  z-index: 3;
}
.input-group-lg > .form-control,
.input-group-lg > .input-group-addon,
.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-group-lg > .form-control,
select.input-group-lg > .input-group-addon,
select.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  line-height: 45px;
}
textarea.input-group-lg > .form-control,
textarea.input-group-lg > .input-group-addon,
textarea.input-group-lg > .input-group-btn > .btn,
select[multiple].input-group-lg > .form-control,
select[multiple].input-group-lg > .input-group-addon,
select[multiple].input-group-lg > .input-group-btn > .btn {
  height: auto;
}
.input-group-sm > .form-control,
.input-group-sm > .input-group-addon,
.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-group-sm > .form-control,
select.input-group-sm > .input-group-addon,
select.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  line-height: 30px;
}
textarea.input-group-sm > .form-control,
textarea.input-group-sm > .input-group-addon,
textarea.input-group-sm > .input-group-btn > .btn,
select[multiple].input-group-sm > .form-control,
select[multiple].input-group-sm > .input-group-addon,
select[multiple].input-group-sm > .input-group-btn > .btn {
  height: auto;
}
.input-group-addon,
.input-group-btn,
.input-group .form-control {
  display: table-cell;
}
.input-group-addon:not(:first-child):not(:last-child),
.input-group-btn:not(:first-child):not(:last-child),
.input-group .form-control:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.input-group-addon,
.input-group-btn {
  width: 1%;
  white-space: nowrap;
  vertical-align: middle;
}
.input-group-addon {
  padding: 6px 12px;
  font-size: 13px;
  font-weight: normal;
  line-height: 1;
  color: #555555;
  text-align: center;
  background-color: #eeeeee;
  border: 1px solid #ccc;
  border-radius: 2px;
}
.input-group-addon.input-sm {
  padding: 5px 10px;
  font-size: 12px;
  border-radius: 1px;
}
.input-group-addon.input-lg {
  padding: 10px 16px;
  font-size: 17px;
  border-radius: 3px;
}
.input-group-addon input[type="radio"],
.input-group-addon input[type="checkbox"] {
  margin-top: 0;
}
.input-group .form-control:first-child,
.input-group-addon:first-child,
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group > .btn,
.input-group-btn:first-child > .dropdown-toggle,
.input-group-btn:last-child > .btn:not(:last-child):not(.dropdown-toggle),
.input-group-btn:last-child > .btn-group:not(:last-child) > .btn {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.input-group-addon:first-child {
  border-right: 0;
}
.input-group .form-control:last-child,
.input-group-addon:last-child,
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group > .btn,
.input-group-btn:last-child > .dropdown-toggle,
.input-group-btn:first-child > .btn:not(:first-child),
.input-group-btn:first-child > .btn-group:not(:first-child) > .btn {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.input-group-addon:last-child {
  border-left: 0;
}
.input-group-btn {
  position: relative;
  font-size: 0;
  white-space: nowrap;
}
.input-group-btn > .btn {
  position: relative;
}
.input-group-btn > .btn + .btn {
  margin-left: -1px;
}
.input-group-btn > .btn:hover,
.input-group-btn > .btn:focus,
.input-group-btn > .btn:active {
  z-index: 2;
}
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group {
  margin-right: -1px;
}
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group {
  z-index: 2;
  margin-left: -1px;
}
.nav {
  margin-bottom: 0;
  padding-left: 0;
  list-style: none;
}
.nav > li {
  position: relative;
  display: block;
}
.nav > li > a {
  position: relative;
  display: block;
  padding: 10px 15px;
}
.nav > li > a:hover,
.nav > li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.nav > li.disabled > a {
  color: #777777;
}
.nav > li.disabled > a:hover,
.nav > li.disabled > a:focus {
  color: #777777;
  text-decoration: none;
  background-color: transparent;
  cursor: not-allowed;
}
.nav .open > a,
.nav .open > a:hover,
.nav .open > a:focus {
  background-color: #eeeeee;
  border-color: #337ab7;
}
.nav .nav-divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.nav > li > a > img {
  max-width: none;
}
.nav-tabs {
  border-bottom: 1px solid #ddd;
}
.nav-tabs > li {
  float: left;
  margin-bottom: -1px;
}
.nav-tabs > li > a {
  margin-right: 2px;
  line-height: 1.42857143;
  border: 1px solid transparent;
  border-radius: 2px 2px 0 0;
}
.nav-tabs > li > a:hover {
  border-color: #eeeeee #eeeeee #ddd;
}
.nav-tabs > li.active > a,
.nav-tabs > li.active > a:hover,
.nav-tabs > li.active > a:focus {
  color: #555555;
  background-color: #fff;
  border: 1px solid #ddd;
  border-bottom-color: transparent;
  cursor: default;
}
.nav-tabs.nav-justified {
  width: 100%;
  border-bottom: 0;
}
.nav-tabs.nav-justified > li {
  float: none;
}
.nav-tabs.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-tabs.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-tabs.nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs.nav-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs.nav-justified > .active > a,
.nav-tabs.nav-justified > .active > a:hover,
.nav-tabs.nav-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs.nav-justified > .active > a,
  .nav-tabs.nav-justified > .active > a:hover,
  .nav-tabs.nav-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.nav-pills > li {
  float: left;
}
.nav-pills > li > a {
  border-radius: 2px;
}
.nav-pills > li + li {
  margin-left: 2px;
}
.nav-pills > li.active > a,
.nav-pills > li.active > a:hover,
.nav-pills > li.active > a:focus {
  color: #fff;
  background-color: #337ab7;
}
.nav-stacked > li {
  float: none;
}
.nav-stacked > li + li {
  margin-top: 2px;
  margin-left: 0;
}
.nav-justified {
  width: 100%;
}
.nav-justified > li {
  float: none;
}
.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs-justified {
  border-bottom: 0;
}
.nav-tabs-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs-justified > .active > a,
.nav-tabs-justified > .active > a:hover,
.nav-tabs-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs-justified > .active > a,
  .nav-tabs-justified > .active > a:hover,
  .nav-tabs-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.tab-content > .tab-pane {
  display: none;
}
.tab-content > .active {
  display: block;
}
.nav-tabs .dropdown-menu {
  margin-top: -1px;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar {
  position: relative;
  min-height: 30px;
  margin-bottom: 18px;
  border: 1px solid transparent;
}
@media (min-width: 541px) {
  .navbar {
    border-radius: 2px;
  }
}
@media (min-width: 541px) {
  .navbar-header {
    float: left;
  }
}
.navbar-collapse {
  overflow-x: visible;
  padding-right: 0px;
  padding-left: 0px;
  border-top: 1px solid transparent;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
  -webkit-overflow-scrolling: touch;
}
.navbar-collapse.in {
  overflow-y: auto;
}
@media (min-width: 541px) {
  .navbar-collapse {
    width: auto;
    border-top: 0;
    box-shadow: none;
  }
  .navbar-collapse.collapse {
    display: block !important;
    height: auto !important;
    padding-bottom: 0;
    overflow: visible !important;
  }
  .navbar-collapse.in {
    overflow-y: visible;
  }
  .navbar-fixed-top .navbar-collapse,
  .navbar-static-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    padding-left: 0;
    padding-right: 0;
  }
}
.navbar-fixed-top .navbar-collapse,
.navbar-fixed-bottom .navbar-collapse {
  max-height: 340px;
}
@media (max-device-width: 540px) and (orientation: landscape) {
  .navbar-fixed-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    max-height: 200px;
  }
}
.container > .navbar-header,
.container-fluid > .navbar-header,
.container > .navbar-collapse,
.container-fluid > .navbar-collapse {
  margin-right: 0px;
  margin-left: 0px;
}
@media (min-width: 541px) {
  .container > .navbar-header,
  .container-fluid > .navbar-header,
  .container > .navbar-collapse,
  .container-fluid > .navbar-collapse {
    margin-right: 0;
    margin-left: 0;
  }
}
.navbar-static-top {
  z-index: 1000;
  border-width: 0 0 1px;
}
@media (min-width: 541px) {
  .navbar-static-top {
    border-radius: 0;
  }
}
.navbar-fixed-top,
.navbar-fixed-bottom {
  position: fixed;
  right: 0;
  left: 0;
  z-index: 1030;
}
@media (min-width: 541px) {
  .navbar-fixed-top,
  .navbar-fixed-bottom {
    border-radius: 0;
  }
}
.navbar-fixed-top {
  top: 0;
  border-width: 0 0 1px;
}
.navbar-fixed-bottom {
  bottom: 0;
  margin-bottom: 0;
  border-width: 1px 0 0;
}
.navbar-brand {
  float: left;
  padding: 6px 0px;
  font-size: 17px;
  line-height: 18px;
  height: 30px;
}
.navbar-brand:hover,
.navbar-brand:focus {
  text-decoration: none;
}
.navbar-brand > img {
  display: block;
}
@media (min-width: 541px) {
  .navbar > .container .navbar-brand,
  .navbar > .container-fluid .navbar-brand {
    margin-left: 0px;
  }
}
.navbar-toggle {
  position: relative;
  float: right;
  margin-right: 0px;
  padding: 9px 10px;
  margin-top: -2px;
  margin-bottom: -2px;
  background-color: transparent;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 2px;
}
.navbar-toggle:focus {
  outline: 0;
}
.navbar-toggle .icon-bar {
  display: block;
  width: 22px;
  height: 2px;
  border-radius: 1px;
}
.navbar-toggle .icon-bar + .icon-bar {
  margin-top: 4px;
}
@media (min-width: 541px) {
  .navbar-toggle {
    display: none;
  }
}
.navbar-nav {
  margin: 3px 0px;
}
.navbar-nav > li > a {
  padding-top: 10px;
  padding-bottom: 10px;
  line-height: 18px;
}
@media (max-width: 540px) {
  .navbar-nav .open .dropdown-menu {
    position: static;
    float: none;
    width: auto;
    margin-top: 0;
    background-color: transparent;
    border: 0;
    box-shadow: none;
  }
  .navbar-nav .open .dropdown-menu > li > a,
  .navbar-nav .open .dropdown-menu .dropdown-header {
    padding: 5px 15px 5px 25px;
  }
  .navbar-nav .open .dropdown-menu > li > a {
    line-height: 18px;
  }
  .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-nav .open .dropdown-menu > li > a:focus {
    background-image: none;
  }
}
@media (min-width: 541px) {
  .navbar-nav {
    float: left;
    margin: 0;
  }
  .navbar-nav > li {
    float: left;
  }
  .navbar-nav > li > a {
    padding-top: 6px;
    padding-bottom: 6px;
  }
}
.navbar-form {
  margin-left: 0px;
  margin-right: 0px;
  padding: 10px 0px;
  border-top: 1px solid transparent;
  border-bottom: 1px solid transparent;
  -webkit-box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  margin-top: -1px;
  margin-bottom: -1px;
}
@media (min-width: 768px) {
  .navbar-form .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .navbar-form .form-control-static {
    display: inline-block;
  }
  .navbar-form .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .navbar-form .input-group .input-group-addon,
  .navbar-form .input-group .input-group-btn,
  .navbar-form .input-group .form-control {
    width: auto;
  }
  .navbar-form .input-group > .form-control {
    width: 100%;
  }
  .navbar-form .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio,
  .navbar-form .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio label,
  .navbar-form .checkbox label {
    padding-left: 0;
  }
  .navbar-form .radio input[type="radio"],
  .navbar-form .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .navbar-form .has-feedback .form-control-feedback {
    top: 0;
  }
}
@media (max-width: 540px) {
  .navbar-form .form-group {
    margin-bottom: 5px;
  }
  .navbar-form .form-group:last-child {
    margin-bottom: 0;
  }
}
@media (min-width: 541px) {
  .navbar-form {
    width: auto;
    border: 0;
    margin-left: 0;
    margin-right: 0;
    padding-top: 0;
    padding-bottom: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
  }
}
.navbar-nav > li > .dropdown-menu {
  margin-top: 0;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar-fixed-bottom .navbar-nav > li > .dropdown-menu {
  margin-bottom: 0;
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.navbar-btn {
  margin-top: -1px;
  margin-bottom: -1px;
}
.navbar-btn.btn-sm {
  margin-top: 0px;
  margin-bottom: 0px;
}
.navbar-btn.btn-xs {
  margin-top: 4px;
  margin-bottom: 4px;
}
.navbar-text {
  margin-top: 6px;
  margin-bottom: 6px;
}
@media (min-width: 541px) {
  .navbar-text {
    float: left;
    margin-left: 0px;
    margin-right: 0px;
  }
}
@media (min-width: 541px) {
  .navbar-left {
    float: left !important;
    float: left;
  }
  .navbar-right {
    float: right !important;
    float: right;
    margin-right: 0px;
  }
  .navbar-right ~ .navbar-right {
    margin-right: 0;
  }
}
.navbar-default {
  background-color: #f8f8f8;
  border-color: #e7e7e7;
}
.navbar-default .navbar-brand {
  color: #777;
}
.navbar-default .navbar-brand:hover,
.navbar-default .navbar-brand:focus {
  color: #5e5e5e;
  background-color: transparent;
}
.navbar-default .navbar-text {
  color: #777;
}
.navbar-default .navbar-nav > li > a {
  color: #777;
}
.navbar-default .navbar-nav > li > a:hover,
.navbar-default .navbar-nav > li > a:focus {
  color: #333;
  background-color: transparent;
}
.navbar-default .navbar-nav > .active > a,
.navbar-default .navbar-nav > .active > a:hover,
.navbar-default .navbar-nav > .active > a:focus {
  color: #555;
  background-color: #e7e7e7;
}
.navbar-default .navbar-nav > .disabled > a,
.navbar-default .navbar-nav > .disabled > a:hover,
.navbar-default .navbar-nav > .disabled > a:focus {
  color: #ccc;
  background-color: transparent;
}
.navbar-default .navbar-toggle {
  border-color: #ddd;
}
.navbar-default .navbar-toggle:hover,
.navbar-default .navbar-toggle:focus {
  background-color: #ddd;
}
.navbar-default .navbar-toggle .icon-bar {
  background-color: #888;
}
.navbar-default .navbar-collapse,
.navbar-default .navbar-form {
  border-color: #e7e7e7;
}
.navbar-default .navbar-nav > .open > a,
.navbar-default .navbar-nav > .open > a:hover,
.navbar-default .navbar-nav > .open > a:focus {
  background-color: #e7e7e7;
  color: #555;
}
@media (max-width: 540px) {
  .navbar-default .navbar-nav .open .dropdown-menu > li > a {
    color: #777;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #333;
    background-color: transparent;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #555;
    background-color: #e7e7e7;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #ccc;
    background-color: transparent;
  }
}
.navbar-default .navbar-link {
  color: #777;
}
.navbar-default .navbar-link:hover {
  color: #333;
}
.navbar-default .btn-link {
  color: #777;
}
.navbar-default .btn-link:hover,
.navbar-default .btn-link:focus {
  color: #333;
}
.navbar-default .btn-link[disabled]:hover,
fieldset[disabled] .navbar-default .btn-link:hover,
.navbar-default .btn-link[disabled]:focus,
fieldset[disabled] .navbar-default .btn-link:focus {
  color: #ccc;
}
.navbar-inverse {
  background-color: #222;
  border-color: #080808;
}
.navbar-inverse .navbar-brand {
  color: #9d9d9d;
}
.navbar-inverse .navbar-brand:hover,
.navbar-inverse .navbar-brand:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-text {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a:hover,
.navbar-inverse .navbar-nav > li > a:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-nav > .active > a,
.navbar-inverse .navbar-nav > .active > a:hover,
.navbar-inverse .navbar-nav > .active > a:focus {
  color: #fff;
  background-color: #080808;
}
.navbar-inverse .navbar-nav > .disabled > a,
.navbar-inverse .navbar-nav > .disabled > a:hover,
.navbar-inverse .navbar-nav > .disabled > a:focus {
  color: #444;
  background-color: transparent;
}
.navbar-inverse .navbar-toggle {
  border-color: #333;
}
.navbar-inverse .navbar-toggle:hover,
.navbar-inverse .navbar-toggle:focus {
  background-color: #333;
}
.navbar-inverse .navbar-toggle .icon-bar {
  background-color: #fff;
}
.navbar-inverse .navbar-collapse,
.navbar-inverse .navbar-form {
  border-color: #101010;
}
.navbar-inverse .navbar-nav > .open > a,
.navbar-inverse .navbar-nav > .open > a:hover,
.navbar-inverse .navbar-nav > .open > a:focus {
  background-color: #080808;
  color: #fff;
}
@media (max-width: 540px) {
  .navbar-inverse .navbar-nav .open .dropdown-menu > .dropdown-header {
    border-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu .divider {
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a {
    color: #9d9d9d;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #fff;
    background-color: transparent;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #fff;
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #444;
    background-color: transparent;
  }
}
.navbar-inverse .navbar-link {
  color: #9d9d9d;
}
.navbar-inverse .navbar-link:hover {
  color: #fff;
}
.navbar-inverse .btn-link {
  color: #9d9d9d;
}
.navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link:focus {
  color: #fff;
}
.navbar-inverse .btn-link[disabled]:hover,
fieldset[disabled] .navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link[disabled]:focus,
fieldset[disabled] .navbar-inverse .btn-link:focus {
  color: #444;
}
.breadcrumb {
  padding: 8px 15px;
  margin-bottom: 18px;
  list-style: none;
  background-color: #f5f5f5;
  border-radius: 2px;
}
.breadcrumb > li {
  display: inline-block;
}
.breadcrumb > li + li:before {
  content: "/\00a0";
  padding: 0 5px;
  color: #5e5e5e;
}
.breadcrumb > .active {
  color: #777777;
}
.pagination {
  display: inline-block;
  padding-left: 0;
  margin: 18px 0;
  border-radius: 2px;
}
.pagination > li {
  display: inline;
}
.pagination > li > a,
.pagination > li > span {
  position: relative;
  float: left;
  padding: 6px 12px;
  line-height: 1.42857143;
  text-decoration: none;
  color: #337ab7;
  background-color: #fff;
  border: 1px solid #ddd;
  margin-left: -1px;
}
.pagination > li:first-child > a,
.pagination > li:first-child > span {
  margin-left: 0;
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.pagination > li:last-child > a,
.pagination > li:last-child > span {
  border-bottom-right-radius: 2px;
  border-top-right-radius: 2px;
}
.pagination > li > a:hover,
.pagination > li > span:hover,
.pagination > li > a:focus,
.pagination > li > span:focus {
  z-index: 2;
  color: #23527c;
  background-color: #eeeeee;
  border-color: #ddd;
}
.pagination > .active > a,
.pagination > .active > span,
.pagination > .active > a:hover,
.pagination > .active > span:hover,
.pagination > .active > a:focus,
.pagination > .active > span:focus {
  z-index: 3;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
  cursor: default;
}
.pagination > .disabled > span,
.pagination > .disabled > span:hover,
.pagination > .disabled > span:focus,
.pagination > .disabled > a,
.pagination > .disabled > a:hover,
.pagination > .disabled > a:focus {
  color: #777777;
  background-color: #fff;
  border-color: #ddd;
  cursor: not-allowed;
}
.pagination-lg > li > a,
.pagination-lg > li > span {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.pagination-lg > li:first-child > a,
.pagination-lg > li:first-child > span {
  border-bottom-left-radius: 3px;
  border-top-left-radius: 3px;
}
.pagination-lg > li:last-child > a,
.pagination-lg > li:last-child > span {
  border-bottom-right-radius: 3px;
  border-top-right-radius: 3px;
}
.pagination-sm > li > a,
.pagination-sm > li > span {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.pagination-sm > li:first-child > a,
.pagination-sm > li:first-child > span {
  border-bottom-left-radius: 1px;
  border-top-left-radius: 1px;
}
.pagination-sm > li:last-child > a,
.pagination-sm > li:last-child > span {
  border-bottom-right-radius: 1px;
  border-top-right-radius: 1px;
}
.pager {
  padding-left: 0;
  margin: 18px 0;
  list-style: none;
  text-align: center;
}
.pager li {
  display: inline;
}
.pager li > a,
.pager li > span {
  display: inline-block;
  padding: 5px 14px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 15px;
}
.pager li > a:hover,
.pager li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.pager .next > a,
.pager .next > span {
  float: right;
}
.pager .previous > a,
.pager .previous > span {
  float: left;
}
.pager .disabled > a,
.pager .disabled > a:hover,
.pager .disabled > a:focus,
.pager .disabled > span {
  color: #777777;
  background-color: #fff;
  cursor: not-allowed;
}
.label {
  display: inline;
  padding: .2em .6em .3em;
  font-size: 75%;
  font-weight: bold;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: .25em;
}
a.label:hover,
a.label:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.label:empty {
  display: none;
}
.btn .label {
  position: relative;
  top: -1px;
}
.label-default {
  background-color: #777777;
}
.label-default[href]:hover,
.label-default[href]:focus {
  background-color: #5e5e5e;
}
.label-primary {
  background-color: #337ab7;
}
.label-primary[href]:hover,
.label-primary[href]:focus {
  background-color: #286090;
}
.label-success {
  background-color: #5cb85c;
}
.label-success[href]:hover,
.label-success[href]:focus {
  background-color: #449d44;
}
.label-info {
  background-color: #5bc0de;
}
.label-info[href]:hover,
.label-info[href]:focus {
  background-color: #31b0d5;
}
.label-warning {
  background-color: #f0ad4e;
}
.label-warning[href]:hover,
.label-warning[href]:focus {
  background-color: #ec971f;
}
.label-danger {
  background-color: #d9534f;
}
.label-danger[href]:hover,
.label-danger[href]:focus {
  background-color: #c9302c;
}
.badge {
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  font-size: 12px;
  font-weight: bold;
  color: #fff;
  line-height: 1;
  vertical-align: middle;
  white-space: nowrap;
  text-align: center;
  background-color: #777777;
  border-radius: 10px;
}
.badge:empty {
  display: none;
}
.btn .badge {
  position: relative;
  top: -1px;
}
.btn-xs .badge,
.btn-group-xs > .btn .badge {
  top: 0;
  padding: 1px 5px;
}
a.badge:hover,
a.badge:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.list-group-item.active > .badge,
.nav-pills > .active > a > .badge {
  color: #337ab7;
  background-color: #fff;
}
.list-group-item > .badge {
  float: right;
}
.list-group-item > .badge + .badge {
  margin-right: 5px;
}
.nav-pills > li > a > .badge {
  margin-left: 3px;
}
.jumbotron {
  padding-top: 30px;
  padding-bottom: 30px;
  margin-bottom: 30px;
  color: inherit;
  background-color: #eeeeee;
}
.jumbotron h1,
.jumbotron .h1 {
  color: inherit;
}
.jumbotron p {
  margin-bottom: 15px;
  font-size: 20px;
  font-weight: 200;
}
.jumbotron > hr {
  border-top-color: #d5d5d5;
}
.container .jumbotron,
.container-fluid .jumbotron {
  border-radius: 3px;
  padding-left: 0px;
  padding-right: 0px;
}
.jumbotron .container {
  max-width: 100%;
}
@media screen and (min-width: 768px) {
  .jumbotron {
    padding-top: 48px;
    padding-bottom: 48px;
  }
  .container .jumbotron,
  .container-fluid .jumbotron {
    padding-left: 60px;
    padding-right: 60px;
  }
  .jumbotron h1,
  .jumbotron .h1 {
    font-size: 59px;
  }
}
.thumbnail {
  display: block;
  padding: 4px;
  margin-bottom: 18px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: border 0.2s ease-in-out;
  -o-transition: border 0.2s ease-in-out;
  transition: border 0.2s ease-in-out;
}
.thumbnail > img,
.thumbnail a > img {
  margin-left: auto;
  margin-right: auto;
}
a.thumbnail:hover,
a.thumbnail:focus,
a.thumbnail.active {
  border-color: #337ab7;
}
.thumbnail .caption {
  padding: 9px;
  color: #000;
}
.alert {
  padding: 15px;
  margin-bottom: 18px;
  border: 1px solid transparent;
  border-radius: 2px;
}
.alert h4 {
  margin-top: 0;
  color: inherit;
}
.alert .alert-link {
  font-weight: bold;
}
.alert > p,
.alert > ul {
  margin-bottom: 0;
}
.alert > p + p {
  margin-top: 5px;
}
.alert-dismissable,
.alert-dismissible {
  padding-right: 35px;
}
.alert-dismissable .close,
.alert-dismissible .close {
  position: relative;
  top: -2px;
  right: -21px;
  color: inherit;
}
.alert-success {
  background-color: #dff0d8;
  border-color: #d6e9c6;
  color: #3c763d;
}
.alert-success hr {
  border-top-color: #c9e2b3;
}
.alert-success .alert-link {
  color: #2b542c;
}
.alert-info {
  background-color: #d9edf7;
  border-color: #bce8f1;
  color: #31708f;
}
.alert-info hr {
  border-top-color: #a6e1ec;
}
.alert-info .alert-link {
  color: #245269;
}
.alert-warning {
  background-color: #fcf8e3;
  border-color: #faebcc;
  color: #8a6d3b;
}
.alert-warning hr {
  border-top-color: #f7e1b5;
}
.alert-warning .alert-link {
  color: #66512c;
}
.alert-danger {
  background-color: #f2dede;
  border-color: #ebccd1;
  color: #a94442;
}
.alert-danger hr {
  border-top-color: #e4b9c0;
}
.alert-danger .alert-link {
  color: #843534;
}
@-webkit-keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
@keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
.progress {
  overflow: hidden;
  height: 18px;
  margin-bottom: 18px;
  background-color: #f5f5f5;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
}
.progress-bar {
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 18px;
  color: #fff;
  text-align: center;
  background-color: #337ab7;
  -webkit-box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  -webkit-transition: width 0.6s ease;
  -o-transition: width 0.6s ease;
  transition: width 0.6s ease;
}
.progress-striped .progress-bar,
.progress-bar-striped {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-size: 40px 40px;
}
.progress.active .progress-bar,
.progress-bar.active {
  -webkit-animation: progress-bar-stripes 2s linear infinite;
  -o-animation: progress-bar-stripes 2s linear infinite;
  animation: progress-bar-stripes 2s linear infinite;
}
.progress-bar-success {
  background-color: #5cb85c;
}
.progress-striped .progress-bar-success {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-info {
  background-color: #5bc0de;
}
.progress-striped .progress-bar-info {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-warning {
  background-color: #f0ad4e;
}
.progress-striped .progress-bar-warning {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-danger {
  background-color: #d9534f;
}
.progress-striped .progress-bar-danger {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.media {
  margin-top: 15px;
}
.media:first-child {
  margin-top: 0;
}
.media,
.media-body {
  zoom: 1;
  overflow: hidden;
}
.media-body {
  width: 10000px;
}
.media-object {
  display: block;
}
.media-object.img-thumbnail {
  max-width: none;
}
.media-right,
.media > .pull-right {
  padding-left: 10px;
}
.media-left,
.media > .pull-left {
  padding-right: 10px;
}
.media-left,
.media-right,
.media-body {
  display: table-cell;
  vertical-align: top;
}
.media-middle {
  vertical-align: middle;
}
.media-bottom {
  vertical-align: bottom;
}
.media-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.media-list {
  padding-left: 0;
  list-style: none;
}
.list-group {
  margin-bottom: 20px;
  padding-left: 0;
}
.list-group-item {
  position: relative;
  display: block;
  padding: 10px 15px;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid #ddd;
}
.list-group-item:first-child {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
}
.list-group-item:last-child {
  margin-bottom: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
a.list-group-item,
button.list-group-item {
  color: #555;
}
a.list-group-item .list-group-item-heading,
button.list-group-item .list-group-item-heading {
  color: #333;
}
a.list-group-item:hover,
button.list-group-item:hover,
a.list-group-item:focus,
button.list-group-item:focus {
  text-decoration: none;
  color: #555;
  background-color: #f5f5f5;
}
button.list-group-item {
  width: 100%;
  text-align: left;
}
.list-group-item.disabled,
.list-group-item.disabled:hover,
.list-group-item.disabled:focus {
  background-color: #eeeeee;
  color: #777777;
  cursor: not-allowed;
}
.list-group-item.disabled .list-group-item-heading,
.list-group-item.disabled:hover .list-group-item-heading,
.list-group-item.disabled:focus .list-group-item-heading {
  color: inherit;
}
.list-group-item.disabled .list-group-item-text,
.list-group-item.disabled:hover .list-group-item-text,
.list-group-item.disabled:focus .list-group-item-text {
  color: #777777;
}
.list-group-item.active,
.list-group-item.active:hover,
.list-group-item.active:focus {
  z-index: 2;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.list-group-item.active .list-group-item-heading,
.list-group-item.active:hover .list-group-item-heading,
.list-group-item.active:focus .list-group-item-heading,
.list-group-item.active .list-group-item-heading > small,
.list-group-item.active:hover .list-group-item-heading > small,
.list-group-item.active:focus .list-group-item-heading > small,
.list-group-item.active .list-group-item-heading > .small,
.list-group-item.active:hover .list-group-item-heading > .small,
.list-group-item.active:focus .list-group-item-heading > .small {
  color: inherit;
}
.list-group-item.active .list-group-item-text,
.list-group-item.active:hover .list-group-item-text,
.list-group-item.active:focus .list-group-item-text {
  color: #c7ddef;
}
.list-group-item-success {
  color: #3c763d;
  background-color: #dff0d8;
}
a.list-group-item-success,
button.list-group-item-success {
  color: #3c763d;
}
a.list-group-item-success .list-group-item-heading,
button.list-group-item-success .list-group-item-heading {
  color: inherit;
}
a.list-group-item-success:hover,
button.list-group-item-success:hover,
a.list-group-item-success:focus,
button.list-group-item-success:focus {
  color: #3c763d;
  background-color: #d0e9c6;
}
a.list-group-item-success.active,
button.list-group-item-success.active,
a.list-group-item-success.active:hover,
button.list-group-item-success.active:hover,
a.list-group-item-success.active:focus,
button.list-group-item-success.active:focus {
  color: #fff;
  background-color: #3c763d;
  border-color: #3c763d;
}
.list-group-item-info {
  color: #31708f;
  background-color: #d9edf7;
}
a.list-group-item-info,
button.list-group-item-info {
  color: #31708f;
}
a.list-group-item-info .list-group-item-heading,
button.list-group-item-info .list-group-item-heading {
  color: inherit;
}
a.list-group-item-info:hover,
button.list-group-item-info:hover,
a.list-group-item-info:focus,
button.list-group-item-info:focus {
  color: #31708f;
  background-color: #c4e3f3;
}
a.list-group-item-info.active,
button.list-group-item-info.active,
a.list-group-item-info.active:hover,
button.list-group-item-info.active:hover,
a.list-group-item-info.active:focus,
button.list-group-item-info.active:focus {
  color: #fff;
  background-color: #31708f;
  border-color: #31708f;
}
.list-group-item-warning {
  color: #8a6d3b;
  background-color: #fcf8e3;
}
a.list-group-item-warning,
button.list-group-item-warning {
  color: #8a6d3b;
}
a.list-group-item-warning .list-group-item-heading,
button.list-group-item-warning .list-group-item-heading {
  color: inherit;
}
a.list-group-item-warning:hover,
button.list-group-item-warning:hover,
a.list-group-item-warning:focus,
button.list-group-item-warning:focus {
  color: #8a6d3b;
  background-color: #faf2cc;
}
a.list-group-item-warning.active,
button.list-group-item-warning.active,
a.list-group-item-warning.active:hover,
button.list-group-item-warning.active:hover,
a.list-group-item-warning.active:focus,
button.list-group-item-warning.active:focus {
  color: #fff;
  background-color: #8a6d3b;
  border-color: #8a6d3b;
}
.list-group-item-danger {
  color: #a94442;
  background-color: #f2dede;
}
a.list-group-item-danger,
button.list-group-item-danger {
  color: #a94442;
}
a.list-group-item-danger .list-group-item-heading,
button.list-group-item-danger .list-group-item-heading {
  color: inherit;
}
a.list-group-item-danger:hover,
button.list-group-item-danger:hover,
a.list-group-item-danger:focus,
button.list-group-item-danger:focus {
  color: #a94442;
  background-color: #ebcccc;
}
a.list-group-item-danger.active,
button.list-group-item-danger.active,
a.list-group-item-danger.active:hover,
button.list-group-item-danger.active:hover,
a.list-group-item-danger.active:focus,
button.list-group-item-danger.active:focus {
  color: #fff;
  background-color: #a94442;
  border-color: #a94442;
}
.list-group-item-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.list-group-item-text {
  margin-bottom: 0;
  line-height: 1.3;
}
.panel {
  margin-bottom: 18px;
  background-color: #fff;
  border: 1px solid transparent;
  border-radius: 2px;
  -webkit-box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
.panel-body {
  padding: 15px;
}
.panel-heading {
  padding: 10px 15px;
  border-bottom: 1px solid transparent;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel-heading > .dropdown .dropdown-toggle {
  color: inherit;
}
.panel-title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 15px;
  color: inherit;
}
.panel-title > a,
.panel-title > small,
.panel-title > .small,
.panel-title > small > a,
.panel-title > .small > a {
  color: inherit;
}
.panel-footer {
  padding: 10px 15px;
  background-color: #f5f5f5;
  border-top: 1px solid #ddd;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .list-group,
.panel > .panel-collapse > .list-group {
  margin-bottom: 0;
}
.panel > .list-group .list-group-item,
.panel > .panel-collapse > .list-group .list-group-item {
  border-width: 1px 0;
  border-radius: 0;
}
.panel > .list-group:first-child .list-group-item:first-child,
.panel > .panel-collapse > .list-group:first-child .list-group-item:first-child {
  border-top: 0;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .list-group:last-child .list-group-item:last-child,
.panel > .panel-collapse > .list-group:last-child .list-group-item:last-child {
  border-bottom: 0;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .panel-heading + .panel-collapse > .list-group .list-group-item:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.panel-heading + .list-group .list-group-item:first-child {
  border-top-width: 0;
}
.list-group + .panel-footer {
  border-top-width: 0;
}
.panel > .table,
.panel > .table-responsive > .table,
.panel > .panel-collapse > .table {
  margin-bottom: 0;
}
.panel > .table caption,
.panel > .table-responsive > .table caption,
.panel > .panel-collapse > .table caption {
  padding-left: 15px;
  padding-right: 15px;
}
.panel > .table:first-child,
.panel > .table-responsive:first-child > .table:first-child {
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child {
  border-top-left-radius: 1px;
  border-top-right-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:first-child {
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:last-child {
  border-top-right-radius: 1px;
}
.panel > .table:last-child,
.panel > .table-responsive:last-child > .table:last-child {
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child {
  border-bottom-left-radius: 1px;
  border-bottom-right-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:first-child {
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:last-child {
  border-bottom-right-radius: 1px;
}
.panel > .panel-body + .table,
.panel > .panel-body + .table-responsive,
.panel > .table + .panel-body,
.panel > .table-responsive + .panel-body {
  border-top: 1px solid #ddd;
}
.panel > .table > tbody:first-child > tr:first-child th,
.panel > .table > tbody:first-child > tr:first-child td {
  border-top: 0;
}
.panel > .table-bordered,
.panel > .table-responsive > .table-bordered {
  border: 0;
}
.panel > .table-bordered > thead > tr > th:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:first-child,
.panel > .table-bordered > tbody > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:first-child,
.panel > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-bordered > thead > tr > td:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:first-child,
.panel > .table-bordered > tbody > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:first-child,
.panel > .table-bordered > tfoot > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:first-child {
  border-left: 0;
}
.panel > .table-bordered > thead > tr > th:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:last-child,
.panel > .table-bordered > tbody > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:last-child,
.panel > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-bordered > thead > tr > td:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:last-child,
.panel > .table-bordered > tbody > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:last-child,
.panel > .table-bordered > tfoot > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:last-child {
  border-right: 0;
}
.panel > .table-bordered > thead > tr:first-child > td,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > td,
.panel > .table-bordered > tbody > tr:first-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > td,
.panel > .table-bordered > thead > tr:first-child > th,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > th,
.panel > .table-bordered > tbody > tr:first-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > th {
  border-bottom: 0;
}
.panel > .table-bordered > tbody > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > td,
.panel > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-bordered > tbody > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > th,
.panel > .table-bordered > tfoot > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > th {
  border-bottom: 0;
}
.panel > .table-responsive {
  border: 0;
  margin-bottom: 0;
}
.panel-group {
  margin-bottom: 18px;
}
.panel-group .panel {
  margin-bottom: 0;
  border-radius: 2px;
}
.panel-group .panel + .panel {
  margin-top: 5px;
}
.panel-group .panel-heading {
  border-bottom: 0;
}
.panel-group .panel-heading + .panel-collapse > .panel-body,
.panel-group .panel-heading + .panel-collapse > .list-group {
  border-top: 1px solid #ddd;
}
.panel-group .panel-footer {
  border-top: 0;
}
.panel-group .panel-footer + .panel-collapse .panel-body {
  border-bottom: 1px solid #ddd;
}
.panel-default {
  border-color: #ddd;
}
.panel-default > .panel-heading {
  color: #333333;
  background-color: #f5f5f5;
  border-color: #ddd;
}
.panel-default > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ddd;
}
.panel-default > .panel-heading .badge {
  color: #f5f5f5;
  background-color: #333333;
}
.panel-default > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ddd;
}
.panel-primary {
  border-color: #337ab7;
}
.panel-primary > .panel-heading {
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.panel-primary > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #337ab7;
}
.panel-primary > .panel-heading .badge {
  color: #337ab7;
  background-color: #fff;
}
.panel-primary > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #337ab7;
}
.panel-success {
  border-color: #d6e9c6;
}
.panel-success > .panel-heading {
  color: #3c763d;
  background-color: #dff0d8;
  border-color: #d6e9c6;
}
.panel-success > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #d6e9c6;
}
.panel-success > .panel-heading .badge {
  color: #dff0d8;
  background-color: #3c763d;
}
.panel-success > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #d6e9c6;
}
.panel-info {
  border-color: #bce8f1;
}
.panel-info > .panel-heading {
  color: #31708f;
  background-color: #d9edf7;
  border-color: #bce8f1;
}
.panel-info > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #bce8f1;
}
.panel-info > .panel-heading .badge {
  color: #d9edf7;
  background-color: #31708f;
}
.panel-info > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #bce8f1;
}
.panel-warning {
  border-color: #faebcc;
}
.panel-warning > .panel-heading {
  color: #8a6d3b;
  background-color: #fcf8e3;
  border-color: #faebcc;
}
.panel-warning > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #faebcc;
}
.panel-warning > .panel-heading .badge {
  color: #fcf8e3;
  background-color: #8a6d3b;
}
.panel-warning > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #faebcc;
}
.panel-danger {
  border-color: #ebccd1;
}
.panel-danger > .panel-heading {
  color: #a94442;
  background-color: #f2dede;
  border-color: #ebccd1;
}
.panel-danger > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ebccd1;
}
.panel-danger > .panel-heading .badge {
  color: #f2dede;
  background-color: #a94442;
}
.panel-danger > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ebccd1;
}
.embed-responsive {
  position: relative;
  display: block;
  height: 0;
  padding: 0;
  overflow: hidden;
}
.embed-responsive .embed-responsive-item,
.embed-responsive iframe,
.embed-responsive embed,
.embed-responsive object,
.embed-responsive video {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
  border: 0;
}
.embed-responsive-16by9 {
  padding-bottom: 56.25%;
}
.embed-responsive-4by3 {
  padding-bottom: 75%;
}
.well {
  min-height: 20px;
  padding: 19px;
  margin-bottom: 20px;
  background-color: #f5f5f5;
  border: 1px solid #e3e3e3;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
}
.well blockquote {
  border-color: #ddd;
  border-color: rgba(0, 0, 0, 0.15);
}
.well-lg {
  padding: 24px;
  border-radius: 3px;
}
.well-sm {
  padding: 9px;
  border-radius: 1px;
}
.close {
  float: right;
  font-size: 19.5px;
  font-weight: bold;
  line-height: 1;
  color: #000;
  text-shadow: 0 1px 0 #fff;
  opacity: 0.2;
  filter: alpha(opacity=20);
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
  opacity: 0.5;
  filter: alpha(opacity=50);
}
button.close {
  padding: 0;
  cursor: pointer;
  background: transparent;
  border: 0;
  -webkit-appearance: none;
}
.modal-open {
  overflow: hidden;
}
.modal {
  display: none;
  overflow: hidden;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1050;
  -webkit-overflow-scrolling: touch;
  outline: 0;
}
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, -25%);
  -ms-transform: translate(0, -25%);
  -o-transform: translate(0, -25%);
  transform: translate(0, -25%);
  -webkit-transition: -webkit-transform 0.3s ease-out;
  -moz-transition: -moz-transform 0.3s ease-out;
  -o-transition: -o-transform 0.3s ease-out;
  transition: transform 0.3s ease-out;
}
.modal.in .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
.modal-open .modal {
  overflow-x: hidden;
  overflow-y: auto;
}
.modal-dialog {
  position: relative;
  width: auto;
  margin: 10px;
}
.modal-content {
  position: relative;
  background-color: #fff;
  border: 1px solid #999;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  background-clip: padding-box;
  outline: 0;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1040;
  background-color: #000;
}
.modal-backdrop.fade {
  opacity: 0;
  filter: alpha(opacity=0);
}
.modal-backdrop.in {
  opacity: 0.5;
  filter: alpha(opacity=50);
}
.modal-header {
  padding: 15px;
  border-bottom: 1px solid #e5e5e5;
}
.modal-header .close {
  margin-top: -2px;
}
.modal-title {
  margin: 0;
  line-height: 1.42857143;
}
.modal-body {
  position: relative;
  padding: 15px;
}
.modal-footer {
  padding: 15px;
  text-align: right;
  border-top: 1px solid #e5e5e5;
}
.modal-footer .btn + .btn {
  margin-left: 5px;
  margin-bottom: 0;
}
.modal-footer .btn-group .btn + .btn {
  margin-left: -1px;
}
.modal-footer .btn-block + .btn-block {
  margin-left: 0;
}
.modal-scrollbar-measure {
  position: absolute;
  top: -9999px;
  width: 50px;
  height: 50px;
  overflow: scroll;
}
@media (min-width: 768px) {
  .modal-dialog {
    width: 600px;
    margin: 30px auto;
  }
  .modal-content {
    -webkit-box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
  }
  .modal-sm {
    width: 300px;
  }
}
@media (min-width: 992px) {
  .modal-lg {
    width: 900px;
  }
}
.tooltip {
  position: absolute;
  z-index: 1070;
  display: block;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 12px;
  opacity: 0;
  filter: alpha(opacity=0);
}
.tooltip.in {
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.tooltip.top {
  margin-top: -3px;
  padding: 5px 0;
}
.tooltip.right {
  margin-left: 3px;
  padding: 0 5px;
}
.tooltip.bottom {
  margin-top: 3px;
  padding: 5px 0;
}
.tooltip.left {
  margin-left: -3px;
  padding: 0 5px;
}
.tooltip-inner {
  max-width: 200px;
  padding: 3px 8px;
  color: #fff;
  text-align: center;
  background-color: #000;
  border-radius: 2px;
}
.tooltip-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.tooltip.top .tooltip-arrow {
  bottom: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-left .tooltip-arrow {
  bottom: 0;
  right: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-right .tooltip-arrow {
  bottom: 0;
  left: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.right .tooltip-arrow {
  top: 50%;
  left: 0;
  margin-top: -5px;
  border-width: 5px 5px 5px 0;
  border-right-color: #000;
}
.tooltip.left .tooltip-arrow {
  top: 50%;
  right: 0;
  margin-top: -5px;
  border-width: 5px 0 5px 5px;
  border-left-color: #000;
}
.tooltip.bottom .tooltip-arrow {
  top: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-left .tooltip-arrow {
  top: 0;
  right: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-right .tooltip-arrow {
  top: 0;
  left: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.popover {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1060;
  display: none;
  max-width: 276px;
  padding: 1px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 13px;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
.popover.top {
  margin-top: -10px;
}
.popover.right {
  margin-left: 10px;
}
.popover.bottom {
  margin-top: 10px;
}
.popover.left {
  margin-left: -10px;
}
.popover-title {
  margin: 0;
  padding: 8px 14px;
  font-size: 13px;
  background-color: #f7f7f7;
  border-bottom: 1px solid #ebebeb;
  border-radius: 2px 2px 0 0;
}
.popover-content {
  padding: 9px 14px;
}
.popover > .arrow,
.popover > .arrow:after {
  position: absolute;
  display: block;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.popover > .arrow {
  border-width: 11px;
}
.popover > .arrow:after {
  border-width: 10px;
  content: "";
}
.popover.top > .arrow {
  left: 50%;
  margin-left: -11px;
  border-bottom-width: 0;
  border-top-color: #999999;
  border-top-color: rgba(0, 0, 0, 0.25);
  bottom: -11px;
}
.popover.top > .arrow:after {
  content: " ";
  bottom: 1px;
  margin-left: -10px;
  border-bottom-width: 0;
  border-top-color: #fff;
}
.popover.right > .arrow {
  top: 50%;
  left: -11px;
  margin-top: -11px;
  border-left-width: 0;
  border-right-color: #999999;
  border-right-color: rgba(0, 0, 0, 0.25);
}
.popover.right > .arrow:after {
  content: " ";
  left: 1px;
  bottom: -10px;
  border-left-width: 0;
  border-right-color: #fff;
}
.popover.bottom > .arrow {
  left: 50%;
  margin-left: -11px;
  border-top-width: 0;
  border-bottom-color: #999999;
  border-bottom-color: rgba(0, 0, 0, 0.25);
  top: -11px;
}
.popover.bottom > .arrow:after {
  content: " ";
  top: 1px;
  margin-left: -10px;
  border-top-width: 0;
  border-bottom-color: #fff;
}
.popover.left > .arrow {
  top: 50%;
  right: -11px;
  margin-top: -11px;
  border-right-width: 0;
  border-left-color: #999999;
  border-left-color: rgba(0, 0, 0, 0.25);
}
.popover.left > .arrow:after {
  content: " ";
  right: 1px;
  border-right-width: 0;
  border-left-color: #fff;
  bottom: -10px;
}
.carousel {
  position: relative;
}
.carousel-inner {
  position: relative;
  overflow: hidden;
  width: 100%;
}
.carousel-inner > .item {
  display: none;
  position: relative;
  -webkit-transition: 0.6s ease-in-out left;
  -o-transition: 0.6s ease-in-out left;
  transition: 0.6s ease-in-out left;
}
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  line-height: 1;
}
@media all and (transform-3d), (-webkit-transform-3d) {
  .carousel-inner > .item {
    -webkit-transition: -webkit-transform 0.6s ease-in-out;
    -moz-transition: -moz-transform 0.6s ease-in-out;
    -o-transition: -o-transform 0.6s ease-in-out;
    transition: transform 0.6s ease-in-out;
    -webkit-backface-visibility: hidden;
    -moz-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-perspective: 1000px;
    -moz-perspective: 1000px;
    perspective: 1000px;
  }
  .carousel-inner > .item.next,
  .carousel-inner > .item.active.right {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.prev,
  .carousel-inner > .item.active.left {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.next.left,
  .carousel-inner > .item.prev.right,
  .carousel-inner > .item.active {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    left: 0;
  }
}
.carousel-inner > .active,
.carousel-inner > .next,
.carousel-inner > .prev {
  display: block;
}
.carousel-inner > .active {
  left: 0;
}
.carousel-inner > .next,
.carousel-inner > .prev {
  position: absolute;
  top: 0;
  width: 100%;
}
.carousel-inner > .next {
  left: 100%;
}
.carousel-inner > .prev {
  left: -100%;
}
.carousel-inner > .next.left,
.carousel-inner > .prev.right {
  left: 0;
}
.carousel-inner > .active.left {
  left: -100%;
}
.carousel-inner > .active.right {
  left: 100%;
}
.carousel-control {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 15%;
  opacity: 0.5;
  filter: alpha(opacity=50);
  font-size: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
  background-color: rgba(0, 0, 0, 0);
}
.carousel-control.left {
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#80000000', endColorstr='#00000000', GradientType=1);
}
.carousel-control.right {
  left: auto;
  right: 0;
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#00000000', endColorstr='#80000000', GradientType=1);
}
.carousel-control:hover,
.carousel-control:focus {
  outline: 0;
  color: #fff;
  text-decoration: none;
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.carousel-control .icon-prev,
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-left,
.carousel-control .glyphicon-chevron-right {
  position: absolute;
  top: 50%;
  margin-top: -10px;
  z-index: 5;
  display: inline-block;
}
.carousel-control .icon-prev,
.carousel-control .glyphicon-chevron-left {
  left: 50%;
  margin-left: -10px;
}
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-right {
  right: 50%;
  margin-right: -10px;
}
.carousel-control .icon-prev,
.carousel-control .icon-next {
  width: 20px;
  height: 20px;
  line-height: 1;
  font-family: serif;
}
.carousel-control .icon-prev:before {
  content: '\2039';
}
.carousel-control .icon-next:before {
  content: '\203a';
}
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  z-index: 15;
  width: 60%;
  margin-left: -30%;
  padding-left: 0;
  list-style: none;
  text-align: center;
}
.carousel-indicators li {
  display: inline-block;
  width: 10px;
  height: 10px;
  margin: 1px;
  text-indent: -999px;
  border: 1px solid #fff;
  border-radius: 10px;
  cursor: pointer;
  background-color: #000 \9;
  background-color: rgba(0, 0, 0, 0);
}
.carousel-indicators .active {
  margin: 0;
  width: 12px;
  height: 12px;
  background-color: #fff;
}
.carousel-caption {
  position: absolute;
  left: 15%;
  right: 15%;
  bottom: 20px;
  z-index: 10;
  padding-top: 20px;
  padding-bottom: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
}
.carousel-caption .btn {
  text-shadow: none;
}
@media screen and (min-width: 768px) {
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-prev,
  .carousel-control .icon-next {
    width: 30px;
    height: 30px;
    margin-top: -10px;
    font-size: 30px;
  }
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .icon-prev {
    margin-left: -10px;
  }
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-next {
    margin-right: -10px;
  }
  .carousel-caption {
    left: 20%;
    right: 20%;
    padding-bottom: 30px;
  }
  .carousel-indicators {
    bottom: 20px;
  }
}
.clearfix:before,
.clearfix:after,
.dl-horizontal dd:before,
.dl-horizontal dd:after,
.container:before,
.container:after,
.container-fluid:before,
.container-fluid:after,
.row:before,
.row:after,
.form-horizontal .form-group:before,
.form-horizontal .form-group:after,
.btn-toolbar:before,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:before,
.btn-group-vertical > .btn-group:after,
.nav:before,
.nav:after,
.navbar:before,
.navbar:after,
.navbar-header:before,
.navbar-header:after,
.navbar-collapse:before,
.navbar-collapse:after,
.pager:before,
.pager:after,
.panel-body:before,
.panel-body:after,
.modal-header:before,
.modal-header:after,
.modal-footer:before,
.modal-footer:after,
.item_buttons:before,
.item_buttons:after {
  content: " ";
  display: table;
}
.clearfix:after,
.dl-horizontal dd:after,
.container:after,
.container-fluid:after,
.row:after,
.form-horizontal .form-group:after,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:after,
.nav:after,
.navbar:after,
.navbar-header:after,
.navbar-collapse:after,
.pager:after,
.panel-body:after,
.modal-header:after,
.modal-footer:after,
.item_buttons:after {
  clear: both;
}
.center-block {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.pull-right {
  float: right !important;
}
.pull-left {
  float: left !important;
}
.hide {
  display: none !important;
}
.show {
  display: block !important;
}
.invisible {
  visibility: hidden;
}
.text-hide {
  font: 0/0 a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
.hidden {
  display: none !important;
}
.affix {
  position: fixed;
}
@-ms-viewport {
  width: device-width;
}
.visible-xs,
.visible-sm,
.visible-md,
.visible-lg {
  display: none !important;
}
.visible-xs-block,
.visible-xs-inline,
.visible-xs-inline-block,
.visible-sm-block,
.visible-sm-inline,
.visible-sm-inline-block,
.visible-md-block,
.visible-md-inline,
.visible-md-inline-block,
.visible-lg-block,
.visible-lg-inline,
.visible-lg-inline-block {
  display: none !important;
}
@media (max-width: 767px) {
  .visible-xs {
    display: block !important;
  }
  table.visible-xs {
    display: table !important;
  }
  tr.visible-xs {
    display: table-row !important;
  }
  th.visible-xs,
  td.visible-xs {
    display: table-cell !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-block {
    display: block !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline {
    display: inline !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm {
    display: block !important;
  }
  table.visible-sm {
    display: table !important;
  }
  tr.visible-sm {
    display: table-row !important;
  }
  th.visible-sm,
  td.visible-sm {
    display: table-cell !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-block {
    display: block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline {
    display: inline !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md {
    display: block !important;
  }
  table.visible-md {
    display: table !important;
  }
  tr.visible-md {
    display: table-row !important;
  }
  th.visible-md,
  td.visible-md {
    display: table-cell !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-block {
    display: block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline {
    display: inline !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg {
    display: block !important;
  }
  table.visible-lg {
    display: table !important;
  }
  tr.visible-lg {
    display: table-row !important;
  }
  th.visible-lg,
  td.visible-lg {
    display: table-cell !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-block {
    display: block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline {
    display: inline !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline-block {
    display: inline-block !important;
  }
}
@media (max-width: 767px) {
  .hidden-xs {
    display: none !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .hidden-sm {
    display: none !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .hidden-md {
    display: none !important;
  }
}
@media (min-width: 1200px) {
  .hidden-lg {
    display: none !important;
  }
}
.visible-print {
  display: none !important;
}
@media print {
  .visible-print {
    display: block !important;
  }
  table.visible-print {
    display: table !important;
  }
  tr.visible-print {
    display: table-row !important;
  }
  th.visible-print,
  td.visible-print {
    display: table-cell !important;
  }
}
.visible-print-block {
  display: none !important;
}
@media print {
  .visible-print-block {
    display: block !important;
  }
}
.visible-print-inline {
  display: none !important;
}
@media print {
  .visible-print-inline {
    display: inline !important;
  }
}
.visible-print-inline-block {
  display: none !important;
}
@media print {
  .visible-print-inline-block {
    display: inline-block !important;
  }
}
@media print {
  .hidden-print {
    display: none !important;
  }
}
/*!
*
* Font Awesome
*
*/
/*!
 *  Font Awesome 4.2.0 by @davegandy - http://fontawesome.io - @fontawesome
 *  License - http://fontawesome.io/license (Font: SIL OFL 1.1, CSS: MIT License)
 */
/* FONT PATH
 * -------------------------- */
@font-face {
  font-family: 'FontAwesome';
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?v=4.2.0');
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?#iefix&v=4.2.0') format('embedded-opentype'), url('../components/font-awesome/fonts/fontawesome-webfont.woff?v=4.2.0') format('woff'), url('../components/font-awesome/fonts/fontawesome-webfont.ttf?v=4.2.0') format('truetype'), url('../components/font-awesome/fonts/fontawesome-webfont.svg?v=4.2.0#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
.fa {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
/* makes the font 33% larger relative to the icon container */
.fa-lg {
  font-size: 1.33333333em;
  line-height: 0.75em;
  vertical-align: -15%;
}
.fa-2x {
  font-size: 2em;
}
.fa-3x {
  font-size: 3em;
}
.fa-4x {
  font-size: 4em;
}
.fa-5x {
  font-size: 5em;
}
.fa-fw {
  width: 1.28571429em;
  text-align: center;
}
.fa-ul {
  padding-left: 0;
  margin-left: 2.14285714em;
  list-style-type: none;
}
.fa-ul > li {
  position: relative;
}
.fa-li {
  position: absolute;
  left: -2.14285714em;
  width: 2.14285714em;
  top: 0.14285714em;
  text-align: center;
}
.fa-li.fa-lg {
  left: -1.85714286em;
}
.fa-border {
  padding: .2em .25em .15em;
  border: solid 0.08em #eee;
  border-radius: .1em;
}
.pull-right {
  float: right;
}
.pull-left {
  float: left;
}
.fa.pull-left {
  margin-right: .3em;
}
.fa.pull-right {
  margin-left: .3em;
}
.fa-spin {
  -webkit-animation: fa-spin 2s infinite linear;
  animation: fa-spin 2s infinite linear;
}
@-webkit-keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
@keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
.fa-rotate-90 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=1);
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}
.fa-rotate-180 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=2);
  -webkit-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  transform: rotate(180deg);
}
.fa-rotate-270 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=3);
  -webkit-transform: rotate(270deg);
  -ms-transform: rotate(270deg);
  transform: rotate(270deg);
}
.fa-flip-horizontal {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1);
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
.fa-flip-vertical {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=2, mirror=1);
  -webkit-transform: scale(1, -1);
  -ms-transform: scale(1, -1);
  transform: scale(1, -1);
}
:root .fa-rotate-90,
:root .fa-rotate-180,
:root .fa-rotate-270,
:root .fa-flip-horizontal,
:root .fa-flip-vertical {
  filter: none;
}
.fa-stack {
  position: relative;
  display: inline-block;
  width: 2em;
  height: 2em;
  line-height: 2em;
  vertical-align: middle;
}
.fa-stack-1x,
.fa-stack-2x {
  position: absolute;
  left: 0;
  width: 100%;
  text-align: center;
}
.fa-stack-1x {
  line-height: inherit;
}
.fa-stack-2x {
  font-size: 2em;
}
.fa-inverse {
  color: #fff;
}
/* Font Awesome uses the Unicode Private Use Area (PUA) to ensure screen
   readers do not read off random characters that represent icons */
.fa-glass:before {
  content: "\f000";
}
.fa-music:before {
  content: "\f001";
}
.fa-search:before {
  content: "\f002";
}
.fa-envelope-o:before {
  content: "\f003";
}
.fa-heart:before {
  content: "\f004";
}
.fa-star:before {
  content: "\f005";
}
.fa-star-o:before {
  content: "\f006";
}
.fa-user:before {
  content: "\f007";
}
.fa-film:before {
  content: "\f008";
}
.fa-th-large:before {
  content: "\f009";
}
.fa-th:before {
  content: "\f00a";
}
.fa-th-list:before {
  content: "\f00b";
}
.fa-check:before {
  content: "\f00c";
}
.fa-remove:before,
.fa-close:before,
.fa-times:before {
  content: "\f00d";
}
.fa-search-plus:before {
  content: "\f00e";
}
.fa-search-minus:before {
  content: "\f010";
}
.fa-power-off:before {
  content: "\f011";
}
.fa-signal:before {
  content: "\f012";
}
.fa-gear:before,
.fa-cog:before {
  content: "\f013";
}
.fa-trash-o:before {
  content: "\f014";
}
.fa-home:before {
  content: "\f015";
}
.fa-file-o:before {
  content: "\f016";
}
.fa-clock-o:before {
  content: "\f017";
}
.fa-road:before {
  content: "\f018";
}
.fa-download:before {
  content: "\f019";
}
.fa-arrow-circle-o-down:before {
  content: "\f01a";
}
.fa-arrow-circle-o-up:before {
  content: "\f01b";
}
.fa-inbox:before {
  content: "\f01c";
}
.fa-play-circle-o:before {
  content: "\f01d";
}
.fa-rotate-right:before,
.fa-repeat:before {
  content: "\f01e";
}
.fa-refresh:before {
  content: "\f021";
}
.fa-list-alt:before {
  content: "\f022";
}
.fa-lock:before {
  content: "\f023";
}
.fa-flag:before {
  content: "\f024";
}
.fa-headphones:before {
  content: "\f025";
}
.fa-volume-off:before {
  content: "\f026";
}
.fa-volume-down:before {
  content: "\f027";
}
.fa-volume-up:before {
  content: "\f028";
}
.fa-qrcode:before {
  content: "\f029";
}
.fa-barcode:before {
  content: "\f02a";
}
.fa-tag:before {
  content: "\f02b";
}
.fa-tags:before {
  content: "\f02c";
}
.fa-book:before {
  content: "\f02d";
}
.fa-bookmark:before {
  content: "\f02e";
}
.fa-print:before {
  content: "\f02f";
}
.fa-camera:before {
  content: "\f030";
}
.fa-font:before {
  content: "\f031";
}
.fa-bold:before {
  content: "\f032";
}
.fa-italic:before {
  content: "\f033";
}
.fa-text-height:before {
  content: "\f034";
}
.fa-text-width:before {
  content: "\f035";
}
.fa-align-left:before {
  content: "\f036";
}
.fa-align-center:before {
  content: "\f037";
}
.fa-align-right:before {
  content: "\f038";
}
.fa-align-justify:before {
  content: "\f039";
}
.fa-list:before {
  content: "\f03a";
}
.fa-dedent:before,
.fa-outdent:before {
  content: "\f03b";
}
.fa-indent:before {
  content: "\f03c";
}
.fa-video-camera:before {
  content: "\f03d";
}
.fa-photo:before,
.fa-image:before,
.fa-picture-o:before {
  content: "\f03e";
}
.fa-pencil:before {
  content: "\f040";
}
.fa-map-marker:before {
  content: "\f041";
}
.fa-adjust:before {
  content: "\f042";
}
.fa-tint:before {
  content: "\f043";
}
.fa-edit:before,
.fa-pencil-square-o:before {
  content: "\f044";
}
.fa-share-square-o:before {
  content: "\f045";
}
.fa-check-square-o:before {
  content: "\f046";
}
.fa-arrows:before {
  content: "\f047";
}
.fa-step-backward:before {
  content: "\f048";
}
.fa-fast-backward:before {
  content: "\f049";
}
.fa-backward:before {
  content: "\f04a";
}
.fa-play:before {
  content: "\f04b";
}
.fa-pause:before {
  content: "\f04c";
}
.fa-stop:before {
  content: "\f04d";
}
.fa-forward:before {
  content: "\f04e";
}
.fa-fast-forward:before {
  content: "\f050";
}
.fa-step-forward:before {
  content: "\f051";
}
.fa-eject:before {
  content: "\f052";
}
.fa-chevron-left:before {
  content: "\f053";
}
.fa-chevron-right:before {
  content: "\f054";
}
.fa-plus-circle:before {
  content: "\f055";
}
.fa-minus-circle:before {
  content: "\f056";
}
.fa-times-circle:before {
  content: "\f057";
}
.fa-check-circle:before {
  content: "\f058";
}
.fa-question-circle:before {
  content: "\f059";
}
.fa-info-circle:before {
  content: "\f05a";
}
.fa-crosshairs:before {
  content: "\f05b";
}
.fa-times-circle-o:before {
  content: "\f05c";
}
.fa-check-circle-o:before {
  content: "\f05d";
}
.fa-ban:before {
  content: "\f05e";
}
.fa-arrow-left:before {
  content: "\f060";
}
.fa-arrow-right:before {
  content: "\f061";
}
.fa-arrow-up:before {
  content: "\f062";
}
.fa-arrow-down:before {
  content: "\f063";
}
.fa-mail-forward:before,
.fa-share:before {
  content: "\f064";
}
.fa-expand:before {
  content: "\f065";
}
.fa-compress:before {
  content: "\f066";
}
.fa-plus:before {
  content: "\f067";
}
.fa-minus:before {
  content: "\f068";
}
.fa-asterisk:before {
  content: "\f069";
}
.fa-exclamation-circle:before {
  content: "\f06a";
}
.fa-gift:before {
  content: "\f06b";
}
.fa-leaf:before {
  content: "\f06c";
}
.fa-fire:before {
  content: "\f06d";
}
.fa-eye:before {
  content: "\f06e";
}
.fa-eye-slash:before {
  content: "\f070";
}
.fa-warning:before,
.fa-exclamation-triangle:before {
  content: "\f071";
}
.fa-plane:before {
  content: "\f072";
}
.fa-calendar:before {
  content: "\f073";
}
.fa-random:before {
  content: "\f074";
}
.fa-comment:before {
  content: "\f075";
}
.fa-magnet:before {
  content: "\f076";
}
.fa-chevron-up:before {
  content: "\f077";
}
.fa-chevron-down:before {
  content: "\f078";
}
.fa-retweet:before {
  content: "\f079";
}
.fa-shopping-cart:before {
  content: "\f07a";
}
.fa-folder:before {
  content: "\f07b";
}
.fa-folder-open:before {
  content: "\f07c";
}
.fa-arrows-v:before {
  content: "\f07d";
}
.fa-arrows-h:before {
  content: "\f07e";
}
.fa-bar-chart-o:before,
.fa-bar-chart:before {
  content: "\f080";
}
.fa-twitter-square:before {
  content: "\f081";
}
.fa-facebook-square:before {
  content: "\f082";
}
.fa-camera-retro:before {
  content: "\f083";
}
.fa-key:before {
  content: "\f084";
}
.fa-gears:before,
.fa-cogs:before {
  content: "\f085";
}
.fa-comments:before {
  content: "\f086";
}
.fa-thumbs-o-up:before {
  content: "\f087";
}
.fa-thumbs-o-down:before {
  content: "\f088";
}
.fa-star-half:before {
  content: "\f089";
}
.fa-heart-o:before {
  content: "\f08a";
}
.fa-sign-out:before {
  content: "\f08b";
}
.fa-linkedin-square:before {
  content: "\f08c";
}
.fa-thumb-tack:before {
  content: "\f08d";
}
.fa-external-link:before {
  content: "\f08e";
}
.fa-sign-in:before {
  content: "\f090";
}
.fa-trophy:before {
  content: "\f091";
}
.fa-github-square:before {
  content: "\f092";
}
.fa-upload:before {
  content: "\f093";
}
.fa-lemon-o:before {
  content: "\f094";
}
.fa-phone:before {
  content: "\f095";
}
.fa-square-o:before {
  content: "\f096";
}
.fa-bookmark-o:before {
  content: "\f097";
}
.fa-phone-square:before {
  content: "\f098";
}
.fa-twitter:before {
  content: "\f099";
}
.fa-facebook:before {
  content: "\f09a";
}
.fa-github:before {
  content: "\f09b";
}
.fa-unlock:before {
  content: "\f09c";
}
.fa-credit-card:before {
  content: "\f09d";
}
.fa-rss:before {
  content: "\f09e";
}
.fa-hdd-o:before {
  content: "\f0a0";
}
.fa-bullhorn:before {
  content: "\f0a1";
}
.fa-bell:before {
  content: "\f0f3";
}
.fa-certificate:before {
  content: "\f0a3";
}
.fa-hand-o-right:before {
  content: "\f0a4";
}
.fa-hand-o-left:before {
  content: "\f0a5";
}
.fa-hand-o-up:before {
  content: "\f0a6";
}
.fa-hand-o-down:before {
  content: "\f0a7";
}
.fa-arrow-circle-left:before {
  content: "\f0a8";
}
.fa-arrow-circle-right:before {
  content: "\f0a9";
}
.fa-arrow-circle-up:before {
  content: "\f0aa";
}
.fa-arrow-circle-down:before {
  content: "\f0ab";
}
.fa-globe:before {
  content: "\f0ac";
}
.fa-wrench:before {
  content: "\f0ad";
}
.fa-tasks:before {
  content: "\f0ae";
}
.fa-filter:before {
  content: "\f0b0";
}
.fa-briefcase:before {
  content: "\f0b1";
}
.fa-arrows-alt:before {
  content: "\f0b2";
}
.fa-group:before,
.fa-users:before {
  content: "\f0c0";
}
.fa-chain:before,
.fa-link:before {
  content: "\f0c1";
}
.fa-cloud:before {
  content: "\f0c2";
}
.fa-flask:before {
  content: "\f0c3";
}
.fa-cut:before,
.fa-scissors:before {
  content: "\f0c4";
}
.fa-copy:before,
.fa-files-o:before {
  content: "\f0c5";
}
.fa-paperclip:before {
  content: "\f0c6";
}
.fa-save:before,
.fa-floppy-o:before {
  content: "\f0c7";
}
.fa-square:before {
  content: "\f0c8";
}
.fa-navicon:before,
.fa-reorder:before,
.fa-bars:before {
  content: "\f0c9";
}
.fa-list-ul:before {
  content: "\f0ca";
}
.fa-list-ol:before {
  content: "\f0cb";
}
.fa-strikethrough:before {
  content: "\f0cc";
}
.fa-underline:before {
  content: "\f0cd";
}
.fa-table:before {
  content: "\f0ce";
}
.fa-magic:before {
  content: "\f0d0";
}
.fa-truck:before {
  content: "\f0d1";
}
.fa-pinterest:before {
  content: "\f0d2";
}
.fa-pinterest-square:before {
  content: "\f0d3";
}
.fa-google-plus-square:before {
  content: "\f0d4";
}
.fa-google-plus:before {
  content: "\f0d5";
}
.fa-money:before {
  content: "\f0d6";
}
.fa-caret-down:before {
  content: "\f0d7";
}
.fa-caret-up:before {
  content: "\f0d8";
}
.fa-caret-left:before {
  content: "\f0d9";
}
.fa-caret-right:before {
  content: "\f0da";
}
.fa-columns:before {
  content: "\f0db";
}
.fa-unsorted:before,
.fa-sort:before {
  content: "\f0dc";
}
.fa-sort-down:before,
.fa-sort-desc:before {
  content: "\f0dd";
}
.fa-sort-up:before,
.fa-sort-asc:before {
  content: "\f0de";
}
.fa-envelope:before {
  content: "\f0e0";
}
.fa-linkedin:before {
  content: "\f0e1";
}
.fa-rotate-left:before,
.fa-undo:before {
  content: "\f0e2";
}
.fa-legal:before,
.fa-gavel:before {
  content: "\f0e3";
}
.fa-dashboard:before,
.fa-tachometer:before {
  content: "\f0e4";
}
.fa-comment-o:before {
  content: "\f0e5";
}
.fa-comments-o:before {
  content: "\f0e6";
}
.fa-flash:before,
.fa-bolt:before {
  content: "\f0e7";
}
.fa-sitemap:before {
  content: "\f0e8";
}
.fa-umbrella:before {
  content: "\f0e9";
}
.fa-paste:before,
.fa-clipboard:before {
  content: "\f0ea";
}
.fa-lightbulb-o:before {
  content: "\f0eb";
}
.fa-exchange:before {
  content: "\f0ec";
}
.fa-cloud-download:before {
  content: "\f0ed";
}
.fa-cloud-upload:before {
  content: "\f0ee";
}
.fa-user-md:before {
  content: "\f0f0";
}
.fa-stethoscope:before {
  content: "\f0f1";
}
.fa-suitcase:before {
  content: "\f0f2";
}
.fa-bell-o:before {
  content: "\f0a2";
}
.fa-coffee:before {
  content: "\f0f4";
}
.fa-cutlery:before {
  content: "\f0f5";
}
.fa-file-text-o:before {
  content: "\f0f6";
}
.fa-building-o:before {
  content: "\f0f7";
}
.fa-hospital-o:before {
  content: "\f0f8";
}
.fa-ambulance:before {
  content: "\f0f9";
}
.fa-medkit:before {
  content: "\f0fa";
}
.fa-fighter-jet:before {
  content: "\f0fb";
}
.fa-beer:before {
  content: "\f0fc";
}
.fa-h-square:before {
  content: "\f0fd";
}
.fa-plus-square:before {
  content: "\f0fe";
}
.fa-angle-double-left:before {
  content: "\f100";
}
.fa-angle-double-right:before {
  content: "\f101";
}
.fa-angle-double-up:before {
  content: "\f102";
}
.fa-angle-double-down:before {
  content: "\f103";
}
.fa-angle-left:before {
  content: "\f104";
}
.fa-angle-right:before {
  content: "\f105";
}
.fa-angle-up:before {
  content: "\f106";
}
.fa-angle-down:before {
  content: "\f107";
}
.fa-desktop:before {
  content: "\f108";
}
.fa-laptop:before {
  content: "\f109";
}
.fa-tablet:before {
  content: "\f10a";
}
.fa-mobile-phone:before,
.fa-mobile:before {
  content: "\f10b";
}
.fa-circle-o:before {
  content: "\f10c";
}
.fa-quote-left:before {
  content: "\f10d";
}
.fa-quote-right:before {
  content: "\f10e";
}
.fa-spinner:before {
  content: "\f110";
}
.fa-circle:before {
  content: "\f111";
}
.fa-mail-reply:before,
.fa-reply:before {
  content: "\f112";
}
.fa-github-alt:before {
  content: "\f113";
}
.fa-folder-o:before {
  content: "\f114";
}
.fa-folder-open-o:before {
  content: "\f115";
}
.fa-smile-o:before {
  content: "\f118";
}
.fa-frown-o:before {
  content: "\f119";
}
.fa-meh-o:before {
  content: "\f11a";
}
.fa-gamepad:before {
  content: "\f11b";
}
.fa-keyboard-o:before {
  content: "\f11c";
}
.fa-flag-o:before {
  content: "\f11d";
}
.fa-flag-checkered:before {
  content: "\f11e";
}
.fa-terminal:before {
  content: "\f120";
}
.fa-code:before {
  content: "\f121";
}
.fa-mail-reply-all:before,
.fa-reply-all:before {
  content: "\f122";
}
.fa-star-half-empty:before,
.fa-star-half-full:before,
.fa-star-half-o:before {
  content: "\f123";
}
.fa-location-arrow:before {
  content: "\f124";
}
.fa-crop:before {
  content: "\f125";
}
.fa-code-fork:before {
  content: "\f126";
}
.fa-unlink:before,
.fa-chain-broken:before {
  content: "\f127";
}
.fa-question:before {
  content: "\f128";
}
.fa-info:before {
  content: "\f129";
}
.fa-exclamation:before {
  content: "\f12a";
}
.fa-superscript:before {
  content: "\f12b";
}
.fa-subscript:before {
  content: "\f12c";
}
.fa-eraser:before {
  content: "\f12d";
}
.fa-puzzle-piece:before {
  content: "\f12e";
}
.fa-microphone:before {
  content: "\f130";
}
.fa-microphone-slash:before {
  content: "\f131";
}
.fa-shield:before {
  content: "\f132";
}
.fa-calendar-o:before {
  content: "\f133";
}
.fa-fire-extinguisher:before {
  content: "\f134";
}
.fa-rocket:before {
  content: "\f135";
}
.fa-maxcdn:before {
  content: "\f136";
}
.fa-chevron-circle-left:before {
  content: "\f137";
}
.fa-chevron-circle-right:before {
  content: "\f138";
}
.fa-chevron-circle-up:before {
  content: "\f139";
}
.fa-chevron-circle-down:before {
  content: "\f13a";
}
.fa-html5:before {
  content: "\f13b";
}
.fa-css3:before {
  content: "\f13c";
}
.fa-anchor:before {
  content: "\f13d";
}
.fa-unlock-alt:before {
  content: "\f13e";
}
.fa-bullseye:before {
  content: "\f140";
}
.fa-ellipsis-h:before {
  content: "\f141";
}
.fa-ellipsis-v:before {
  content: "\f142";
}
.fa-rss-square:before {
  content: "\f143";
}
.fa-play-circle:before {
  content: "\f144";
}
.fa-ticket:before {
  content: "\f145";
}
.fa-minus-square:before {
  content: "\f146";
}
.fa-minus-square-o:before {
  content: "\f147";
}
.fa-level-up:before {
  content: "\f148";
}
.fa-level-down:before {
  content: "\f149";
}
.fa-check-square:before {
  content: "\f14a";
}
.fa-pencil-square:before {
  content: "\f14b";
}
.fa-external-link-square:before {
  content: "\f14c";
}
.fa-share-square:before {
  content: "\f14d";
}
.fa-compass:before {
  content: "\f14e";
}
.fa-toggle-down:before,
.fa-caret-square-o-down:before {
  content: "\f150";
}
.fa-toggle-up:before,
.fa-caret-square-o-up:before {
  content: "\f151";
}
.fa-toggle-right:before,
.fa-caret-square-o-right:before {
  content: "\f152";
}
.fa-euro:before,
.fa-eur:before {
  content: "\f153";
}
.fa-gbp:before {
  content: "\f154";
}
.fa-dollar:before,
.fa-usd:before {
  content: "\f155";
}
.fa-rupee:before,
.fa-inr:before {
  content: "\f156";
}
.fa-cny:before,
.fa-rmb:before,
.fa-yen:before,
.fa-jpy:before {
  content: "\f157";
}
.fa-ruble:before,
.fa-rouble:before,
.fa-rub:before {
  content: "\f158";
}
.fa-won:before,
.fa-krw:before {
  content: "\f159";
}
.fa-bitcoin:before,
.fa-btc:before {
  content: "\f15a";
}
.fa-file:before {
  content: "\f15b";
}
.fa-file-text:before {
  content: "\f15c";
}
.fa-sort-alpha-asc:before {
  content: "\f15d";
}
.fa-sort-alpha-desc:before {
  content: "\f15e";
}
.fa-sort-amount-asc:before {
  content: "\f160";
}
.fa-sort-amount-desc:before {
  content: "\f161";
}
.fa-sort-numeric-asc:before {
  content: "\f162";
}
.fa-sort-numeric-desc:before {
  content: "\f163";
}
.fa-thumbs-up:before {
  content: "\f164";
}
.fa-thumbs-down:before {
  content: "\f165";
}
.fa-youtube-square:before {
  content: "\f166";
}
.fa-youtube:before {
  content: "\f167";
}
.fa-xing:before {
  content: "\f168";
}
.fa-xing-square:before {
  content: "\f169";
}
.fa-youtube-play:before {
  content: "\f16a";
}
.fa-dropbox:before {
  content: "\f16b";
}
.fa-stack-overflow:before {
  content: "\f16c";
}
.fa-instagram:before {
  content: "\f16d";
}
.fa-flickr:before {
  content: "\f16e";
}
.fa-adn:before {
  content: "\f170";
}
.fa-bitbucket:before {
  content: "\f171";
}
.fa-bitbucket-square:before {
  content: "\f172";
}
.fa-tumblr:before {
  content: "\f173";
}
.fa-tumblr-square:before {
  content: "\f174";
}
.fa-long-arrow-down:before {
  content: "\f175";
}
.fa-long-arrow-up:before {
  content: "\f176";
}
.fa-long-arrow-left:before {
  content: "\f177";
}
.fa-long-arrow-right:before {
  content: "\f178";
}
.fa-apple:before {
  content: "\f179";
}
.fa-windows:before {
  content: "\f17a";
}
.fa-android:before {
  content: "\f17b";
}
.fa-linux:before {
  content: "\f17c";
}
.fa-dribbble:before {
  content: "\f17d";
}
.fa-skype:before {
  content: "\f17e";
}
.fa-foursquare:before {
  content: "\f180";
}
.fa-trello:before {
  content: "\f181";
}
.fa-female:before {
  content: "\f182";
}
.fa-male:before {
  content: "\f183";
}
.fa-gittip:before {
  content: "\f184";
}
.fa-sun-o:before {
  content: "\f185";
}
.fa-moon-o:before {
  content: "\f186";
}
.fa-archive:before {
  content: "\f187";
}
.fa-bug:before {
  content: "\f188";
}
.fa-vk:before {
  content: "\f189";
}
.fa-weibo:before {
  content: "\f18a";
}
.fa-renren:before {
  content: "\f18b";
}
.fa-pagelines:before {
  content: "\f18c";
}
.fa-stack-exchange:before {
  content: "\f18d";
}
.fa-arrow-circle-o-right:before {
  content: "\f18e";
}
.fa-arrow-circle-o-left:before {
  content: "\f190";
}
.fa-toggle-left:before,
.fa-caret-square-o-left:before {
  content: "\f191";
}
.fa-dot-circle-o:before {
  content: "\f192";
}
.fa-wheelchair:before {
  content: "\f193";
}
.fa-vimeo-square:before {
  content: "\f194";
}
.fa-turkish-lira:before,
.fa-try:before {
  content: "\f195";
}
.fa-plus-square-o:before {
  content: "\f196";
}
.fa-space-shuttle:before {
  content: "\f197";
}
.fa-slack:before {
  content: "\f198";
}
.fa-envelope-square:before {
  content: "\f199";
}
.fa-wordpress:before {
  content: "\f19a";
}
.fa-openid:before {
  content: "\f19b";
}
.fa-institution:before,
.fa-bank:before,
.fa-university:before {
  content: "\f19c";
}
.fa-mortar-board:before,
.fa-graduation-cap:before {
  content: "\f19d";
}
.fa-yahoo:before {
  content: "\f19e";
}
.fa-google:before {
  content: "\f1a0";
}
.fa-reddit:before {
  content: "\f1a1";
}
.fa-reddit-square:before {
  content: "\f1a2";
}
.fa-stumbleupon-circle:before {
  content: "\f1a3";
}
.fa-stumbleupon:before {
  content: "\f1a4";
}
.fa-delicious:before {
  content: "\f1a5";
}
.fa-digg:before {
  content: "\f1a6";
}
.fa-pied-piper:before {
  content: "\f1a7";
}
.fa-pied-piper-alt:before {
  content: "\f1a8";
}
.fa-drupal:before {
  content: "\f1a9";
}
.fa-joomla:before {
  content: "\f1aa";
}
.fa-language:before {
  content: "\f1ab";
}
.fa-fax:before {
  content: "\f1ac";
}
.fa-building:before {
  content: "\f1ad";
}
.fa-child:before {
  content: "\f1ae";
}
.fa-paw:before {
  content: "\f1b0";
}
.fa-spoon:before {
  content: "\f1b1";
}
.fa-cube:before {
  content: "\f1b2";
}
.fa-cubes:before {
  content: "\f1b3";
}
.fa-behance:before {
  content: "\f1b4";
}
.fa-behance-square:before {
  content: "\f1b5";
}
.fa-steam:before {
  content: "\f1b6";
}
.fa-steam-square:before {
  content: "\f1b7";
}
.fa-recycle:before {
  content: "\f1b8";
}
.fa-automobile:before,
.fa-car:before {
  content: "\f1b9";
}
.fa-cab:before,
.fa-taxi:before {
  content: "\f1ba";
}
.fa-tree:before {
  content: "\f1bb";
}
.fa-spotify:before {
  content: "\f1bc";
}
.fa-deviantart:before {
  content: "\f1bd";
}
.fa-soundcloud:before {
  content: "\f1be";
}
.fa-database:before {
  content: "\f1c0";
}
.fa-file-pdf-o:before {
  content: "\f1c1";
}
.fa-file-word-o:before {
  content: "\f1c2";
}
.fa-file-excel-o:before {
  content: "\f1c3";
}
.fa-file-powerpoint-o:before {
  content: "\f1c4";
}
.fa-file-photo-o:before,
.fa-file-picture-o:before,
.fa-file-image-o:before {
  content: "\f1c5";
}
.fa-file-zip-o:before,
.fa-file-archive-o:before {
  content: "\f1c6";
}
.fa-file-sound-o:before,
.fa-file-audio-o:before {
  content: "\f1c7";
}
.fa-file-movie-o:before,
.fa-file-video-o:before {
  content: "\f1c8";
}
.fa-file-code-o:before {
  content: "\f1c9";
}
.fa-vine:before {
  content: "\f1ca";
}
.fa-codepen:before {
  content: "\f1cb";
}
.fa-jsfiddle:before {
  content: "\f1cc";
}
.fa-life-bouy:before,
.fa-life-buoy:before,
.fa-life-saver:before,
.fa-support:before,
.fa-life-ring:before {
  content: "\f1cd";
}
.fa-circle-o-notch:before {
  content: "\f1ce";
}
.fa-ra:before,
.fa-rebel:before {
  content: "\f1d0";
}
.fa-ge:before,
.fa-empire:before {
  content: "\f1d1";
}
.fa-git-square:before {
  content: "\f1d2";
}
.fa-git:before {
  content: "\f1d3";
}
.fa-hacker-news:before {
  content: "\f1d4";
}
.fa-tencent-weibo:before {
  content: "\f1d5";
}
.fa-qq:before {
  content: "\f1d6";
}
.fa-wechat:before,
.fa-weixin:before {
  content: "\f1d7";
}
.fa-send:before,
.fa-paper-plane:before {
  content: "\f1d8";
}
.fa-send-o:before,
.fa-paper-plane-o:before {
  content: "\f1d9";
}
.fa-history:before {
  content: "\f1da";
}
.fa-circle-thin:before {
  content: "\f1db";
}
.fa-header:before {
  content: "\f1dc";
}
.fa-paragraph:before {
  content: "\f1dd";
}
.fa-sliders:before {
  content: "\f1de";
}
.fa-share-alt:before {
  content: "\f1e0";
}
.fa-share-alt-square:before {
  content: "\f1e1";
}
.fa-bomb:before {
  content: "\f1e2";
}
.fa-soccer-ball-o:before,
.fa-futbol-o:before {
  content: "\f1e3";
}
.fa-tty:before {
  content: "\f1e4";
}
.fa-binoculars:before {
  content: "\f1e5";
}
.fa-plug:before {
  content: "\f1e6";
}
.fa-slideshare:before {
  content: "\f1e7";
}
.fa-twitch:before {
  content: "\f1e8";
}
.fa-yelp:before {
  content: "\f1e9";
}
.fa-newspaper-o:before {
  content: "\f1ea";
}
.fa-wifi:before {
  content: "\f1eb";
}
.fa-calculator:before {
  content: "\f1ec";
}
.fa-paypal:before {
  content: "\f1ed";
}
.fa-google-wallet:before {
  content: "\f1ee";
}
.fa-cc-visa:before {
  content: "\f1f0";
}
.fa-cc-mastercard:before {
  content: "\f1f1";
}
.fa-cc-discover:before {
  content: "\f1f2";
}
.fa-cc-amex:before {
  content: "\f1f3";
}
.fa-cc-paypal:before {
  content: "\f1f4";
}
.fa-cc-stripe:before {
  content: "\f1f5";
}
.fa-bell-slash:before {
  content: "\f1f6";
}
.fa-bell-slash-o:before {
  content: "\f1f7";
}
.fa-trash:before {
  content: "\f1f8";
}
.fa-copyright:before {
  content: "\f1f9";
}
.fa-at:before {
  content: "\f1fa";
}
.fa-eyedropper:before {
  content: "\f1fb";
}
.fa-paint-brush:before {
  content: "\f1fc";
}
.fa-birthday-cake:before {
  content: "\f1fd";
}
.fa-area-chart:before {
  content: "\f1fe";
}
.fa-pie-chart:before {
  content: "\f200";
}
.fa-line-chart:before {
  content: "\f201";
}
.fa-lastfm:before {
  content: "\f202";
}
.fa-lastfm-square:before {
  content: "\f203";
}
.fa-toggle-off:before {
  content: "\f204";
}
.fa-toggle-on:before {
  content: "\f205";
}
.fa-bicycle:before {
  content: "\f206";
}
.fa-bus:before {
  content: "\f207";
}
.fa-ioxhost:before {
  content: "\f208";
}
.fa-angellist:before {
  content: "\f209";
}
.fa-cc:before {
  content: "\f20a";
}
.fa-shekel:before,
.fa-sheqel:before,
.fa-ils:before {
  content: "\f20b";
}
.fa-meanpath:before {
  content: "\f20c";
}
/*!
*
* IPython base
*
*/
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
code {
  color: #000;
}
pre {
  font-size: inherit;
  line-height: inherit;
}
label {
  font-weight: normal;
}
/* Make the page background atleast 100% the height of the view port */
/* Make the page itself atleast 70% the height of the view port */
.border-box-sizing {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.corner-all {
  border-radius: 2px;
}
.no-padding {
  padding: 0px;
}
/* Flexible box model classes */
/* Taken from Alex Russell http://infrequently.org/2009/08/css-3-progress/ */
/* This file is a compatability layer.  It allows the usage of flexible box 
model layouts accross multiple browsers, including older browsers.  The newest,
universal implementation of the flexible box model is used when available (see
`Modern browsers` comments below).  Browsers that are known to implement this 
new spec completely include:

    Firefox 28.0+
    Chrome 29.0+
    Internet Explorer 11+ 
    Opera 17.0+

Browsers not listed, including Safari, are supported via the styling under the
`Old browsers` comments below.
*/
.hbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
.hbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.vbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
.vbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.hbox.reverse,
.vbox.reverse,
.reverse {
  /* Old browsers */
  -webkit-box-direction: reverse;
  -moz-box-direction: reverse;
  box-direction: reverse;
  /* Modern browsers */
  flex-direction: row-reverse;
}
.hbox.box-flex0,
.vbox.box-flex0,
.box-flex0 {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
  width: auto;
}
.hbox.box-flex1,
.vbox.box-flex1,
.box-flex1 {
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex,
.vbox.box-flex,
.box-flex {
  /* Old browsers */
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex2,
.vbox.box-flex2,
.box-flex2 {
  /* Old browsers */
  -webkit-box-flex: 2;
  -moz-box-flex: 2;
  box-flex: 2;
  /* Modern browsers */
  flex: 2;
}
.box-group1 {
  /*  Deprecated */
  -webkit-box-flex-group: 1;
  -moz-box-flex-group: 1;
  box-flex-group: 1;
}
.box-group2 {
  /* Deprecated */
  -webkit-box-flex-group: 2;
  -moz-box-flex-group: 2;
  box-flex-group: 2;
}
.hbox.start,
.vbox.start,
.start {
  /* Old browsers */
  -webkit-box-pack: start;
  -moz-box-pack: start;
  box-pack: start;
  /* Modern browsers */
  justify-content: flex-start;
}
.hbox.end,
.vbox.end,
.end {
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
}
.hbox.center,
.vbox.center,
.center {
  /* Old browsers */
  -webkit-box-pack: center;
  -moz-box-pack: center;
  box-pack: center;
  /* Modern browsers */
  justify-content: center;
}
.hbox.baseline,
.vbox.baseline,
.baseline {
  /* Old browsers */
  -webkit-box-pack: baseline;
  -moz-box-pack: baseline;
  box-pack: baseline;
  /* Modern browsers */
  justify-content: baseline;
}
.hbox.stretch,
.vbox.stretch,
.stretch {
  /* Old browsers */
  -webkit-box-pack: stretch;
  -moz-box-pack: stretch;
  box-pack: stretch;
  /* Modern browsers */
  justify-content: stretch;
}
.hbox.align-start,
.vbox.align-start,
.align-start {
  /* Old browsers */
  -webkit-box-align: start;
  -moz-box-align: start;
  box-align: start;
  /* Modern browsers */
  align-items: flex-start;
}
.hbox.align-end,
.vbox.align-end,
.align-end {
  /* Old browsers */
  -webkit-box-align: end;
  -moz-box-align: end;
  box-align: end;
  /* Modern browsers */
  align-items: flex-end;
}
.hbox.align-center,
.vbox.align-center,
.align-center {
  /* Old browsers */
  -webkit-box-align: center;
  -moz-box-align: center;
  box-align: center;
  /* Modern browsers */
  align-items: center;
}
.hbox.align-baseline,
.vbox.align-baseline,
.align-baseline {
  /* Old browsers */
  -webkit-box-align: baseline;
  -moz-box-align: baseline;
  box-align: baseline;
  /* Modern browsers */
  align-items: baseline;
}
.hbox.align-stretch,
.vbox.align-stretch,
.align-stretch {
  /* Old browsers */
  -webkit-box-align: stretch;
  -moz-box-align: stretch;
  box-align: stretch;
  /* Modern browsers */
  align-items: stretch;
}
div.error {
  margin: 2em;
  text-align: center;
}
div.error > h1 {
  font-size: 500%;
  line-height: normal;
}
div.error > p {
  font-size: 200%;
  line-height: normal;
}
div.traceback-wrapper {
  text-align: left;
  max-width: 800px;
  margin: auto;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
body {
  background-color: #fff;
  /* This makes sure that the body covers the entire window and needs to
       be in a different element than the display: box in wrapper below */
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  overflow: visible;
}
body > #header {
  /* Initially hidden to prevent FLOUC */
  display: none;
  background-color: #fff;
  /* Display over codemirror */
  position: relative;
  z-index: 100;
}
body > #header #header-container {
  padding-bottom: 5px;
  padding-top: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
body > #header .header-bar {
  width: 100%;
  height: 1px;
  background: #e7e7e7;
  margin-bottom: -1px;
}
@media print {
  body > #header {
    display: none !important;
  }
}
#header-spacer {
  width: 100%;
  visibility: hidden;
}
@media print {
  #header-spacer {
    display: none;
  }
}
#ipython_notebook {
  padding-left: 0px;
  padding-top: 1px;
  padding-bottom: 1px;
}
@media (max-width: 991px) {
  #ipython_notebook {
    margin-left: 10px;
  }
}
[dir="rtl"] #ipython_notebook {
  float: right !important;
}
#noscript {
  width: auto;
  padding-top: 16px;
  padding-bottom: 16px;
  text-align: center;
  font-size: 22px;
  color: red;
  font-weight: bold;
}
#ipython_notebook img {
  height: 28px;
}
#site {
  width: 100%;
  display: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  overflow: auto;
}
@media print {
  #site {
    height: auto !important;
  }
}
/* Smaller buttons */
.ui-button .ui-button-text {
  padding: 0.2em 0.8em;
  font-size: 77%;
}
input.ui-button {
  padding: 0.3em 0.9em;
}
span#login_widget {
  float: right;
}
span#login_widget > .button,
#logout {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button:focus,
#logout:focus,
span#login_widget > .button.focus,
#logout.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
span#login_widget > .button:hover,
#logout:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active:hover,
#logout:active:hover,
span#login_widget > .button.active:hover,
#logout.active:hover,
.open > .dropdown-togglespan#login_widget > .button:hover,
.open > .dropdown-toggle#logout:hover,
span#login_widget > .button:active:focus,
#logout:active:focus,
span#login_widget > .button.active:focus,
#logout.active:focus,
.open > .dropdown-togglespan#login_widget > .button:focus,
.open > .dropdown-toggle#logout:focus,
span#login_widget > .button:active.focus,
#logout:active.focus,
span#login_widget > .button.active.focus,
#logout.active.focus,
.open > .dropdown-togglespan#login_widget > .button.focus,
.open > .dropdown-toggle#logout.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  background-image: none;
}
span#login_widget > .button.disabled:hover,
#logout.disabled:hover,
span#login_widget > .button[disabled]:hover,
#logout[disabled]:hover,
fieldset[disabled] span#login_widget > .button:hover,
fieldset[disabled] #logout:hover,
span#login_widget > .button.disabled:focus,
#logout.disabled:focus,
span#login_widget > .button[disabled]:focus,
#logout[disabled]:focus,
fieldset[disabled] span#login_widget > .button:focus,
fieldset[disabled] #logout:focus,
span#login_widget > .button.disabled.focus,
#logout.disabled.focus,
span#login_widget > .button[disabled].focus,
#logout[disabled].focus,
fieldset[disabled] span#login_widget > .button.focus,
fieldset[disabled] #logout.focus {
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button .badge,
#logout .badge {
  color: #fff;
  background-color: #333;
}
.nav-header {
  text-transform: none;
}
#header > span {
  margin-top: 10px;
}
.modal_stretch .modal-dialog {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  min-height: 80vh;
}
.modal_stretch .modal-dialog .modal-body {
  max-height: calc(100vh - 200px);
  overflow: auto;
  flex: 1;
}
@media (min-width: 768px) {
  .modal .modal-dialog {
    width: 700px;
  }
}
@media (min-width: 768px) {
  select.form-control {
    margin-left: 12px;
    margin-right: 12px;
  }
}
/*!
*
* IPython auth
*
*/
.center-nav {
  display: inline-block;
  margin-bottom: -4px;
}
/*!
*
* IPython tree view
*
*/
/* We need an invisible input field on top of the sentense*/
/* "Drag file onto the list ..." */
.alternate_upload {
  background-color: none;
  display: inline;
}
.alternate_upload.form {
  padding: 0;
  margin: 0;
}
.alternate_upload input.fileinput {
  text-align: center;
  vertical-align: middle;
  display: inline;
  opacity: 0;
  z-index: 2;
  width: 12ex;
  margin-right: -12ex;
}
.alternate_upload .btn-upload {
  height: 22px;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
[dir="rtl"] #tabs li {
  float: right;
}
ul#tabs {
  margin-bottom: 4px;
}
[dir="rtl"] ul#tabs {
  margin-right: 0px;
}
ul#tabs a {
  padding-top: 6px;
  padding-bottom: 4px;
}
ul.breadcrumb a:focus,
ul.breadcrumb a:hover {
  text-decoration: none;
}
ul.breadcrumb i.icon-home {
  font-size: 16px;
  margin-right: 4px;
}
ul.breadcrumb span {
  color: #5e5e5e;
}
.list_toolbar {
  padding: 4px 0 4px 0;
  vertical-align: middle;
}
.list_toolbar .tree-buttons {
  padding-top: 1px;
}
[dir="rtl"] .list_toolbar .tree-buttons {
  float: left !important;
}
[dir="rtl"] .list_toolbar .pull-right {
  padding-top: 1px;
  float: left !important;
}
[dir="rtl"] .list_toolbar .pull-left {
  float: right !important;
}
.dynamic-buttons {
  padding-top: 3px;
  display: inline-block;
}
.list_toolbar [class*="span"] {
  min-height: 24px;
}
.list_header {
  font-weight: bold;
  background-color: #EEE;
}
.list_placeholder {
  font-weight: bold;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
}
.list_container {
  margin-top: 4px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 2px;
}
.list_container > div {
  border-bottom: 1px solid #ddd;
}
.list_container > div:hover .list-item {
  background-color: red;
}
.list_container > div:last-child {
  border: none;
}
.list_item:hover .list_item {
  background-color: #ddd;
}
.list_item a {
  text-decoration: none;
}
.list_item:hover {
  background-color: #fafafa;
}
.list_header > div,
.list_item > div {
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
.list_header > div input,
.list_item > div input {
  margin-right: 7px;
  margin-left: 14px;
  vertical-align: baseline;
  line-height: 22px;
  position: relative;
  top: -1px;
}
.list_header > div .item_link,
.list_item > div .item_link {
  margin-left: -1px;
  vertical-align: baseline;
  line-height: 22px;
}
.new-file input[type=checkbox] {
  visibility: hidden;
}
.item_name {
  line-height: 22px;
  height: 24px;
}
.item_icon {
  font-size: 14px;
  color: #5e5e5e;
  margin-right: 7px;
  margin-left: 7px;
  line-height: 22px;
  vertical-align: baseline;
}
.item_buttons {
  line-height: 1em;
  margin-left: -5px;
}
.item_buttons .btn,
.item_buttons .btn-group,
.item_buttons .input-group {
  float: left;
}
.item_buttons > .btn,
.item_buttons > .btn-group,
.item_buttons > .input-group {
  margin-left: 5px;
}
.item_buttons .btn {
  min-width: 13ex;
}
.item_buttons .running-indicator {
  padding-top: 4px;
  color: #5cb85c;
}
.item_buttons .kernel-name {
  padding-top: 4px;
  color: #5bc0de;
  margin-right: 7px;
  float: left;
}
.toolbar_info {
  height: 24px;
  line-height: 24px;
}
.list_item input:not([type=checkbox]) {
  padding-top: 3px;
  padding-bottom: 3px;
  height: 22px;
  line-height: 14px;
  margin: 0px;
}
.highlight_text {
  color: blue;
}
#project_name {
  display: inline-block;
  padding-left: 7px;
  margin-left: -2px;
}
#project_name > .breadcrumb {
  padding: 0px;
  margin-bottom: 0px;
  background-color: transparent;
  font-weight: bold;
}
#tree-selector {
  padding-right: 0px;
}
[dir="rtl"] #tree-selector a {
  float: right;
}
#button-select-all {
  min-width: 50px;
}
#select-all {
  margin-left: 7px;
  margin-right: 2px;
}
.menu_icon {
  margin-right: 2px;
}
.tab-content .row {
  margin-left: 0px;
  margin-right: 0px;
}
.folder_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f114";
}
.folder_icon:before.pull-left {
  margin-right: .3em;
}
.folder_icon:before.pull-right {
  margin-left: .3em;
}
.notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
}
.notebook_icon:before.pull-left {
  margin-right: .3em;
}
.notebook_icon:before.pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
  color: #5cb85c;
}
.running_notebook_icon:before.pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.pull-right {
  margin-left: .3em;
}
.file_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f016";
  position: relative;
  top: -2px;
}
.file_icon:before.pull-left {
  margin-right: .3em;
}
.file_icon:before.pull-right {
  margin-left: .3em;
}
#notebook_toolbar .pull-right {
  padding-top: 0px;
  margin-right: -1px;
}
ul#new-menu {
  left: auto;
  right: 0;
}
[dir="rtl"] #new-menu {
  text-align: right;
}
.kernel-menu-icon {
  padding-right: 12px;
  width: 24px;
  content: "\f096";
}
.kernel-menu-icon:before {
  content: "\f096";
}
.kernel-menu-icon-current:before {
  content: "\f00c";
}
#tab_content {
  padding-top: 20px;
}
#running .panel-group .panel {
  margin-top: 3px;
  margin-bottom: 1em;
}
#running .panel-group .panel .panel-heading {
  background-color: #EEE;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
#running .panel-group .panel .panel-heading a:focus,
#running .panel-group .panel .panel-heading a:hover {
  text-decoration: none;
}
#running .panel-group .panel .panel-body {
  padding: 0px;
}
#running .panel-group .panel .panel-body .list_container {
  margin-top: 0px;
  margin-bottom: 0px;
  border: 0px;
  border-radius: 0px;
}
#running .panel-group .panel .panel-body .list_container .list_item {
  border-bottom: 1px solid #ddd;
}
#running .panel-group .panel .panel-body .list_container .list_item:last-child {
  border-bottom: 0px;
}
[dir="rtl"] #running .col-sm-8 {
  float: right !important;
}
.delete-button {
  display: none;
}
.duplicate-button {
  display: none;
}
.rename-button {
  display: none;
}
.shutdown-button {
  display: none;
}
.dynamic-instructions {
  display: inline-block;
  padding-top: 4px;
}
/*!
*
* IPython text editor webapp
*
*/
.selected-keymap i.fa {
  padding: 0px 5px;
}
.selected-keymap i.fa:before {
  content: "\f00c";
}
#mode-menu {
  overflow: auto;
  max-height: 20em;
}
.edit_app #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.edit_app #menubar .navbar {
  /* Use a negative 1 bottom margin, so the border overlaps the border of the
    header */
  margin-bottom: -1px;
}
.dirty-indicator {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator.pull-left {
  margin-right: .3em;
}
.dirty-indicator.pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-dirty.pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-clean.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f00c";
}
.dirty-indicator-clean:before.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.pull-right {
  margin-left: .3em;
}
#filename {
  font-size: 16pt;
  display: table;
  padding: 0px 5px;
}
#current-mode {
  padding-left: 5px;
  padding-right: 5px;
}
#texteditor-backdrop {
  padding-top: 20px;
  padding-bottom: 20px;
}
@media not print {
  #texteditor-backdrop {
    background-color: #EEE;
  }
}
@media print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container {
    padding: 0px;
    background-color: #fff;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
/*!
*
* IPython notebook
*
*/
/* CSS font colors for translated ANSI colors. */
.ansibold {
  font-weight: bold;
}
/* use dark versions for foreground, to improve visibility */
.ansiblack {
  color: black;
}
.ansired {
  color: darkred;
}
.ansigreen {
  color: darkgreen;
}
.ansiyellow {
  color: #c4a000;
}
.ansiblue {
  color: darkblue;
}
.ansipurple {
  color: darkviolet;
}
.ansicyan {
  color: steelblue;
}
.ansigray {
  color: gray;
}
/* and light for background, for the same reason */
.ansibgblack {
  background-color: black;
}
.ansibgred {
  background-color: red;
}
.ansibggreen {
  background-color: green;
}
.ansibgyellow {
  background-color: yellow;
}
.ansibgblue {
  background-color: blue;
}
.ansibgpurple {
  background-color: magenta;
}
.ansibgcyan {
  background-color: cyan;
}
.ansibggray {
  background-color: gray;
}
div.cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-radius: 2px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border-width: 1px;
  border-style: solid;
  border-color: transparent;
  width: 100%;
  padding: 5px;
  /* This acts as a spacer between cells, that is outside the border */
  margin: 0px;
  outline: none;
  border-left-width: 1px;
  padding-left: 5px;
  background: linear-gradient(to right, transparent -40px, transparent 1px, transparent 1px, transparent 100%);
}
div.cell.jupyter-soft-selected {
  border-left-color: #90CAF9;
  border-left-color: #E3F2FD;
  border-left-width: 1px;
  padding-left: 5px;
  border-right-color: #E3F2FD;
  border-right-width: 1px;
  background: #E3F2FD;
}
@media print {
  div.cell.jupyter-soft-selected {
    border-color: transparent;
  }
}
div.cell.selected {
  border-color: #ababab;
  border-left-width: 0px;
  padding-left: 6px;
  background: linear-gradient(to right, #42A5F5 -40px, #42A5F5 5px, transparent 5px, transparent 100%);
}
@media print {
  div.cell.selected {
    border-color: transparent;
  }
}
div.cell.selected.jupyter-soft-selected {
  border-left-width: 0;
  padding-left: 6px;
  background: linear-gradient(to right, #42A5F5 -40px, #42A5F5 7px, #E3F2FD 7px, #E3F2FD 100%);
}
.edit_mode div.cell.selected {
  border-color: #66BB6A;
  border-left-width: 0px;
  padding-left: 6px;
  background: linear-gradient(to right, #66BB6A -40px, #66BB6A 5px, transparent 5px, transparent 100%);
}
@media print {
  .edit_mode div.cell.selected {
    border-color: transparent;
  }
}
.prompt {
  /* This needs to be wide enough for 3 digit prompt numbers: In[100]: */
  min-width: 14ex;
  /* This padding is tuned to match the padding on the CodeMirror editor. */
  padding: 0.4em;
  margin: 0px;
  font-family: monospace;
  text-align: right;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
  /* Don't highlight prompt number selection */
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  /* Use default cursor */
  cursor: default;
}
@media (max-width: 540px) {
  .prompt {
    text-align: left;
  }
}
div.inner_cell {
  min-width: 0;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_area {
  border: 1px solid #cfcfcf;
  border-radius: 2px;
  background: #f7f7f7;
  line-height: 1.21429em;
}
/* This is needed so that empty prompt areas can collapse to zero height when there
   is no content in the output_subarea and the prompt. The main purpose of this is
   to make sure that empty JavaScript output_subareas have no height. */
div.prompt:empty {
  padding-top: 0;
  padding-bottom: 0;
}
div.unrecognized_cell {
  padding: 5px 5px 5px 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.unrecognized_cell .inner_cell {
  border-radius: 2px;
  padding: 5px;
  font-weight: bold;
  color: red;
  border: 1px solid #cfcfcf;
  background: #eaeaea;
}
div.unrecognized_cell .inner_cell a {
  color: inherit;
  text-decoration: none;
}
div.unrecognized_cell .inner_cell a:hover {
  color: inherit;
  text-decoration: none;
}
@media (max-width: 540px) {
  div.unrecognized_cell > div.prompt {
    display: none;
  }
}
div.code_cell {
  /* avoid page breaking on code cells when printing */
}
@media print {
  div.code_cell {
    page-break-inside: avoid;
  }
}
/* any special styling for code cells that are currently running goes here */
div.input {
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.input {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_prompt {
  color: #303F9F;
  border-top: 1px solid transparent;
}
div.input_area > div.highlight {
  margin: 0.4em;
  border: none;
  padding: 0px;
  background-color: transparent;
}
div.input_area > div.highlight > pre {
  margin: 0px;
  border: none;
  padding: 0px;
  background-color: transparent;
}
/* The following gets added to the <head> if it is detected that the user has a
 * monospace font with inconsistent normal/bold/italic height.  See
 * notebookmain.js.  Such fonts will have keywords vertically offset with
 * respect to the rest of the text.  The user should select a better font.
 * See: https://github.com/ipython/ipython/issues/1503
 *
 * .CodeMirror span {
 *      vertical-align: bottom;
 * }
 */
.CodeMirror {
  line-height: 1.21429em;
  /* Changed from 1em to our global default */
  font-size: 14px;
  height: auto;
  /* Changed to auto to autogrow */
  background: none;
  /* Changed from white to allow our bg to show through */
}
.CodeMirror-scroll {
  /*  The CodeMirror docs are a bit fuzzy on if overflow-y should be hidden or visible.*/
  /*  We have found that if it is visible, vertical scrollbars appear with font size changes.*/
  overflow-y: hidden;
  overflow-x: auto;
}
.CodeMirror-lines {
  /* In CM2, this used to be 0.4em, but in CM3 it went to 4px. We need the em value because */
  /* we have set a different line-height and want this to scale with that. */
  padding: 0.4em;
}
.CodeMirror-linenumber {
  padding: 0 8px 0 4px;
}
.CodeMirror-gutters {
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.CodeMirror pre {
  /* In CM3 this went to 4px from 0 in CM2. We need the 0 value because of how we size */
  /* .CodeMirror-lines */
  padding: 0;
  border: 0;
  border-radius: 0;
}
/*

Original style from softwaremaniacs.org (c) Ivan Sagalaev <Maniac@SoftwareManiacs.Org>
Adapted from GitHub theme

*/
.highlight-base {
  color: #000;
}
.highlight-variable {
  color: #000;
}
.highlight-variable-2 {
  color: #1a1a1a;
}
.highlight-variable-3 {
  color: #333333;
}
.highlight-string {
  color: #BA2121;
}
.highlight-comment {
  color: #408080;
  font-style: italic;
}
.highlight-number {
  color: #080;
}
.highlight-atom {
  color: #88F;
}
.highlight-keyword {
  color: #008000;
  font-weight: bold;
}
.highlight-builtin {
  color: #008000;
}
.highlight-error {
  color: #f00;
}
.highlight-operator {
  color: #AA22FF;
  font-weight: bold;
}
.highlight-meta {
  color: #AA22FF;
}
/* previously not defined, copying from default codemirror */
.highlight-def {
  color: #00f;
}
.highlight-string-2 {
  color: #f50;
}
.highlight-qualifier {
  color: #555;
}
.highlight-bracket {
  color: #997;
}
.highlight-tag {
  color: #170;
}
.highlight-attribute {
  color: #00c;
}
.highlight-header {
  color: blue;
}
.highlight-quote {
  color: #090;
}
.highlight-link {
  color: #00c;
}
/* apply the same style to codemirror */
.cm-s-ipython span.cm-keyword {
  color: #008000;
  font-weight: bold;
}
.cm-s-ipython span.cm-atom {
  color: #88F;
}
.cm-s-ipython span.cm-number {
  color: #080;
}
.cm-s-ipython span.cm-def {
  color: #00f;
}
.cm-s-ipython span.cm-variable {
  color: #000;
}
.cm-s-ipython span.cm-operator {
  color: #AA22FF;
  font-weight: bold;
}
.cm-s-ipython span.cm-variable-2 {
  color: #1a1a1a;
}
.cm-s-ipython span.cm-variable-3 {
  color: #333333;
}
.cm-s-ipython span.cm-comment {
  color: #408080;
  font-style: italic;
}
.cm-s-ipython span.cm-string {
  color: #BA2121;
}
.cm-s-ipython span.cm-string-2 {
  color: #f50;
}
.cm-s-ipython span.cm-meta {
  color: #AA22FF;
}
.cm-s-ipython span.cm-qualifier {
  color: #555;
}
.cm-s-ipython span.cm-builtin {
  color: #008000;
}
.cm-s-ipython span.cm-bracket {
  color: #997;
}
.cm-s-ipython span.cm-tag {
  color: #170;
}
.cm-s-ipython span.cm-attribute {
  color: #00c;
}
.cm-s-ipython span.cm-header {
  color: blue;
}
.cm-s-ipython span.cm-quote {
  color: #090;
}
.cm-s-ipython span.cm-link {
  color: #00c;
}
.cm-s-ipython span.cm-error {
  color: #f00;
}
.cm-s-ipython span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}
div.output_wrapper {
  /* this position must be relative to enable descendents to be absolute within it */
  position: relative;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  z-index: 1;
}
/* class for the output area when it should be height-limited */
div.output_scroll {
  /* ideally, this would be max-height, but FF barfs all over that */
  height: 24em;
  /* FF needs this *and the wrapper* to specify full width, or it will shrinkwrap */
  width: 100%;
  overflow: auto;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  display: block;
}
/* output div while it is collapsed */
div.output_collapsed {
  margin: 0px;
  padding: 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
div.out_prompt_overlay {
  height: 100%;
  padding: 0px 0.4em;
  position: absolute;
  border-radius: 2px;
}
div.out_prompt_overlay:hover {
  /* use inner shadow to get border that is computed the same on WebKit/FF */
  -webkit-box-shadow: inset 0 0 1px #000;
  box-shadow: inset 0 0 1px #000;
  background: rgba(240, 240, 240, 0.5);
}
div.output_prompt {
  color: #D84315;
}
/* This class is the outer container of all output sections. */
div.output_area {
  padding: 0px;
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.output_area .MathJax_Display {
  text-align: left !important;
}
div.output_area .rendered_html table {
  margin-left: 0;
  margin-right: 0;
}
div.output_area .rendered_html img {
  margin-left: 0;
  margin-right: 0;
}
div.output_area img,
div.output_area svg {
  max-width: 100%;
  height: auto;
}
div.output_area img.unconfined,
div.output_area svg.unconfined {
  max-width: none;
}
/* This is needed to protect the pre formating from global settings such
   as that of bootstrap */
.output {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.output_area {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
div.output_area pre {
  margin: 0;
  padding: 0;
  border: 0;
  vertical-align: baseline;
  color: black;
  background-color: transparent;
  border-radius: 0;
}
/* This class is for the output subarea inside the output_area and after
   the prompt div. */
div.output_subarea {
  overflow-x: auto;
  padding: 0.4em;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
  max-width: calc(100% - 14ex);
}
div.output_scroll div.output_subarea {
  overflow-x: visible;
}
/* The rest of the output_* classes are for special styling of the different
   output types */
/* all text output has this class: */
div.output_text {
  text-align: left;
  color: #000;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
}
/* stdout/stderr are 'text' as well as 'stream', but execute_result/error are *not* streams */
div.output_stderr {
  background: #fdd;
  /* very light red background for stderr */
}
div.output_latex {
  text-align: left;
}
/* Empty output_javascript divs should have no height */
div.output_javascript:empty {
  padding: 0;
}
.js-error {
  color: darkred;
}
/* raw_input styles */
div.raw_input_container {
  line-height: 1.21429em;
  padding-top: 5px;
}
pre.raw_input_prompt {
  /* nothing needed here. */
}
input.raw_input {
  font-family: monospace;
  font-size: inherit;
  color: inherit;
  width: auto;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
}
input.raw_input:focus {
  box-shadow: none;
}
p.p-space {
  margin-bottom: 10px;
}
div.output_unrecognized {
  padding: 5px;
  font-weight: bold;
  color: red;
}
div.output_unrecognized a {
  color: inherit;
  text-decoration: none;
}
div.output_unrecognized a:hover {
  color: inherit;
  text-decoration: none;
}
.rendered_html {
  color: #000;
  /* any extras will just be numbers: */
}
.rendered_html em {
  font-style: italic;
}
.rendered_html strong {
  font-weight: bold;
}
.rendered_html u {
  text-decoration: underline;
}
.rendered_html :link {
  text-decoration: underline;
}
.rendered_html :visited {
  text-decoration: underline;
}
.rendered_html h1 {
  font-size: 185.7%;
  margin: 1.08em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h2 {
  font-size: 157.1%;
  margin: 1.27em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h3 {
  font-size: 128.6%;
  margin: 1.55em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h4 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h5 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h6 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h1:first-child {
  margin-top: 0.538em;
}
.rendered_html h2:first-child {
  margin-top: 0.636em;
}
.rendered_html h3:first-child {
  margin-top: 0.777em;
}
.rendered_html h4:first-child {
  margin-top: 1em;
}
.rendered_html h5:first-child {
  margin-top: 1em;
}
.rendered_html h6:first-child {
  margin-top: 1em;
}
.rendered_html ul {
  list-style: disc;
  margin: 0em 2em;
  padding-left: 0px;
}
.rendered_html ul ul {
  list-style: square;
  margin: 0em 2em;
}
.rendered_html ul ul ul {
  list-style: circle;
  margin: 0em 2em;
}
.rendered_html ol {
  list-style: decimal;
  margin: 0em 2em;
  padding-left: 0px;
}
.rendered_html ol ol {
  list-style: upper-alpha;
  margin: 0em 2em;
}
.rendered_html ol ol ol {
  list-style: lower-alpha;
  margin: 0em 2em;
}
.rendered_html ol ol ol ol {
  list-style: lower-roman;
  margin: 0em 2em;
}
.rendered_html ol ol ol ol ol {
  list-style: decimal;
  margin: 0em 2em;
}
.rendered_html * + ul {
  margin-top: 1em;
}
.rendered_html * + ol {
  margin-top: 1em;
}
.rendered_html hr {
  color: black;
  background-color: black;
}
.rendered_html pre {
  margin: 1em 2em;
}
.rendered_html pre,
.rendered_html code {
  border: 0;
  background-color: #fff;
  color: #000;
  font-size: 100%;
  padding: 0px;
}
.rendered_html blockquote {
  margin: 1em 2em;
}
.rendered_html table {
  margin-left: auto;
  margin-right: auto;
  border: 1px solid black;
  border-collapse: collapse;
}
.rendered_html tr,
.rendered_html th,
.rendered_html td {
  border: 1px solid black;
  border-collapse: collapse;
  margin: 1em 2em;
}
.rendered_html td,
.rendered_html th {
  text-align: left;
  vertical-align: middle;
  padding: 4px;
}
.rendered_html th {
  font-weight: bold;
}
.rendered_html * + table {
  margin-top: 1em;
}
.rendered_html p {
  text-align: left;
}
.rendered_html * + p {
  margin-top: 1em;
}
.rendered_html img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.rendered_html * + img {
  margin-top: 1em;
}
.rendered_html img,
.rendered_html svg {
  max-width: 100%;
  height: auto;
}
.rendered_html img.unconfined,
.rendered_html svg.unconfined {
  max-width: none;
}
div.text_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.text_cell > div.prompt {
    display: none;
  }
}
div.text_cell_render {
  /*font-family: "Helvetica Neue", Arial, Helvetica, Geneva, sans-serif;*/
  outline: none;
  resize: none;
  width: inherit;
  border-style: none;
  padding: 0.5em 0.5em 0.5em 0.4em;
  color: #000;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
a.anchor-link:link {
  text-decoration: none;
  padding: 0px 20px;
  visibility: hidden;
}
h1:hover .anchor-link,
h2:hover .anchor-link,
h3:hover .anchor-link,
h4:hover .anchor-link,
h5:hover .anchor-link,
h6:hover .anchor-link {
  visibility: visible;
}
.text_cell.rendered .input_area {
  display: none;
}
.text_cell.rendered .rendered_html {
  overflow-x: auto;
  overflow-y: hidden;
}
.text_cell.unrendered .text_cell_render {
  display: none;
}
.cm-header-1,
.cm-header-2,
.cm-header-3,
.cm-header-4,
.cm-header-5,
.cm-header-6 {
  font-weight: bold;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
.cm-header-1 {
  font-size: 185.7%;
}
.cm-header-2 {
  font-size: 157.1%;
}
.cm-header-3 {
  font-size: 128.6%;
}
.cm-header-4 {
  font-size: 110%;
}
.cm-header-5 {
  font-size: 100%;
  font-style: italic;
}
.cm-header-6 {
  font-size: 100%;
  font-style: italic;
}
/*!
*
* IPython notebook webapp
*
*/
@media (max-width: 767px) {
  .notebook_app {
    padding-left: 0px;
    padding-right: 0px;
  }
}
#ipython-main-app {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook_panel {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook {
  font-size: 14px;
  line-height: 20px;
  overflow-y: hidden;
  overflow-x: auto;
  width: 100%;
  /* This spaces the page away from the edge of the notebook area */
  padding-top: 20px;
  margin: 0px;
  outline: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  min-height: 100%;
}
@media not print {
  #notebook-container {
    padding: 15px;
    background-color: #fff;
    min-height: 0;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
@media print {
  #notebook-container {
    width: 100%;
  }
}
div.ui-widget-content {
  border: 1px solid #ababab;
  outline: none;
}
pre.dialog {
  background-color: #f7f7f7;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0.4em;
  padding-left: 2em;
}
p.dialog {
  padding: 0.2em;
}
/* Word-wrap output correctly.  This is the CSS3 spelling, though Firefox seems
   to not honor it correctly.  Webkit browsers (Chrome, rekonq, Safari) do.
 */
pre,
code,
kbd,
samp {
  white-space: pre-wrap;
}
#fonttest {
  font-family: monospace;
}
p {
  margin-bottom: 0;
}
.end_space {
  min-height: 100px;
  transition: height .2s ease;
}
.notebook_app > #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
@media not print {
  .notebook_app {
    background-color: #EEE;
  }
}
kbd {
  border-style: solid;
  border-width: 1px;
  box-shadow: none;
  margin: 2px;
  padding-left: 2px;
  padding-right: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
/* CSS for the cell toolbar */
.celltoolbar {
  border: thin solid #CFCFCF;
  border-bottom: none;
  background: #EEE;
  border-radius: 2px 2px 0px 0px;
  width: 100%;
  height: 29px;
  padding-right: 4px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
  display: -webkit-flex;
}
@media print {
  .celltoolbar {
    display: none;
  }
}
.ctb_hideshow {
  display: none;
  vertical-align: bottom;
}
/* ctb_show is added to the ctb_hideshow div to show the cell toolbar.
   Cell toolbars are only shown when the ctb_global_show class is also set.
*/
.ctb_global_show .ctb_show.ctb_hideshow {
  display: block;
}
.ctb_global_show .ctb_show + .input_area,
.ctb_global_show .ctb_show + div.text_cell_input,
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border-top-right-radius: 0px;
  border-top-left-radius: 0px;
}
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border: 1px solid #cfcfcf;
}
.celltoolbar {
  font-size: 87%;
  padding-top: 3px;
}
.celltoolbar select {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  width: inherit;
  font-size: inherit;
  height: 22px;
  padding: 0px;
  display: inline-block;
}
.celltoolbar select:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.celltoolbar select::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.celltoolbar select:-ms-input-placeholder {
  color: #999;
}
.celltoolbar select::-webkit-input-placeholder {
  color: #999;
}
.celltoolbar select::-ms-expand {
  border: 0;
  background-color: transparent;
}
.celltoolbar select[disabled],
.celltoolbar select[readonly],
fieldset[disabled] .celltoolbar select {
  background-color: #eeeeee;
  opacity: 1;
}
.celltoolbar select[disabled],
fieldset[disabled] .celltoolbar select {
  cursor: not-allowed;
}
textarea.celltoolbar select {
  height: auto;
}
select.celltoolbar select {
  height: 30px;
  line-height: 30px;
}
textarea.celltoolbar select,
select[multiple].celltoolbar select {
  height: auto;
}
.celltoolbar label {
  margin-left: 5px;
  margin-right: 5px;
}
.completions {
  position: absolute;
  z-index: 110;
  overflow: hidden;
  border: 1px solid #ababab;
  border-radius: 2px;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  line-height: 1;
}
.completions select {
  background: white;
  outline: none;
  border: none;
  padding: 0px;
  margin: 0px;
  overflow: auto;
  font-family: monospace;
  font-size: 110%;
  color: #000;
  width: auto;
}
.completions select option.context {
  color: #286090;
}
#kernel_logo_widget {
  float: right !important;
  float: right;
}
#kernel_logo_widget .current_kernel_logo {
  display: none;
  margin-top: -1px;
  margin-bottom: -1px;
  width: 32px;
  height: 32px;
}
#menubar {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  margin-top: 1px;
}
#menubar .navbar {
  border-top: 1px;
  border-radius: 0px 0px 2px 2px;
  margin-bottom: 0px;
}
#menubar .navbar-toggle {
  float: left;
  padding-top: 7px;
  padding-bottom: 7px;
  border: none;
}
#menubar .navbar-collapse {
  clear: left;
}
.nav-wrapper {
  border-bottom: 1px solid #e7e7e7;
}
i.menu-icon {
  padding-top: 4px;
}
ul#help_menu li a {
  overflow: hidden;
  padding-right: 2.2em;
}
ul#help_menu li a i {
  margin-right: -1.2em;
}
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu > .dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
}
.dropdown-submenu:hover > .dropdown-menu {
  display: block;
}
.dropdown-submenu > a:after {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  content: "\f0da";
  float: right;
  color: #333333;
  margin-top: 2px;
  margin-right: -10px;
}
.dropdown-submenu > a:after.pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.pull-right {
  margin-left: .3em;
}
.dropdown-submenu:hover > a:after {
  color: #262626;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left > .dropdown-menu {
  left: -100%;
  margin-left: 10px;
}
#notification_area {
  float: right !important;
  float: right;
  z-index: 10;
}
.indicator_area {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
#kernel_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  border-left: 1px solid;
}
#kernel_indicator .kernel_indicator_name {
  padding-left: 5px;
  padding-right: 5px;
}
#modal_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
#readonly-indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  margin-top: 2px;
  margin-bottom: 0px;
  margin-left: 0px;
  margin-right: 0px;
  display: none;
}
.modal_indicator:before {
  width: 1.28571429em;
  text-align: center;
}
.edit_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f040";
}
.edit_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: ' ';
}
.command_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f10c";
}
.kernel_idle_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f111";
}
.kernel_busy_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f1e2";
}
.kernel_dead_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f127";
}
.kernel_disconnected_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.pull-right {
  margin-left: .3em;
}
.notification_widget {
  color: #777;
  z-index: 10;
  background: rgba(240, 240, 240, 0.5);
  margin-right: 4px;
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget:focus,
.notification_widget.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.notification_widget:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active:hover,
.notification_widget.active:hover,
.open > .dropdown-toggle.notification_widget:hover,
.notification_widget:active:focus,
.notification_widget.active:focus,
.open > .dropdown-toggle.notification_widget:focus,
.notification_widget:active.focus,
.notification_widget.active.focus,
.open > .dropdown-toggle.notification_widget.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  background-image: none;
}
.notification_widget.disabled:hover,
.notification_widget[disabled]:hover,
fieldset[disabled] .notification_widget:hover,
.notification_widget.disabled:focus,
.notification_widget[disabled]:focus,
fieldset[disabled] .notification_widget:focus,
.notification_widget.disabled.focus,
.notification_widget[disabled].focus,
fieldset[disabled] .notification_widget.focus {
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget .badge {
  color: #fff;
  background-color: #333;
}
.notification_widget.warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning:focus,
.notification_widget.warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.notification_widget.warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active:hover,
.notification_widget.warning.active:hover,
.open > .dropdown-toggle.notification_widget.warning:hover,
.notification_widget.warning:active:focus,
.notification_widget.warning.active:focus,
.open > .dropdown-toggle.notification_widget.warning:focus,
.notification_widget.warning:active.focus,
.notification_widget.warning.active.focus,
.open > .dropdown-toggle.notification_widget.warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  background-image: none;
}
.notification_widget.warning.disabled:hover,
.notification_widget.warning[disabled]:hover,
fieldset[disabled] .notification_widget.warning:hover,
.notification_widget.warning.disabled:focus,
.notification_widget.warning[disabled]:focus,
fieldset[disabled] .notification_widget.warning:focus,
.notification_widget.warning.disabled.focus,
.notification_widget.warning[disabled].focus,
fieldset[disabled] .notification_widget.warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.notification_widget.success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success:focus,
.notification_widget.success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.notification_widget.success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active:hover,
.notification_widget.success.active:hover,
.open > .dropdown-toggle.notification_widget.success:hover,
.notification_widget.success:active:focus,
.notification_widget.success.active:focus,
.open > .dropdown-toggle.notification_widget.success:focus,
.notification_widget.success:active.focus,
.notification_widget.success.active.focus,
.open > .dropdown-toggle.notification_widget.success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  background-image: none;
}
.notification_widget.success.disabled:hover,
.notification_widget.success[disabled]:hover,
fieldset[disabled] .notification_widget.success:hover,
.notification_widget.success.disabled:focus,
.notification_widget.success[disabled]:focus,
fieldset[disabled] .notification_widget.success:focus,
.notification_widget.success.disabled.focus,
.notification_widget.success[disabled].focus,
fieldset[disabled] .notification_widget.success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.notification_widget.info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info:focus,
.notification_widget.info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.notification_widget.info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active:hover,
.notification_widget.info.active:hover,
.open > .dropdown-toggle.notification_widget.info:hover,
.notification_widget.info:active:focus,
.notification_widget.info.active:focus,
.open > .dropdown-toggle.notification_widget.info:focus,
.notification_widget.info:active.focus,
.notification_widget.info.active.focus,
.open > .dropdown-toggle.notification_widget.info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  background-image: none;
}
.notification_widget.info.disabled:hover,
.notification_widget.info[disabled]:hover,
fieldset[disabled] .notification_widget.info:hover,
.notification_widget.info.disabled:focus,
.notification_widget.info[disabled]:focus,
fieldset[disabled] .notification_widget.info:focus,
.notification_widget.info.disabled.focus,
.notification_widget.info[disabled].focus,
fieldset[disabled] .notification_widget.info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.notification_widget.danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger:focus,
.notification_widget.danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.notification_widget.danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active:hover,
.notification_widget.danger.active:hover,
.open > .dropdown-toggle.notification_widget.danger:hover,
.notification_widget.danger:active:focus,
.notification_widget.danger.active:focus,
.open > .dropdown-toggle.notification_widget.danger:focus,
.notification_widget.danger:active.focus,
.notification_widget.danger.active.focus,
.open > .dropdown-toggle.notification_widget.danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  background-image: none;
}
.notification_widget.danger.disabled:hover,
.notification_widget.danger[disabled]:hover,
fieldset[disabled] .notification_widget.danger:hover,
.notification_widget.danger.disabled:focus,
.notification_widget.danger[disabled]:focus,
fieldset[disabled] .notification_widget.danger:focus,
.notification_widget.danger.disabled.focus,
.notification_widget.danger[disabled].focus,
fieldset[disabled] .notification_widget.danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger .badge {
  color: #d9534f;
  background-color: #fff;
}
div#pager {
  background-color: #fff;
  font-size: 14px;
  line-height: 20px;
  overflow: hidden;
  display: none;
  position: fixed;
  bottom: 0px;
  width: 100%;
  max-height: 50%;
  padding-top: 8px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  /* Display over codemirror */
  z-index: 100;
  /* Hack which prevents jquery ui resizable from changing top. */
  top: auto !important;
}
div#pager pre {
  line-height: 1.21429em;
  color: #000;
  background-color: #f7f7f7;
  padding: 0.4em;
}
div#pager #pager-button-area {
  position: absolute;
  top: 8px;
  right: 20px;
}
div#pager #pager-contents {
  position: relative;
  overflow: auto;
  width: 100%;
  height: 100%;
}
div#pager #pager-contents #pager-container {
  position: relative;
  padding: 15px 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
div#pager .ui-resizable-handle {
  top: 0px;
  height: 8px;
  background: #f7f7f7;
  border-top: 1px solid #cfcfcf;
  border-bottom: 1px solid #cfcfcf;
  /* This injects handle bars (a short, wide = symbol) for 
        the resize handle. */
}
div#pager .ui-resizable-handle::after {
  content: '';
  top: 2px;
  left: 50%;
  height: 3px;
  width: 30px;
  margin-left: -15px;
  position: absolute;
  border-top: 1px solid #cfcfcf;
}
.quickhelp {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  line-height: 1.8em;
}
.shortcut_key {
  display: inline-block;
  width: 21ex;
  text-align: right;
  font-family: monospace;
}
.shortcut_descr {
  display: inline-block;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
span.save_widget {
  margin-top: 6px;
}
span.save_widget span.filename {
  height: 1em;
  line-height: 1em;
  padding: 3px;
  margin-left: 16px;
  border: none;
  font-size: 146.5%;
  border-radius: 2px;
}
span.save_widget span.filename:hover {
  background-color: #e6e6e6;
}
span.checkpoint_status,
span.autosave_status {
  font-size: small;
}
@media (max-width: 767px) {
  span.save_widget {
    font-size: small;
  }
  span.checkpoint_status,
  span.autosave_status {
    display: none;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  span.checkpoint_status {
    display: none;
  }
  span.autosave_status {
    font-size: x-small;
  }
}
.toolbar {
  padding: 0px;
  margin-left: -5px;
  margin-top: 2px;
  margin-bottom: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.toolbar select,
.toolbar label {
  width: auto;
  vertical-align: middle;
  margin-right: 2px;
  margin-bottom: 0px;
  display: inline;
  font-size: 92%;
  margin-left: 0.3em;
  margin-right: 0.3em;
  padding: 0px;
  padding-top: 3px;
}
.toolbar .btn {
  padding: 2px 8px;
}
.toolbar .btn-group {
  margin-top: 0px;
  margin-left: 5px;
}
#maintoolbar {
  margin-bottom: -3px;
  margin-top: -8px;
  border: 0px;
  min-height: 27px;
  margin-left: 0px;
  padding-top: 11px;
  padding-bottom: 3px;
}
#maintoolbar .navbar-text {
  float: none;
  vertical-align: middle;
  text-align: right;
  margin-left: 5px;
  margin-right: 0px;
  margin-top: 0px;
}
.select-xs {
  height: 24px;
}
.pulse,
.dropdown-menu > li > a.pulse,
li.pulse > a.dropdown-toggle,
li.pulse.open > a.dropdown-toggle {
  background-color: #F37626;
  color: white;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
/** WARNING IF YOU ARE EDITTING THIS FILE, if this is a .css file, It has a lot
 * of chance of beeing generated from the ../less/[samename].less file, you can
 * try to get back the less file by reverting somme commit in history
 **/
/*
 * We'll try to get something pretty, so we
 * have some strange css to have the scroll bar on
 * the left with fix button on the top right of the tooltip
 */
@-moz-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-webkit-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-moz-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/*properties of tooltip after "expand"*/
.bigtooltip {
  overflow: auto;
  height: 200px;
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
}
/*properties of tooltip before "expand"*/
.smalltooltip {
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
  text-overflow: ellipsis;
  overflow: hidden;
  height: 80px;
}
.tooltipbuttons {
  position: absolute;
  padding-right: 15px;
  top: 0px;
  right: 0px;
}
.tooltiptext {
  /*avoid the button to overlap on some docstring*/
  padding-right: 30px;
}
.ipython_tooltip {
  max-width: 700px;
  /*fade-in animation when inserted*/
  -webkit-animation: fadeOut 400ms;
  -moz-animation: fadeOut 400ms;
  animation: fadeOut 400ms;
  -webkit-animation: fadeIn 400ms;
  -moz-animation: fadeIn 400ms;
  animation: fadeIn 400ms;
  vertical-align: middle;
  background-color: #f7f7f7;
  overflow: visible;
  border: #ababab 1px solid;
  outline: none;
  padding: 3px;
  margin: 0px;
  padding-left: 7px;
  font-family: monospace;
  min-height: 50px;
  -moz-box-shadow: 0px 6px 10px -1px #adadad;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  border-radius: 2px;
  position: absolute;
  z-index: 1000;
}
.ipython_tooltip a {
  float: right;
}
.ipython_tooltip .tooltiptext pre {
  border: 0;
  border-radius: 0;
  font-size: 100%;
  background-color: #f7f7f7;
}
.pretooltiparrow {
  left: 0px;
  margin: 0px;
  top: -16px;
  width: 40px;
  height: 16px;
  overflow: hidden;
  position: absolute;
}
.pretooltiparrow:before {
  background-color: #f7f7f7;
  border: 1px #ababab solid;
  z-index: 11;
  content: "";
  position: absolute;
  left: 15px;
  top: 10px;
  width: 25px;
  height: 25px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
}
ul.typeahead-list i {
  margin-left: -10px;
  width: 18px;
}
ul.typeahead-list {
  max-height: 80vh;
  overflow: auto;
}
ul.typeahead-list > li > a {
  /** Firefox bug **/
  /* see https://github.com/jupyter/notebook/issues/559 */
  white-space: normal;
}
.cmd-palette .modal-body {
  padding: 7px;
}
.cmd-palette form {
  background: white;
}
.cmd-palette input {
  outline: none;
}
.no-shortcut {
  display: none;
}
.command-shortcut:before {
  content: "(command)";
  padding-right: 3px;
  color: #777777;
}
.edit-shortcut:before {
  content: "(edit)";
  padding-right: 3px;
  color: #777777;
}
#find-and-replace #replace-preview .match,
#find-and-replace #replace-preview .insert {
  background-color: #BBDEFB;
  border-color: #90CAF9;
  border-style: solid;
  border-width: 1px;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .match {
  background-color: #FFCDD2;
  border-color: #EF9A9A;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .insert {
  background-color: #C8E6C9;
  border-color: #A5D6A7;
  border-radius: 0px;
}
#find-and-replace #replace-preview {
  max-height: 60vh;
  overflow: auto;
}
#find-and-replace #replace-preview pre {
  padding: 5px 10px;
}
.terminal-app {
  background: #EEE;
}
.terminal-app #header {
  background: #fff;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.terminal-app .terminal {
  width: 100%;
  float: left;
  font-family: monospace;
  color: white;
  background: black;
  padding: 0.4em;
  border-radius: 2px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
}
.terminal-app .terminal,
.terminal-app .terminal dummy-screen {
  line-height: 1em;
  font-size: 14px;
}
.terminal-app .terminal .xterm-rows {
  padding: 10px;
}
.terminal-app .terminal-cursor {
  color: black;
  background: white;
}
.terminal-app #terminado-container {
  margin-top: 20px;
}
/*# sourceMappingURL=style.min.css.map */
    </style>
<style type="text/css">
    .highlight .hll { background-color: #ffffcc }
.highlight  { background: #f8f8f8; }
.highlight .c { color: #408080; font-style: italic } /* Comment */
.highlight .err { border: 1px solid #FF0000 } /* Error */
.highlight .k { color: #008000; font-weight: bold } /* Keyword */
.highlight .o { color: #666666 } /* Operator */
.highlight .ch { color: #408080; font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: #408080; font-style: italic } /* Comment.Multiline */
.highlight .cp { color: #BC7A00 } /* Comment.Preproc */
.highlight .cpf { color: #408080; font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: #408080; font-style: italic } /* Comment.Single */
.highlight .cs { color: #408080; font-style: italic } /* Comment.Special */
.highlight .gd { color: #A00000 } /* Generic.Deleted */
.highlight .ge { font-style: italic } /* Generic.Emph */
.highlight .gr { color: #FF0000 } /* Generic.Error */
.highlight .gh { color: #000080; font-weight: bold } /* Generic.Heading */
.highlight .gi { color: #00A000 } /* Generic.Inserted */
.highlight .go { color: #888888 } /* Generic.Output */
.highlight .gp { color: #000080; font-weight: bold } /* Generic.Prompt */
.highlight .gs { font-weight: bold } /* Generic.Strong */
.highlight .gu { color: #800080; font-weight: bold } /* Generic.Subheading */
.highlight .gt { color: #0044DD } /* Generic.Traceback */
.highlight .kc { color: #008000; font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: #008000; font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: #008000; font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: #008000 } /* Keyword.Pseudo */
.highlight .kr { color: #008000; font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: #B00040 } /* Keyword.Type */
.highlight .m { color: #666666 } /* Literal.Number */
.highlight .s { color: #BA2121 } /* Literal.String */
.highlight .na { color: #7D9029 } /* Name.Attribute */
.highlight .nb { color: #008000 } /* Name.Builtin */
.highlight .nc { color: #0000FF; font-weight: bold } /* Name.Class */
.highlight .no { color: #880000 } /* Name.Constant */
.highlight .nd { color: #AA22FF } /* Name.Decorator */
.highlight .ni { color: #999999; font-weight: bold } /* Name.Entity */
.highlight .ne { color: #D2413A; font-weight: bold } /* Name.Exception */
.highlight .nf { color: #0000FF } /* Name.Function */
.highlight .nl { color: #A0A000 } /* Name.Label */
.highlight .nn { color: #0000FF; font-weight: bold } /* Name.Namespace */
.highlight .nt { color: #008000; font-weight: bold } /* Name.Tag */
.highlight .nv { color: #19177C } /* Name.Variable */
.highlight .ow { color: #AA22FF; font-weight: bold } /* Operator.Word */
.highlight .w { color: #bbbbbb } /* Text.Whitespace */
.highlight .mb { color: #666666 } /* Literal.Number.Bin */
.highlight .mf { color: #666666 } /* Literal.Number.Float */
.highlight .mh { color: #666666 } /* Literal.Number.Hex */
.highlight .mi { color: #666666 } /* Literal.Number.Integer */
.highlight .mo { color: #666666 } /* Literal.Number.Oct */
.highlight .sa { color: #BA2121 } /* Literal.String.Affix */
.highlight .sb { color: #BA2121 } /* Literal.String.Backtick */
.highlight .sc { color: #BA2121 } /* Literal.String.Char */
.highlight .dl { color: #BA2121 } /* Literal.String.Delimiter */
.highlight .sd { color: #BA2121; font-style: italic } /* Literal.String.Doc */
.highlight .s2 { color: #BA2121 } /* Literal.String.Double */
.highlight .se { color: #BB6622; font-weight: bold } /* Literal.String.Escape */
.highlight .sh { color: #BA2121 } /* Literal.String.Heredoc */
.highlight .si { color: #BB6688; font-weight: bold } /* Literal.String.Interpol */
.highlight .sx { color: #008000 } /* Literal.String.Other */
.highlight .sr { color: #BB6688 } /* Literal.String.Regex */
.highlight .s1 { color: #BA2121 } /* Literal.String.Single */
.highlight .ss { color: #19177C } /* Literal.String.Symbol */
.highlight .bp { color: #008000 } /* Name.Builtin.Pseudo */
.highlight .fm { color: #0000FF } /* Name.Function.Magic */
.highlight .vc { color: #19177C } /* Name.Variable.Class */
.highlight .vg { color: #19177C } /* Name.Variable.Global */
.highlight .vi { color: #19177C } /* Name.Variable.Instance */
.highlight .vm { color: #19177C } /* Name.Variable.Magic */
.highlight .il { color: #666666 } /* Literal.Number.Integer.Long */
    </style>
<style type="text/css">
    
/* Temporary definitions which will become obsolete with Notebook release 5.0 */
.ansi-black-fg { color: #3E424D; }
.ansi-black-bg { background-color: #3E424D; }
.ansi-black-intense-fg { color: #282C36; }
.ansi-black-intense-bg { background-color: #282C36; }
.ansi-red-fg { color: #E75C58; }
.ansi-red-bg { background-color: #E75C58; }
.ansi-red-intense-fg { color: #B22B31; }
.ansi-red-intense-bg { background-color: #B22B31; }
.ansi-green-fg { color: #00A250; }
.ansi-green-bg { background-color: #00A250; }
.ansi-green-intense-fg { color: #007427; }
.ansi-green-intense-bg { background-color: #007427; }
.ansi-yellow-fg { color: #DDB62B; }
.ansi-yellow-bg { background-color: #DDB62B; }
.ansi-yellow-intense-fg { color: #B27D12; }
.ansi-yellow-intense-bg { background-color: #B27D12; }
.ansi-blue-fg { color: #208FFB; }
.ansi-blue-bg { background-color: #208FFB; }
.ansi-blue-intense-fg { color: #0065CA; }
.ansi-blue-intense-bg { background-color: #0065CA; }
.ansi-magenta-fg { color: #D160C4; }
.ansi-magenta-bg { background-color: #D160C4; }
.ansi-magenta-intense-fg { color: #A03196; }
.ansi-magenta-intense-bg { background-color: #A03196; }
.ansi-cyan-fg { color: #60C6C8; }
.ansi-cyan-bg { background-color: #60C6C8; }
.ansi-cyan-intense-fg { color: #258F8F; }
.ansi-cyan-intense-bg { background-color: #258F8F; }
.ansi-white-fg { color: #C5C1B4; }
.ansi-white-bg { background-color: #C5C1B4; }
.ansi-white-intense-fg { color: #A1A6B2; }
.ansi-white-intense-bg { background-color: #A1A6B2; }

.ansi-bold { font-weight: bold; }

    </style>


<style type="text/css">
/* Overrides of notebook CSS for static HTML export */
body {
  overflow: visible;
  padding: 8px;
}

div#notebook {
  overflow: visible;
  border-top: none;
}@media print {
  div.cell {
    display: block;
    page-break-inside: avoid;
  } 
  div.output_wrapper { 
    display: block;
    page-break-inside: avoid; 
  }
  div.output { 
    display: block;
    page-break-inside: avoid; 
  }
}
</style>

<!-- Custom stylesheet, it must be in the same directory as the html file -->
<link rel="stylesheet" href="custom.css">

<!-- Loading mathjax macro -->
<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS_HTML"></script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
            processEscapes: true,
            processEnvironments: true
        },
        // Center justify equations in code and markdown cells. Elsewhere
        // we use CSS to left justify single line equations in code cells.
        displayAlign: 'center',
        "HTML-CSS": {
            styles: {'.MathJax_Display': {"margin": 0}},
            linebreaks: { automatic: true }
        }
    });
    </script>
    <!-- End of mathjax configuration --></head>
<body>
  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="House-Price-Prediction-----version-2"><strong>House Price Prediction --- version 2</strong><a class="anchor-link" href="#House-Price-Prediction-----version-2">&#182;</a></h1><p><strong><em>Charles Zhang</em></strong> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Jan 19 2020</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Introduction">Introduction<a class="anchor-link" href="#Introduction">&#182;</a></h1><p><img src="https://i.ytimg.com/vi/LvfbopVq-WE/maxresdefault.jpg" alt=""></p>
<h4 id="This-is-my-second-version-House-Price-Prediction-Model-for-the-Kaggle-Competition.-In-this-version,-I-improve-methods-for-processing-missing-value-more-accurately,-use-Ridge,-LGBM,-XGB,-and-Stacking-CV-Regressor-to-build-machie-learning-models,-and-add-blended-models.-Since-some-contents-are-repeated,-I-will-just-breifly-describe-the-dataset-at-the-beginning.">This is my second version <strong><em>House Price Prediction</em></strong> Model for the Kaggle Competition. In this version, I improve methods for processing missing value more accurately, use Ridge, LGBM, XGB, and Stacking CV Regressor to build machie learning models, and add blended models. Since some contents are repeated, I will just breifly describe the dataset at the beginning.<a class="anchor-link" href="#This-is-my-second-version-House-Price-Prediction-Model-for-the-Kaggle-Competition.-In-this-version,-I-improve-methods-for-processing-missing-value-more-accurately,-use-Ridge,-LGBM,-XGB,-and-Stacking-CV-Regressor-to-build-machie-learning-models,-and-add-blended-models.-Since-some-contents-are-repeated,-I-will-just-breifly-describe-the-dataset-at-the-beginning.">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[82]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># This Python 3 environment comes with many helpful analytics libraries installed</span>
<span class="c1"># It is defined by the kaggle/python docker image: https://github.com/kaggle/docker-python</span>
<span class="c1"># For example, here&#39;s several helpful packages to load in </span>

<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span> <span class="c1"># linear algebra</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span> <span class="c1"># data processing, CSV file I/O (e.g. pd.read_csv)</span>

<span class="c1"># Input data files are available in the &quot;../input/&quot; directory.</span>
<span class="c1"># For example, running this (by clicking run or pressing Shift+Enter) will list the files in the input directory</span>
<span class="kn">import</span> <span class="nn">matplotlib.gridspec</span> <span class="k">as</span> <span class="nn">gridspec</span>
<span class="kn">from</span> <span class="nn">datetime</span> <span class="k">import</span> <span class="n">datetime</span>
<span class="kn">from</span> <span class="nn">scipy.stats</span> <span class="k">import</span> <span class="n">skew</span>  <span class="c1"># for some statistics</span>
<span class="kn">from</span> <span class="nn">scipy.special</span> <span class="k">import</span> <span class="n">boxcox1p</span>
<span class="kn">from</span> <span class="nn">scipy.stats</span> <span class="k">import</span> <span class="n">boxcox_normmax</span>
<span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="k">import</span> <span class="n">ElasticNetCV</span><span class="p">,</span> <span class="n">LassoCV</span><span class="p">,</span> <span class="n">RidgeCV</span>
<span class="kn">from</span> <span class="nn">sklearn.ensemble</span> <span class="k">import</span> <span class="n">GradientBoostingRegressor</span>
<span class="kn">from</span> <span class="nn">sklearn.svm</span> <span class="k">import</span> <span class="n">SVR</span>
<span class="kn">from</span> <span class="nn">sklearn.pipeline</span> <span class="k">import</span> <span class="n">make_pipeline</span>
<span class="kn">from</span> <span class="nn">sklearn.preprocessing</span> <span class="k">import</span> <span class="n">RobustScaler</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">KFold</span><span class="p">,</span> <span class="n">cross_val_score</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">mean_squared_error</span>
<span class="kn">from</span> <span class="nn">mlxtend.regressor</span> <span class="k">import</span> <span class="n">StackingCVRegressor</span>
<span class="kn">from</span> <span class="nn">xgboost</span> <span class="k">import</span> <span class="n">XGBRegressor</span>
<span class="kn">from</span> <span class="nn">lightgbm</span> <span class="k">import</span> <span class="n">LGBMRegressor</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">import</span> <span class="nn">scipy.stats</span> <span class="k">as</span> <span class="nn">stats</span>
<span class="kn">import</span> <span class="nn">sklearn.linear_model</span> <span class="k">as</span> <span class="nn">linear_model</span>
<span class="kn">import</span> <span class="nn">matplotlib.style</span> <span class="k">as</span> <span class="nn">style</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
<span class="kn">from</span> <span class="nn">sklearn.manifold</span> <span class="k">import</span> <span class="n">TSNE</span>
<span class="kn">from</span> <span class="nn">sklearn.cluster</span> <span class="k">import</span> <span class="n">KMeans</span>
<span class="kn">from</span> <span class="nn">sklearn.decomposition</span> <span class="k">import</span> <span class="n">PCA</span>
<span class="kn">from</span> <span class="nn">sklearn.preprocessing</span> <span class="k">import</span> <span class="n">StandardScaler</span>


<span class="kn">import</span> <span class="nn">warnings</span>
<span class="n">warnings</span><span class="o">.</span><span class="n">filterwarnings</span><span class="p">(</span><span class="s1">&#39;ignore&#39;</span><span class="p">)</span>

<span class="c1"># Any results you write to the current directory are saved as output.</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="A-Glimpse-of-the-datasets.">A Glimpse of the datasets.<a class="anchor-link" href="#A-Glimpse-of-the-datasets.">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[83]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">train</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;../input/house-prices-advanced-regression-techniques/train.csv&quot;</span><span class="p">)</span>
<span class="n">test</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;../input/house-prices-advanced-regression-techniques/test.csv&quot;</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># gives us statistical info about the numerical variables. </span>
<span class="n">train</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span><span class="o">.</span><span class="n">T</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[5]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Id</td>
      <td>1460.0</td>
      <td>730.500000</td>
      <td>421.610009</td>
      <td>1.0</td>
      <td>365.75</td>
      <td>730.5</td>
      <td>1095.25</td>
      <td>1460.0</td>
    </tr>
    <tr>
      <td>MSSubClass</td>
      <td>1460.0</td>
      <td>56.897260</td>
      <td>42.300571</td>
      <td>20.0</td>
      <td>20.00</td>
      <td>50.0</td>
      <td>70.00</td>
      <td>190.0</td>
    </tr>
    <tr>
      <td>LotFrontage</td>
      <td>1201.0</td>
      <td>70.049958</td>
      <td>24.284752</td>
      <td>21.0</td>
      <td>59.00</td>
      <td>69.0</td>
      <td>80.00</td>
      <td>313.0</td>
    </tr>
    <tr>
      <td>LotArea</td>
      <td>1460.0</td>
      <td>10516.828082</td>
      <td>9981.264932</td>
      <td>1300.0</td>
      <td>7553.50</td>
      <td>9478.5</td>
      <td>11601.50</td>
      <td>215245.0</td>
    </tr>
    <tr>
      <td>OverallQual</td>
      <td>1460.0</td>
      <td>6.099315</td>
      <td>1.382997</td>
      <td>1.0</td>
      <td>5.00</td>
      <td>6.0</td>
      <td>7.00</td>
      <td>10.0</td>
    </tr>
    <tr>
      <td>OverallCond</td>
      <td>1460.0</td>
      <td>5.575342</td>
      <td>1.112799</td>
      <td>1.0</td>
      <td>5.00</td>
      <td>5.0</td>
      <td>6.00</td>
      <td>9.0</td>
    </tr>
    <tr>
      <td>YearBuilt</td>
      <td>1460.0</td>
      <td>1971.267808</td>
      <td>30.202904</td>
      <td>1872.0</td>
      <td>1954.00</td>
      <td>1973.0</td>
      <td>2000.00</td>
      <td>2010.0</td>
    </tr>
    <tr>
      <td>YearRemodAdd</td>
      <td>1460.0</td>
      <td>1984.865753</td>
      <td>20.645407</td>
      <td>1950.0</td>
      <td>1967.00</td>
      <td>1994.0</td>
      <td>2004.00</td>
      <td>2010.0</td>
    </tr>
    <tr>
      <td>MasVnrArea</td>
      <td>1452.0</td>
      <td>103.685262</td>
      <td>181.066207</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>166.00</td>
      <td>1600.0</td>
    </tr>
    <tr>
      <td>BsmtFinSF1</td>
      <td>1460.0</td>
      <td>443.639726</td>
      <td>456.098091</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>383.5</td>
      <td>712.25</td>
      <td>5644.0</td>
    </tr>
    <tr>
      <td>BsmtFinSF2</td>
      <td>1460.0</td>
      <td>46.549315</td>
      <td>161.319273</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>1474.0</td>
    </tr>
    <tr>
      <td>BsmtUnfSF</td>
      <td>1460.0</td>
      <td>567.240411</td>
      <td>441.866955</td>
      <td>0.0</td>
      <td>223.00</td>
      <td>477.5</td>
      <td>808.00</td>
      <td>2336.0</td>
    </tr>
    <tr>
      <td>TotalBsmtSF</td>
      <td>1460.0</td>
      <td>1057.429452</td>
      <td>438.705324</td>
      <td>0.0</td>
      <td>795.75</td>
      <td>991.5</td>
      <td>1298.25</td>
      <td>6110.0</td>
    </tr>
    <tr>
      <td>1stFlrSF</td>
      <td>1460.0</td>
      <td>1162.626712</td>
      <td>386.587738</td>
      <td>334.0</td>
      <td>882.00</td>
      <td>1087.0</td>
      <td>1391.25</td>
      <td>4692.0</td>
    </tr>
    <tr>
      <td>2ndFlrSF</td>
      <td>1460.0</td>
      <td>346.992466</td>
      <td>436.528436</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>728.00</td>
      <td>2065.0</td>
    </tr>
    <tr>
      <td>LowQualFinSF</td>
      <td>1460.0</td>
      <td>5.844521</td>
      <td>48.623081</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>572.0</td>
    </tr>
    <tr>
      <td>GrLivArea</td>
      <td>1460.0</td>
      <td>1515.463699</td>
      <td>525.480383</td>
      <td>334.0</td>
      <td>1129.50</td>
      <td>1464.0</td>
      <td>1776.75</td>
      <td>5642.0</td>
    </tr>
    <tr>
      <td>BsmtFullBath</td>
      <td>1460.0</td>
      <td>0.425342</td>
      <td>0.518911</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>1.00</td>
      <td>3.0</td>
    </tr>
    <tr>
      <td>BsmtHalfBath</td>
      <td>1460.0</td>
      <td>0.057534</td>
      <td>0.238753</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>2.0</td>
    </tr>
    <tr>
      <td>FullBath</td>
      <td>1460.0</td>
      <td>1.565068</td>
      <td>0.550916</td>
      <td>0.0</td>
      <td>1.00</td>
      <td>2.0</td>
      <td>2.00</td>
      <td>3.0</td>
    </tr>
    <tr>
      <td>HalfBath</td>
      <td>1460.0</td>
      <td>0.382877</td>
      <td>0.502885</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>1.00</td>
      <td>2.0</td>
    </tr>
    <tr>
      <td>BedroomAbvGr</td>
      <td>1460.0</td>
      <td>2.866438</td>
      <td>0.815778</td>
      <td>0.0</td>
      <td>2.00</td>
      <td>3.0</td>
      <td>3.00</td>
      <td>8.0</td>
    </tr>
    <tr>
      <td>KitchenAbvGr</td>
      <td>1460.0</td>
      <td>1.046575</td>
      <td>0.220338</td>
      <td>0.0</td>
      <td>1.00</td>
      <td>1.0</td>
      <td>1.00</td>
      <td>3.0</td>
    </tr>
    <tr>
      <td>TotRmsAbvGrd</td>
      <td>1460.0</td>
      <td>6.517808</td>
      <td>1.625393</td>
      <td>2.0</td>
      <td>5.00</td>
      <td>6.0</td>
      <td>7.00</td>
      <td>14.0</td>
    </tr>
    <tr>
      <td>Fireplaces</td>
      <td>1460.0</td>
      <td>0.613014</td>
      <td>0.644666</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>1.0</td>
      <td>1.00</td>
      <td>3.0</td>
    </tr>
    <tr>
      <td>GarageYrBlt</td>
      <td>1379.0</td>
      <td>1978.506164</td>
      <td>24.689725</td>
      <td>1900.0</td>
      <td>1961.00</td>
      <td>1980.0</td>
      <td>2002.00</td>
      <td>2010.0</td>
    </tr>
    <tr>
      <td>GarageCars</td>
      <td>1460.0</td>
      <td>1.767123</td>
      <td>0.747315</td>
      <td>0.0</td>
      <td>1.00</td>
      <td>2.0</td>
      <td>2.00</td>
      <td>4.0</td>
    </tr>
    <tr>
      <td>GarageArea</td>
      <td>1460.0</td>
      <td>472.980137</td>
      <td>213.804841</td>
      <td>0.0</td>
      <td>334.50</td>
      <td>480.0</td>
      <td>576.00</td>
      <td>1418.0</td>
    </tr>
    <tr>
      <td>WoodDeckSF</td>
      <td>1460.0</td>
      <td>94.244521</td>
      <td>125.338794</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>168.00</td>
      <td>857.0</td>
    </tr>
    <tr>
      <td>OpenPorchSF</td>
      <td>1460.0</td>
      <td>46.660274</td>
      <td>66.256028</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>25.0</td>
      <td>68.00</td>
      <td>547.0</td>
    </tr>
    <tr>
      <td>EnclosedPorch</td>
      <td>1460.0</td>
      <td>21.954110</td>
      <td>61.119149</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>552.0</td>
    </tr>
    <tr>
      <td>3SsnPorch</td>
      <td>1460.0</td>
      <td>3.409589</td>
      <td>29.317331</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>508.0</td>
    </tr>
    <tr>
      <td>ScreenPorch</td>
      <td>1460.0</td>
      <td>15.060959</td>
      <td>55.757415</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>480.0</td>
    </tr>
    <tr>
      <td>PoolArea</td>
      <td>1460.0</td>
      <td>2.758904</td>
      <td>40.177307</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>738.0</td>
    </tr>
    <tr>
      <td>MiscVal</td>
      <td>1460.0</td>
      <td>43.489041</td>
      <td>496.123024</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>15500.0</td>
    </tr>
    <tr>
      <td>MoSold</td>
      <td>1460.0</td>
      <td>6.321918</td>
      <td>2.703626</td>
      <td>1.0</td>
      <td>5.00</td>
      <td>6.0</td>
      <td>8.00</td>
      <td>12.0</td>
    </tr>
    <tr>
      <td>YrSold</td>
      <td>1460.0</td>
      <td>2007.815753</td>
      <td>1.328095</td>
      <td>2006.0</td>
      <td>2007.00</td>
      <td>2008.0</td>
      <td>2009.00</td>
      <td>2010.0</td>
    </tr>
    <tr>
      <td>SalePrice</td>
      <td>1460.0</td>
      <td>180921.195890</td>
      <td>79442.502883</td>
      <td>34900.0</td>
      <td>129975.00</td>
      <td>163000.0</td>
      <td>214000.00</td>
      <td>755000.0</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Checking-for-Missing-Values">Checking for Missing Values<a class="anchor-link" href="#Checking-for-Missing-Values">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Missing-Train-values">Missing Train values<a class="anchor-link" href="#Missing-Train-values">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">missing_percentage</span><span class="p">(</span><span class="n">df</span><span class="p">):</span>
    <span class="sd">&quot;&quot;&quot;This function takes a DataFrame(df) as input and returns two columns, total missing values and total missing values percentage&quot;&quot;&quot;</span>
    <span class="c1">## the two following line may seem complicated but its actually very simple. </span>
    <span class="n">total</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">ascending</span> <span class="o">=</span> <span class="kc">False</span><span class="p">)[</span><span class="n">df</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">ascending</span> <span class="o">=</span> <span class="kc">False</span><span class="p">)</span> <span class="o">!=</span> <span class="mi">0</span><span class="p">]</span>
    <span class="n">percent</span> <span class="o">=</span> <span class="nb">round</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">ascending</span> <span class="o">=</span> <span class="kc">False</span><span class="p">)</span><span class="o">/</span><span class="nb">len</span><span class="p">(</span><span class="n">df</span><span class="p">)</span><span class="o">*</span><span class="mi">100</span><span class="p">,</span><span class="mi">2</span><span class="p">)[</span><span class="nb">round</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">ascending</span> <span class="o">=</span> <span class="kc">False</span><span class="p">)</span><span class="o">/</span><span class="nb">len</span><span class="p">(</span><span class="n">df</span><span class="p">)</span><span class="o">*</span><span class="mi">100</span><span class="p">,</span><span class="mi">2</span><span class="p">)</span> <span class="o">!=</span> <span class="mi">0</span><span class="p">]</span>
    <span class="k">return</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">total</span><span class="p">,</span> <span class="n">percent</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">keys</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">,</span><span class="s1">&#39;Percent&#39;</span><span class="p">])</span>

<span class="n">missing_percentage</span><span class="p">(</span><span class="n">train</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[8]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total</th>
      <th>Percent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>PoolQC</td>
      <td>1453</td>
      <td>99.52</td>
    </tr>
    <tr>
      <td>MiscFeature</td>
      <td>1406</td>
      <td>96.30</td>
    </tr>
    <tr>
      <td>Alley</td>
      <td>1369</td>
      <td>93.77</td>
    </tr>
    <tr>
      <td>Fence</td>
      <td>1179</td>
      <td>80.75</td>
    </tr>
    <tr>
      <td>FireplaceQu</td>
      <td>690</td>
      <td>47.26</td>
    </tr>
    <tr>
      <td>LotFrontage</td>
      <td>259</td>
      <td>17.74</td>
    </tr>
    <tr>
      <td>GarageCond</td>
      <td>81</td>
      <td>5.55</td>
    </tr>
    <tr>
      <td>GarageType</td>
      <td>81</td>
      <td>5.55</td>
    </tr>
    <tr>
      <td>GarageYrBlt</td>
      <td>81</td>
      <td>5.55</td>
    </tr>
    <tr>
      <td>GarageFinish</td>
      <td>81</td>
      <td>5.55</td>
    </tr>
    <tr>
      <td>GarageQual</td>
      <td>81</td>
      <td>5.55</td>
    </tr>
    <tr>
      <td>BsmtExposure</td>
      <td>38</td>
      <td>2.60</td>
    </tr>
    <tr>
      <td>BsmtFinType2</td>
      <td>38</td>
      <td>2.60</td>
    </tr>
    <tr>
      <td>BsmtFinType1</td>
      <td>37</td>
      <td>2.53</td>
    </tr>
    <tr>
      <td>BsmtCond</td>
      <td>37</td>
      <td>2.53</td>
    </tr>
    <tr>
      <td>BsmtQual</td>
      <td>37</td>
      <td>2.53</td>
    </tr>
    <tr>
      <td>MasVnrArea</td>
      <td>8</td>
      <td>0.55</td>
    </tr>
    <tr>
      <td>MasVnrType</td>
      <td>8</td>
      <td>0.55</td>
    </tr>
    <tr>
      <td>Electrical</td>
      <td>1</td>
      <td>0.07</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<blockquote><h3 id="Missing-Test-values">Missing Test values<a class="anchor-link" href="#Missing-Test-values">&#182;</a></h3>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[9]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">missing_percentage</span><span class="p">(</span><span class="n">test</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[9]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total</th>
      <th>Percent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>PoolQC</td>
      <td>1456</td>
      <td>99.79</td>
    </tr>
    <tr>
      <td>MiscFeature</td>
      <td>1408</td>
      <td>96.50</td>
    </tr>
    <tr>
      <td>Alley</td>
      <td>1352</td>
      <td>92.67</td>
    </tr>
    <tr>
      <td>Fence</td>
      <td>1169</td>
      <td>80.12</td>
    </tr>
    <tr>
      <td>FireplaceQu</td>
      <td>730</td>
      <td>50.03</td>
    </tr>
    <tr>
      <td>LotFrontage</td>
      <td>227</td>
      <td>15.56</td>
    </tr>
    <tr>
      <td>GarageCond</td>
      <td>78</td>
      <td>5.35</td>
    </tr>
    <tr>
      <td>GarageQual</td>
      <td>78</td>
      <td>5.35</td>
    </tr>
    <tr>
      <td>GarageYrBlt</td>
      <td>78</td>
      <td>5.35</td>
    </tr>
    <tr>
      <td>GarageFinish</td>
      <td>78</td>
      <td>5.35</td>
    </tr>
    <tr>
      <td>GarageType</td>
      <td>76</td>
      <td>5.21</td>
    </tr>
    <tr>
      <td>BsmtCond</td>
      <td>45</td>
      <td>3.08</td>
    </tr>
    <tr>
      <td>BsmtQual</td>
      <td>44</td>
      <td>3.02</td>
    </tr>
    <tr>
      <td>BsmtExposure</td>
      <td>44</td>
      <td>3.02</td>
    </tr>
    <tr>
      <td>BsmtFinType1</td>
      <td>42</td>
      <td>2.88</td>
    </tr>
    <tr>
      <td>BsmtFinType2</td>
      <td>42</td>
      <td>2.88</td>
    </tr>
    <tr>
      <td>MasVnrType</td>
      <td>16</td>
      <td>1.10</td>
    </tr>
    <tr>
      <td>MasVnrArea</td>
      <td>15</td>
      <td>1.03</td>
    </tr>
    <tr>
      <td>MSZoning</td>
      <td>4</td>
      <td>0.27</td>
    </tr>
    <tr>
      <td>BsmtHalfBath</td>
      <td>2</td>
      <td>0.14</td>
    </tr>
    <tr>
      <td>Utilities</td>
      <td>2</td>
      <td>0.14</td>
    </tr>
    <tr>
      <td>Functional</td>
      <td>2</td>
      <td>0.14</td>
    </tr>
    <tr>
      <td>BsmtFullBath</td>
      <td>2</td>
      <td>0.14</td>
    </tr>
    <tr>
      <td>BsmtFinSF2</td>
      <td>1</td>
      <td>0.07</td>
    </tr>
    <tr>
      <td>BsmtFinSF1</td>
      <td>1</td>
      <td>0.07</td>
    </tr>
    <tr>
      <td>Exterior2nd</td>
      <td>1</td>
      <td>0.07</td>
    </tr>
    <tr>
      <td>BsmtUnfSF</td>
      <td>1</td>
      <td>0.07</td>
    </tr>
    <tr>
      <td>TotalBsmtSF</td>
      <td>1</td>
      <td>0.07</td>
    </tr>
    <tr>
      <td>SaleType</td>
      <td>1</td>
      <td>0.07</td>
    </tr>
    <tr>
      <td>Exterior1st</td>
      <td>1</td>
      <td>0.07</td>
    </tr>
    <tr>
      <td>KitchenQual</td>
      <td>1</td>
      <td>0.07</td>
    </tr>
    <tr>
      <td>GarageArea</td>
      <td>1</td>
      <td>0.07</td>
    </tr>
    <tr>
      <td>GarageCars</td>
      <td>1</td>
      <td>0.07</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Observation">Observation<a class="anchor-link" href="#Observation">&#182;</a></h1><ul>
<li>There are multiple types of features. </li>
<li>Some features have missing values. </li>
<li>Most of the features are object( includes string values in the variable).</li>
</ul>
<h4 id="Similarly,-I-will-normalize-the-distrbution-of-the-SalePrice-by-log-next.">Similarly, I will normalize the distrbution of the SalePrice by log next.<a class="anchor-link" href="#Similarly,-I-will-normalize-the-distrbution-of-the-SalePrice-by-log-next.">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">plotting_3_chart</span><span class="p">(</span><span class="n">df</span><span class="p">,</span> <span class="n">feature</span><span class="p">):</span>
    <span class="c1">## Importing seaborn, matplotlab and scipy modules. </span>
    <span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
    <span class="kn">import</span> <span class="nn">matplotlib.gridspec</span> <span class="k">as</span> <span class="nn">gridspec</span>
    <span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
    <span class="kn">from</span> <span class="nn">scipy</span> <span class="k">import</span> <span class="n">stats</span>
    <span class="kn">import</span> <span class="nn">matplotlib.style</span> <span class="k">as</span> <span class="nn">style</span>
    <span class="n">style</span><span class="o">.</span><span class="n">use</span><span class="p">(</span><span class="s1">&#39;fivethirtyeight&#39;</span><span class="p">)</span>

    <span class="c1">## Creating a customized chart. and giving in figsize and everything. </span>
    <span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">constrained_layout</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">15</span><span class="p">,</span><span class="mi">10</span><span class="p">))</span>
    <span class="c1">## creating a grid of 3 cols and 3 rows. </span>
    <span class="n">grid</span> <span class="o">=</span> <span class="n">gridspec</span><span class="o">.</span><span class="n">GridSpec</span><span class="p">(</span><span class="n">ncols</span><span class="o">=</span><span class="mi">3</span><span class="p">,</span> <span class="n">nrows</span><span class="o">=</span><span class="mi">3</span><span class="p">,</span> <span class="n">figure</span><span class="o">=</span><span class="n">fig</span><span class="p">)</span>
    <span class="c1">#gs = fig3.add_gridspec(3, 3)</span>

    <span class="c1">## Customizing the histogram grid. </span>
    <span class="n">ax1</span> <span class="o">=</span> <span class="n">fig</span><span class="o">.</span><span class="n">add_subplot</span><span class="p">(</span><span class="n">grid</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="p">:</span><span class="mi">2</span><span class="p">])</span>
    <span class="c1">## Set the title. </span>
    <span class="n">ax1</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Histogram&#39;</span><span class="p">)</span>
    <span class="c1">## plot the histogram. </span>
    <span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">loc</span><span class="p">[:,</span><span class="n">feature</span><span class="p">],</span> <span class="n">norm_hist</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">ax</span> <span class="o">=</span> <span class="n">ax1</span><span class="p">)</span>

    <span class="c1"># customizing the QQ_plot. </span>
    <span class="n">ax2</span> <span class="o">=</span> <span class="n">fig</span><span class="o">.</span><span class="n">add_subplot</span><span class="p">(</span><span class="n">grid</span><span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="p">:</span><span class="mi">2</span><span class="p">])</span>
    <span class="c1">## Set the title. </span>
    <span class="n">ax2</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;QQ_plot&#39;</span><span class="p">)</span>
    <span class="c1">## Plotting the QQ_Plot. </span>
    <span class="n">stats</span><span class="o">.</span><span class="n">probplot</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">loc</span><span class="p">[:,</span><span class="n">feature</span><span class="p">],</span> <span class="n">plot</span> <span class="o">=</span> <span class="n">ax2</span><span class="p">)</span>

    <span class="c1">## Customizing the Box Plot. </span>
    <span class="n">ax3</span> <span class="o">=</span> <span class="n">fig</span><span class="o">.</span><span class="n">add_subplot</span><span class="p">(</span><span class="n">grid</span><span class="p">[:,</span> <span class="mi">2</span><span class="p">])</span>
    <span class="c1">## Set title. </span>
    <span class="n">ax3</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Box Plot&#39;</span><span class="p">)</span>
    <span class="c1">## Plotting the box plot. </span>
    <span class="n">sns</span><span class="o">.</span><span class="n">boxplot</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">loc</span><span class="p">[:,</span><span class="n">feature</span><span class="p">],</span> <span class="n">orient</span><span class="o">=</span><span class="s1">&#39;v&#39;</span><span class="p">,</span> <span class="n">ax</span> <span class="o">=</span> <span class="n">ax3</span> <span class="p">);</span>
    
<span class="n">plotting_3_chart</span><span class="p">(</span><span class="n">train</span><span class="p">,</span> <span class="s1">&#39;SalePrice&#39;</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAABEAAAALYCAYAAAB8GodbAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADl0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uIDMuMC4zLCBodHRwOi8vbWF0cGxvdGxpYi5vcmcvnQurowAAIABJREFUeJzs3Xtck+fZB/BfToCggCAkUoqWaiOlajwMepQSV0Xb1Y4qqJvSdFZstYfXA572stWPs6O4dV21ihXa4soq3dzUlq1vKwGkTuhasZ21Ka1VEVQqyEklkJD3D0bgCQFCCCTC7/v58Cl5cj13Lq4STK7c9/2IampqTCAiIiIiIiIiGsTEzk6AiIiIiIiIiKi/sQFCRERERERERIMeGyBERERERERENOixAUJEREREREREgx4bIEREREREREQ06LEBQkRERERERESDHhsgRETkEBMnTsTEiROdnQYRERHRTeull16Cr68vjh496uxUBiU2QIiIyMzX1xe+vr7dxjz88MP98g+zr68vGyhERETUrbbXKh2/AgICcOedd+KJJ57AZ5995uwUBZ5++ulO+Y4ePRo/+tGPkJSUhIsXL/bL47a9Xjt37ly/jH+zkjo7ASIiGhwOHTrk7BSIiIhoiFi/fr35+4aGBnz55Zc4ePAg3n//fbz77rv48Y9/7MTsOps7d675g54rV67gyJEj2LNnDw4cOIAjR45gzJgxTs5waGADhIiIHOK2225zdgpEREQ0RGzcuLHTsT/+8Y9ITk7GK6+84nINkIcffhg/+9nPzLebm5sRGxuLo0ePIjU1FTt27HBidkMHl8AQEZFDWNsDRK/X4/XXX8eMGTMwduxYKBQK3HXXXZg/f755xsjRo0fNy27KysoEU0SffvppwXgFBQVYsGABbrvtNgQGBmLy5MlYv349fvjhB6s5lZaW4uc//znGjBmDoKAgzJo1Cx9++CHeeecd+Pr64qWXXhLEt00XPXv2LF577TXcfffdkMvlWLx4MQCgtrYWr776Kh555BGEhYUhICAAt99+OxYuXIiioiKrObQt7WloaMDGjRsRHh4OhUKB+++/H++//z4AwGAw4OWXX8bUqVMhl8uhUqmwZ8+eXv4fICIiGtpmzpwJAKiqqup0n16vx6uvvor77rsPo0ePRnBwMH784x8jMzMTJpNJELt582b4+voiKSmp0zgHDx6Er68v1Go1mpub7c5VJpNBo9EAgM3Ldmx9HeTr64tPPvkEADB58mTz6youNeYMECIi6kcrVqzA3/72N0yYMAFxcXHw8vLCxYsX8fnnn+P999/Ho48+ipCQEKxfvx4pKSnw9vYWND06/kP95ptvYvXq1Rg2bBjmzZsHhUKBoqIipKWl4YMPPsA//vEP3HrrreZ4nU6HWbNmoba2FrNmzcJdd92Fc+fO4ec//zkeeuihbvNOSkpCUVERZs+ejVmzZmH48OEAgG+++QZbt27Fvffei9mzZ8PX1xdlZWXIycnBRx99hD//+c+YNWtWp/EMBgN++tOfoq6uDg8//DDq6+vx17/+FUuXLsWBAweQlpaGU6dOmV+4/fWvf0VSUhJGjRqF2NjYPv0/ICIiGipyc3MBAFOnThUcb25uxuOPP47CwkKMGzcOTz75JJqamvD+++/jueeew7Fjx7B7925z/K9//WscP34ce/bswf33349HH30UAHD27Fk8++yz8Pb2RkZGBmQy2YD9bL15HbR+/XpkZWWhrKwMK1asgI+PDwCY/zuUsQFCRESdWM6M6Oj8+fM2jVFbW4u///3vmDx5Mo4cOQKpVPhPTtunM2PGjMHGjRuRkpICHx8fq1Naz58/j/Xr18PT0xMff/wxwsLCzPdt3boV27dvx5o1a5CdnW0+vmbNGtTW1iIlJQWJiYnm41qtFj/96U+7zf3LL79EQUFBp/W4d9xxB77++mv4+/t3yu/HP/4xNm/ebLUBcvHiRUyfPh0ffPAB3NzcALR+SrVs2TIsXboUd955J44dO2ZutCxcuBCzZ8/GK6+8wgYIERGRFR1fq1y7dg2nTp1Cfn4+7rnnHvzqV78SxL722msoLCyEWq3Gu+++a/63+Je//CViYmLw7rvvIiYmBo899hiA1tkZGRkZmDFjBp599llMnjwZo0ePxpNPPom6ujq8/fbbGDt2bJ/yNxgMeOuttwB0bthY6u3roI0bN6KwsBBlZWV4+umnub9IB2yAEBFRJykpKX0eQywWw2Qywd3dHRKJpNP9lk2E7mRnZ6OpqQkrVqwQ/KMPAOvWrcM777yD//u//0NFRQWCgoJQVlaGwsJCjBkzBsuWLRPER0dHIzo6GlqttsvHe/bZZ62+WOjqk5OQkBDMmzcPb7zxBsrKygQzUdr85je/Mb/gAoCf/vSnePrpp1FXV4f//d//NTc/ACAyMhJjx47FV199BaPRaLV+REREQ5m11yq33norFi5cCLlcLjj+pz/9CUDnf4t9fHyQnJyMRYsW4e233zY3QIDWD2hee+01LF26FE8++SSmTp2Kzz//HMuWLcO8efN6ne8HH3xg/hCpqqoKR44cwffffw8/Pz+sW7eu23N7+zqIusY9QIiIqJOampouv+677z6bxhgxYgTmzp2L4uJi3Hfffdi2bRu0Wi0aGhp6nc/JkycBADNmzOh0n7u7O+6++24AwBdffAGgdQYHAPzoRz+y2jyIjIzs9vGmT5/e5X3Hjx/HE088gfDwcAQGBprX1b7xxhsAYPVydr6+vggJCREck0gkCAgIAACra3IVCgWMRiMuX77cba5ERERDUcfXJuXl5Thy5AjGjh2L559/Hps3bzbH1dfX48yZMwgMDOzUPACAqKgoAO2vNTp69NFH8dRTT+Gzzz7DG2+8gYkTJ+I3v/mNXfnm5OQgJSUFKSkp2LdvH8RiMZ566ikUFBT0OJukt6+DqGucAUJERP0mIyMDr732Gt577z28/PLLAFqnlcbExGDr1q02T8msq6sDAAQGBlq9v+2Tnra4+vp6ADA3GCx1NU5P9x8+fBgJCQnw8PBAdHQ0xo4dC09PT4jFYhQWFuKTTz6BXq/vdN6IESOsjtfWnPH29u7yvr5ssEZERDQUeHl5Ydq0adi3bx/Cw8Oxe/duJCYmIiQkpMfXEJ6envD29jbHWWqb4QkAv/jFL+Du7m5Xjjt37hRcBaY3evs6iLrGBggREfUbDw8PrFu3DuvWrcPFixfxr3/9C9nZ2Th8+DC+/vprHDt2zKYNxNoaBJWVlVbvb5sl0RbX1nDo6uowXY3TRiQSWT2+bds2uLm5QavVQqlUCu574YUXzDuuExER0cDz9fXFuHHjcPLkSXzxxRcICQnp8TXE9evXUVdXBz8/v0731dTU4Omnn4abmxvc3d3x61//GjNnzrS61LU/9fZ1EHWNS2CIiGhAjB49GrGxsXj33XcRERGB0tJS6HQ68/1isRgtLS1Wz508eTKA1kvmWtLr9eZL0LbFTZo0CQDw6aefwmg0djqnq0vW9uTMmTNQKpWdmh8tLS04fvy4XWMSERGR49TU1ACA+dK2I0aMQGhoKCorK/H11193ii8oKAAAqFSqTvc988wzKCsrw5YtW/Dqq6+ipqYGy5Ytg8Fg6MefoLPevg4C2meSdvXaaqhiA4SIiPrFlStX8Omnn3Y6rtfrUVtbC6B1hkgbf39/XLlyBTdu3Oh0TlxcHNzc3JCeno5vvvlGcN/vf/97VFRUYNasWRg9ejQAIDg4GPfffz/OnTuHvXv3CuK1Wm23G6B2JyQkBGfOnEFFRYX5mMlkwm9/+1urL6qIiIho4Lz//vs4d+4cZDKZYL+vJUuWAGi96kvHpaV1dXXYsmULAGDp0qWCsV5//XXk5ORg7ty5WLFiBWJjY6HRaFBUVIStW7cOwE/Trrevg4D2zebLysoGNFdXxyUwRETULyoqKvDQQw9h/PjxUKlUuOWWW3Dt2jXk5ubiu+++w09+8hOMGzfOHB8dHY3s7Gw8/vjjuPfee+Hu7o677roLc+bMQUhICFJSUrB69WpER0fjscceg1wuR1FRET755BPccsst+N3vfid4/O3bt2P27NlYv349jhw5gokTJ+LcuXM4ePAg5s6di5ycHIjFvfsc4JlnnsH//M//ICoqCo8++iikUimKioqg0+kQExODf/7znw6pHREREXWv42Vwr1+/Dp1Oh48++ggAkJycLNgvY+XKlfj444/x8ccf495778Xs2bPR3NyMw4cPo6KiAgsXLhRcAebEiRP49a9/jeDgYOzcuVPwmMXFxXj11VfxwAMPYObMmQPwk8Ku10HR0dH429/+hueffx7z5s2Dl5cXfHx8sHz58gHJ2VWxAUJERP0iJCQEmzZtwtGjR/HJJ5/gypUr8PHxQWhoKJ5//nksXrxYEP/b3/4WYrEYWq0WRUVFMBqNWLRoEebMmQMA0Gg0CA0NxWuvvYYPPvgA165dw+jRo7F8+XKsXbu208ZgEyZMwEcffYQtW7agoKAAhYWFCA8Px5/+9Cd88803yMnJ6fVaWY1GAzc3N+zatQt//vOf4eHhgXvuuQc7d+7EoUOH2AAhIiIaIB0vgyuRSDBq1CjExMRg+fLliI6OFsS6ubnhwIED2LVrF7Kzs7F3716IxWKEhYVhw4YN5hkiAFBbWwuNRoOWlhakp6dj5MiR5vs8PDzw1ltvITo6GomJiTh69Khg1kV/6u3roJ///OcoLy9HdnY2du7ciebmZtx6661DvgEiqqmpMTk7CSIiooH01FNP4b333sOBAwegVqudnQ4RERERDQDuAUJERIOSyWTCpUuXOh3Pz8/HgQMH4O/vj/vuu88JmRERERGRM3AJDBERDUpGoxHh4eGYMWMGxo8fD6lUiq+//hparRZisRi/+93v4O7u7uw0iYiIiGiAcAkMERENSiaTCRs3bkRhYSEuXLiAhoYG+Pr6IiIiAs899xzuvvtuZ6dIRERERAOIDRAiIiIiIiIiGvS4BwgRERERERERDXpsgBARERERERHRoMcGCBERERERERENemyADFGlpaXOTuGmxvrZj7WzH2tnP9bOfqxd37B+9mPt7MfaERFZxwYIEREREREREQ16bIAQERERERER0aDHBggRERERERERDXpsgBARERERERHRoMcGCBERERERERENemyAEBEREREREdGgxwYIEREREREREQ16bIAQERERERER0aDHBggRERERERERDXpsgBARERERERHRoMcGCBERERERERENelJnJ0A0lL2lu2Zz7BNKr37MhIiIiIiIaHDjDBAiIiIiIiIiGvTYACEiIiIiIiKiQY8NECIiIiIiIiIa9BzaANm7dy8mTZoEuVyOqKgoHDt2rNv4wsJCREVFQS6XY/LkycjIyOj1mHq9HuvWrUNoaCiCgoKwcOFClJeXC2LKysoQHx+PoKAghIaGIikpCU1NTb3KxWg0YuvWreZcJk2ahK1bt8JgMPSmRERERERERETkBA5rgBw4cAAbNmzAmjVrUFBQgIiICCxYsABlZWVW48+ePYu4uDhERESgoKAAq1evRlJSEg4ePNirMTdu3IjDhw8jPT0dOTk5qK+vR3x8PIxGI4DWxkV8fDwaGhqQk5OD9PR0HDp0CJs3b+5VLn/4wx+wd+9epKSkoLi4GL/97W/xxhtv4Pe//72jSkhERERERERE/cRhDZCdO3di8eLFSEhIgFKpRGpqKuRyudVZHQDw5ptvQqFQIDU1FUqlEgkJCVi0aBF27Nhh85i1tbXYt28ftmzZgujoaKhUKqSlpeHUqVPIy8sDAOTm5uL06dNIS0uDSqVCdHQ0XnzxRWRmZqKurs7mXIqLixETE4M5c+ZgzJgxmDt3LubMmYPPPvvMUSUkIiIiIiIion7ikAZIU1MTSkpKoFarBcfVajWKioqsnlNcXNwpfubMmThx4gSam5ttGrOkpATNzc2CmODgYCiVSnNMcXExlEol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D4GJj4/H8OHDhe29e/eiUaNG2LhxIzQ0NPD8+XPs378fixYtqpCgRERERFRzmZvLkZBQuNjB1V2IiEhVKvcAef36NbS1tYXtiIgIdOvWDRoa+aewsbFBcnJy+SckIiIiohqvqBVfuLoLERGVhcoFECsrK0RGRgIALl++jPv376Nr167C8dTUVNStW7f8ExIRERFRjefp+abQii9c3YWIiMpC5SEwo0aNwvTp03H79m08fPgQDRs2RPfu3YXjsbGxaNasWYWEJCIiIiLy9HzDggcREb03lQsgPj4+0NLSwvHjx9G8eXNMnjwZUqkUAJCRkYHExESMGTOmwoISEREREREREb0vlQsgAODt7Q1vb+9C+w0NDXHu3LlyC0VEREREREREVJ7KVAABgFevXuHPP//E48eP4eLiAiMjo4rIRURERERERERUblSeBBUANm7ciGbNmqFnz5746quvcPXqVQBAeno6PvroI2zfvr1CQhIRERFRzRMWpgVHRz0YGurD0VEPYWFaYkciIqIqTOUCyK5duzBt2jR07twZq1atglz+dhkyIyMjdOzYEXv27KmQkERERERUs4SFacHXV4qEBA3I5RIkJGjA11fKIggREb03lQsga9asQffu3bFt2zb06dOn0PFWrVrh5s2b5RqOiIiIiGomf38dZGdLlPZlZ0vg768jUiIiIqrqVC6A/PXXX+jRo0exx42MjJCenl4uoYiIiIioZnv4UFKm/URERKVRuQCiq6uLZ8+eFXv8r7/+grGxcbmEIiIiIqKazdxcXqb9REREpVG5ANK5c2fs3LkTb968KXQsKSkJ27ZtQ9euXcs1HBERERHVTHPn5kAqVS52SKVyzJ2bI1IiIiKq6lQugMyePRvJycn47LPPsGXLFkgkEpw6dQoBAQFwdXWFpqYmpk+fXpFZiYiIiKgae3fVF39/HQwf/hoWFjJIJHJYWMiwenU2PD0L/zGOiIhIFbVUbWhra4tjx45h2rRpCAgIAACsXr0aANChQwesWrUK5ubmFZOSiIiIiKo1xaoviolPExIk2LlTm0UPIiIqNyoXQADA3t4eBw8exJMnT3D37l3IZDJYW1vD1NS0ovIRERERUQ1Q0qovLIAQEVF5KFMBRKF+/fpo165deWchIiIiohomLEwL/v46SEjgqi9ERFSxVC6AhIWFqdTO09PzvcMQERER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Ui2MY8fcgUdaGvbsbMtzOG65xaOHh9mmjQ8qFRERERERkbpIAYj4hPH99+4jadPSsH/7reU5HD16uHt4xMdjhof7oKIacXQAABYsSURBVFIRERERERGpDxSAyI0zTYzDh2nx0UcEHTxY2sPjyBFrUxgGzltv9Qw8WrTwUcEiIiIiIiJS3ygAEetME9s337i2swSkpWH74QeaWJnCZsNx223uHh79+0NYmM9KFhERERERkfpNAYhUzDSx7d9f2qy0LPDIybE2RUAAjjvucPfwiIuDJlYiExEREREREZHKUwAi5Tmd2PbscffwSE/Hdvq0pSnMwEAcMTHuwCM2FoKDfVSwiIiIiIiIyPUpABFwOLB9+aVn4JGba2kKs1Ej8nr2JHDo0NLQo29fCAryUcEiIiIiIiIi1igAqY9KSrDv3u3u4bFlC8a5c5amMBs3piQ21tXDwxETQ/b33xMVFeWjokVEREREREQqTwFIfVBcjH3nTteRtAGZmRj5+ZamMENCKOnXzx143H47BAb6qGARERERERGRqqUApC4qKsK+fbt7S0tWFkZhoaUpzCZNKOnfn5IBA3AkJODo3RsC9L+LiIiIiIiI1E76irYOComPx37okKWPcTZrhiM+vvRI2oQEnLfeCna7jyoUERERERERqV4KQOogR0xMhQGIs2VL13aWkoQEnN27g81WTRWKiIiIiIiIVC8FIHVQSUICgcnJHu85W7d2H0mbkIDzllvAMPxUoYiIiIiIiEj1UgBSBzkSEnC2a0dJfLyrh4fz5psVeIiIiIiIiEi9pQCkDnJ26ULel18q8BARERERERG5RAFIXaTgQ0RERERERMSDul6KiIiIiIiISJ2nAERERERERERE6jwFICIiIiIiIiJS5ykAEREREREREZE6TwGIiIiIiIiIiNR5CkBEREREREREpM5TACIiIiIiIiIidZ4CEBERERERERGp84zc3FzT30WIiIiIiIiIVCQxMdHfJdRKH374ob9LqBG0AkRERERERERE6jwFICIiIiIiIiJS5ykAEREREREREZE6Tz1ARERERERERKTO0woQEREREREREanzFIBIlZs6dSq33347rVu3pnPnzjz88MMcOHDA32XVK2fPnmXmzJn07duX1q1b07NnT37zm99w5swZf5dWr/zlL39h5MiRREZGEhYWxuHDh/1dUr3w9ttv07t3byIiIhg4cCDp6en+LqleSUtL46GHHqJ79+6EhYWxatUqf5dUryxZsoRBgwbRvn17OnfuzLhx49i7d6+/y6p3li9fTnx8PO3bt6d9+/b827/9Gx9//LG/yxIRqfcUgEiVu+OOO3jjjTfIzMzk73//O6ZpkpiYyMWLF/1dWr1x/Phxjh8/zrx580hPT+fNN98kPT2diRMn+ru0euX8+fMMHjyYZ5991t+l1BspKSk8++yz/Pa3v2Xjxo3ExsYyduxYjhw54u/S6o2CggJ69OjByy+/TFBQkL/LqXc2b97MxIkT+fjjj/noo48ICAggMTGRs2fP+ru0eqVt27bMmzePDRs2kJqayl133cUvf/lLvvrqK3+XJiJSr6kHiPjcV199xYABA9i6dStRUVH+Lqfe+uSTTxg3bhyHDx+mSZMm/i6nXtm5cyeDBg1i9+7ddOjQwd/l1GlDhgyhZ8+eLFu2zPVedHQ0o0aN4oUXXvBjZfXTTTfdxKJFi/jlL3/p71Lqrfz8fCIjI1m1ahXDhw/3dzn1WseOHXnhhRcYP368v0sREam3tAJEfKqgoIBVq1bRrl07IiMj/V1OvZaXl0fDhg1p3Lixv0sR8Yni4mJ27drF4MGDPd4fPHgwmZmZfqpKxL/y8/NxOp2EhYX5u5R6y+Fw8Pe//52CggJiY2P9XY6ISL0W4O8CpG56++23eeGFFygoKCAqKoqPPvqIhg0b+ruseis3N5c//OEP/OpXvyIgQL/tpW46ffo0DoeDVq1aebzfqlUrTp486aeqRPzr2WefpVevXvrC2w/27NnDsGHDKCoqIjg4mJUrV9KzZ09/lyUiUq9pBYh4Zf78+YSFhV33x6ZNm1zjx44dy8aNG/nHP/5B586d+fWvf8358+f9+BnUDVafA5Suwnn44Ydp06YNL774op8qrzsq8wykehmG4fHaNM1y74nUB8899xwZGRm899572O12f5dT70RFRbFp0yY+/fRTJk6cyKRJk9SQVkTEz/StYPHKpEmTePDBB687pl27dq6fN23alKZNm9K5c2f69u1Lx44d+eijj3jooYd8XWqdZvU55OfnM3bsWABWr15No0aNfFpffWD1GUj1adGiBXa7vdxqj1OnTpVbFSJS182ZM4eUlBTWrl1Lx44d/V1OvRQYGMjNN98MlDaI37FjB2+88QZ/+tOf/FyZiEj9pQBEvNKiRQtatGhRqY81TRPTNCkuLq7iquofK88hLy+PsWPHYpom77//PiEhIT6urn64kd8L4luBgYHcfvvtpKamkpiY6Ho/NTWV+++/34+ViVSv2bNnk5KSwrp167jlllv8XY5c4nQ69W8hERE/UwAiVerQoUN89NFH3H333bRo0YJjx47x6quvEhgYyD333OPv8uqNvLw8Ro8eTV5eHqtWreL8+fOuLUjNmjUjMDDQzxXWDzk5OeTk5HDw4EEADhw4wE8//UT79u1p1qyZn6urm6ZMmcITTzxBTEwMcXFxrFixghMnTujUhWqUn5/PoUOHgNIv+I4ePcoXX3xBs2bNaN++vZ+rq/tmzJjB6tWrWblyJWFhYeTk5AAQHBysILwazZ07l2HDhnHTTTeRn5/P+++/z+bNm/nb3/7m79JEROo1HYMrVero0aNMmzaNXbt28dNPPxEeHk58fDwzZ87Ud6Gq0aZNm7jvvvuuem3t2rXceeed1VxR/bRgwQIWLlxY7v3XX39dx4L60Ntvv83SpUvJycmhe/fuvPTSSyQkJPi7rHrjWn/+PPzwwyQlJfmhovrlWqe9zJ49mzlz5lRzNfXXpEmT2LRpEydPnqRJkyb07NmTqVOnMmTIEH+XJiJSrykAEREREREREZE6T6fAiIiIiIiIiEidpwBEREREREREROo8BSAiIiIiIiIiUucpABERERERERGROk8BiIiIiIiIiIjUeQpARERERERERKTOUwAiIlLDHT58mLCwMF599VV/l+ITI0aMYMSIET6bf9KkSfTq1ctn89ckV/u1DAsLY8GCBX6qSERERKTmUAAiIuIHYWFhXv1YtWqVv0utElu2bGHBggXk5ub6u5RaT7+WIiIiIpUT4O8CRETqozfffNPj9V/+8he2bdvGn/70J4/34+LiqrMsn8nIyGDhwoX84he/ICwszOPaBx984Keqaif9WoqIiIhUjgIQERE/GDdunMfrzz//nB07dpR7H0q3wNQ0hYWFBAUFVclcgYGBVTKP6NdSRERE5Hq0BUZEpBb5n//5H/r27Ut4eDjx8fF8/vnn5cacOHGCZ555hm7duhEeHk50dDRLly7FNE2PcYWFhcydO5devXoRHh5O7969mT9/PhcuXPAY16tXL37+85+zceNGhg4dSkREBK+99prrempqKiNHjqRd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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>These <strong>three</strong> charts above can tell us a lot about our target variable.</p>
<ul>
<li>Our target variable, <strong>SalePrice</strong> is not normally distributed.</li>
<li>Our target variable is right-skewed. </li>
<li>There are multiple outliers in the variable. </li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[11]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#skewness and kurtosis</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Skewness: &quot;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">train</span><span class="p">[</span><span class="s1">&#39;SalePrice&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">skew</span><span class="p">()))</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Kurtosis: &quot;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">train</span><span class="p">[</span><span class="s1">&#39;SalePrice&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">kurt</span><span class="p">()))</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Skewness: 1.8828757597682129
Kurtosis: 6.536281860064529
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[24]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## trainsforming target variable using numpy.log1p, </span>
<span class="n">train</span><span class="p">[</span><span class="s2">&quot;SalePrice&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">log1p</span><span class="p">(</span><span class="n">train</span><span class="p">[</span><span class="s2">&quot;SalePrice&quot;</span><span class="p">])</span>

<span class="c1">## Plotting the newly transformed response variable</span>
<span class="n">plotting_3_chart</span><span class="p">(</span><span class="n">train</span><span class="p">,</span> <span class="s1">&#39;SalePrice&#39;</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAABEAAAALYCAYAAAB8GodbAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADl0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uIDMuMC4zLCBodHRwOi8vbWF0cGxvdGxpYi5vcmcvnQurowAAIABJREFUeJzs3Xl4VOX5//HPzGQPJCExJEFZNWBYFcuiLJGokWoVRVZtVQRFQcV+LSBa22pVRLTWIlqFoqBQib9iRaEoAg07biiIECMIJiwJZCFkzyy/PyhJThYgkMyZmbxf15XLnuecM7nnkM6cuee+n8eSn5/vEgAAAAAAgA+zmh0AAAAAAABAUyMBAgAAAAAAfB4JEAAAAAAA4PNIgAAAAAAAAJ9HAgQAAAAAAPg8EiAAAAAAAMDnkQABADRYjx491KNHD7PDAAAA8FozZ85URESENmzYYHYozQYJEABopiIiIhQREXHaY2688cYmeWOOiIgggQIAAE7r1L1K9Z/o6Gh17dpVd999t7766iuzQzR44IEHasUbFxenPn36aNq0aTp8+HCT/N5T92sHDhxoksf3JX5mBwAA8D7Lly83OwQAANBMTJ8+vfJ/FxYWaufOnfrwww/18ccf67333tO1115rYnS13XDDDZVf9Bw7dkxr1qzRm2++qWXLlmnNmjVq3769yRE2XyRAAAAN1rFjR7NDAAAAzcSMGTNqjf3tb3/TH/7wB7388sselwC58cYbdccdd1RuV1RUaPjw4dqwYYNmz56tV1991cTomjdaYAAADVbXHCBlZWV67bXXNHjwYHXo0EGxsbHq3r27RowYUVkxsmHDhsq2m4yMDEOJ6AMPPGB4vPXr12vkyJHq2LGjWrdurV69emn69Ok6evRonTGlp6fr17/+tdq3b682bdooOTlZn3zyiRYvXqyIiAjNnDnTcPypctH9+/drzpw56t+/v2JiYnT77bdLko4fP65XXnlFv/rVr5SQkKDo6GhdfPHFGjNmjLZt21ZnDKdaewoLCzVjxgx169ZNsbGxGjhwoD7++GNJkt1u1wsvvKDevXsrJiZGl112md58880G/gsAANC8XXPNNZKknJycWvvKysr0yiuvaMCAAYqLi9NFF12ka6+9VosWLZLL5TIc+8QTTygiIkLTpk2r9TgffvihIiIilJSUpIqKinOO1d/fX+PGjZOks27bOdv7oIiICG3atEmS1KtXr8r7KlqN60YFCACgUdx///364IMPdOmll2rUqFEKDQ3V4cOH9fXXX+vjjz/WzTffrHbt2mn69OmaNWuWwsLCDEmP6m/Ub731lv7v//5PwcHBGjZsmGJjY7Vt2za98cYbWrFihf7zn/+obdu2lcenpaUpOTlZx48fV3Jysrp3764DBw7o17/+ta677rrTxj1t2jRt27ZN119/vZKTk9WiRQtJ0g8//KBnnnlGV111la6//npFREQoIyNDK1eu1OrVq/XPf/5TycnJtR7Pbrfr1ltvVUFBgW688UadOHFC//rXv3TnnXdq2bJleuONN7Rr167KG7d//etfmjZtmi644AINHz78vP4NAABoLtauXStJ6t27t2G8oqJCt912mzZu3KhLLrlE99xzj8rLy/Xxxx/r4Ycf1ubNm/X3v/+98vg//elP2rp1q958800NHDhQN998syRp//79euihhxQWFqYFCxbI39/fbc+tIfdB06dP15IlS5SRkaH7779f4eHhklT5XxiRAAGAZq5mZUR1P//881k9xvHjx/Xvf/9bvXr10po1a+TnZ3x7OfXtTPv27TVjxgzNmjVL4eHhdZa0/vzzz5o+fbpCQkL02WefKSEhoXLfM888oxdffFGPPvqoUlJSKscfffRRHT9+XLNmzdLEiRMrx9etW6dbb731tLHv3LlT69evr9WP27lzZ+3Zs0dRUVG14rv22mv1xBNP1JkAOXz4sH7xi19oxYoVCggIkHTyW6oJEybozjvvVNeuXbV58+bKRMuYMWN0/fXX6+WXXyYBAgBAHarfqxQVFWnXrl1KTU3VlVdeqT/+8Y+GY+fMmaONGzcqKSlJ7733XuV78e9//3sNHTpU7733noYOHapbbrlF0snqjAULFmjw4MF66KGH1KtXL8XFxemee+5RQUGBFi5cqA4dOpxX/Ha7XW+//bak2gmbmhp6HzRjxgxt3LhRGRkZeuCBB5hf5AxIgABAMzdr1qzzfgyr1SqXy6XAwEDZbLZa+2smEU4nJSVF5eXluv/++w1v+pI0depULV68WJ9++qkOHTqkNm3aKCMjQxs3blT79u01YcIEw/FDhgzRkCFDtG7dunp/30MPPVTnzUJ935y0a9dOw4YN07x585SRkWGoRDnl2WefrbzhkqRbb71VDzzwgAoKCvTkk09WJj8kqV+/furQoYO+//57ORyOOq8fAADNWV33Km3bttWYMWMUExNjGH/33Xcl1X4vDg8P1x/+8AeNHTtWCxcurEyASCe/oJkzZ47uvPNO3XPPPerdu7e+/vprTZgwQcOGDWtwvCtWrKj8EiknJ0dr1qzRTz/9pMjISE2dOvW05zb0PggNwxwgANDM5efn1/szYMCAs3qMli1b6oYbbtDnn3+uAQMG6LnnntO6detUWFjY4Hi+/fZbSdLgwYNr7QsMDFT//v0lSTt27JB0soJDkvr06VNn8qBfv36n/X2/+MUv6t23detW3X333erWrZtat25d2Vc7b948SapzObuIiAi1a9fOMGaz2RQdHS1JdfbkxsbGyuFwKCsr67SxAgDQHFW/Nzl48KDWrFmjDh06aMqUKXriiScqjztx4oT27dun1q1b10oeSFJiYqKkqnuN6m6++Wbde++9+uqrrzRv3jz16NFDzz777DnFu3LlSs2aNUuzZs3SO++8I6vVqnvvvVfr168/YzVJQ++D0DBUgAAAGsWCBQs0Z84cvf/++3rhhRcknSwrHTp0qJ555pmzLsksKCiQJLVu3brO/ae+6Tl13IkTJySpMsFQU32Pc6b9H330ke666y4FBQVpyJAh6tChg0JCQmS1WrVx40Zt2rRJZWVltc5r2bJlnY93KjkTFhZW777zmWANAIDmIDQ0VFdccYXeeecddevWTX//+981ceJEtWvX7oz3ECEhIQoLC6s8rqZTFZ6SNH78eAUGBp5TjHPnzjWsAtMQDb0PQsOQAAEANIqgoCBNnTpVU6dO1eHDh7VlyxalpKToo48+0p49e7R58+azmkDsVIIgOzu7zv2nqiROHXcq4VDf6jD1Pc4pFoulzvHnnntOAQEBWrdunbp06WLY98gjj1TOuA4AANwvIiJCl1xyib799lvt2LFD7dq1O+M9RHFxsQoKChQZGVlrX35+vh544AEFBAQoMDBQf/rTn3TNNdfU2eralBp6H4SGoQUGANDo4uLiNHz4cL333nvq27ev0tPTlZaWVrnfarXK6XTWeW6vXr0knVwyt6aysrLKJWhPHdezZ09J0hdffCGHw1HrnPqWrD2Tffv2qUuXLrWSH06nU1u3bj2nxwQAAI0nPz9fkiqXtm3ZsqU6deqk7Oxs7dmzp9bx69evlyRddtlltfZNmjRJGRkZevrpp/XKK68oPz9fEyZMkN1ub8JnUFtD74OkqkrS+u6tUIUECADgvB07dkxffPFFrfGysjIdP35c0skKkVOioqJ07NgxlZSU1Dpn1KhRCggI0D/+8Q/98MMPhn1/+ctfdOjQISUnJysuLk6SdNFFF2ngwIE6cOCA5s+fbzh+3bp1p50A9XTatWunffv26dChQ5VjLpdLzz//fJ03VQAAwH0+/vhjHThwQP7+/ob5vn7zm99IOrnqS/XW0oKCAj399NOSpDvvvNPwWK+99ppWrlypG264Qffff7+GDx+ucePGadu2bXrmmWfc8GyqNPQ+SKqabD4jI8OtsXojWmAAAOft0KFDuu666xQfH6/LLrtMF154oYqKirR27Vrt3btXN910ky655JLK44cMGaKUlBTddtttuuqqqxQYGKju3bvrl7/8pdq1a6dZs2bp//7v/zRkyBDdcsstiomJ0bZt27Rp0yZdeOGFeumllwy//8UXX9T111+v6dOna82aNerRo4cOHDigDz/8UDfccINWrlwpq7VhOf9Jkybpt7/9rRITE3XzzTfLz89P27ZtU1pamoYOHapVq1Y1yrUDAACnV30Z3OLiYqWlpWn16tWSpD/84Q+G+TImT56szz77TJ999pmuuuoqXX/99aqoqNBHH32kQ4cOacyYMYYVYLZv364//elPuuiiizR37lzD7/z888/1yiuvaNCgQbrmmmvc8Ex1TvdBQ4YM0QcffKApU6Zo2LBhCg0NVXh4uO677z63xOxNSIAAAM5bu3bt9Pjjj2vDhg3atGmTjh07pvDwcHXq1ElTpkzR7bffbjj++eefl9Vq1bp167Rt2zY5HA6NHTtWv/zlLyVJ48aNU6dOnTRnzhytWLFCRUVFiouL03333aff/e53tSYGu/TSS7V69Wo9/fTTWr9+vTZu3Khu3brp3Xff1Q8//KCVK1c2uFd23LhxCggI0Ouvv65//vOfCgoK0pVXXqm5c+dq+fLlJEAAAHCT6svg2mw2XXDBBRo6dKjuu+8+DRkyxHBsQECAli1bptdff10pKSmaP3++rFarEhIS9Nhjj1VWiEjS8ePHNW7cODmdTv3jH/9Qq1atKvcFBQXp7bff1pAhQzRx4kRt2LDBUHXRlBp6H/TrX/9aBw8eVEpKiubOnauKigq1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06fPZft87733iIqK4l//+hcALVu2ZNOmTbz55psKQERERES86HILmubkGPD3d6zp4c5WtheLCjrOf0db6PLLJwSsWYPhfavLNoU33eTYvSUxEVt0dIU/i4iIXH2qzRog+fn5zJ07l7CwMNq2bVvqfRs3bqR3797FzvXp04cFCxZgtVoxGo3eLlVERESkxnFnQdOyN2KxU7eunVDbSXqcWMqfgszcbl2B/3tuhB6tW18IPWJiruBTiIjI1cznA5Dly5czbtw48vLyiIqKIiUlpdTpLwCHDx+mV69exc41aNCAgoICjh07RlQp+7hnZWV5suxqp6Z/fl+l9+Kb9F58k96Lb9J78U2efi+fflqXZ55pgc1WsQVNa3OaP9ZZxLS271Hnq6/wwwrnym5ztkULcvr143jfvpxr0eLChWr831xN/fsSo9BKRCqJzwcg3bt3JyMjg2PHjjF37lzuuecePv/881KDDACDofj/+Np//3XDpecvVpO/8WZlZdXoz++r9F58k96Lb9J78U16L77pSt5L0RSXAwcundYC7q7pUSSEMwwmDRNm7mAZQSfPw9qy2xTeeKNj95akJGyxsdQGalfok/ge/X0REfE+nw9AQkJCuP7667n++uvp2LEj7du3Z968eUyZMuWy9zds2JDDhw8XO3f06FECAgKoW7duZZQsIiIictW5dIqLe9NairuGXAaRjgkzg0gn2NUwD6AwOtoxvSUpCVvr1o7ERUREpAJ8PgC5lM1mIz8/v9TrcXFxpKenFzu3Zs0a2rVrp/U/RERERMqpIju3XCyYPAbyKSbMDCaNEPJctils0QLrsGGONT1uukmhh4iIeESVBiBnzpxh7969gCPYyM7OZtu2bURERFCnTh1mzJjBgAEDiIyM5NixY8yZM4eDBw+SmJjo7GPChAkAzJo1C4CxY8cyZ84cHnvsMcaOHcuGDRv46KOP+M9//lP5H1BERESkmrqS4COIswzkU8YEmumfn0Ztcl22sTVrRn5R6HHzzQo9RETE46o0ANm8eTNDhgxxHk+fPp3p06czevRoXn75ZXbs2MGHH35ITk4OdevWpV27dixbtoybbrrJ2SY7O7tYn82bN8dsNvPEE0/w7rvvEhUVxYsvvqgtcEVERETcUNHgoxbn6M9nmDAzlCWEcgZKH7QLgK1JE+f0lsJbb1XoISIiXlWlAUj3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reoSfI7bAcgTTzzBqlWr6NKlC/3798dgMDB//nzmzp1LWloaTZo04ZFHHvFmrSIiJCRcw9q1F3/rqthoiwCs9GY1JswkkUJdjrtsY4uM5EivXoTccw+FnTop9BARERERqUbcDkAiIyP54osveP7551myZAl2ux2LxUJoaCjJyck888wzhIeHe7NWEamBLr+OR8VCD38K6MUXmDAzjEXU55jLNraGDR0jPRITKezcmQN79xITE1Oh54uIiIiISNVxOwABqF+/Pq+//jqvv/46R48exWazUb9+ffz0W1AR8YLOnUPYudOfigYeAH4U0pO1mDAznE9owFGXbWz162MdOtSxpkeXLuDvX+Hni4iIiIiIbyhXAHKx+vXre7IOEZFiriT88KOQbnxJMgsZzidEcthlG1vduhdCj65dIaDC3x5FRERE5Ar4+toV//73v/nss8/o378/999/f1WXI+VQ6k/4L774Yrk7MxgMTJky5YoKEpGarfiUF/fDDwM2upKJCTMj+JhrKX3XqiK2iAgKhgzBmpREQbduYDRWsGoRERERqQlycnJYvXo1drud1atXk5ycTERERFWXJW4qNQB54YUXSpwr2v3FbreXOG+328sdgGRmZvLGG2+wdetWDh06xFtvvcWYMWOc15csWcL777/P1q1bOXbsGEuXLqV79+5l9pmRkcGQIUNKnN+4cSM33nij27WJiPdZLEYeeiiI3NxLgw73gg8DNv7A187Q4zoOumxjr1MH6+DBjtCjZ0+FHiIiIiLiNrPZjNVqBcBqtbJw4UKNAqlGSl284/jx48W+du7cyU033cSIESNYvXo1+/fvZ//+/axatYrhw4fTtm1bduzYUa6H5+bm0rp1a1544QWCg4NLXM/LyyMuLo5p06aV+4OtX7+eXbt2Ob+io6PL3YeIeM/kyUH8+c/B5Ob64Qg8Lv4qnQEbnfmaV/gb+2lKJt14kBllhh/2sDDyR48m12zmVFYWZ996i4K+fRV+iIiISKkylgbn8wAAIABJREFUMzMZNWoUsbGxhIeHM3/+/GLXlyxZwrBhw4iOjiY8PJyMjAy3+v3yyy/p2bMnkZGR3HLLLbz77rveKF+8ZO3atc4BAXa7nbVr11ZxRVIebk9ynzJlCs2aNWP27NnFzrdv3545c+Zw1113MWXKFObOnev2w+Pj44mPjwdg4sSJJa6P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N2+99Zb5+I4dOxg2bBi+vr7cfvvtDBs2jAMHDpiPx8TE8MorrwDQuXNn8/Ce3bt3AyXPW2EymVi6dCm9e/fGx8eHVq1aERoayueff24+JzY2lpCQEO666y6aNm1Kt27deOuttzAajZX7cIEtW7bQq1cvvL296datG++//z4xMTEWPS0K52QpaXhSx44dGTdunHk7PT2d6dOnExAQgK+vL82aNWPYsGHs37/f4rrr53kpq40r81mW5PLly0yfPt3c9h06dGDWrFnF2j4pKYkHHniAFi1a0KxZM+69914mTZpk/YMUERERqSbUA0RExA6tX7+eixcvMnbsWFxdXVm8eDGPPPIIhw8fxsPDA4Bff/2VAQMGkJeXx2OPPYaPjw/79u1j5syZnD17ljlz5gAFAcOjjz7Ktm3bGDlyJPfeey/79+9n3rx5HD16tNiX+xMnTjBmzBjGjBnDI488gq+vLwBr1qzhiSeeoE+fPrz88ssYjUZiY2MZMWIEmzZt4t5772X48OEcP36chIQEoqOjady4MQB33313qe86ceJE3n//ffr168fDDz+MyWTiiy++YN++fQQEBACwdOlSWrduzYABA3Bzc2PHjh3MmjWLy5cvM2PGjAp/vklJSTz88MO0atWKl19+mZycHF599VW8vb0rfK9Cp06dYv369YSEhNCqVSsuXbrE+++/T0hICDt27KBdu3YW51tr48p8ljfKzs5m2LBhnD59mscff5w77riDw4cPs3DhQv7zn/+wcuVKAH788UciIyNp164dL774InXr1uXUqVNs2bKl0p+HiIiIiL1RACIiYodOnjzJ119/TZMmTQDo3bs3gYGBrFmzhr/+9a8A5h4ce/fupWnTpgCMHTsWHx8fFi5cyLhx42jRogVbtmxh27ZtTJ48menTpwPwl7/8BS8vLxYvXszOnTvp16+fxbNXrlzJkCFDzPuuXLnC5MmTiYqKYvHixeb9Y8eO5b777mP27Nls2LCBDh060LFjRxISEhg6dCgtWrQo8z13797N+++/z2OPPcb8+fPN+59++mmLXiybN2+mbt265u2//OUvPPvssyxZsoSpU6dSp06dCn2+M2bMwN3dna1bt5oDpZCQEHPgUhnt2rXju+++w9HR0bzv8ccfp3v37rzzzjssWLDA4nxrbVzRz7IkixYt4vjx4+zcudMiOGnbti2TJ0/m888/JyAggB07dnD16lXWrFljDloAZs6cWeFnioiIiNgrDYEREbFDoaGh5i/GAJ06daJhw4acOnUKKOjVsX79egYNGoSjoyMXL140/wQHB2M0Gtm7dy9QMNTDYDDwzDPPWDxj4sSJ5uPXa9asmUX4AQVDXzIyMoiMjLR4VnZ2Nv369WPfvn3k5uZW+D03bNgAYA5mrmcwGMz/XBh+5Ofnk5GRwcWLF+nduzdXrlzh+PHjFXpmamoqBw8eZOTIkebwAwp6VgQHB1f4HQrVqVPHHH7k5OSQlpaG0WikW7dufPfdd8XOt9bGVWHt2rX07NmTJk2aWLRbYeC1a9cuABo0aADApk2b/tCwIhERERF7ph4gIiJ2yM/Pr9i+Ro0akZ6eDsCFCxfIyMjgww8/5MMPPyzxHhcuXADgzJkzeHt7F1tFxMfHh0aNGnHmzBmL/SX1NPj5558BCAsLK7XmS5cuWXyhL4+TJ0/i5eWFl5dXmeft27eP2bNn8/XXX3Pt2rViz62Iwvdt3bp1sWN33nknW7durdD9ChmNRubPn8+KFSuKTWZb0mdqrY2rws8//8z333+Pv79/iccL/4w8+OCDfPDBB0yYMIFZs2YRGBjIkCFDCAsLw9nZucrqEREREbElBSAiInbo+mEU1yscFlL4W/qHHnqIRx55pMRzW7VqZfU5N06WCpS44kvh8xYtWsTtt99e4r0aNmxo9XklPf/6nh4lOXXqFGFhYbRq1YqYmBh8fX2pU6cOBw8eZObMmRXusVD4ziU998bPo6zabnzuW2+9xezZsxk1ahTTp0/H09MTR0dH3nzzTU6ePFnsemttXBWMRiOBgYG88MILJR4vbEs3Nzc+/fRT9uzZw7Zt20hMTOSJJ55g4cKFbNmypcpWARIRERGxJQUgIiLVUJMmTWjYsCF5eXkW83eUpHnz5mzfvp2MjAyLXiCpqalcvnyZ5s2bW33eHXfcYX6utedZCzSu16pVKxITE/n1119L7QWyefNmcnJyWLVqlUWtlV0yuLA3xn/+859ixwp7uhQqHCJzYy+Tq1evcu7cOYt9CQkJ9O7d22KOFChYzaWyKvJZluSOO+4gKyvLapsBODg4EBgYSGBgILNnz+bdd99l0qRJbNy4kcjIyD9Uh4iIiIg90BwgIiLVkKOjIyNGjOCTTz4pcX6JS5cumefkGDRoECaTiUWLFlmcUzgp56BBg6w+Lzg4mEaNGjFv3rxiy6dC0VAKKJqvIyMjw+p9R4wYAUB0dHSxY4U9IQp7SlzfM+Lq1av861//snr/knh7e9OpUydWrVplMdzk2LFjJCYmWpzboEEDmjRpYl56ttDy5cvJz8+32Ofo6Fis98aBAwf44osvKlUnVOyzLEl4eDjffPMNmzdvLnYsOzubrKwsANLS0ood79y58x96toiIiIi9UQ8QEZFqatasWezdu5fBgwfz6KOP0q5dOzIzMzly5AgbN27km2++wdvbm0GDBjFgwABef/11UlJS6Nq1K1988QVxcXEMGTKkXL0DGjRowPz58/nzn/9M7969iYiIwNvbm//+97/s3r2bevXqsWbNGgDuueceAF599VUefPBBXFxcCAwMLLGHR58+fXj44Yd57733OHXqFAMHDgTgyy+/pH379kyaNIng4GBcXFwYOXIkjz/+ONeuXWPVqlU4OFQ+w3/llVd48MEHGThwIGPGjCE7O5ulS5fStm1bvv/+e4tzH3/8cebNm8f48ePp3r073377LUlJSRarpQA88MADzJkzhyeffJKAgAB+/vlnVqxYQZs2bcxBQ0VV5LMsybPPPsvWrVt59NFHiYyMpFu3bly9epWffvqJtWvXEh8fT/fu3Xn99dfZs2cPgwYNonnz5mRkZLB8+XLq1avH4MGDK1W7iIiIiL1RACIiUk01adKExMRE/v73v7Np0yZWrFhBo0aNuPPOO3nxxRfNwzcMBgMffPABc+bM4eOPPyY+Ph4fHx8mT57MlClTyv280NBQbrvtNt58800WLVpEdnY23t7e3HvvvYwZM8Z8Xvfu3Zk+fTorVqzg6aefxmg0snHjxlK/tC9cuJD27dvzwQcfMHPmTOrXr0/nzp3p1asXUDAxaWxsLLNnz2bmzJk0btyYkSNH0rt37zInZS1L//79iY2N5dVXX+XVV1/Fz8+Pv/3tb/z3v/8tFoBMnjyZtLQ0EhISWLduHb1792b9+vUMHz7c4rwXXniB7Oxs4uPjWb9+PW3btmX58uV8/PHH7Nmzp1J1VvSzvJGbmxsbNmxg/vz5JCQk8PHHH1OvXj1atmzJuHHjzBPBDhkyhJSUFD766CMuXLiAp6cn3bt353//93/LNURKREREpDowZGRkVN1sayIiItVYTEwMc+fO1bAPERERkRpIc4CIiIiIiIiISI2nAEREREREREREajwFICIiIiIiIiJS42kOEBERERERERGp8dQDRERERERERERqPAUgIiIiIiIiIlLjKQARERERERERkRpPAYiIiIiIiIiI1HgKQERERERERESkxlMAIiIiIiIiIiI13v8HVdx6+gUNSxIAAAAASUVORK5CYII=
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As you can see the log transformation removes the normality of errors. This solves some of the other assumptions that we talked about above like Homoscedasticity. Let's make a comparison of the pre-transformed and post-transformed state of residual plots.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[25]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Customizing grid for two plots. </span>
<span class="n">fig</span><span class="p">,</span> <span class="p">(</span><span class="n">ax1</span><span class="p">,</span> <span class="n">ax2</span><span class="p">)</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">subplots</span><span class="p">(</span><span class="n">figsize</span> <span class="o">=</span> <span class="p">(</span><span class="mi">20</span><span class="p">,</span><span class="mi">6</span><span class="p">),</span> <span class="n">ncols</span><span class="o">=</span><span class="mi">2</span><span class="p">,</span> <span class="n">sharey</span> <span class="o">=</span> <span class="kc">False</span><span class="p">,</span> <span class="n">sharex</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="c1">## doing the first scatter plot. </span>
<span class="n">sns</span><span class="o">.</span><span class="n">residplot</span><span class="p">(</span><span class="n">x</span> <span class="o">=</span> <span class="n">previous_train</span><span class="o">.</span><span class="n">GrLivArea</span><span class="p">,</span> <span class="n">y</span> <span class="o">=</span> <span class="n">previous_train</span><span class="o">.</span><span class="n">SalePrice</span><span class="p">,</span> <span class="n">ax</span> <span class="o">=</span> <span class="n">ax1</span><span class="p">)</span>
<span class="c1">## doing the scatter plot for GrLivArea and SalePrice. </span>
<span class="n">sns</span><span class="o">.</span><span class="n">residplot</span><span class="p">(</span><span class="n">x</span> <span class="o">=</span> <span class="n">train</span><span class="o">.</span><span class="n">GrLivArea</span><span class="p">,</span> <span class="n">y</span> <span class="o">=</span> <span class="n">train</span><span class="o">.</span><span class="n">SalePrice</span><span class="p">,</span> <span class="n">ax</span> <span class="o">=</span> <span class="n">ax2</span><span class="p">);</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAABU0AAAGWCAYAAABM0KKqAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADl0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uIDMuMC4zLCBodHRwOi8vbWF0cGxvdGxpYi5vcmcvnQurowAAIABJREFUeJzs3XlwXOWZP/rve07v2iVrM7ZlEjxs11FmSJBhCjJADBGZsA3OaCbFEAhjwHDBLnBBZoYackkGE99gBwccNt8Chvw8mNUhP0N5frgmZmLLpGoiOzgBOzGKZcvaW1JLvZzlvX+83ae7pda+tvr7qXKA06dPv91HdqSvn/d5RDAYlCAiIiIiIiIiIiIiAIA21wsgIiIiIiIiIiIimk8YmhIRERERERERERGlYGhKRERERERERERElIKhKREREREREREREVEKhqZEREREREREREREKRiaEhEREREREREREaVgaEpERERERERERESUgqEpEREREVEW++///m80NDTg/PPPR3FxMV599dUxn/Pxxx/j2muvRVVVFc4//3w88cQTkFLOwmqJiIiIsgNDUyIiIiKiLDYwMIALLrgAmzZtgt/vH/P8vr4+3HjjjaioqMAHH3yATZs2Ydu2bfjJT34yC6slIiIiyg6uuV4AERERERFN3tVXX42rr74aALBu3boxz9+1axfC4TC2b98Ov9+PCy64AJ9++imeeeYZ3HvvvRBCzPSSiYiIiOY9VpoSTcKxY8fmegk0y3jPcw/vee7hPadccejQIVxyySVpValXXXUVWltb0dzcPIcro+nEP9NyD+95buH9zj2857OPlaZERERERDmkvb0dixcvTjtWXl7uPLZ8+fKMz+MPa9mH9yz38J7nFt7v3MN7Pr1WrFgx6uMMTYmIiIiIcszQLfiJIVCjbc0f6wcLml+OHTvGe5ZjeM9zC+937uE9n33cnk9ERERElEMqKirQ3t6edqyzsxNAsuKUiIiIKNcxNCUiIiIiyiEXX3wxDhw4gEgk4hzbt28fqqurUVNTM4crIyIiIpo/GJoSEREREWWxUCiEw4cP4/Dhw7BtGy0tLTh8+DBOnjwJAPje976H6667zjn/5ptvht/vx7p163D06FHs3r0bW7duxbp160bdnk9ERESUSxiaEhERERFlsf/5n//B5ZdfjssvvxzhcBiPP/44Lr/8cvzbv/0bAODMmTM4ceKEc35RURHeeusttLa24oorrsDGjRtxzz334N57752rt0BEREQ073AQFBERERFRFrvssssQDAZHfHz79u3Djl144YXYs2fPTC6LiIiIKKux0pSIiIiIiIiIiIgoBUNTIiIiIiIiIiIiohQMTYmIiIiIiIiIiIhSsKcpEdECtLcljKeOhNAcslCTr+O+lflYvcQ/18siIiIimhC9qRHuPTuhdbTCLq+GUd8Aq7ZurpdFREQ5gJWmREQLzN6WMDYe7EVb2EKJR6AtbGHjwV7sbQnP9dKIiIiIxk1vaoT3la0QwS7IvAKIYBe8r2yF3tQ410sjIqIcwNCUiGiBeepICB4NCLg0CCEQcGnwaOo4ERERUbZw79kJ6XIDXh8gBOD1QbrccO/ZOddLIyKiHMDQlIhogWkOWfDrIu2YXxdoDllztCIiIiKiidM6WgGPN/2gx6uOExERzTCGpkREC0xNvo6wJdOOhS2Jmnx9jlZERERENHF2eTUQi6YfjEXVcSIiohnG0JSIaIG5b2U+YjYwaNqQUmLQtBGz1XEiIiKibGHUN0CYBhCNAFIC0QiEacCob5jrpRERUQ5gaEpEtMCsXuLH5lVFqPTr6IlJVPp1bF5VhNVL/HO9NCIiIqJxs2rrEL1lPWRxGcRAP2RxGaK3rIdVWzfXSyMiohzgmusFEBHR9Fu9xM+QlIiIiLKeVVvHkJSIiOYEK02JiIiIiIiIiIiIUjA0JSIiIiIiIiIiIkrB0JSIiIiIiIiIiIgoBUNTIiIiIiIiIiIiohQMTYmIiIiIiIiIiIhSMDQlIiIiIiIiIiIiSuGa6wUQERERERERUe7Qmxrh3rMTWkcr7PJqGPUNsGrr5npZRERpWGlKRERERERERLNCb2qE95WtEMEuyLwCiGAXvK9shd7UONdLIyJKw9CUiIiIiIiIiGaFe89OSJcb8PoAIQCvD9LlhnvPzrleGhFRGoamRERERERERDQrtI5WwONNP+jxquNERPMIQ1MiIiIiIiIimhV2eTUQi6YfjEXVcSKieSRrQtPnn38el156KZYuXYqlS5di9erVeP/9953HpZR4/PHHcd5556Gqqgpf//rX8bvf/S7tGsFgEGvXrsWyZcuwbNkyrF27FsFgMO2cjz/+GNdeey2qqqpw/vnn44knnoCUMu2cd955B3V1daioqEBdXR1+/vOfpz0+nrUQERERERHR/KM3NcK3aQMCDzTAt2kDe21OM6O+AcI0gGgEkBKIRiBMA0Z9w1wvjYgoTdaEposXL8b3vvc9/Nd//Rf27duHyy+/HN/61rfw29/+FgDw4x//GE8//TSeeOIJfPDBBygvL8eNN96I/v5+5xp33HEHDh8+jF27duH111/H4cOHceeddzqP9/X14cYbb0RFRQU++OADbNq0Cdu2bcNPfvIT55xDhw7h9ttvx5o1a7B//36sWbMG3/72t/HrX//aOWc8ayEiIiIiIqL5hUOKZp5VW4foLeshi8sgBvohi8sQvWU9rNq6uV4aEVEa11wvYLy+/vWvp/33I488ghdffBEfffQRLrzwQmzfvh3r16/H9ddfDwDYvn07VqxYgddffx233XYbPvnkE/znf/4n3nvvPdTVqT+Mt2zZgvr6ehw7dgwrVqzArl27EA6HsX37dvj9flxwwQX49NNP8cwzz+Dee++FEALbt2/HZZddhgcffBAAcO6552L//v3Yvn07XnzxRUgpx1wLERERERERzT9pQ4oANaQofpyh3vSxauv4eRLRvJc1laapLMvCG2+8gYGBAVx88cVobm5GW1sbrrzySuccv9+PSy+9FI2N6m8EDx06hPz8fCcwBYBVq1YhLy8v7ZxLLrkEfr/fOeeqq65Ca2srmpubAQAfffRR2uskzklcYzxrISIiIiIiovmHQ4qIiCghaypNAdVv9Oqrr0YkEkFeXh7+/d//HRdeeKETRpaXl6edX15ejtZW9X9u7e3tKCsrgxDCeVwIgUWLFqG9vd05Z/HixcOukXhs+fLlaGtry/g6iWu0tbWNuZaRHDt2bOwPgeYN3q/cw3uee3jPcw/v+fRasWLFXC+BiGhC7PJqiGBXstIU4JAiIqIclVWh6YoVK7B//3709vZi9+7duPvuu/Huu+86j6cGooAayDQ0JB1qrHMSQ6DGOmfosfGck+n9UXZItHSg3MF7nnt4z3MP7zkRERn1DfC+shUSUBWnsSiEaSDGIUVERDknq7bnezwefO5zn8Of//mf41//9V+xcuVKPPPMM6isrAQAp9ozobOz06n4rKioQGdnpxOCAirI7OrqSjsn0zWAZOVoZWXlqK8znrUQERERERHR/MMhRURElJBVoelQtm0jFouh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iYiIRsGohqarVq3CbbfdFveYioqK0L+7XC4sW7YMAPDCCy8gLy8vdF9paSnOnTsXEUxKKXH+/PlQVWhpaWmfSs9z584B6K0cLSsri3lM+P2AUU0avrbwYxJZCxERUSotqrAxJCUiorSiza1iSEpERBljVHualpSU4MILL4z7J9iztLOzE0uXLoWu63jxxRdht9sjzjV//ny4XC7U19eHbquvr0dXV1eot+j8+fNx5MgReDye0DGHDx9GeXk5KisrAQDz5s3D4cOHI859+PDh0DkqKytRVlYWcYzH48GRI0cinmegtRAREREREREREVF6yohBUJ2dnbj11lvhdDrx3HPPobu7G83NzWhubobP5wNgTLn/xje+gbVr1+LYsWOor6/H2rVr8c1vfjO01W7p0qWw2WxYvXo1PvjgA+zfvx87duzA6tWrQxWh3/ve9/Daa6/h6aefxieffIKnn34adXV1WLVqFQBj2/2qVauwY8cO7N+/Hx988AFWryYZGA0AABClSURBVF6NgoICLF26NOG1EBERERERERERUXrKiEFQ7777Lo4dOwYAuOyyyyLuC+95+rOf/QwbNmzArbfeCgCorq7Gk08+GTq2qKgIv//977Fu3TpcffXVKC4uxv33348HHnggdExVVRV27dqFzZs3Y8uWLbjggguwa9cuXH755aFjvv/978PtdmP9+vVwOp247LLL8Lvf/Q5jxowJHTPQWoiIiIiIiIiIiCg9CafTKUd7EUSZhsNCcg+vee7hNc89vOZElE34My338JrnFl7v3MNrPvIyYns+ERERERERERER0UhhaEpEREREREREREQUhqEpERERERERERERURiGpkRERERERERERERhGJoSERERERERERERhWFoSkRERERERERERBRGOJ1OOdqLICIiIiIiIiIiIkoXrDQlIiIiIiIiIiIiCsPQlIiIiIiIiIiIiCgMQ1MiIiIiIiIiIiKiMAxNiYiIiIiIiIiIiMIwNCUiIiIiIiIiIiIKw9CUctIbb7yB5cuX4+KLL0ZxcTF+/etfR9wvpcSWLVswa9YsTJgwAddffz0+/PDDiGOcTidWrlyJKVOmYMqUKVi5ciWcTmfEMe+//z6uu+46TJgwARdffDG2bt0KKWXKXx/19fTTT+Pqq6/G5MmTMX36dNx+++344IMPIo7hdc8uP/vZz3DllVdi8uTJmDx5MhYtWoQ//vGPoft5vbPbj3/8YxQXF2P9+vWh23jNiSiT8PNqbuFn1dzDz6q5jZ9VMwNDU8pJXV1dmD17Np544gnYbLY+9z/zzDN49tlnsXXrVhw6dAgOhwO33HILOjs7Q8fce++9OH78OPbu3Yt9+/bh+PHjuO+++0L3d3R04JZbbkFpaSkOHTqEJ554Aj/5yU/w05/+dEReI0V6/fXX8d3vfhd//OMfsX//fphMJtx8881oa2sLHcPrnl0mTpyIH/7wh/jTn/6Ew4cP42tf+xruvPNO/N///R8AXu9sduzYMfzyl7/EJZdcEnE7rzkRZRJ+Xs0t/Kyae/hZNXfxs2rmEE6nk3Ez5bRJkybhySefxJ133gnA+O3OrFmz8A//8A9Yt24dAMDtdmPmzJn4p3/6J9xzzz34+OOPUVVVhVdeeQULFiwAABw5cgTV1dU4duwYZs6ciV/84hfYtGkTPvnkk9AH3W3btmHXrl344IMPIIQYnRdMAACXy4UpU6bg17/+Naqrq3ndc8TUqVPx2GOP4e677+b1zlLt7e34+te/jmeeeQZPPvkkZs+ejW3btvF7nIgyGj+v5h5+Vs1N/Kya/fhZNbOw0pQoSkNDA5qbm3HNNdeEbrPZbLjyyitx9OhRAEB9fT3sdjuqqqpCxyxYsAAFBQURx1xxxRURlQHXXnstmpqa0NDQMEKvhvrjcrmg6zqKi4sB8LpnO03T8NJLL6Grqwvz58/n9c5iDz74IG666SZ8/etfj7id15yIsgl/pmU/flbNLfysmjv4WTWzMDQlitLc3AwAcDgcEbc7HA6cPXsWAHD27FmUlJRE/JZGCIHx48dHHBPrHMH7aHRt3LgRc+bMwfz58wHwumer999/H5MmTUJpaSnWrl2LX/3qV7jkkkt4vbPUL3/5S3z++ed49NFH+9zHa05E2YQ/07IfP6vmBn5WzS38rJp5TKO9AKJ0FV22LqXs88Mp2kDHBJsvsyR+dP3gBz/AW2+9hVdeeQWqqkbcx+ueXWbOnIm6ujq0t7dj//79WLVqFf7whz+E7uf1zh4nT57E448/jtraWlgsln6P4zUnomzCn2nZiZ9Vcwc/q+YOflbNTKw0JYpSVlYGoO9vYc6dOxf6DU1paSnOnTsXMYFOSonz589HHBPrHEDf3x7RyHnkkUfw0ksvYf/+/Zg6dWrodl737GSxWDBt2jR85StfwWOPPYY5c+bgueee4/XOQvX19Th//jyuuOIKlJSUoKSkBG+88QZ+/vOfo6SkBOPGjQPAa05E2YF/j2UvflbNLfysmjv4WTUzMTQlilJZWYmysjIcPnw4dJvH48GRI0dCvUPmz58Pl8uF+vr60DH19fXo6uqKOObIkSPweDyhYw4fPozy8nJUVlaO0KuhcBs2bMC+ffuwf/9+XHjhhRH38brnBl3X4fP5eL2z0PXXX48333wTdXV1oT9f+cpXsGTJEtTV1WHGjBm85kSUNfj3WHbiZ1XiZ9Xsxc+qmUnduHHjptFeBNFIc7lc+Oijj9Dc3Izdu3dj9uzZKCwshM/nQ1FRETRNw/bt2zFjxgxomoZHH30Uzc3N2LFjB6xWK8aPH4+3334b+/btw6WXXopTp05h7dq1+OpXv4r77rsPADB9+nT827/9G06cOIGZM2fiyJEj+Md//Ec8+OCDEY2baWSsW7cOe/bswfPPP4+Kigp0dXWhq6sLgPEbXiEEr3uW2bRpEywWC3Rdx6lTp1BTU4MXX3wRmzZtwvTp03m9s0xeXh4cDkfEn71792LKlCm48847+T1ORBmHn1dzCz+r5h5+Vs0t/KyamYTT6ZQDH0aUXerq6rB48eI+t99xxx2oqamBlBJPPPEEnn/+eTidTlx22WV46qmnMHv27NCxbW1t2LBhA2prawEA1dXVePLJJ0MTLgGjsfe6devwv//7vyguLsY999yDDRs2sJfIKAi/LuE2bNiARx55BAB43bPMqlWrUFdXh7Nnz6KwsBCXXHIJ1qxZg2uvvRYAr3cuuP766zF79mxs27YNAK85EWUWfl7NLfysmnv4WZX4WTX9MTQlIiIiIiIiIiIiCsOepkRERERERERERERhGJoSERERERERERERhWFoSkRERERERERERBSGoSkRERERERERERFRGIamRERERERERERERGEYmhIRERERERERERGFYWhKRJQFiouLsWXLltFeBhERERFRTPy8SkSZhqEpEVEKtLW14Uc/+hEWLlyIyZMno7S0FF/60pdw11134cCBA5BSJnSeuro6FBcX46WXXkrxioHXX38dxcXFqKioQHd3d8qfj4iIiIhGDz+vEhHFZxrtBRARZZv33nsPt912G9ra2nDzzTdjxYoVsNlsOHXqFA4ePIgVK1bgqaeewr333pu05zxz5gxMpuH9SH/xxRcxefJkNDY24j//8z+xdOnSJK2OiIiIiNIJP68SEQ2MoSkRURK1t7fjW9/6FqSU+O///m/Mnj074v6NGzfitddeQ3t7e9zzdHd3Iz8/P+HnzcvLG9J6g7xeL15++WWsWbMG//Vf/4UXX3wx4Q+hbrcbNpttWM9PRERERCODn1eJiBLD7flEREn0/PPP49SpU/jRj37U5wNo0Ne+9jUsXrw49N+//vWvUVxcjNdeew0bN27EhRdeiIkTJw7qecN7RL3zzjsoLi7Gv//7v/c5rr/7XnnlFbS3t2PJkiVYunQpDh06hHPnzvV5/Jw5c7BkyRK89tpr+MY3voGysjLs2LEjdP/hw4dxww03oKKiAhMnTsQNN9yAo0ePRpzjr3/9Kx5++GHMmzcP5eXlmDJlCm6//XZ8+OGHg3rNRERERDR4/LzKz6tElBiGpkRESVRbWwubzYabbrpp0I/dsGED3n33XTz00EP4wQ9+MOQ1fOUrX8G0adPwu9/9rs99L730EsxmM2688caI21944QVcdtllmDp1Km6++WYIIfrtS/X555/j29/+Nq688kps3boV8+bNAwDs27cPS5YsgaqqePTRR/Hoo4+itbUVN954I95+++3Q49955x288cYbWLx4MbZs2YJVq1bhnXfewXXXXYfm5uYhv24iIiIiGhg/r/LzKhElhtvziYiS6KOPPsL06dNhsVgibu/q6oLH4wn9t8lkQlFRUcQx+fn5+MMf/jDsXk8AcOutt2L79u1oaWmBw+EAAEgp8R//8R+45pprUFxcHDq2ra0Nr776Kh577DEAwLhx43D11VfjxRdfxH333dfn3H/+85/xm9/8Btddd13E61u3bh1uv/121NTUhG6/5557sGDBAjz++OPYv38/AGDRokV9PqTffvvtuOKKK7B7926sW7du2K+fiIiIiGLj51V+XiWixLDSlIgoiTo7OzFmzJg+t2/atAnTp08P/fnWt77V55i77rorKR9AAWDp0qXQNA0vv/xy6LajR4+isbERS5YsiTj297//PQKBAG655ZaIx//P//wPPvvssz7nnjRpUsQHUMDY5uR0OnHbbbfh/PnzoT9utxt/+7d/iyNHjsDv9wNARO+r7u5utLa2oqioCNOnT8e7776blNdPRERERLHx8yo/rxJRYlhpSkSURGPGjEFnZ2ef21euXInrr78eAPDAAw/EfOzUqVOTto5Zs2Zh9uzZeOmll0JTT1966SXYbLY+HyBfeOEFzJkzB36/Hw0NDQCAL33pSzCbzXjhhRf6bL2qrKzs83zBD6vhH2Sjtbe3Y/z48fB4PPjnf/5nvPjiizhz5kzEMSUlJYN/sURERESUMH5e5edVIkoMQ1MioiSaNWsW3n33Xfh8vogtTzNnzsTMmTMBoN/Jncme6LlkyRJs3rwZp06dQnl5Ofbv34+/+7u/g91uDx3zl7/8JdT4fu7cuX3OsXfv3j4fQv9/e/cP0kgQh2H4O0PAKJuAiEFsFGwUhIBLsBAVLDRikUT8U4kgWFnZSUglaAoRbGJjJQq6xF0LRQJ2gohgJShCsBMVLFIIIoJecSAb4mmU3B0H7wOBMDM7O5vq45dh9r11vry8SJLS6fRvXwrg9/sl/Xoj69ramqamptTR0SG/36+KigrNzs6+zQMAAIA/g7xKXgVQGoqmAFBGkUhEx8fH2tnZ0cjIyD9dy9DQkObm5uQ4jtra2nR3d6d4PF4wxrIseTwera6uyuv1FvSdn59rfn5eJycnCofDH96rqalJklRbW6uenp4Px9q2rbGxMaVSqYL2fD6vmpqaEp8OAAAA30FeJa8CKA1nmgJAGU1MTKihoUGJREIXFxfvjnl9ff0ra2lsbFR7e7scx5Ft2zIMQ319fQVjLMtSOBxWLBbT4OBgwWd6elo+n0+WZX16r97eXgUCAS0uLurp6amo//7+/u27x+Mp+g0ymYxubm6++aQAAAAoFXmVvAqgNOw0BYAyCgQC2tjY0OjoqLq7uxWNRmWapnw+n25vb5XNZpXL5WSa5pfm3d3d1dXVVVF7LBZTc3Pzb6+Lx+NKJBK6vLzUwMCAKisr3/pOT0+Vy+U0Pj7+7rVVVVXq6uqSbdtaWFgo+mffzTAMLS8va3JyUp2dnRoeHlYwGNT19bUODw9VXV2tTCYj6dfuhs3NTRmGodbWVp2dncm27bKekQUAAID3kVfJqwBKQ9EUAMosFArp6OhIKysr2t/f197enp6fn1VXVyfTNDUzM6NIJPKlOR3HkeM4Re0tLS2fhtBkMqmHh4eit5BubW1J0odr6e/vVzab1cHBwadrjkajqq+v19LSktLptB4fHxUMBmWaZkHQTaVS8nq9chxH6+vrCoVC2t7eVjKZ/HB+AAAAlAd5lbwK4HM/8vn839l3DwAAAAAAAAD/Ac40BQAAAAAAAAAXiqYAAAAAAAAA4ELRFAAAAAAAAABcKJoCAAAAAAAAgAtFUwAAAAAAAABwoWgKAAAAAAAAAC4UTQEAAAAAAADAhaIpAAAAAAAAALhQNAUAAAAAAAAAF4qmAAAAAAAAAODyEzsKQzDxdtlXAAAAAElFTkSuQmCC
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Here, we can see that the pre-transformed chart on the left has heteroscedasticity, and the post-transformed chart on the right has almost an equal amount of variance across the zero lines.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[26]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Plot fig sizing. </span>
<span class="n">style</span><span class="o">.</span><span class="n">use</span><span class="p">(</span><span class="s1">&#39;ggplot&#39;</span><span class="p">)</span>
<span class="n">sns</span><span class="o">.</span><span class="n">set_style</span><span class="p">(</span><span class="s1">&#39;whitegrid&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">subplots</span><span class="p">(</span><span class="n">figsize</span> <span class="o">=</span> <span class="p">(</span><span class="mi">30</span><span class="p">,</span><span class="mi">20</span><span class="p">))</span>
<span class="c1">## Plotting heatmap. </span>

<span class="c1"># Generate a mask for the upper triangle (taken from seaborn example gallery)</span>
<span class="n">mask</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros_like</span><span class="p">(</span><span class="n">train</span><span class="o">.</span><span class="n">corr</span><span class="p">(),</span> <span class="n">dtype</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">bool</span><span class="p">)</span>
<span class="n">mask</span><span class="p">[</span><span class="n">np</span><span class="o">.</span><span class="n">triu_indices_from</span><span class="p">(</span><span class="n">mask</span><span class="p">)]</span> <span class="o">=</span> <span class="kc">True</span>


<span class="n">sns</span><span class="o">.</span><span class="n">heatmap</span><span class="p">(</span><span class="n">train</span><span class="o">.</span><span class="n">corr</span><span class="p">(),</span> <span class="n">cmap</span><span class="o">=</span><span class="n">sns</span><span class="o">.</span><span class="n">diverging_palette</span><span class="p">(</span><span class="mi">20</span><span class="p">,</span> <span class="mi">220</span><span class="p">,</span> <span class="n">n</span><span class="o">=</span><span class="mi">200</span><span class="p">),</span> <span class="n">mask</span> <span class="o">=</span> <span class="n">mask</span><span class="p">,</span> <span class="n">annot</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">center</span> <span class="o">=</span> <span class="mi">0</span><span class="p">,</span> <span class="p">);</span>
<span class="c1">## Give title. </span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s2">&quot;Heatmap of all the Features&quot;</span><span class="p">,</span> <span class="n">fontsize</span> <span class="o">=</span> <span class="mi">30</span><span class="p">);</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[27]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Dropping the &quot;Id&quot; from train and test set. </span>
<span class="c1"># train.drop(columns=[&#39;Id&#39;],axis=1, inplace=True)</span>

<span class="n">train</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Id&#39;</span><span class="p">],</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">test</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Id&#39;</span><span class="p">],</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="c1">## Saving the target values in &quot;y_train&quot;. </span>
<span class="n">y</span> <span class="o">=</span> <span class="n">train</span><span class="p">[</span><span class="s1">&#39;SalePrice&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>



<span class="c1"># getting a copy of train</span>
<span class="n">previous_train</span> <span class="o">=</span> <span class="n">train</span><span class="o">.</span><span class="n">copy</span><span class="p">()</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[29]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Combining train and test datasets together so that we can do all the work at once. </span>
<span class="n">all_data</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">((</span><span class="n">train</span><span class="p">,</span> <span class="n">test</span><span class="p">))</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span> <span class="o">=</span> <span class="kc">True</span><span class="p">)</span>
<span class="c1">## Dropping the target variable. </span>
<span class="n">all_data</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;SalePrice&#39;</span><span class="p">],</span> <span class="n">axis</span> <span class="o">=</span> <span class="mi">1</span><span class="p">,</span> <span class="n">inplace</span> <span class="o">=</span> <span class="kc">True</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Dealing-with-Missing-Values">Dealing with Missing Values<a class="anchor-link" href="#Dealing-with-Missing-Values">&#182;</a></h2><blockquote><p><strong>Missing data in train and test data(all_data)</strong></p>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<blockquote><p><strong>Imputing Missing Values</strong></p>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[31]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Some missing values are intentionally left blank, for example: In the Alley feature </span>
<span class="c1">## there are blank values meaning that there are no alley&#39;s in that specific house. </span>
<span class="n">missing_val_col</span> <span class="o">=</span> <span class="p">[</span><span class="s2">&quot;Alley&quot;</span><span class="p">,</span> 
                   <span class="s2">&quot;PoolQC&quot;</span><span class="p">,</span> 
                   <span class="s2">&quot;MiscFeature&quot;</span><span class="p">,</span>
                   <span class="s2">&quot;Fence&quot;</span><span class="p">,</span>
                   <span class="s2">&quot;FireplaceQu&quot;</span><span class="p">,</span>
                   <span class="s2">&quot;GarageType&quot;</span><span class="p">,</span>
                   <span class="s2">&quot;GarageFinish&quot;</span><span class="p">,</span>
                   <span class="s2">&quot;GarageQual&quot;</span><span class="p">,</span>
                   <span class="s2">&quot;GarageCond&quot;</span><span class="p">,</span>
                   <span class="s1">&#39;BsmtQual&#39;</span><span class="p">,</span>
                   <span class="s1">&#39;BsmtCond&#39;</span><span class="p">,</span>
                   <span class="s1">&#39;BsmtExposure&#39;</span><span class="p">,</span>
                   <span class="s1">&#39;BsmtFinType1&#39;</span><span class="p">,</span>
                   <span class="s1">&#39;BsmtFinType2&#39;</span><span class="p">,</span>
                   <span class="s1">&#39;MasVnrType&#39;</span><span class="p">]</span>

<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="n">missing_val_col</span><span class="p">:</span>
    <span class="n">all_data</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="n">i</span><span class="p">]</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="s1">&#39;None&#39;</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[32]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## These features are continous variable, we used &quot;0&quot; to replace the null values. </span>
<span class="n">missing_val_col2</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;BsmtFinSF1&#39;</span><span class="p">,</span>
                    <span class="s1">&#39;BsmtFinSF2&#39;</span><span class="p">,</span>
                    <span class="s1">&#39;BsmtUnfSF&#39;</span><span class="p">,</span>
                    <span class="s1">&#39;TotalBsmtSF&#39;</span><span class="p">,</span>
                    <span class="s1">&#39;BsmtFullBath&#39;</span><span class="p">,</span> 
                    <span class="s1">&#39;BsmtHalfBath&#39;</span><span class="p">,</span> 
                    <span class="s1">&#39;GarageYrBlt&#39;</span><span class="p">,</span>
                    <span class="s1">&#39;GarageArea&#39;</span><span class="p">,</span>
                    <span class="s1">&#39;GarageCars&#39;</span><span class="p">,</span>
                    <span class="s1">&#39;MasVnrArea&#39;</span><span class="p">]</span>

<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="n">missing_val_col2</span><span class="p">:</span>
    <span class="n">all_data</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="n">i</span><span class="p">]</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="mi">0</span><span class="p">)</span>
    
<span class="c1">## Replaced all missing values in LotFrontage by imputing the median value of each neighborhood. </span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;LotFrontage&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s1">&#39;Neighborhood&#39;</span><span class="p">)[</span><span class="s1">&#39;LotFrontage&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">transform</span><span class="p">(</span> <span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">x</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">mean</span><span class="p">()))</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[33]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## the &quot;OverallCond&quot; and &quot;OverallQual&quot; of the house. </span>
<span class="c1"># all_data[&#39;OverallCond&#39;] = all_data[&#39;OverallCond&#39;].astype(str) </span>
<span class="c1"># all_data[&#39;OverallQual&#39;] = all_data[&#39;OverallQual&#39;].astype(str)</span>

<span class="c1">## Zoning class are given in numerical; therefore converted to categorical variables. </span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;MSSubClass&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;MSSubClass&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">str</span><span class="p">)</span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;MSZoning&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s1">&#39;MSSubClass&#39;</span><span class="p">)[</span><span class="s1">&#39;MSZoning&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">transform</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">x</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">mode</span><span class="p">()[</span><span class="mi">0</span><span class="p">]))</span>

<span class="c1">## Important years and months that should be categorical variables not numerical. </span>
<span class="c1"># all_data[&#39;YearBuilt&#39;] = all_data[&#39;YearBuilt&#39;].astype(str)</span>
<span class="c1"># all_data[&#39;YearRemodAdd&#39;] = all_data[&#39;YearRemodAdd&#39;].astype(str)</span>
<span class="c1"># all_data[&#39;GarageYrBlt&#39;] = all_data[&#39;GarageYrBlt&#39;].astype(str)</span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;YrSold&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;YrSold&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">str</span><span class="p">)</span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;MoSold&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;MoSold&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">str</span><span class="p">)</span> 
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[34]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Functional&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Functional&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="s1">&#39;Typ&#39;</span><span class="p">)</span> 
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Utilities&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Utilities&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="s1">&#39;AllPub&#39;</span><span class="p">)</span> 
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Exterior1st&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Exterior1st&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Exterior1st&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">mode</span><span class="p">()[</span><span class="mi">0</span><span class="p">])</span> 
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Exterior2nd&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Exterior2nd&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Exterior2nd&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">mode</span><span class="p">()[</span><span class="mi">0</span><span class="p">])</span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;KitchenQual&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;KitchenQual&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="s2">&quot;TA&quot;</span><span class="p">)</span> 
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;SaleType&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;SaleType&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;SaleType&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">mode</span><span class="p">()[</span><span class="mi">0</span><span class="p">])</span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Electrical&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Electrical&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="s2">&quot;SBrkr&quot;</span><span class="p">)</span> 
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[35]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">missing_percentage</span><span class="p">(</span><span class="n">all_data</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[35]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total</th>
      <th>Percent</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>So, there are no missing value left.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[36]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;1stFlrSF&#39;</span><span class="p">]);</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[37]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">numeric_feats</span> <span class="o">=</span> <span class="n">all_data</span><span class="o">.</span><span class="n">dtypes</span><span class="p">[</span><span class="n">all_data</span><span class="o">.</span><span class="n">dtypes</span> <span class="o">!=</span> <span class="s2">&quot;object&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">index</span>

<span class="n">skewed_feats</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="n">numeric_feats</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">skew</span><span class="p">(</span><span class="n">x</span><span class="p">))</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>

<span class="n">skewed_feats</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[37]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>MiscVal          21.939672
PoolArea         17.688664
LotArea          13.109495
LowQualFinSF     12.084539
3SsnPorch        11.372080
KitchenAbvGr      4.300550
BsmtFinSF2        4.144503
EnclosedPorch     4.002344
ScreenPorch       3.945101
BsmtHalfBath      3.929996
MasVnrArea        2.621719
OpenPorchSF       2.529358
WoodDeckSF        1.844792
1stFlrSF          1.257286
GrLivArea         1.068750
LotFrontage       1.058803
BsmtFinSF1        0.980645
BsmtUnfSF         0.919688
2ndFlrSF          0.861556
TotRmsAbvGrd      0.749232
Fireplaces        0.725278
HalfBath          0.696666
TotalBsmtSF       0.671751
BsmtFullBath      0.622415
OverallCond       0.569314
BedroomAbvGr      0.326568
GarageArea        0.216857
OverallQual       0.189591
FullBath          0.165514
GarageCars       -0.219297
YearRemodAdd     -0.450134
YearBuilt        -0.599194
GarageYrBlt      -3.904632
dtype: float64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[38]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Fixing Skewed features using boxcox transformation. </span>


<span class="k">def</span> <span class="nf">fixing_skewness</span><span class="p">(</span><span class="n">df</span><span class="p">):</span>
    <span class="sd">&quot;&quot;&quot;</span>
<span class="sd">    This function takes in a dataframe and return fixed skewed dataframe</span>
<span class="sd">    &quot;&quot;&quot;</span>
    <span class="c1">## Import necessary modules </span>
    <span class="kn">from</span> <span class="nn">scipy.stats</span> <span class="k">import</span> <span class="n">skew</span>
    <span class="kn">from</span> <span class="nn">scipy.special</span> <span class="k">import</span> <span class="n">boxcox1p</span>
    <span class="kn">from</span> <span class="nn">scipy.stats</span> <span class="k">import</span> <span class="n">boxcox_normmax</span>
    
    <span class="c1">## Getting all the data that are not of &quot;object&quot; type. </span>
    <span class="n">numeric_feats</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">dtypes</span><span class="p">[</span><span class="n">df</span><span class="o">.</span><span class="n">dtypes</span> <span class="o">!=</span> <span class="s2">&quot;object&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">index</span>

    <span class="c1"># Check the skew of all numerical features</span>
    <span class="n">skewed_feats</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="n">numeric_feats</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">skew</span><span class="p">(</span><span class="n">x</span><span class="p">))</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
    <span class="n">high_skew</span> <span class="o">=</span> <span class="n">skewed_feats</span><span class="p">[</span><span class="nb">abs</span><span class="p">(</span><span class="n">skewed_feats</span><span class="p">)</span> <span class="o">&gt;</span> <span class="mf">0.5</span><span class="p">]</span>
    <span class="n">skewed_features</span> <span class="o">=</span> <span class="n">high_skew</span><span class="o">.</span><span class="n">index</span>

    <span class="k">for</span> <span class="n">feat</span> <span class="ow">in</span> <span class="n">skewed_features</span><span class="p">:</span>
        <span class="n">df</span><span class="p">[</span><span class="n">feat</span><span class="p">]</span> <span class="o">=</span> <span class="n">boxcox1p</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="n">feat</span><span class="p">],</span> <span class="n">boxcox_normmax</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="n">feat</span><span class="p">]</span> <span class="o">+</span> <span class="mi">1</span><span class="p">))</span>

<span class="n">fixing_skewness</span><span class="p">(</span><span class="n">all_data</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[39]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;1stFlrSF&#39;</span><span class="p">]);</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[40]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">all_data</span> <span class="o">=</span> <span class="n">all_data</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;Utilities&#39;</span><span class="p">,</span> <span class="s1">&#39;Street&#39;</span><span class="p">,</span> <span class="s1">&#39;PoolQC&#39;</span><span class="p">,],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>

<span class="c1"># feture engineering a new feature &quot;TotalFS&quot;</span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;TotalSF&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;TotalBsmtSF&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;1stFlrSF&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;2ndFlrSF&#39;</span><span class="p">]</span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;YrBltAndRemod&#39;</span><span class="p">]</span><span class="o">=</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;YearBuilt&#39;</span><span class="p">]</span><span class="o">+</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;YearRemodAdd&#39;</span><span class="p">]</span>

<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Total_sqr_footage&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="p">(</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;BsmtFinSF1&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;BsmtFinSF2&#39;</span><span class="p">]</span> <span class="o">+</span>
                                 <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;1stFlrSF&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;2ndFlrSF&#39;</span><span class="p">])</span>

<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Total_Bathrooms&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="p">(</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;FullBath&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="p">(</span><span class="mf">0.5</span> <span class="o">*</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;HalfBath&#39;</span><span class="p">])</span> <span class="o">+</span>
                               <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;BsmtFullBath&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="p">(</span><span class="mf">0.5</span> <span class="o">*</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;BsmtHalfBath&#39;</span><span class="p">]))</span>

<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Total_porch_sf&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="p">(</span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;OpenPorchSF&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;3SsnPorch&#39;</span><span class="p">]</span> <span class="o">+</span>
                              <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;EnclosedPorch&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;ScreenPorch&#39;</span><span class="p">]</span> <span class="o">+</span>
                              <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;WoodDeckSF&#39;</span><span class="p">])</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[41]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;haspool&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;PoolArea&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="mi">1</span> <span class="k">if</span> <span class="n">x</span> <span class="o">&gt;</span> <span class="mi">0</span> <span class="k">else</span> <span class="mi">0</span><span class="p">)</span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;has2ndfloor&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;2ndFlrSF&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="mi">1</span> <span class="k">if</span> <span class="n">x</span> <span class="o">&gt;</span> <span class="mi">0</span> <span class="k">else</span> <span class="mi">0</span><span class="p">)</span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;hasgarage&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;GarageArea&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="mi">1</span> <span class="k">if</span> <span class="n">x</span> <span class="o">&gt;</span> <span class="mi">0</span> <span class="k">else</span> <span class="mi">0</span><span class="p">)</span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;hasbsmt&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;TotalBsmtSF&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="mi">1</span> <span class="k">if</span> <span class="n">x</span> <span class="o">&gt;</span> <span class="mi">0</span> <span class="k">else</span> <span class="mi">0</span><span class="p">)</span>
<span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;hasfireplace&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">all_data</span><span class="p">[</span><span class="s1">&#39;Fireplaces&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="mi">1</span> <span class="k">if</span> <span class="n">x</span> <span class="o">&gt;</span> <span class="mi">0</span> <span class="k">else</span> <span class="mi">0</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[42]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">all_data</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[42]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(2917, 86)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Creating-Dummy-Variables.">Creating Dummy Variables.<a class="anchor-link" href="#Creating-Dummy-Variables.">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[43]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Creating dummy variable </span>
<span class="n">final_features</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">get_dummies</span><span class="p">(</span><span class="n">all_data</span><span class="p">)</span><span class="o">.</span><span class="n">reset_index</span><span class="p">(</span><span class="n">drop</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">final_features</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[43]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(2917, 333)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[44]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">X</span> <span class="o">=</span> <span class="n">final_features</span><span class="o">.</span><span class="n">iloc</span><span class="p">[:</span><span class="nb">len</span><span class="p">(</span><span class="n">y</span><span class="p">),</span> <span class="p">:]</span>

<span class="n">X_sub</span> <span class="o">=</span> <span class="n">final_features</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="nb">len</span><span class="p">(</span><span class="n">y</span><span class="p">):,</span> <span class="p">:]</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[45]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">outliers</span> <span class="o">=</span> <span class="p">[</span><span class="mi">30</span><span class="p">,</span> <span class="mi">88</span><span class="p">,</span> <span class="mi">462</span><span class="p">,</span> <span class="mi">631</span><span class="p">,</span> <span class="mi">1322</span><span class="p">]</span>
<span class="n">X</span> <span class="o">=</span> <span class="n">X</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="n">X</span><span class="o">.</span><span class="n">index</span><span class="p">[</span><span class="n">outliers</span><span class="p">])</span>
<span class="n">y</span> <span class="o">=</span> <span class="n">y</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="n">y</span><span class="o">.</span><span class="n">index</span><span class="p">[</span><span class="n">outliers</span><span class="p">])</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[46]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">overfit_reducer</span><span class="p">(</span><span class="n">df</span><span class="p">):</span>
    <span class="sd">&quot;&quot;&quot;</span>
<span class="sd">    This function takes in a dataframe and returns a list of features that are overfitted.</span>
<span class="sd">    &quot;&quot;&quot;</span>
    <span class="n">overfit</span> <span class="o">=</span> <span class="p">[]</span>
    <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="n">df</span><span class="o">.</span><span class="n">columns</span><span class="p">:</span>
        <span class="n">counts</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="n">i</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span>
        <span class="n">zeros</span> <span class="o">=</span> <span class="n">counts</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span>
        <span class="k">if</span> <span class="n">zeros</span> <span class="o">/</span> <span class="nb">len</span><span class="p">(</span><span class="n">df</span><span class="p">)</span> <span class="o">*</span> <span class="mi">100</span> <span class="o">&gt;</span> <span class="mf">99.94</span><span class="p">:</span>
            <span class="n">overfit</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">i</span><span class="p">)</span>
    <span class="n">overfit</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">overfit</span><span class="p">)</span>
    <span class="k">return</span> <span class="n">overfit</span>


<span class="n">overfitted_features</span> <span class="o">=</span> <span class="n">overfit_reducer</span><span class="p">(</span><span class="n">X</span><span class="p">)</span>

<span class="n">X</span> <span class="o">=</span> <span class="n">X</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="n">overfitted_features</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="n">X_sub</span> <span class="o">=</span> <span class="n">X_sub</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="n">overfitted_features</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[47]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">X</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span><span class="n">y</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">X_sub</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[47]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>((1453, 332), (1453,), (1459, 332))</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Fitting-model(simple-approach)">Fitting model(simple approach)<a class="anchor-link" href="#Fitting-model(simple-approach)">&#182;</a></h1><h2 id="Train_test-split">Train_test split<a class="anchor-link" href="#Train_test-split">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[48]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Train test s</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">train_test_split</span>
<span class="c1">## Train test split follows this distinguished code pattern and helps creating train and test set to build machine learning. </span>
<span class="n">X_train</span><span class="p">,</span> <span class="n">X_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="p">,</span><span class="n">test_size</span> <span class="o">=</span> <span class="o">.</span><span class="mi">33</span><span class="p">,</span> <span class="n">random_state</span> <span class="o">=</span> <span class="mi">0</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[84]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">X_train</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">y_train</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">X_test</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">y_test</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[84]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>((973, 332), (973,), (480, 332), (480,))</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Regularization-Models">Regularization Models<a class="anchor-link" href="#Regularization-Models">&#182;</a></h3><p>What makes regression model more effective is its ability of <em>regularizing</em>. The term "regularizing" stands for models ability <strong>to structurally prevent overfitting by imposing a penalty on the coefficients.</strong></p>
<p>There are three types of regularizations.</p>
<ul>
<li><strong>Ridge</strong></li>
<li><strong>Lasso</strong></li>
<li><strong>Elastic Net</strong></li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[63]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Importing Ridge. </span>
<span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="k">import</span> <span class="n">Ridge</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">mean_absolute_error</span><span class="p">,</span> <span class="n">mean_squared_error</span>
<span class="c1">## Assiging different sets of alpha values to explore which can be the best fit for the model. </span>
<span class="n">alpha_ridge</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mi">3</span><span class="p">,</span><span class="o">-</span><span class="mi">2</span><span class="p">,</span><span class="o">-</span><span class="mi">1</span><span class="p">,</span><span class="mf">1e-15</span><span class="p">,</span> <span class="mf">1e-10</span><span class="p">,</span> <span class="mf">1e-8</span><span class="p">,</span><span class="mf">1e-5</span><span class="p">,</span><span class="mf">1e-4</span><span class="p">,</span> <span class="mf">1e-3</span><span class="p">,</span><span class="mf">1e-2</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span><span class="mi">3</span><span class="p">,</span><span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">20</span><span class="p">,</span> <span class="mi">30</span><span class="p">,</span> <span class="mi">40</span><span class="p">]</span>
<span class="n">temp_rss</span> <span class="o">=</span> <span class="p">{}</span>
<span class="n">temp_mse</span> <span class="o">=</span> <span class="p">{}</span>
<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="n">alpha_ridge</span><span class="p">:</span>
    <span class="c1">## Assigin each model. </span>
    <span class="n">ridge</span> <span class="o">=</span> <span class="n">Ridge</span><span class="p">(</span><span class="n">alpha</span><span class="o">=</span> <span class="n">i</span><span class="p">,</span> <span class="n">normalize</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    <span class="c1">## fit the model. </span>
    <span class="n">ridge</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
    <span class="c1">## Predicting the target value based on &quot;Test_x&quot;</span>
    <span class="n">y_pred</span> <span class="o">=</span> <span class="n">ridge</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>

    <span class="n">mse</span> <span class="o">=</span> <span class="n">mean_squared_error</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span> <span class="n">y_pred</span><span class="p">)</span>
    <span class="n">rss</span> <span class="o">=</span> <span class="nb">sum</span><span class="p">((</span><span class="n">y_pred</span><span class="o">-</span><span class="n">y_test</span><span class="p">)</span><span class="o">**</span><span class="mi">2</span><span class="p">)</span>
    <span class="n">temp_mse</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">=</span> <span class="n">mse</span>
    <span class="n">temp_rss</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">=</span> <span class="n">rss</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[64]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">for</span> <span class="n">key</span><span class="p">,</span> <span class="n">value</span> <span class="ow">in</span> <span class="nb">sorted</span><span class="p">(</span><span class="n">temp_mse</span><span class="o">.</span><span class="n">items</span><span class="p">(),</span> <span class="n">key</span><span class="o">=</span><span class="k">lambda</span> <span class="n">item</span><span class="p">:</span> <span class="n">item</span><span class="p">[</span><span class="mi">1</span><span class="p">]):</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;</span><span class="si">%s</span><span class="s2">: </span><span class="si">%s</span><span class="s2">&quot;</span> <span class="o">%</span> <span class="p">(</span><span class="n">key</span><span class="p">,</span> <span class="n">value</span><span class="p">))</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>0.01: 0.012058094362558029
0.001: 0.012361806597259932
0.5: 0.012398339976451882
0.0001: 0.01245484128284161
1e-05: 0.012608710731947215
1e-15: 0.0126876442980313
1e-08: 0.012689390127616456
1e-10: 0.012689491191917741
1: 0.013828461568989092
1.5: 0.015292912807173023
2: 0.016759826630923253
3: 0.019679216533917247
4: 0.02256515576039871
5: 0.02540603527247574
10: 0.03869750099582716
20: 0.06016951688745736
30: 0.07597213357728104
40: 0.08783870545120151
-1: 22.58422122267688
-3: 37.77842304072701
-2: 1127.9896486631667
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[65]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">for</span> <span class="n">key</span><span class="p">,</span> <span class="n">value</span> <span class="ow">in</span> <span class="nb">sorted</span><span class="p">(</span><span class="n">temp_rss</span><span class="o">.</span><span class="n">items</span><span class="p">(),</span> <span class="n">key</span><span class="o">=</span><span class="k">lambda</span> <span class="n">item</span><span class="p">:</span> <span class="n">item</span><span class="p">[</span><span class="mi">1</span><span class="p">]):</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;</span><span class="si">%s</span><span class="s2">: </span><span class="si">%s</span><span class="s2">&quot;</span> <span class="o">%</span> <span class="p">(</span><span class="n">key</span><span class="p">,</span> <span class="n">value</span><span class="p">))</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>0.01: 5.787885294027853
0.001: 5.9336671666847645
0.5: 5.951203188696909
0.0001: 5.978323815763974
1e-05: 6.052181151334658
1e-15: 6.090069263055022
1e-08: 6.090907261255897
1e-10: 6.09095577212052
1: 6.637661553114765
1.5: 7.34059814744305
2: 8.044716782843166
3: 9.446023936280277
4: 10.831274764991383
5: 12.194896930788355
10: 18.574800477997016
20: 28.881368105979536
30: 36.46662411709491
40: 42.16257861657673
-1: 10840.426186884908
-3: 18133.64305954895
-2: 541435.0313583203
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Lasso:">Lasso:<a class="anchor-link" href="#Lasso:">&#182;</a></h3><p>Lasso adds penalty equivalent to the absolute value of the sum of coefficients. This penalty is added to the least square loss function and replaces the squared sum of coefficients from Ridge.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[66]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="k">import</span> <span class="n">Lasso</span> 
<span class="n">temp_rss</span> <span class="o">=</span> <span class="p">{}</span>
<span class="n">temp_mse</span> <span class="o">=</span> <span class="p">{}</span>
<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="n">alpha_ridge</span><span class="p">:</span>
    <span class="c1">## Assigin each model. </span>
    <span class="n">lasso_reg</span> <span class="o">=</span> <span class="n">Lasso</span><span class="p">(</span><span class="n">alpha</span><span class="o">=</span> <span class="n">i</span><span class="p">,</span> <span class="n">normalize</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    <span class="c1">## fit the model. </span>
    <span class="n">lasso_reg</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
    <span class="c1">## Predicting the target value based on &quot;Test_x&quot;</span>
    <span class="n">y_pred</span> <span class="o">=</span> <span class="n">lasso_reg</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>

    <span class="n">mse</span> <span class="o">=</span> <span class="n">mean_squared_error</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span> <span class="n">y_pred</span><span class="p">)</span>
    <span class="n">rss</span> <span class="o">=</span> <span class="nb">sum</span><span class="p">((</span><span class="n">y_pred</span><span class="o">-</span><span class="n">y_test</span><span class="p">)</span><span class="o">**</span><span class="mi">2</span><span class="p">)</span>
    <span class="n">temp_mse</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">=</span> <span class="n">mse</span>
    <span class="n">temp_rss</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">=</span> <span class="n">rss</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[67]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">for</span> <span class="n">key</span><span class="p">,</span> <span class="n">value</span> <span class="ow">in</span> <span class="nb">sorted</span><span class="p">(</span><span class="n">temp_mse</span><span class="o">.</span><span class="n">items</span><span class="p">(),</span> <span class="n">key</span><span class="o">=</span><span class="k">lambda</span> <span class="n">item</span><span class="p">:</span> <span class="n">item</span><span class="p">[</span><span class="mi">1</span><span class="p">]):</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;</span><span class="si">%s</span><span class="s2">: </span><span class="si">%s</span><span class="s2">&quot;</span> <span class="o">%</span> <span class="p">(</span><span class="n">key</span><span class="p">,</span> <span class="n">value</span><span class="p">))</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>0.0001: 0.010061658258835855
1e-05: 0.011553103092552693
1e-08: 0.012464777509974378
1e-10: 0.012469892082710245
1e-15: 0.01246993993780167
0.001: 0.01834391027644981
0.01: 0.15998234085337285
0.5: 0.16529633945001213
1: 0.16529633945001213
1.5: 0.16529633945001213
2: 0.16529633945001213
3: 0.16529633945001213
4: 0.16529633945001213
5: 0.16529633945001213
10: 0.16529633945001213
20: 0.16529633945001213
30: 0.16529633945001213
40: 0.16529633945001213
-1: 14648689598.250006
-2: 58594759730.8125
-3: 131838210397.70003
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[68]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">for</span> <span class="n">key</span><span class="p">,</span> <span class="n">value</span> <span class="ow">in</span> <span class="nb">sorted</span><span class="p">(</span><span class="n">temp_rss</span><span class="o">.</span><span class="n">items</span><span class="p">(),</span> <span class="n">key</span><span class="o">=</span><span class="k">lambda</span> <span class="n">item</span><span class="p">:</span> <span class="n">item</span><span class="p">[</span><span class="mi">1</span><span class="p">]):</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;</span><span class="si">%s</span><span class="s2">: </span><span class="si">%s</span><span class="s2">&quot;</span> <span class="o">%</span> <span class="p">(</span><span class="n">key</span><span class="p">,</span> <span class="n">value</span><span class="p">))</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>0.0001: 4.82959596424121
1e-05: 5.545489484425293
1e-08: 5.9830932047877035
1e-10: 5.985548199700918
1e-15: 5.9855711701448
0.001: 8.805076932695897
0.01: 76.79152360961895
0.5: 79.34224293600582
1: 79.34224293600582
1.5: 79.34224293600582
2: 79.34224293600582
3: 79.34224293600582
4: 79.34224293600582
5: 79.34224293600582
10: 79.34224293600582
20: 79.34224293600582
30: 79.34224293600582
40: 79.34224293600582
-1: 7031371007160.002
-2: 28125484670789.992
-3: 63282340990896.01
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Elastic-Net:">Elastic Net:<a class="anchor-link" href="#Elastic-Net:">&#182;</a></h3><p>Elastic Net is the combination of both Ridge and Lasso. It adds both the sum of squared coefficients and the absolute sum of the coefficients with the ordinary least square function. Let's look at the function.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[69]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="k">import</span> <span class="n">ElasticNet</span>
<span class="n">temp_rss</span> <span class="o">=</span> <span class="p">{}</span>
<span class="n">temp_mse</span> <span class="o">=</span> <span class="p">{}</span>
<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="n">alpha_ridge</span><span class="p">:</span>
    <span class="c1">## Assigin each model. </span>
    <span class="n">lasso_reg</span> <span class="o">=</span> <span class="n">ElasticNet</span><span class="p">(</span><span class="n">alpha</span><span class="o">=</span> <span class="n">i</span><span class="p">,</span> <span class="n">normalize</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
    <span class="c1">## fit the model. </span>
    <span class="n">lasso_reg</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
    <span class="c1">## Predicting the target value based on &quot;Test_x&quot;</span>
    <span class="n">y_pred</span> <span class="o">=</span> <span class="n">lasso_reg</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>

    <span class="n">mse</span> <span class="o">=</span> <span class="n">mean_squared_error</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span> <span class="n">y_pred</span><span class="p">)</span>
    <span class="n">rss</span> <span class="o">=</span> <span class="nb">sum</span><span class="p">((</span><span class="n">y_pred</span><span class="o">-</span><span class="n">y_test</span><span class="p">)</span><span class="o">**</span><span class="mi">2</span><span class="p">)</span>
    <span class="n">temp_mse</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">=</span> <span class="n">mse</span>
    <span class="n">temp_rss</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">=</span> <span class="n">rss</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[70]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">for</span> <span class="n">key</span><span class="p">,</span> <span class="n">value</span> <span class="ow">in</span> <span class="nb">sorted</span><span class="p">(</span><span class="n">temp_mse</span><span class="o">.</span><span class="n">items</span><span class="p">(),</span> <span class="n">key</span><span class="o">=</span><span class="k">lambda</span> <span class="n">item</span><span class="p">:</span> <span class="n">item</span><span class="p">[</span><span class="mi">1</span><span class="p">]):</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;</span><span class="si">%s</span><span class="s2">: </span><span class="si">%s</span><span class="s2">&quot;</span> <span class="o">%</span> <span class="p">(</span><span class="n">key</span><span class="p">,</span> <span class="n">value</span><span class="p">))</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>0.0001: 0.010410247442255985
1e-05: 0.011786774263401294
1e-08: 0.012466548787037617
1e-10: 0.012469905615434403
1e-15: 0.012469939937937151
0.001: 0.014971538718578314
0.01: 0.10870291488354142
0.5: 0.16529633945001213
1: 0.16529633945001213
1.5: 0.16529633945001213
2: 0.16529633945001213
3: 0.16529633945001213
4: 0.16529633945001213
5: 0.16529633945001213
10: 0.16529633945001213
20: 0.16529633945001213
30: 0.16529633945001213
40: 0.16529633945001213
-3: 5.388825733568653
-2: 5.470945111059094
-1: 5.729175782943725
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[71]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">for</span> <span class="n">key</span><span class="p">,</span> <span class="n">value</span> <span class="ow">in</span> <span class="nb">sorted</span><span class="p">(</span><span class="n">temp_rss</span><span class="o">.</span><span class="n">items</span><span class="p">(),</span> <span class="n">key</span><span class="o">=</span><span class="k">lambda</span> <span class="n">item</span><span class="p">:</span> <span class="n">item</span><span class="p">[</span><span class="mi">1</span><span class="p">]):</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;</span><span class="si">%s</span><span class="s2">: </span><span class="si">%s</span><span class="s2">&quot;</span> <span class="o">%</span> <span class="p">(</span><span class="n">key</span><span class="p">,</span> <span class="n">value</span><span class="p">))</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>0.0001: 4.996918772282872
1e-05: 5.65765164643262
1e-08: 5.983943417778055
1e-10: 5.985554695408507
1e-15: 5.9855711702098295
0.001: 7.186338584917596
0.01: 52.17739914409985
0.5: 79.34224293600582
1: 79.34224293600582
1.5: 79.34224293600582
2: 79.34224293600582
3: 79.34224293600582
4: 79.34224293600582
5: 79.34224293600582
10: 79.34224293600582
20: 79.34224293600582
30: 79.34224293600582
40: 79.34224293600582
-3: 2586.6363521129515
-2: 2626.053653308364
-1: 2750.0043758129887
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Fitting-model-(Advanced-approach)">Fitting model (Advanced approach)<a class="anchor-link" href="#Fitting-model-(Advanced-approach)">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[72]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">kfolds</span> <span class="o">=</span> <span class="n">KFold</span><span class="p">(</span><span class="n">n_splits</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span> <span class="n">shuffle</span><span class="o">=</span><span class="kc">True</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">42</span><span class="p">)</span>

<span class="k">def</span> <span class="nf">rmsle</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">y_pred</span><span class="p">):</span>
    <span class="k">return</span> <span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="n">mean_squared_error</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">y_pred</span><span class="p">))</span>

<span class="k">def</span> <span class="nf">cv_rmse</span><span class="p">(</span><span class="n">model</span><span class="p">,</span> <span class="n">X</span><span class="o">=</span><span class="n">X</span><span class="p">):</span>
    <span class="n">rmse</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="o">-</span><span class="n">cross_val_score</span><span class="p">(</span><span class="n">model</span><span class="p">,</span> <span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="p">,</span> <span class="n">scoring</span><span class="o">=</span><span class="s2">&quot;neg_mean_squared_error&quot;</span><span class="p">,</span> <span class="n">cv</span><span class="o">=</span><span class="n">kfolds</span><span class="p">))</span>
    <span class="k">return</span> <span class="p">(</span><span class="n">rmse</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[73]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">alphas_alt</span> <span class="o">=</span> <span class="p">[</span><span class="mf">14.5</span><span class="p">,</span> <span class="mf">14.6</span><span class="p">,</span> <span class="mf">14.7</span><span class="p">,</span> <span class="mf">14.8</span><span class="p">,</span> <span class="mf">14.9</span><span class="p">,</span> <span class="mi">15</span><span class="p">,</span> <span class="mf">15.1</span><span class="p">,</span> <span class="mf">15.2</span><span class="p">,</span> <span class="mf">15.3</span><span class="p">,</span> <span class="mf">15.4</span><span class="p">,</span> <span class="mf">15.5</span><span class="p">]</span>
<span class="n">alphas2</span> <span class="o">=</span> <span class="p">[</span><span class="mf">5e-05</span><span class="p">,</span> <span class="mf">0.0001</span><span class="p">,</span> <span class="mf">0.0002</span><span class="p">,</span> <span class="mf">0.0003</span><span class="p">,</span> <span class="mf">0.0004</span><span class="p">,</span> <span class="mf">0.0005</span><span class="p">,</span> <span class="mf">0.0006</span><span class="p">,</span> <span class="mf">0.0007</span><span class="p">,</span> <span class="mf">0.0008</span><span class="p">]</span>
<span class="n">e_alphas</span> <span class="o">=</span> <span class="p">[</span><span class="mf">0.0001</span><span class="p">,</span> <span class="mf">0.0002</span><span class="p">,</span> <span class="mf">0.0003</span><span class="p">,</span> <span class="mf">0.0004</span><span class="p">,</span> <span class="mf">0.0005</span><span class="p">,</span> <span class="mf">0.0006</span><span class="p">,</span> <span class="mf">0.0007</span><span class="p">]</span>
<span class="n">e_l1ratio</span> <span class="o">=</span> <span class="p">[</span><span class="mf">0.8</span><span class="p">,</span> <span class="mf">0.85</span><span class="p">,</span> <span class="mf">0.9</span><span class="p">,</span> <span class="mf">0.95</span><span class="p">,</span> <span class="mf">0.99</span><span class="p">,</span> <span class="mi">1</span><span class="p">]</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[74]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ridge</span> <span class="o">=</span> <span class="n">make_pipeline</span><span class="p">(</span><span class="n">RobustScaler</span><span class="p">(),</span> <span class="n">RidgeCV</span><span class="p">(</span><span class="n">alphas</span><span class="o">=</span><span class="n">alphas_alt</span><span class="p">,</span> <span class="n">cv</span><span class="o">=</span><span class="n">kfolds</span><span class="p">))</span>
<span class="n">lasso</span> <span class="o">=</span> <span class="n">make_pipeline</span><span class="p">(</span><span class="n">RobustScaler</span><span class="p">(),</span> <span class="n">LassoCV</span><span class="p">(</span><span class="n">max_iter</span><span class="o">=</span><span class="mf">1e7</span><span class="p">,</span> <span class="n">alphas</span><span class="o">=</span><span class="n">alphas2</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">42</span><span class="p">,</span> <span class="n">cv</span><span class="o">=</span><span class="n">kfolds</span><span class="p">))</span>
<span class="n">elasticnet</span> <span class="o">=</span> <span class="n">make_pipeline</span><span class="p">(</span><span class="n">RobustScaler</span><span class="p">(),</span> <span class="n">ElasticNetCV</span><span class="p">(</span><span class="n">max_iter</span><span class="o">=</span><span class="mf">1e7</span><span class="p">,</span> <span class="n">alphas</span><span class="o">=</span><span class="n">e_alphas</span><span class="p">,</span> <span class="n">cv</span><span class="o">=</span><span class="n">kfolds</span><span class="p">,</span> <span class="n">l1_ratio</span><span class="o">=</span><span class="n">e_l1ratio</span><span class="p">))</span>                                
<span class="n">svr</span> <span class="o">=</span> <span class="n">make_pipeline</span><span class="p">(</span><span class="n">RobustScaler</span><span class="p">(),</span> <span class="n">SVR</span><span class="p">(</span><span class="n">C</span><span class="o">=</span> <span class="mi">20</span><span class="p">,</span> <span class="n">epsilon</span><span class="o">=</span> <span class="mf">0.008</span><span class="p">,</span> <span class="n">gamma</span><span class="o">=</span><span class="mf">0.0003</span><span class="p">,))</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[75]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">gbr</span> <span class="o">=</span> <span class="n">GradientBoostingRegressor</span><span class="p">(</span><span class="n">n_estimators</span><span class="o">=</span><span class="mi">3000</span><span class="p">,</span> <span class="n">learning_rate</span><span class="o">=</span><span class="mf">0.05</span><span class="p">,</span> <span class="n">max_depth</span><span class="o">=</span><span class="mi">4</span><span class="p">,</span> <span class="n">max_features</span><span class="o">=</span><span class="s1">&#39;sqrt&#39;</span><span class="p">,</span> <span class="n">min_samples_leaf</span><span class="o">=</span><span class="mi">15</span><span class="p">,</span> <span class="n">min_samples_split</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span> <span class="n">loss</span><span class="o">=</span><span class="s1">&#39;huber&#39;</span><span class="p">,</span> <span class="n">random_state</span> <span class="o">=</span><span class="mi">42</span><span class="p">)</span>                             
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[76]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">lightgbm</span> <span class="o">=</span> <span class="n">LGBMRegressor</span><span class="p">(</span><span class="n">objective</span><span class="o">=</span><span class="s1">&#39;regression&#39;</span><span class="p">,</span> 
                                       <span class="n">num_leaves</span><span class="o">=</span><span class="mi">4</span><span class="p">,</span>
                                       <span class="n">learning_rate</span><span class="o">=</span><span class="mf">0.01</span><span class="p">,</span> 
                                       <span class="n">n_estimators</span><span class="o">=</span><span class="mi">5000</span><span class="p">,</span>
                                       <span class="n">max_bin</span><span class="o">=</span><span class="mi">200</span><span class="p">,</span> 
                                       <span class="n">bagging_fraction</span><span class="o">=</span><span class="mf">0.75</span><span class="p">,</span>
                                       <span class="n">bagging_freq</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span> 
                                       <span class="n">bagging_seed</span><span class="o">=</span><span class="mi">7</span><span class="p">,</span>
                                       <span class="n">feature_fraction</span><span class="o">=</span><span class="mf">0.2</span><span class="p">,</span>
                                       <span class="n">feature_fraction_seed</span><span class="o">=</span><span class="mi">7</span><span class="p">,</span>
                                       <span class="n">verbose</span><span class="o">=-</span><span class="mi">1</span><span class="p">,</span>
                                       <span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[77]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">xgboost</span> <span class="o">=</span> <span class="n">XGBRegressor</span><span class="p">(</span><span class="n">learning_rate</span><span class="o">=</span><span class="mf">0.01</span><span class="p">,</span><span class="n">n_estimators</span><span class="o">=</span><span class="mi">3460</span><span class="p">,</span>
                                     <span class="n">max_depth</span><span class="o">=</span><span class="mi">3</span><span class="p">,</span> <span class="n">min_child_weight</span><span class="o">=</span><span class="mi">0</span><span class="p">,</span>
                                     <span class="n">gamma</span><span class="o">=</span><span class="mi">0</span><span class="p">,</span> <span class="n">subsample</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span>
                                     <span class="n">colsample_bytree</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span>
                                     <span class="n">objective</span><span class="o">=</span><span class="s1">&#39;reg:linear&#39;</span><span class="p">,</span> <span class="n">nthread</span><span class="o">=-</span><span class="mi">1</span><span class="p">,</span>
                                     <span class="n">scale_pos_weight</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">seed</span><span class="o">=</span><span class="mi">27</span><span class="p">,</span>
                                     <span class="n">reg_alpha</span><span class="o">=</span><span class="mf">0.00006</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[78]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">stack_gen</span> <span class="o">=</span> <span class="n">StackingCVRegressor</span><span class="p">(</span><span class="n">regressors</span><span class="o">=</span><span class="p">(</span><span class="n">ridge</span><span class="p">,</span> <span class="n">lasso</span><span class="p">,</span> <span class="n">elasticnet</span><span class="p">,</span> <span class="n">xgboost</span><span class="p">,</span> <span class="n">lightgbm</span><span class="p">),</span>
                                <span class="n">meta_regressor</span><span class="o">=</span><span class="n">xgboost</span><span class="p">,</span>
                                <span class="n">use_features_in_secondary</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># score = cv_rmse(stack_gen)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[80]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">score</span> <span class="o">=</span> <span class="n">cv_rmse</span><span class="p">(</span><span class="n">ridge</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Ridge: </span><span class="si">{:.4f}</span><span class="s2"> (</span><span class="si">{:.4f}</span><span class="s2">)</span><span class="se">\n</span><span class="s2">&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">score</span><span class="o">.</span><span class="n">mean</span><span class="p">(),</span> <span class="n">score</span><span class="o">.</span><span class="n">std</span><span class="p">()),</span> <span class="n">datetime</span><span class="o">.</span><span class="n">now</span><span class="p">(),</span> <span class="p">)</span>

<span class="n">score</span> <span class="o">=</span> <span class="n">cv_rmse</span><span class="p">(</span><span class="n">lasso</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;LASSO: </span><span class="si">{:.4f}</span><span class="s2"> (</span><span class="si">{:.4f}</span><span class="s2">)</span><span class="se">\n</span><span class="s2">&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">score</span><span class="o">.</span><span class="n">mean</span><span class="p">(),</span> <span class="n">score</span><span class="o">.</span><span class="n">std</span><span class="p">()),</span> <span class="n">datetime</span><span class="o">.</span><span class="n">now</span><span class="p">(),</span> <span class="p">)</span>

<span class="n">score</span> <span class="o">=</span> <span class="n">cv_rmse</span><span class="p">(</span><span class="n">elasticnet</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;elastic net: </span><span class="si">{:.4f}</span><span class="s2"> (</span><span class="si">{:.4f}</span><span class="s2">)</span><span class="se">\n</span><span class="s2">&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">score</span><span class="o">.</span><span class="n">mean</span><span class="p">(),</span> <span class="n">score</span><span class="o">.</span><span class="n">std</span><span class="p">()),</span> <span class="n">datetime</span><span class="o">.</span><span class="n">now</span><span class="p">(),</span> <span class="p">)</span>

<span class="n">score</span> <span class="o">=</span> <span class="n">cv_rmse</span><span class="p">(</span><span class="n">svr</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;SVR: </span><span class="si">{:.4f}</span><span class="s2"> (</span><span class="si">{:.4f}</span><span class="s2">)</span><span class="se">\n</span><span class="s2">&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">score</span><span class="o">.</span><span class="n">mean</span><span class="p">(),</span> <span class="n">score</span><span class="o">.</span><span class="n">std</span><span class="p">()),</span> <span class="n">datetime</span><span class="o">.</span><span class="n">now</span><span class="p">(),</span> <span class="p">)</span>

<span class="n">score</span> <span class="o">=</span> <span class="n">cv_rmse</span><span class="p">(</span><span class="n">lightgbm</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;lightgbm: </span><span class="si">{:.4f}</span><span class="s2"> (</span><span class="si">{:.4f}</span><span class="s2">)</span><span class="se">\n</span><span class="s2">&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">score</span><span class="o">.</span><span class="n">mean</span><span class="p">(),</span> <span class="n">score</span><span class="o">.</span><span class="n">std</span><span class="p">()),</span> <span class="n">datetime</span><span class="o">.</span><span class="n">now</span><span class="p">(),</span> <span class="p">)</span>

<span class="c1"># score = cv_rmse(gbr)</span>
<span class="c1"># print(&quot;gbr: {:.4f} ({:.4f})\n&quot;.format(score.mean(), score.std()), datetime.now(), )</span>

<span class="n">score</span> <span class="o">=</span> <span class="n">cv_rmse</span><span class="p">(</span><span class="n">xgboost</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;xgboost: </span><span class="si">{:.4f}</span><span class="s2"> (</span><span class="si">{:.4f}</span><span class="s2">)</span><span class="se">\n</span><span class="s2">&quot;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">score</span><span class="o">.</span><span class="n">mean</span><span class="p">(),</span> <span class="n">score</span><span class="o">.</span><span class="n">std</span><span class="p">()),</span> <span class="n">datetime</span><span class="o">.</span><span class="n">now</span><span class="p">(),</span> <span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Ridge: 0.1011 (0.0141)
 2020-01-22 15:12:38.941969
LASSO: 0.0997 (0.0142)
 2020-01-22 15:12:45.519931
elastic net: 0.0998 (0.0143)
 2020-01-22 15:13:12.882048
SVR: 0.1020 (0.0146)
 2020-01-22 15:13:26.262319
lightgbm: 0.1054 (0.0154)
 2020-01-22 15:13:44.348901
[15:13:44] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:13:58] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:14:12] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:14:28] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:14:42] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:14:55] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:15:09] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:15:25] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:15:39] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:15:53] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
xgboost: 0.1061 (0.0147)
 2020-01-22 15:16:07.581332
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[81]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s1">&#39;START Fit&#39;</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;stack_gen&#39;</span><span class="p">)</span>
<span class="n">stack_gen_model</span> <span class="o">=</span> <span class="n">stack_gen</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">X</span><span class="p">),</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">y</span><span class="p">))</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;elasticnet&#39;</span><span class="p">)</span>
<span class="n">elastic_model_full_data</span> <span class="o">=</span> <span class="n">elasticnet</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Lasso&#39;</span><span class="p">)</span>
<span class="n">lasso_model_full_data</span> <span class="o">=</span> <span class="n">lasso</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Ridge&#39;</span><span class="p">)</span> 
<span class="n">ridge_model_full_data</span> <span class="o">=</span> <span class="n">ridge</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Svr&#39;</span><span class="p">)</span>
<span class="n">svr_model_full_data</span> <span class="o">=</span> <span class="n">svr</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="p">)</span>

<span class="c1"># print(&#39;GradientBoosting&#39;)</span>
<span class="c1"># gbr_model_full_data = gbr.fit(X, y)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;xgboost&#39;</span><span class="p">)</span>
<span class="n">xgb_model_full_data</span> <span class="o">=</span> <span class="n">xgboost</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;lightgbm&#39;</span><span class="p">)</span>
<span class="n">lgb_model_full_data</span> <span class="o">=</span> <span class="n">lightgbm</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>START Fit
stack_gen
[15:17:42] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:17:54] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:18:07] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:18:21] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:18:34] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:18:54] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
[15:19:15] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
elasticnet
Lasso
Ridge
Svr
xgboost
[15:19:40] WARNING: /workspace/src/objective/regression_obj.cu:152: reg:linear is now deprecated in favor of reg:squarederror.
lightgbm
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Blending-Models">Blending Models<a class="anchor-link" href="#Blending-Models">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[85]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="mf">1.0</span> <span class="o">*</span> <span class="n">elastic_model_full_data</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt output_prompt">Out[85]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>array([12.2252765 , 12.19482971, 12.28743582, ..., 12.45057568,
       11.846052  , 11.9162269 ])</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[86]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">blend_models_predict</span><span class="p">(</span><span class="n">X</span><span class="p">):</span>
    <span class="k">return</span> <span class="p">((</span><span class="mf">0.1</span> <span class="o">*</span> <span class="n">elastic_model_full_data</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X</span><span class="p">))</span> <span class="o">+</span> \
            <span class="p">(</span><span class="mf">0.05</span> <span class="o">*</span> <span class="n">lasso_model_full_data</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X</span><span class="p">))</span> <span class="o">+</span> \
            <span class="p">(</span><span class="mf">0.2</span> <span class="o">*</span> <span class="n">ridge_model_full_data</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X</span><span class="p">))</span> <span class="o">+</span> \
            <span class="p">(</span><span class="mf">0.1</span> <span class="o">*</span> <span class="n">svr_model_full_data</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X</span><span class="p">))</span> <span class="o">+</span> \
<span class="c1">#             (0.1 * gbr_model_full_data.predict(X)) + \</span>
            <span class="p">(</span><span class="mf">0.15</span> <span class="o">*</span> <span class="n">xgb_model_full_data</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X</span><span class="p">))</span> <span class="o">+</span> \
            <span class="p">(</span><span class="mf">0.1</span> <span class="o">*</span> <span class="n">lgb_model_full_data</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X</span><span class="p">))</span> <span class="o">+</span> \
            <span class="p">(</span><span class="mf">0.3</span> <span class="o">*</span> <span class="n">stack_gen_model</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">(</span><span class="n">X</span><span class="p">))))</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[87]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s1">&#39;RMSLE score on train data:&#39;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">rmsle</span><span class="p">(</span><span class="n">y</span><span class="p">,</span> <span class="n">blend_models_predict</span><span class="p">(</span><span class="n">X</span><span class="p">)))</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>RMSLE score on train data:
0.06279142797823006
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[88]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">submission</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;../input/house-prices-advanced-regression-techniques/sample_submission.csv&quot;</span><span class="p">)</span>
<span class="n">submission</span><span class="o">.</span><span class="n">iloc</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">floor</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">expm1</span><span class="p">(</span><span class="n">blend_models_predict</span><span class="p">(</span><span class="n">X_sub</span><span class="p">)))</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

<div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Predict submission
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Submission">Submission<a class="anchor-link" href="#Submission">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[92]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">q1</span> <span class="o">=</span> <span class="n">submission</span><span class="p">[</span><span class="s1">&#39;SalePrice&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">quantile</span><span class="p">(</span><span class="mf">0.005</span><span class="p">)</span>
<span class="n">q2</span> <span class="o">=</span> <span class="n">submission</span><span class="p">[</span><span class="s1">&#39;SalePrice&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">quantile</span><span class="p">(</span><span class="mf">0.995</span><span class="p">)</span>
<span class="n">submission</span><span class="p">[</span><span class="s1">&#39;SalePrice&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">submission</span><span class="p">[</span><span class="s1">&#39;SalePrice&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">x</span> <span class="k">if</span> <span class="n">x</span> <span class="o">&gt;</span> <span class="n">q1</span> <span class="k">else</span> <span class="n">x</span><span class="o">*</span><span class="mf">0.77</span><span class="p">)</span>
<span class="n">submission</span><span class="p">[</span><span class="s1">&#39;SalePrice&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">submission</span><span class="p">[</span><span class="s1">&#39;SalePrice&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">x</span> <span class="k">if</span> <span class="n">x</span> <span class="o">&lt;</span> <span class="n">q2</span> <span class="k">else</span> <span class="n">x</span><span class="o">*</span><span class="mf">1.1</span><span class="p">)</span>
<span class="n">submission</span><span class="o">.</span><span class="n">to_csv</span><span class="p">(</span><span class="s2">&quot;submission.csv&quot;</span><span class="p">,</span> <span class="n">index</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
    </div>
  </div>
</body>

 


</html>