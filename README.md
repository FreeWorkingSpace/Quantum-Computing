# Quantum-Computing<!DOCTYPE html>
<html>
<head><meta charset="utf-8" />

<title>Quantum Computing Deutsch-Jozsa Algorithm</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
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
body {
  margin: 0;
}
article,
aside,
details,
figcaption,
figure,
footer,
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
 *  Font Awesome 4.7.0 by @davegandy - http://fontawesome.io - @fontawesome
 *  License - http://fontawesome.io/license (Font: SIL OFL 1.1, CSS: MIT License)
 */
/* FONT PATH
 * -------------------------- */
@font-face {
  font-family: 'FontAwesome';
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?v=4.7.0');
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?#iefix&v=4.7.0') format('embedded-opentype'), url('../components/font-awesome/fonts/fontawesome-webfont.woff2?v=4.7.0') format('woff2'), url('../components/font-awesome/fonts/fontawesome-webfont.woff?v=4.7.0') format('woff'), url('../components/font-awesome/fonts/fontawesome-webfont.ttf?v=4.7.0') format('truetype'), url('../components/font-awesome/fonts/fontawesome-webfont.svg?v=4.7.0#fontawesomeregular') format('svg');
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
.fa-pull-left {
  float: left;
}
.fa-pull-right {
  float: right;
}
.fa.fa-pull-left {
  margin-right: .3em;
}
.fa.fa-pull-right {
  margin-left: .3em;
}
/* Deprecated as of 4.4.0 */
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
.fa-pulse {
  -webkit-animation: fa-spin 1s infinite steps(8);
  animation: fa-spin 1s infinite steps(8);
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
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=1)";
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}
.fa-rotate-180 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2)";
  -webkit-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  transform: rotate(180deg);
}
.fa-rotate-270 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=3)";
  -webkit-transform: rotate(270deg);
  -ms-transform: rotate(270deg);
  transform: rotate(270deg);
}
.fa-flip-horizontal {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1)";
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
.fa-flip-vertical {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2, mirror=1)";
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
.fa-facebook-f:before,
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
.fa-feed:before,
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
.fa-gittip:before,
.fa-gratipay:before {
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
.fa-pied-piper-pp:before {
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
.fa-resistance:before,
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
.fa-y-combinator-square:before,
.fa-yc-square:before,
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
.fa-buysellads:before {
  content: "\f20d";
}
.fa-connectdevelop:before {
  content: "\f20e";
}
.fa-dashcube:before {
  content: "\f210";
}
.fa-forumbee:before {
  content: "\f211";
}
.fa-leanpub:before {
  content: "\f212";
}
.fa-sellsy:before {
  content: "\f213";
}
.fa-shirtsinbulk:before {
  content: "\f214";
}
.fa-simplybuilt:before {
  content: "\f215";
}
.fa-skyatlas:before {
  content: "\f216";
}
.fa-cart-plus:before {
  content: "\f217";
}
.fa-cart-arrow-down:before {
  content: "\f218";
}
.fa-diamond:before {
  content: "\f219";
}
.fa-ship:before {
  content: "\f21a";
}
.fa-user-secret:before {
  content: "\f21b";
}
.fa-motorcycle:before {
  content: "\f21c";
}
.fa-street-view:before {
  content: "\f21d";
}
.fa-heartbeat:before {
  content: "\f21e";
}
.fa-venus:before {
  content: "\f221";
}
.fa-mars:before {
  content: "\f222";
}
.fa-mercury:before {
  content: "\f223";
}
.fa-intersex:before,
.fa-transgender:before {
  content: "\f224";
}
.fa-transgender-alt:before {
  content: "\f225";
}
.fa-venus-double:before {
  content: "\f226";
}
.fa-mars-double:before {
  content: "\f227";
}
.fa-venus-mars:before {
  content: "\f228";
}
.fa-mars-stroke:before {
  content: "\f229";
}
.fa-mars-stroke-v:before {
  content: "\f22a";
}
.fa-mars-stroke-h:before {
  content: "\f22b";
}
.fa-neuter:before {
  content: "\f22c";
}
.fa-genderless:before {
  content: "\f22d";
}
.fa-facebook-official:before {
  content: "\f230";
}
.fa-pinterest-p:before {
  content: "\f231";
}
.fa-whatsapp:before {
  content: "\f232";
}
.fa-server:before {
  content: "\f233";
}
.fa-user-plus:before {
  content: "\f234";
}
.fa-user-times:before {
  content: "\f235";
}
.fa-hotel:before,
.fa-bed:before {
  content: "\f236";
}
.fa-viacoin:before {
  content: "\f237";
}
.fa-train:before {
  content: "\f238";
}
.fa-subway:before {
  content: "\f239";
}
.fa-medium:before {
  content: "\f23a";
}
.fa-yc:before,
.fa-y-combinator:before {
  content: "\f23b";
}
.fa-optin-monster:before {
  content: "\f23c";
}
.fa-opencart:before {
  content: "\f23d";
}
.fa-expeditedssl:before {
  content: "\f23e";
}
.fa-battery-4:before,
.fa-battery:before,
.fa-battery-full:before {
  content: "\f240";
}
.fa-battery-3:before,
.fa-battery-three-quarters:before {
  content: "\f241";
}
.fa-battery-2:before,
.fa-battery-half:before {
  content: "\f242";
}
.fa-battery-1:before,
.fa-battery-quarter:before {
  content: "\f243";
}
.fa-battery-0:before,
.fa-battery-empty:before {
  content: "\f244";
}
.fa-mouse-pointer:before {
  content: "\f245";
}
.fa-i-cursor:before {
  content: "\f246";
}
.fa-object-group:before {
  content: "\f247";
}
.fa-object-ungroup:before {
  content: "\f248";
}
.fa-sticky-note:before {
  content: "\f249";
}
.fa-sticky-note-o:before {
  content: "\f24a";
}
.fa-cc-jcb:before {
  content: "\f24b";
}
.fa-cc-diners-club:before {
  content: "\f24c";
}
.fa-clone:before {
  content: "\f24d";
}
.fa-balance-scale:before {
  content: "\f24e";
}
.fa-hourglass-o:before {
  content: "\f250";
}
.fa-hourglass-1:before,
.fa-hourglass-start:before {
  content: "\f251";
}
.fa-hourglass-2:before,
.fa-hourglass-half:before {
  content: "\f252";
}
.fa-hourglass-3:before,
.fa-hourglass-end:before {
  content: "\f253";
}
.fa-hourglass:before {
  content: "\f254";
}
.fa-hand-grab-o:before,
.fa-hand-rock-o:before {
  content: "\f255";
}
.fa-hand-stop-o:before,
.fa-hand-paper-o:before {
  content: "\f256";
}
.fa-hand-scissors-o:before {
  content: "\f257";
}
.fa-hand-lizard-o:before {
  content: "\f258";
}
.fa-hand-spock-o:before {
  content: "\f259";
}
.fa-hand-pointer-o:before {
  content: "\f25a";
}
.fa-hand-peace-o:before {
  content: "\f25b";
}
.fa-trademark:before {
  content: "\f25c";
}
.fa-registered:before {
  content: "\f25d";
}
.fa-creative-commons:before {
  content: "\f25e";
}
.fa-gg:before {
  content: "\f260";
}
.fa-gg-circle:before {
  content: "\f261";
}
.fa-tripadvisor:before {
  content: "\f262";
}
.fa-odnoklassniki:before {
  content: "\f263";
}
.fa-odnoklassniki-square:before {
  content: "\f264";
}
.fa-get-pocket:before {
  content: "\f265";
}
.fa-wikipedia-w:before {
  content: "\f266";
}
.fa-safari:before {
  content: "\f267";
}
.fa-chrome:before {
  content: "\f268";
}
.fa-firefox:before {
  content: "\f269";
}
.fa-opera:before {
  content: "\f26a";
}
.fa-internet-explorer:before {
  content: "\f26b";
}
.fa-tv:before,
.fa-television:before {
  content: "\f26c";
}
.fa-contao:before {
  content: "\f26d";
}
.fa-500px:before {
  content: "\f26e";
}
.fa-amazon:before {
  content: "\f270";
}
.fa-calendar-plus-o:before {
  content: "\f271";
}
.fa-calendar-minus-o:before {
  content: "\f272";
}
.fa-calendar-times-o:before {
  content: "\f273";
}
.fa-calendar-check-o:before {
  content: "\f274";
}
.fa-industry:before {
  content: "\f275";
}
.fa-map-pin:before {
  content: "\f276";
}
.fa-map-signs:before {
  content: "\f277";
}
.fa-map-o:before {
  content: "\f278";
}
.fa-map:before {
  content: "\f279";
}
.fa-commenting:before {
  content: "\f27a";
}
.fa-commenting-o:before {
  content: "\f27b";
}
.fa-houzz:before {
  content: "\f27c";
}
.fa-vimeo:before {
  content: "\f27d";
}
.fa-black-tie:before {
  content: "\f27e";
}
.fa-fonticons:before {
  content: "\f280";
}
.fa-reddit-alien:before {
  content: "\f281";
}
.fa-edge:before {
  content: "\f282";
}
.fa-credit-card-alt:before {
  content: "\f283";
}
.fa-codiepie:before {
  content: "\f284";
}
.fa-modx:before {
  content: "\f285";
}
.fa-fort-awesome:before {
  content: "\f286";
}
.fa-usb:before {
  content: "\f287";
}
.fa-product-hunt:before {
  content: "\f288";
}
.fa-mixcloud:before {
  content: "\f289";
}
.fa-scribd:before {
  content: "\f28a";
}
.fa-pause-circle:before {
  content: "\f28b";
}
.fa-pause-circle-o:before {
  content: "\f28c";
}
.fa-stop-circle:before {
  content: "\f28d";
}
.fa-stop-circle-o:before {
  content: "\f28e";
}
.fa-shopping-bag:before {
  content: "\f290";
}
.fa-shopping-basket:before {
  content: "\f291";
}
.fa-hashtag:before {
  content: "\f292";
}
.fa-bluetooth:before {
  content: "\f293";
}
.fa-bluetooth-b:before {
  content: "\f294";
}
.fa-percent:before {
  content: "\f295";
}
.fa-gitlab:before {
  content: "\f296";
}
.fa-wpbeginner:before {
  content: "\f297";
}
.fa-wpforms:before {
  content: "\f298";
}
.fa-envira:before {
  content: "\f299";
}
.fa-universal-access:before {
  content: "\f29a";
}
.fa-wheelchair-alt:before {
  content: "\f29b";
}
.fa-question-circle-o:before {
  content: "\f29c";
}
.fa-blind:before {
  content: "\f29d";
}
.fa-audio-description:before {
  content: "\f29e";
}
.fa-volume-control-phone:before {
  content: "\f2a0";
}
.fa-braille:before {
  content: "\f2a1";
}
.fa-assistive-listening-systems:before {
  content: "\f2a2";
}
.fa-asl-interpreting:before,
.fa-american-sign-language-interpreting:before {
  content: "\f2a3";
}
.fa-deafness:before,
.fa-hard-of-hearing:before,
.fa-deaf:before {
  content: "\f2a4";
}
.fa-glide:before {
  content: "\f2a5";
}
.fa-glide-g:before {
  content: "\f2a6";
}
.fa-signing:before,
.fa-sign-language:before {
  content: "\f2a7";
}
.fa-low-vision:before {
  content: "\f2a8";
}
.fa-viadeo:before {
  content: "\f2a9";
}
.fa-viadeo-square:before {
  content: "\f2aa";
}
.fa-snapchat:before {
  content: "\f2ab";
}
.fa-snapchat-ghost:before {
  content: "\f2ac";
}
.fa-snapchat-square:before {
  content: "\f2ad";
}
.fa-pied-piper:before {
  content: "\f2ae";
}
.fa-first-order:before {
  content: "\f2b0";
}
.fa-yoast:before {
  content: "\f2b1";
}
.fa-themeisle:before {
  content: "\f2b2";
}
.fa-google-plus-circle:before,
.fa-google-plus-official:before {
  content: "\f2b3";
}
.fa-fa:before,
.fa-font-awesome:before {
  content: "\f2b4";
}
.fa-handshake-o:before {
  content: "\f2b5";
}
.fa-envelope-open:before {
  content: "\f2b6";
}
.fa-envelope-open-o:before {
  content: "\f2b7";
}
.fa-linode:before {
  content: "\f2b8";
}
.fa-address-book:before {
  content: "\f2b9";
}
.fa-address-book-o:before {
  content: "\f2ba";
}
.fa-vcard:before,
.fa-address-card:before {
  content: "\f2bb";
}
.fa-vcard-o:before,
.fa-address-card-o:before {
  content: "\f2bc";
}
.fa-user-circle:before {
  content: "\f2bd";
}
.fa-user-circle-o:before {
  content: "\f2be";
}
.fa-user-o:before {
  content: "\f2c0";
}
.fa-id-badge:before {
  content: "\f2c1";
}
.fa-drivers-license:before,
.fa-id-card:before {
  content: "\f2c2";
}
.fa-drivers-license-o:before,
.fa-id-card-o:before {
  content: "\f2c3";
}
.fa-quora:before {
  content: "\f2c4";
}
.fa-free-code-camp:before {
  content: "\f2c5";
}
.fa-telegram:before {
  content: "\f2c6";
}
.fa-thermometer-4:before,
.fa-thermometer:before,
.fa-thermometer-full:before {
  content: "\f2c7";
}
.fa-thermometer-3:before,
.fa-thermometer-three-quarters:before {
  content: "\f2c8";
}
.fa-thermometer-2:before,
.fa-thermometer-half:before {
  content: "\f2c9";
}
.fa-thermometer-1:before,
.fa-thermometer-quarter:before {
  content: "\f2ca";
}
.fa-thermometer-0:before,
.fa-thermometer-empty:before {
  content: "\f2cb";
}
.fa-shower:before {
  content: "\f2cc";
}
.fa-bathtub:before,
.fa-s15:before,
.fa-bath:before {
  content: "\f2cd";
}
.fa-podcast:before {
  content: "\f2ce";
}
.fa-window-maximize:before {
  content: "\f2d0";
}
.fa-window-minimize:before {
  content: "\f2d1";
}
.fa-window-restore:before {
  content: "\f2d2";
}
.fa-times-rectangle:before,
.fa-window-close:before {
  content: "\f2d3";
}
.fa-times-rectangle-o:before,
.fa-window-close-o:before {
  content: "\f2d4";
}
.fa-bandcamp:before {
  content: "\f2d5";
}
.fa-grav:before {
  content: "\f2d6";
}
.fa-etsy:before {
  content: "\f2d7";
}
.fa-imdb:before {
  content: "\f2d8";
}
.fa-ravelry:before {
  content: "\f2d9";
}
.fa-eercast:before {
  content: "\f2da";
}
.fa-microchip:before {
  content: "\f2db";
}
.fa-snowflake-o:before {
  content: "\f2dc";
}
.fa-superpowers:before {
  content: "\f2dd";
}
.fa-wpexplorer:before {
  content: "\f2de";
}
.fa-meetup:before {
  content: "\f2e0";
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
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
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
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
div.traceback-wrapper pre.traceback {
  max-height: 600px;
  overflow: auto;
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
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 5px;
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
[dir="rtl"] #ipython_notebook {
  margin-right: 10px;
  margin-left: 0;
}
[dir="rtl"] #ipython_notebook.pull-left {
  float: right !important;
  float: right;
}
.flex-spacer {
  flex: 1;
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
span#kernel_logo_widget {
  margin: 0 10px;
}
span#login_widget {
  float: right;
}
[dir="rtl"] span#login_widget {
  float: left;
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
.modal-header {
  cursor: move;
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
[dir="rtl"] .center-nav form.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] .center-nav .navbar-text {
  float: right;
}
[dir="rtl"] .navbar-inner {
  text-align: right;
}
[dir="rtl"] div.text-left {
  text-align: right;
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
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  overflow: hidden;
  cursor: pointer;
  opacity: 0;
  z-index: 2;
}
.alternate_upload .btn-xs > input.fileinput {
  margin: -1px -5px;
}
.alternate_upload .btn-upload {
  position: relative;
  height: 22px;
}
::-webkit-file-upload-button {
  cursor: pointer;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
ul#tabs {
  margin-bottom: 4px;
}
ul#tabs a {
  padding-top: 6px;
  padding-bottom: 4px;
}
[dir="rtl"] ul#tabs.nav-tabs > li {
  float: right;
}
[dir="rtl"] ul#tabs.nav.nav-tabs {
  padding-right: 0;
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
[dir="rtl"] .list_toolbar .tree-buttons .pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .list_toolbar .col-sm-4,
[dir="rtl"] .list_toolbar .col-sm-8 {
  float: right;
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
  vertical-align: text-bottom;
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
[dir="rtl"] .list_item > div input {
  margin-right: 0;
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
.item_modified {
  margin-right: 7px;
  margin-left: 7px;
}
[dir="rtl"] .item_modified.pull-right {
  float: left !important;
  float: left;
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
[dir="rtl"] .item_buttons.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .item_buttons .kernel-name {
  margin-left: 7px;
  float: right;
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
.sort_button {
  display: inline-block;
  padding-left: 7px;
}
[dir="rtl"] .sort_button.pull-right {
  float: left !important;
  float: left;
}
#tree-selector {
  padding-right: 0px;
}
#button-select-all {
  min-width: 50px;
}
[dir="rtl"] #button-select-all.btn {
  float: right ;
}
#select-all {
  margin-left: 7px;
  margin-right: 2px;
  margin-top: 2px;
  height: 16px;
}
[dir="rtl"] #select-all.pull-left {
  float: right !important;
  float: right;
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
.folder_icon:before.fa-pull-left {
  margin-right: .3em;
}
.folder_icon:before.fa-pull-right {
  margin-left: .3em;
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
.notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.notebook_icon:before.fa-pull-right {
  margin-left: .3em;
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
.running_notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.fa-pull-right {
  margin-left: .3em;
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
.file_icon:before.fa-pull-left {
  margin-right: .3em;
}
.file_icon:before.fa-pull-right {
  margin-left: .3em;
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
#new-menu .dropdown-header {
  font-size: 10px;
  border-bottom: 1px solid #e5e5e5;
  padding: 0 0 3px;
  margin: -3px 20px 0;
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
.delete-button {
  display: none;
}
.duplicate-button {
  display: none;
}
.rename-button {
  display: none;
}
.move-button {
  display: none;
}
.download-button {
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
.dirty-indicator.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator.fa-pull-right {
  margin-left: .3em;
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
.dirty-indicator-dirty.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.fa-pull-right {
  margin-left: .3em;
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
.dirty-indicator-clean.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.fa-pull-right {
  margin-left: .3em;
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
.dirty-indicator-clean:before.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.fa-pull-right {
  margin-left: .3em;
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
.CodeMirror-dialog {
  background-color: #fff;
}
/*!
*
* IPython notebook
*
*/
/* CSS font colors for translated ANSI escape sequences */
/* The color values are a mix of
   http://www.xcolors.net/dl/baskerville-ivorylight and
   http://www.xcolors.net/dl/euphrasia */
.ansi-black-fg {
  color: #3E424D;
}
.ansi-black-bg {
  background-color: #3E424D;
}
.ansi-black-intense-fg {
  color: #282C36;
}
.ansi-black-intense-bg {
  background-color: #282C36;
}
.ansi-red-fg {
  color: #E75C58;
}
.ansi-red-bg {
  background-color: #E75C58;
}
.ansi-red-intense-fg {
  color: #B22B31;
}
.ansi-red-intense-bg {
  background-color: #B22B31;
}
.ansi-green-fg {
  color: #00A250;
}
.ansi-green-bg {
  background-color: #00A250;
}
.ansi-green-intense-fg {
  color: #007427;
}
.ansi-green-intense-bg {
  background-color: #007427;
}
.ansi-yellow-fg {
  color: #DDB62B;
}
.ansi-yellow-bg {
  background-color: #DDB62B;
}
.ansi-yellow-intense-fg {
  color: #B27D12;
}
.ansi-yellow-intense-bg {
  background-color: #B27D12;
}
.ansi-blue-fg {
  color: #208FFB;
}
.ansi-blue-bg {
  background-color: #208FFB;
}
.ansi-blue-intense-fg {
  color: #0065CA;
}
.ansi-blue-intense-bg {
  background-color: #0065CA;
}
.ansi-magenta-fg {
  color: #D160C4;
}
.ansi-magenta-bg {
  background-color: #D160C4;
}
.ansi-magenta-intense-fg {
  color: #A03196;
}
.ansi-magenta-intense-bg {
  background-color: #A03196;
}
.ansi-cyan-fg {
  color: #60C6C8;
}
.ansi-cyan-bg {
  background-color: #60C6C8;
}
.ansi-cyan-intense-fg {
  color: #258F8F;
}
.ansi-cyan-intense-bg {
  background-color: #258F8F;
}
.ansi-white-fg {
  color: #C5C1B4;
}
.ansi-white-bg {
  background-color: #C5C1B4;
}
.ansi-white-intense-fg {
  color: #A1A6B2;
}
.ansi-white-intense-bg {
  background-color: #A1A6B2;
}
.ansi-default-inverse-fg {
  color: #FFFFFF;
}
.ansi-default-inverse-bg {
  background-color: #000000;
}
.ansi-bold {
  font-weight: bold;
}
.ansi-underline {
  text-decoration: underline;
}
/* The following styles are deprecated an will be removed in a future version */
.ansibold {
  font-weight: bold;
}
.ansi-inverse {
  outline: 0.5px dotted;
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
  position: relative;
  overflow: visible;
}
div.cell:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: transparent;
}
div.cell.jupyter-soft-selected {
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
div.cell.selected,
div.cell.selected.jupyter-soft-selected {
  border-color: #ababab;
}
div.cell.selected:before,
div.cell.selected.jupyter-soft-selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #42A5F5;
}
@media print {
  div.cell.selected,
  div.cell.selected.jupyter-soft-selected {
    border-color: transparent;
  }
}
.edit_mode div.cell.selected {
  border-color: #66BB6A;
}
.edit_mode div.cell.selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #66BB6A;
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
  /* Note that this should set vertical padding only, since CodeMirror assumes
       that horizontal padding will be set on CodeMirror pre */
  padding: 0.4em 0;
}
.CodeMirror-linenumber {
  padding: 0 8px 0 4px;
}
.CodeMirror-gutters {
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.CodeMirror pre {
  /* In CM3 this went to 4px from 0 in CM2. This sets horizontal padding only,
    use .CodeMirror-lines for vertical */
  padding: 0 0.4em;
  border: 0;
  border-radius: 0;
}
.CodeMirror-cursor {
  border-left: 1.4px solid black;
}
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .CodeMirror-cursor {
    border-left: 2px solid black;
  }
}
@media screen and (min-width: 4320px) {
  .CodeMirror-cursor {
    border-left: 4px solid black;
  }
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
div.output_area .mglyph > img {
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
  padding: 1px 0 1px 0;
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
.rendered_html ul:not(.list-inline),
.rendered_html ol:not(.list-inline) {
  padding-left: 2em;
}
.rendered_html ul {
  list-style: disc;
}
.rendered_html ul ul {
  list-style: square;
  margin-top: 0;
}
.rendered_html ul ul ul {
  list-style: circle;
}
.rendered_html ol {
  list-style: decimal;
}
.rendered_html ol ol {
  list-style: upper-alpha;
  margin-top: 0;
}
.rendered_html ol ol ol {
  list-style: lower-alpha;
}
.rendered_html ol ol ol ol {
  list-style: lower-roman;
}
.rendered_html ol ol ol ol ol {
  list-style: decimal;
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
  padding: 0px;
  background-color: #fff;
}
.rendered_html code {
  background-color: #eff0f1;
}
.rendered_html p code {
  padding: 1px 5px;
}
.rendered_html pre code {
  background-color: #fff;
}
.rendered_html pre,
.rendered_html code {
  border: 0;
  color: #000;
  font-size: 100%;
}
.rendered_html blockquote {
  margin: 1em 2em;
}
.rendered_html table {
  margin-left: auto;
  margin-right: auto;
  border: none;
  border-collapse: collapse;
  border-spacing: 0;
  color: black;
  font-size: 12px;
  table-layout: fixed;
}
.rendered_html thead {
  border-bottom: 1px solid black;
  vertical-align: bottom;
}
.rendered_html tr,
.rendered_html th,
.rendered_html td {
  text-align: right;
  vertical-align: middle;
  padding: 0.5em 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}
.rendered_html th {
  font-weight: bold;
}
.rendered_html tbody tr:nth-child(odd) {
  background: #f5f5f5;
}
.rendered_html tbody tr:hover {
  background: rgba(66, 165, 245, 0.2);
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
.rendered_html .alert {
  margin-bottom: initial;
}
.rendered_html * + .alert {
  margin-top: 1em;
}
[dir="rtl"] .rendered_html p {
  text-align: right;
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
.text_cell.rendered .rendered_html tr,
.text_cell.rendered .rendered_html th,
.text_cell.rendered .rendered_html td {
  max-width: none;
}
.text_cell.unrendered .text_cell_render {
  display: none;
}
.text_cell .dropzone .input_area {
  border: 2px dashed #bababa;
  margin: -1px;
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
.jupyter-keybindings {
  padding: 1px;
  line-height: 24px;
  border-bottom: 1px solid gray;
}
.jupyter-keybindings input {
  margin: 0;
  padding: 0;
  border: none;
}
.jupyter-keybindings i {
  padding: 6px;
}
.well code {
  background-color: #ffffff;
  border-color: #ababab;
  border-width: 1px;
  border-style: solid;
  padding: 2px;
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
.tags_button_container {
  width: 100%;
  display: flex;
}
.tag-container {
  display: flex;
  flex-direction: row;
  flex-grow: 1;
  overflow: hidden;
  position: relative;
}
.tag-container > * {
  margin: 0 4px;
}
.remove-tag-btn {
  margin-left: 4px;
}
.tags-input {
  display: flex;
}
.cell-tag:last-child:after {
  content: "";
  position: absolute;
  right: 0;
  width: 40px;
  height: 100%;
  /* Fade to background color of cell toolbar */
  background: linear-gradient(to right, rgba(0, 0, 0, 0), #EEE);
}
.tags-input > * {
  margin-left: 4px;
}
.cell-tag,
.tags-input input,
.tags-input button {
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
  box-shadow: none;
  width: inherit;
  font-size: inherit;
  height: 22px;
  line-height: 22px;
  padding: 0px 4px;
  display: inline-block;
}
.cell-tag:focus,
.tags-input input:focus,
.tags-input button:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.cell-tag::-moz-placeholder,
.tags-input input::-moz-placeholder,
.tags-input button::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.cell-tag:-ms-input-placeholder,
.tags-input input:-ms-input-placeholder,
.tags-input button:-ms-input-placeholder {
  color: #999;
}
.cell-tag::-webkit-input-placeholder,
.tags-input input::-webkit-input-placeholder,
.tags-input button::-webkit-input-placeholder {
  color: #999;
}
.cell-tag::-ms-expand,
.tags-input input::-ms-expand,
.tags-input button::-ms-expand {
  border: 0;
  background-color: transparent;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
.cell-tag[readonly],
.tags-input input[readonly],
.tags-input button[readonly],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  background-color: #eeeeee;
  opacity: 1;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  cursor: not-allowed;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button {
  height: auto;
}
select.cell-tag,
select.tags-input input,
select.tags-input button {
  height: 30px;
  line-height: 30px;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button,
select[multiple].cell-tag,
select[multiple].tags-input input,
select[multiple].tags-input button {
  height: auto;
}
.cell-tag,
.tags-input button {
  padding: 0px 4px;
}
.cell-tag {
  background-color: #fff;
  white-space: nowrap;
}
.tags-input input[type=text]:focus {
  outline: none;
  box-shadow: none;
  border-color: #ccc;
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
#kernel_logo_widget .current_kernel_logo {
  display: none;
  margin-top: -1px;
  margin-bottom: -1px;
  width: 32px;
  height: 32px;
}
[dir="rtl"] #kernel_logo_widget {
  float: left !important;
  float: left;
}
.modal .modal-body .move-path {
  display: flex;
  flex-direction: row;
  justify-content: space;
  align-items: center;
}
.modal .modal-body .move-path .server-root {
  padding-right: 20px;
}
.modal .modal-body .move-path .path-input {
  flex: 1;
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
[dir="rtl"] #menubar .navbar-toggle {
  float: right;
}
[dir="rtl"] #menubar .navbar-collapse {
  clear: right;
}
[dir="rtl"] #menubar .navbar-nav {
  float: right;
}
[dir="rtl"] #menubar .nav {
  padding-right: 0px;
}
[dir="rtl"] #menubar .navbar-nav > li {
  float: right;
}
[dir="rtl"] #menubar .navbar-right {
  float: left !important;
}
[dir="rtl"] ul.dropdown-menu {
  text-align: right;
  left: auto;
}
[dir="rtl"] ul#new-menu.dropdown-menu {
  right: auto;
  left: 0;
}
.nav-wrapper {
  border-bottom: 1px solid #e7e7e7;
}
i.menu-icon {
  padding-top: 4px;
}
[dir="rtl"] i.menu-icon.pull-right {
  float: left !important;
  float: left;
}
ul#help_menu li a {
  overflow: hidden;
  padding-right: 2.2em;
}
ul#help_menu li a i {
  margin-right: -1.2em;
}
[dir="rtl"] ul#help_menu li a {
  padding-left: 2.2em;
}
[dir="rtl"] ul#help_menu li a i {
  margin-right: 0;
  margin-left: -1.2em;
}
[dir="rtl"] ul#help_menu li a i.pull-right {
  float: left !important;
  float: left;
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
[dir="rtl"] .dropdown-submenu > .dropdown-menu {
  right: 100%;
  margin-right: -1px;
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
.dropdown-submenu > a:after.fa-pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.fa-pull-right {
  margin-left: .3em;
}
.dropdown-submenu > a:after.pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.pull-right {
  margin-left: .3em;
}
[dir="rtl"] .dropdown-submenu > a:after {
  float: left;
  content: "\f0d9";
  margin-right: 0;
  margin-left: -10px;
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
[dir="rtl"] #notification_area {
  float: left !important;
  float: left;
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
[dir="rtl"] .indicator_area {
  float: left !important;
  float: left;
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
[dir="rtl"] #kernel_indicator {
  float: left !important;
  float: left;
  border-left: 0;
  border-right: 1px solid;
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
[dir="rtl"] #modal_indicator {
  float: left !important;
  float: left;
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
.edit_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
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
.command_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
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
.kernel_idle_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.fa-pull-right {
  margin-left: .3em;
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
.kernel_busy_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.fa-pull-right {
  margin-left: .3em;
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
.kernel_dead_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.fa-pull-right {
  margin-left: .3em;
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
.kernel_disconnected_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.fa-pull-right {
  margin-left: .3em;
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
  height: 30px;
  margin-top: 4px;
  display: flex;
  justify-content: flex-start;
  align-items: baseline;
  width: 50%;
  flex: 1;
}
span.save_widget span.filename {
  height: 100%;
  line-height: 1em;
  margin-left: 16px;
  border: none;
  font-size: 146.5%;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  border-radius: 2px;
}
span.save_widget span.filename:hover {
  background-color: #e6e6e6;
}
[dir="rtl"] span.save_widget.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] span.save_widget span.filename {
  margin-left: 0;
  margin-right: 16px;
}
span.checkpoint_status,
span.autosave_status {
  font-size: small;
  white-space: nowrap;
  padding: 0 5px;
}
@media (max-width: 767px) {
  span.save_widget {
    font-size: small;
    padding: 0 0 0 5px;
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
.toolbar-btn-label {
  margin-left: 6px;
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
[dir="rtl"] .btn-group > .btn,
.btn-group-vertical > .btn {
  float: right;
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
[dir="rtl"] ul.typeahead-list i {
  margin-left: 0;
  margin-right: -10px;
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
ul.typeahead-list  > li > a.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .typeahead-list {
  text-align: right;
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
  min-width: 20px;
  color: transparent;
}
[dir="rtl"] .no-shortcut.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .command-shortcut.pull-right {
  float: left !important;
  float: left;
}
.command-shortcut:before {
  content: "(command mode)";
  padding-right: 3px;
  color: #777777;
}
.edit-shortcut:before {
  content: "(edit)";
  padding-right: 3px;
  color: #777777;
}
[dir="rtl"] .edit-shortcut.pull-right {
  float: left !important;
  float: left;
}
#find-and-replace #replace-preview .match,
#find-and-replace #replace-preview .insert {
  background-color: #BBDEFB;
  border-color: #90CAF9;
  border-style: solid;
  border-width: 1px;
  border-radius: 0px;
}
[dir="ltr"] #find-and-replace .input-group-btn + .form-control {
  border-left: none;
}
[dir="rtl"] #find-and-replace .input-group-btn + .form-control {
  border-right: none;
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
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-AMS_HTML"></script>
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

<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="o">%</span><span class="k">matplotlib</span> inline
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>

<span class="kn">from</span> <span class="nn">qiskit</span> <span class="k">import</span> <span class="n">IBMQ</span><span class="p">,</span> <span class="n">BasicAer</span>
<span class="kn">from</span> <span class="nn">qiskit.providers.ibmq</span> <span class="k">import</span> <span class="n">least_busy</span>
<span class="kn">from</span> <span class="nn">qiskit</span> <span class="k">import</span> <span class="n">QuantumCircuit</span><span class="p">,</span> <span class="n">ClassicalRegister</span><span class="p">,</span> <span class="n">QuantumRegister</span><span class="p">,</span> <span class="n">execute</span>

<span class="kn">from</span> <span class="nn">qiskit.tools.visualization</span> <span class="k">import</span> <span class="n">plot_histogram</span>
<span class="kn">from</span> <span class="nn">IPython.display</span> <span class="k">import</span> <span class="n">display</span><span class="p">,</span> <span class="n">Math</span><span class="p">,</span> <span class="n">Latex</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Quantum-Computing-and-the-Deutsch-Jozsa-Algorithm">Quantum Computing and the Deutsch-Jozsa Algorithm<a class="anchor-link" href="#Quantum-Computing-and-the-Deutsch-Jozsa-Algorithm">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Why-Quantum-Computing-?">Why Quantum Computing ?<a class="anchor-link" href="#Why-Quantum-Computing-?">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In 1981, the Nobel laureate Richard Feynman asked, “What kind of computer are we going to use to simulate physics?”</p>
<p><em>Nature isn’t classical, dammit, and if you want to make a simulation of Nature, you’d better make it quantum mechanical, and by golly it’s a wonderful problem, because it doesn’t look so easy.</em></p>
<p>Richard Feynman speech can be used to see how powerful quantum computing could be to let us understand more about our universe, since quantum physics try to explain and understand how our universe is built from the deepest subatomic dimensions to huge macroscopic phenomena. What can lead as to ask ourselves if our classical compurters are going to be able to solve and deal with problems that nature by essence shows to be a quantum complex behavior, that most likely are exponential problems for our classical computers, like the nitrogen-fixing process on agriculture, where dealing with several atoms interections, as the number of atoms grows the dimesion of our problem grows exponencially, what is impossible for a classical computer to solve nowdays.</p>
<p>So the question is, how quantum computers could solve these kind of problems some day ? With a different model of treating information closer with how our universe and nature behave, from the deepest levels and beyond.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Classical-Bit-vs-Qubit">Classical Bit vs Qubit<a class="anchor-link" href="#Classical-Bit-vs-Qubit">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Our classical computers, those that we've in home, desktops, notebooks, cellphones all of them in the deepest level stores the information as different sequences of <strong>0s</strong> and <strong>1s</strong>, so as <strong>0100100100</strong> where each entrie is either 0 or either 1. What makes a huge difference when we compare it with how the quantum computers stores information and work with it, where a state 0 or 1 can be seen as a unitary vector state $|\psi\rangle$ in a Hilbert space $\mathcal{H}$ or a Qubit, in the computational basis, defined as:</p>
$$\left|\psi\right\rangle = \alpha\left|0\right\rangle + \beta\left|1\right\rangle$$$$|\alpha|^2 + |\beta|^2 = 1$$<p><img src="data:image/png;base64,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" alt="image.png"></p>
<p>Where the scalars alpha and beta are used to see the amplitude of each state, or more generally, its probability to colapse over its respective state $|0\rangle$ or $|1\rangle$, which is like we could have all possible states at the same time, but we can only measure and see a small piece of this huge information.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Quantum-Superpostion-and-Entanglement">Quantum Superpostion and Entanglement<a class="anchor-link" href="#Quantum-Superpostion-and-Entanglement">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As we're dealing with quantum behavior some pretty important features of quantum mechanics that are used in quantum computing are the <strong>Quantum Superposition</strong> and the <strong>Quantum Entanglement</strong>. If were given to us a state $\psi$, when neither of its constants, lets say for example $\alpha$ and $\beta$, are null, we say that this state is in <strong>superpostion</strong>. More generally, which means that before a potential measure a phisical system is partially over all possible existants theoretical states.</p>
$$
|\psi\rangle = a_0|0\rangle + a_1|1\rangle + \dots + a_{n-1}|n-1 \rangle = \sum_{i=0}^{n-1}a_i|i\rangle
$$$$
\sum_{i = 0}^{n-1} |a_i|^2 = 1
$$<p>However when we measure it, it colapses to a unique state, so its like nature is doing a massive work, but it is willing to share with us just a small piece of it, a hint, for us to solve some very difficult problems.</p>
<p>The space of these vector states can be seen by tensor product of this system states, so if we've <strong>n</strong> components we can write those as</p>
$$
\begin{align*}
|\Psi\rangle &amp;= |\psi_0\rangle \otimes |\psi_1\rangle \otimes \dots \otimes |\psi_{n-1}\rangle\\
             &amp;= |\psi_0\rangle |\psi_1\rangle \dots |\psi_{n-1}\rangle\\
             &amp;= |\psi_0 \psi_1 \dots \psi_{n-1}\rangle
\end{align*}
$$<p>If a state can not be writen by the tensor product of other states we've that this states is <strong>entangled</strong>, so as the wellknown Bell-State</p>
$$
\begin{align*}
|\Psi\rangle = \frac{|00\rangle + |11\rangle}{\sqrt{2}}
\end{align*}
$$<p>Where if we measure one of the Qubits we know exactly the state of the other, even if the other Qubit is in the other side of the galaxy, with is forbidden by the theory of relativity, since it would be faster then the speed of light, which is known as the <em>EPR Paradox</em>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Programming-with-Quantum-Gates">Programming with Quantum Gates<a class="anchor-link" href="#Programming-with-Quantum-Gates">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>While in Classical Computers works by applying simple boolean operators like (NOT, NAND, XOR, AND, OR), Quantum Computers works Quantum Gates, which mathematically speaking are unitary operators, that manipulates our state over the bloch sphere, so let $\mathcal{U}$ be our unitary operator and $|\psi\rangle$ our qubit.</p>
$$
UU^\dagger = I
$$$$
|\psi\rangle \rightarrow \mathcal{U}|\psi\rangle
$$$$
|||\psi\rangle|| = ||\mathcal{U}|\psi\rangle|| = 1
$$<p>In this context the gates that we'll use are those that work in an unique qubit, therefore our operators will be defined by $M_{2x2}$ matrices over a state $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$, and some of those operators are the Pauli Matrices, which besides its importance all over quantum computing, they are going to have a great importance to the understanding of the Deutsch-Jozsa Algorithm.</p>
$$
\sigma_I = I = \begin{bmatrix}
                1 &amp; 0 \\
                0 &amp; 1
               \end{bmatrix}
$$$$
\sigma_X = X = \begin{bmatrix}
                0 &amp; 1 \\
                1 &amp; 0
               \end{bmatrix}
$$$$
\sigma_Y = Y = \begin{bmatrix}
                0 &amp; -i \\
                i &amp; 0
               \end{bmatrix}
$$$$
\sigma_Z = Z = \begin{bmatrix}
                1 &amp; 0 \\
                0 &amp; -1
               \end{bmatrix}
               \\
$$<p><img src="data:image/png;base64,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" alt="image.png"></p>
<p>As we already settled superposition is a important feature in quantum computing, how we can solve problems over multiple states at the same time, so if we've a state $|0\rangle$ or $|1\rangle$ and want to put it on superposition we can apply we one of the most common and important quantum gates, the Hadarmard Gate, given by the matrix</p>
$$
\begin{align*}
H &amp;= \frac{1}{\sqrt{2}} \begin{bmatrix}
                       1 &amp; 1\\
                       1 &amp; -1
                       \end{bmatrix}\\\\
  &amp;= \frac{|0\rangle + |1\rangle}{\sqrt{2}}\langle0| + \frac{|0\rangle - |1\rangle}{\sqrt{2}}\langle1|
\end{align*}
$$<p>Hence, if we apply this matrix on the states $|0\rangle$ or $|1\rangle$ we'll get the states $|+\rangle$ and $|-\rangle$ respectively</p>
$$
\begin{align*}
\\H|0\rangle = \frac{1}{\sqrt{2}} \begin{bmatrix}
                                   1 &amp; 1\\
                                   1 &amp; -1
                                \end{bmatrix} 
                                %
             \begin{bmatrix}
             1 \\
             0
             \end{bmatrix}
             =
             \frac{|0\rangle + |1\rangle}{\sqrt{2}}
             =
             |+\rangle
\\\\H|1\rangle = \frac{1}{\sqrt{2}} \begin{bmatrix}
                                   1 &amp; 1\\
                                   1 &amp; -1
                                \end{bmatrix} 
                                %
             \begin{bmatrix}
             0 \\
             1
             \end{bmatrix}
             =
             \frac{|0\rangle - |1\rangle}{\sqrt{2}}
             =
             |-\rangle
\end{align*}
$$<p>Which are the resultant states after we put them on superposition. And since $H$ = $H^\dagger$, when we apply $HH^\dagger|\psi\rangle = HH^\dagger|\psi\rangle = |\psi\rangle $, it restores it to the original input state.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="The-Deutsch-Jozsa-Algorithm">The Deutsch-Jozsa Algorithm<a class="anchor-link" href="#The-Deutsch-Jozsa-Algorithm">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The Deutsch-Jozsa Algorithm was one of the first algorithms to show a improvement over the classical solution to find whether a function is balanced or constant. Even though the algorithm does not has a important application in real life it show us in very simple way how this new kind of computing can improve our classical computers algorithm solutions.</p>
<p>The functions that will be considerend in this algorithm are those that maps a input $\{0, 1\}^{n}$ to an output $\{0, 1\}$, i.e, $\   \mathcal{f}:\ \{0, 1\}^n \mapsto \{0, 1\}$ , and a function is called baleced if exactly half of its inputs give us an output equal to <strong>0</strong> and the other half equals <strong>1</strong>.</p>
$$
\begin{align*}
Constant:\ &amp; f(0, 0) = 1 &amp;&amp; f(0, 1) = 1  &amp;&amp; f(1, 0) = 1 &amp;&amp; f(1, 1) = 1 \\
Constant:\ &amp; f(0, 0) = 0 &amp;&amp; f(0, 1) = 0  &amp;&amp; f(1, 0) = 0 &amp;&amp; f(1, 1) = 0 \\
Balanced:\ &amp; f(0, 0) = 1 &amp;&amp; f(0, 1) = 0  &amp;&amp; f(1, 0) = 1 &amp;&amp; f(1, 1) = 0 \\
Balanced:\ &amp; f(0, 0) = 0 &amp;&amp; f(0, 1) = 1  &amp;&amp; f(1, 0) = 0 &amp;&amp; f(1, 1) = 1 
\end{align*}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>However, even being the "Hello World" of the Quantum Algorithms, the The Deutsch-Jozsa Algorithm is not as simple as it looks like. Therefore, as we already discussed the quantum circuits works by applying several unitary matrices operations over a quantum state on the computational basis.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
$$
|0\rangle = \begin{bmatrix}
                1 \\
                0
            \end{bmatrix}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
$$
|1\rangle = \begin{bmatrix}
                0 \\
                1
            \end{bmatrix}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can apply our operations over several qubits, i.e, over the tensor product of simpler, in order to get more complex systems and inputs. Therefore we can introduce the Deutsch-Jozsa Algorithm Circuit.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><img src="data:image/png;base64,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" alt="image.png"></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Firstly</strong> we can itialize our register as the tensor product of <strong>n</strong> $|0\rangle$ states and one $|1\rangle$ that will be used to give us what is called a kick-back, therefore:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
$$
\begin{align*}
    |\psi_0\rangle &amp; =  |0\rangle^{\otimes n} \otimes |1\rangle\\
                   &amp; =  |0\rangle^{\otimes n} |1\rangle
\end{align*}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The <strong>second</strong> step is to put our state in superposition, by applying Hadarmard gates in our input as it follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
$$
\begin{align*}
    |\psi_1\rangle &amp; =  H^{\otimes n}|0\rangle^{\otimes n} \otimes H|1\rangle\\
                   &amp; =  H^{\otimes n}|0\rangle^{\otimes n} H|1\rangle\\
                   &amp; =  |+\rangle^{\otimes n}|-\rangle\\
                   &amp; = {\frac{1}{\sqrt{2^n}}}\sum_{x \in \{0, 1\}^{n}} |x\rangle\bigg(\frac{|0\rangle - |1\rangle}{\sqrt2}\bigg)
\end{align*}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>After that, the next step is to apply the $U_f$ oracle, which is the main function in our circuit that give us if the our input function is balanced or constant, but this result will not be observable yet.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
$$
\begin{align*}
    |\psi_2\rangle 
                   &amp; = {\frac{1}{\sqrt{2^n}}}\mathrm{U_f}\bigg(\sum_{x \in \{0, 1\}^{n}} |x\rangle\bigg(\frac{|0\rangle - |1\rangle}{\sqrt2}\bigg)\bigg)
\end{align*}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The function will not change the first <strong>n</strong> qubits, but the second one will be change as it follows:</p>
$$
\begin{align*}
    |\psi_2\rangle 
                   &amp; = {\frac{1}{\sqrt{2^n}}}\sum_{x \in \{0, 1\}^{n}} |x\rangle\bigg(\frac{|0 \oplus f(x)\rangle - |1 \oplus f(x)\rangle}{\sqrt2}\bigg)\\
                   &amp; \equiv {\frac{1}{\sqrt{2^n}}}\sum_{x \in \{0, 1\}^{n}} (-1)^{f(x)} |x\rangle\bigg(\frac{|0\rangle - |1\rangle}{\sqrt2}\bigg) &amp; \text{The kickback give us this formulation}\\
                   &amp; \equiv {\frac{1}{\sqrt{2^n}}}\sum_{x \in \{0, 1\}^{n}} (-1)^{f(x)} |x\rangle &amp;\text{            Ignoring the second qubit}\\
\end{align*}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now that we already have our $U_f$ oracle function output for the first <strong>n</strong> qubits remains to us only to apply the Hadamard Gate on it and to measure the result. The general formulation for applying the Hadarmard gate on n qubit on superposition is given by</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
$$
|\psi_3\rangle = \frac{1}{2^n}\sum_{x \in \{0, 1\}^n}(-1)^{f(x)}\sum_{z \in \{0, 1\}^n} (-1)^{\langle x, z\rangle}|x\rangle
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Then, when $f(x)$ is balance $z = |00000 \dots 0\rangle$ the inner procuct sum will cancel each other term by term, which will give us that the amplitude to find the result on the state $|0000 \dots 0\rangle$ is null. Otherwise, we have a constant function and the amplitude of $|0000 \dots 0\rangle$ after the result on the measurement is either 1 or -1, which is a 1 probability of finding it on the state $|0000 \dots 0\rangle$.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Example">Example<a class="anchor-link" href="#Example">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Lets do a small example to see how it work properly for one random function in the required format, so as</p>
$$
    f(0, 0) = 0\\
    f(0, 1) = 1\\
    f(1, 0) = 1\\
    f(0, 0) = 0
$$<p>We know that this is a balanced function, since it is a pretty small example, but the algorithm still blinded for it.</p>
<p>We will need three Qubits in our input, where there first two will be equal to $|0\rangle$ and the third one will be $|1\rangle$.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
$$
\begin{align*}
    |\psi_0\rangle &amp; =  |0\rangle^{\otimes 2} \otimes |1\rangle\\
                   &amp; =  |0\rangle^{\otimes 2} |1\rangle\\
                   &amp; =  |00\rangle|1\rangle
\end{align*}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now we must apply the Hadarmard Gates on it as it follow</p>
$$
\begin{align*}
    |\psi_1\rangle &amp; =  H^{\otimes 2}|00\rangle H|1\rangle\\
                   &amp; = |+\rangle^{\otimes 2}|-\rangle\\
                   &amp; = \bigg(\frac{|0\rangle + |1\rangle}{\sqrt{2}}\bigg)\otimes\bigg(\frac{|0\rangle + |1\rangle}{\sqrt{2}}\bigg)\otimes\bigg(\frac{|0\rangle - |1\rangle}{\sqrt{2}}\bigg)\\
                   &amp; = \frac{1}{2}\bigg(|00\rangle + |01\rangle + |10\rangle + |11\rangle\bigg)\otimes\bigg(\frac{|0\rangle - |1\rangle}{\sqrt{2}}\bigg)\\
                   &amp; = \frac{1}{2}\bigg(|00\rangle + |01\rangle + |10\rangle + |11\rangle\bigg)\bigg(\frac{|0\rangle - |1\rangle}{\sqrt{2}}\bigg)
\end{align*}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now that we've our state on superpostion we must apply the $U_f$ function on the state $|\psi_1\rangle$, so that</p>
$$
\begin{align*}
|\psi_2\rangle &amp; = \frac{1}{2}\bigg(|00\rangle + |01\rangle + |10\rangle + |11\rangle\bigg)U_f\bigg(\bigg(\frac{|0\rangle - |1\rangle}{\sqrt{2}}\bigg)\bigg)\\
               &amp; = \frac{1}{2\sqrt{2}} \sum_{x \in \{0, 1\}^2} |x\rangle \bigg(|0 \oplus f(x)\rangle - |1 \oplus f(x)\rangle\bigg)\\
               &amp; = \frac{1}{2\sqrt{2}}\bigg[|00\rangle \bigg(|0\rangle - |1\rangle\bigg) - |01\rangle \bigg(|0\rangle - |1\rangle\bigg) - |10\rangle \bigg(|0\rangle - |1\rangle\bigg) + |11\rangle \bigg(|0\rangle - |1\rangle\bigg)\bigg]
\end{align*}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now as we did at the explanation above we will ignore the last Qubit and evaluate our circuit only by the first <strong>n</strong> Qubits.</p>
$$
  |\psi_2\rangle = \frac{1}{2}\bigg[|00\rangle - |01\rangle - |10\rangle + |11\rangle\bigg]
$$<p>Then remain to us only to apply the Hadamard Gate on this state to get our result, in order to make it simpler we will use the matrix notation of the Hadamard $H^{\otimes 2}$ to get the computation result.</p>
$$
\begin{align*}
    |\psi_3\rangle &amp; =  H^{\otimes 2}|\psi_2\rangle\\ 
                &amp; = \begin{bmatrix}
                      1 &amp; 1 &amp; 1 &amp; 1\\
                      1 &amp; -1 &amp; 1 &amp; -1\\
                      1 &amp; 1 &amp; -1 &amp; -1\\
                      1 &amp; -1 &amp; -1 &amp; 1
                      \end{bmatrix}%
                      \frac{1}{2}
                      %
                     \begin{bmatrix}
                      1\\
                      -1\\
                      -1\\
                      1
                      \end{bmatrix}\\
                 &amp; = |11\rangle
\end{align*}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Where the measurement on the first two Qubits will be strictly different then $|00\rangle$, therefore our function is balanced, as expected.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Implemention">Implemention<a class="anchor-link" href="#Implemention">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now that we understand how the algorithm works and saw a small example we can use the Qiskit library to simulate it and observe the results, comparing it with our theoretical explanations.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="sd">&#39;&#39;&#39;</span>
<span class="sd">RANDOM EXAMPLE BASED ON IBM</span>
<span class="sd">QISKIT TUTORIAL EXAMPLE</span>
<span class="sd">reference: https://community.qiskit.org/textbook/ch-algorithms/deutsch-josza.html</span>
<span class="sd">&#39;&#39;&#39;</span>

<span class="c1">#n is the number of elements needed in the function input</span>
<span class="n">n</span> <span class="o">=</span> <span class="mi">5</span>

<span class="c1">#define the oracle type, i.e, if our function is constant or balanced</span>
<span class="n">oracle</span> <span class="o">=</span> <span class="s2">&quot;b&quot;</span>

<span class="c1">#if is balanced we define which of the vector 2**n will held</span>
<span class="c1">#the algorithm result</span>
<span class="k">if</span> <span class="n">oracle</span> <span class="o">==</span> <span class="s2">&quot;b&quot;</span><span class="p">:</span>
    <span class="n">b</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">random</span><span class="o">.</span><span class="n">randint</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">2</span><span class="o">**</span><span class="n">n</span><span class="p">)</span> 
    
<span class="c1">#if it&#39;s constant we set randomly if the results are 0 or 1</span>
<span class="k">if</span> <span class="n">oracle</span> <span class="o">==</span> <span class="s2">&quot;c&quot;</span><span class="p">:</span>
    <span class="n">c</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">random</span><span class="o">.</span><span class="n">randint</span><span class="p">(</span><span class="mi">2</span><span class="p">)</span>

<span class="c1">#set n_qbits as the number of quantum register on the input</span>
<span class="c1">#and the classical register as n_bits</span>
<span class="n">n_qbits</span> <span class="o">=</span> <span class="n">QuantumRegister</span><span class="p">(</span><span class="n">n</span><span class="o">+</span><span class="mi">1</span><span class="p">)</span>
<span class="n">n_bits</span> <span class="o">=</span> <span class="n">ClassicalRegister</span><span class="p">(</span><span class="n">n</span><span class="p">)</span>

<span class="c1">#build the circuit based on it</span>
<span class="n">djAlgCircuit</span> <span class="o">=</span> <span class="n">QuantumCircuit</span><span class="p">(</span><span class="n">n_qbits</span><span class="p">,</span> <span class="n">n_bits</span><span class="p">)</span>

<span class="c1">#as we need a |1&gt; qbit to do the kickback in our circuit</span>
<span class="c1">#we apply the X operator on the last |0&gt; qbit to flip its</span>
<span class="c1">#entrie and change it to |1&gt;</span>
<span class="n">djAlgCircuit</span><span class="o">.</span><span class="n">x</span><span class="p">(</span><span class="n">n_qbits</span><span class="p">[</span><span class="n">n</span><span class="p">])</span>

<span class="c1">#Apply this in order to viasualize our oracle on the </span>
<span class="c1">#circuit plot</span>

<span class="c1">#Apply the Hadarmard gates on the n qbits and put them</span>
<span class="c1">#on the superposition state</span>
<span class="n">djAlgCircuit</span><span class="o">.</span><span class="n">h</span><span class="p">(</span><span class="n">n_qbits</span><span class="p">)</span>    

<span class="n">djAlgCircuit</span><span class="o">.</span><span class="n">barrier</span><span class="p">()</span>

<span class="c1">#If it is constants just flip the value of the last qbit to 0 if c is one,</span>
<span class="c1">#Apply the identity otherwise</span>
<span class="c1">#If it is balanced we will shift the bits and apply the CNOT operator at the</span>
<span class="c1">#marked position b and the last qbit, it works like our $|y \oplus f(x)&gt;$</span>
<span class="k">if</span> <span class="n">oracle</span> <span class="o">==</span> <span class="s2">&quot;c&quot;</span><span class="p">:</span> 
    <span class="k">if</span> <span class="n">c</span> <span class="o">==</span> <span class="mi">1</span><span class="p">:</span>
        <span class="n">djAlgCircuit</span><span class="o">.</span><span class="n">x</span><span class="p">(</span><span class="n">n_qbits</span><span class="p">[</span><span class="n">n</span><span class="p">])</span>
    <span class="k">else</span><span class="p">:</span>
        <span class="n">djAlgCircuit</span><span class="o">.</span><span class="n">iden</span><span class="p">(</span><span class="n">n_qbits</span><span class="p">[</span><span class="n">n</span><span class="p">])</span>
<span class="k">else</span><span class="p">:</span>  
    <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">n</span><span class="p">):</span>
        <span class="k">if</span> <span class="p">(</span><span class="n">b</span> <span class="o">&amp;</span> <span class="p">(</span><span class="mi">1</span> <span class="o">&lt;&lt;</span> <span class="n">i</span><span class="p">)):</span>
            <span class="n">djAlgCircuit</span><span class="o">.</span><span class="n">cx</span><span class="p">(</span><span class="n">n_qbits</span><span class="p">[</span><span class="n">i</span><span class="p">],</span> <span class="n">n_qbits</span><span class="p">[</span><span class="n">n</span><span class="p">])</span>


<span class="n">djAlgCircuit</span><span class="o">.</span><span class="n">barrier</span><span class="p">()</span>

<span class="c1">#Apply the Hadamard gates to get our result</span>
<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">n</span><span class="p">):</span>
    <span class="n">djAlgCircuit</span><span class="o">.</span><span class="n">h</span><span class="p">(</span><span class="n">n_qbits</span><span class="p">[</span><span class="n">i</span><span class="p">])</span>

<span class="c1">#Measure the amplitude of the first n qbits</span>
<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">n</span><span class="p">):</span>
    <span class="n">djAlgCircuit</span><span class="o">.</span><span class="n">measure</span><span class="p">(</span><span class="n">n_qbits</span><span class="p">[</span><span class="n">i</span><span class="p">],</span> <span class="n">n_bits</span><span class="p">[</span><span class="n">i</span><span class="p">])</span>
    
<span class="n">backend</span> <span class="o">=</span> <span class="n">BasicAer</span><span class="o">.</span><span class="n">get_backend</span><span class="p">(</span><span class="s1">&#39;qasm_simulator&#39;</span><span class="p">)</span>
<span class="n">shots</span> <span class="o">=</span> <span class="mi">1024</span>
<span class="n">results</span> <span class="o">=</span> <span class="n">execute</span><span class="p">(</span><span class="n">djAlgCircuit</span><span class="p">,</span> <span class="n">backend</span><span class="o">=</span><span class="n">backend</span><span class="p">,</span> <span class="n">shots</span><span class="o">=</span><span class="n">shots</span><span class="p">)</span><span class="o">.</span><span class="n">result</span><span class="p">()</span>
<span class="n">answer</span> <span class="o">=</span> <span class="n">results</span><span class="o">.</span><span class="n">get_counts</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">djAlgCircuit</span><span class="o">.</span><span class="n">draw</span><span class="p">(</span><span class="n">output</span><span class="o">=</span><span class="s1">&#39;mpl&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[3]:</div>




<div class="output_png output_subarea output_execute_result">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAArUAAAFlCAYAAAD1dhDzAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADl0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uIDIuMS4xLCBodHRwOi8vbWF0cGxvdGxpYi5vcmcvAOZPmwAAIABJREFUeJzs3XlcVPX+P/DXwLDjxhC44JogOAKKG4YCbkWm0jUlzd1MROxa1k29dF2y3C5Xrbx5sXKpXK5AJl/Tq3gVytQuroVLaES4IOKCCiqyzO8PfkyOLHPQGT7nMK/n4+HjgZ8558xr5O2HN2c+54xKp9PpQERERESkYFaiAxARERERPSk2tURERESkeGxqiYiIiEjx2NQSERERkeKxqSUiIiIixWNTS0RERESKx6aWiIiIiBSPTS0RERERKR6bWiIiIiJSPDa1RERERKR4bGqJiIiISPHY1BIRERGR4rGpJSIiIiLFY1NLRERERIrHppaIiIiIFI9NLREREREpHptaIiIiIlI8NrVEREREpHhsaomIiIhI8djUEhEREZHisaklIiIiIsVjU0tEREREisemloiIiIgUTy06AFF9dfbs2RofX7VqFaZPn17jNt7e3qaMRDJirD4A1ggRUW3wTC2RIP/85z9FRyCZY40QEUnHppaIiIiIFI9NLREREREpHptaIkESEhJERyCZY40QEUnHppaIiIiIFI9NLZEgw4cPFx2BZI41QkQkHZtaIiIiIlI83qe2nnpjY90/58rRdf+cRGR6IuYP4MnnEJVKZZogtaDT6er8OYmoajxTSyRIdHS06Agkc6wRIiLp2NQSCWLsk6KIWCNERNKxqSUSJDg4WHQEkjnWCBGRdGxqiQTJy8sTHYFkjjVCRCQdm1oiIiIiUjw2tUSCdOzYUXQEkjnWCBGRdLylF5EgiYmJoiOQzLFGzKdNmzbo2bMn/P390bBhQzx48AAZGRk4evQojh07htLS0kr7zJs3DyqVCvPnz6/7wERkFJvaGty6dQuzZs3C119/jYKCAnTp0gVLly5F7969RUejemDu3Ll47733RMcgGWONmN6IESPw+uuvo0+fPtVuc+HCBcTFxeHjjz/G7du3AZQ3tPPnz0dpaSkSExPx888/11VkIpKITW01dDodwsPDcebMGcTGxqJ58+b4+OOP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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plot_histogram</span><span class="p">(</span><span class="n">answer</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[4]:</div>




<div class="output_png output_subarea output_execute_result">
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
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="sd">&#39;&#39;&#39;</span>
<span class="sd">CODE OF THE EXAMPLE</span>
<span class="sd">DESCRIBED ABOVE</span>

<span class="sd">f(0, 0) = 0 / f(0, 1) = 1 / f(1, 0) = 1 / f(1, 1) = 0</span>

<span class="sd">balanced function</span>
<span class="sd">&#39;&#39;&#39;</span>

<span class="n">size</span> <span class="o">=</span> <span class="mi">2</span>
<span class="n">m</span> <span class="o">=</span> <span class="mi">3</span>

<span class="c1">#Initialize registers</span>
<span class="n">qb_rg</span> <span class="o">=</span> <span class="n">QuantumRegister</span><span class="p">(</span><span class="n">size</span><span class="o">+</span><span class="mi">1</span><span class="p">)</span>
<span class="n">b_rg</span> <span class="o">=</span> <span class="n">ClassicalRegister</span><span class="p">(</span><span class="n">size</span><span class="p">)</span>

<span class="c1">#Build Circuit</span>
<span class="n">exDjCircuit</span> <span class="o">=</span> <span class="n">QuantumCircuit</span><span class="p">(</span><span class="n">qb_rg</span><span class="p">,</span> <span class="n">b_rg</span><span class="p">)</span>

<span class="c1">#Apply X gate on the last one</span>
<span class="n">exDjCircuit</span><span class="o">.</span><span class="n">x</span><span class="p">(</span><span class="n">qb_rg</span><span class="p">[</span><span class="n">size</span><span class="p">])</span>

<span class="c1">#Apply H gates</span>
<span class="n">exDjCircuit</span><span class="o">.</span><span class="n">h</span><span class="p">(</span><span class="n">qb_rg</span><span class="p">)</span>

<span class="n">exDjCircuit</span><span class="o">.</span><span class="n">barrier</span><span class="p">()</span>

<span class="c1">#Apply CNOT gate in function of m</span>
<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">size</span><span class="p">):</span>
    <span class="k">if</span> <span class="p">(</span><span class="n">m</span> <span class="o">&amp;</span> <span class="p">(</span><span class="mi">1</span> <span class="o">&lt;&lt;</span> <span class="n">i</span><span class="p">)):</span>
        <span class="n">exDjCircuit</span><span class="o">.</span><span class="n">cx</span><span class="p">(</span><span class="n">qb_rg</span><span class="p">[</span><span class="n">i</span><span class="p">],</span> <span class="n">qb_rg</span><span class="p">[</span><span class="n">size</span><span class="p">])</span>

<span class="n">exDjCircuit</span><span class="o">.</span><span class="n">barrier</span><span class="p">()</span>

<span class="c1">#Apply H gates</span>
<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">size</span><span class="p">):</span>
    <span class="n">exDjCircuit</span><span class="o">.</span><span class="n">h</span><span class="p">(</span><span class="n">qb_rg</span><span class="p">[</span><span class="n">i</span><span class="p">])</span>

<span class="c1">#Measure the first n qbits</span>
<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">size</span><span class="p">):</span>
    <span class="n">exDjCircuit</span><span class="o">.</span><span class="n">measure</span><span class="p">(</span><span class="n">qb_rg</span><span class="p">[</span><span class="n">i</span><span class="p">],</span> <span class="n">b_rg</span><span class="p">[</span><span class="n">i</span><span class="p">])</span>
    
<span class="n">bk</span> <span class="o">=</span> <span class="n">BasicAer</span><span class="o">.</span><span class="n">get_backend</span><span class="p">(</span><span class="s1">&#39;qasm_simulator&#39;</span><span class="p">)</span>
<span class="n">atp</span> <span class="o">=</span> <span class="mi">1024</span>
<span class="n">res</span> <span class="o">=</span> <span class="n">execute</span><span class="p">(</span><span class="n">exDjCircuit</span><span class="p">,</span> <span class="n">backend</span><span class="o">=</span><span class="n">bk</span><span class="p">,</span> <span class="n">shots</span><span class="o">=</span><span class="n">atp</span><span class="p">)</span><span class="o">.</span><span class="n">result</span><span class="p">()</span>
<span class="n">ans</span> <span class="o">=</span> <span class="n">res</span><span class="o">.</span><span class="n">get_counts</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">exDjCircuit</span><span class="o">.</span><span class="n">draw</span><span class="p">(</span><span class="n">output</span><span class="o">=</span><span class="s1">&#39;mpl&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[6]:</div>




<div class="output_png output_subarea output_execute_result">
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
<div class="prompt input_prompt">In&nbsp;[7]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plot_histogram</span><span class="p">(</span><span class="n">ans</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[7]:</div>




<div class="output_png output_subarea output_execute_result">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="References">References<a class="anchor-link" href="#References">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong><a href="https://en.wikipedia.org/wiki/Deutsch%E2%80%93Jozsa_algorithm">Wikipedia Deutsch-Jozsa Algorithm</a></strong>\
<strong><a href="https://medium.com/@jonathan_hui/qc-quantum-computing-series-10ddd7977abd">QC - Quantum Computing Series</a></strong>\
<strong><a href="https://community.qiskit.org/textbook/">Learn Quantum Computation using Qiskit</a></strong></p>

</div>
</div>
</div>
    </div>
  </div>
</body>

 


</html>
