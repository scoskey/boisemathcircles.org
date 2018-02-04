---
title: Falling chickens
tags: games
---

In this circle we investigated something called the "falling sand pile". But sand is boring, so instead we studied falling chickens! The primary rule of falling chickens is

<blockquote>
  When 4 chickens land in someone's backyard, they "break out" and go to the neighbors' yards instead.
</blockquote>

## Summary

In the process we discovered a new sequence: When the chickens fall on one square in the middle of the grid, how long does it take for the chicken fractal to spread n units up from the center? Our answer so far:

<blockquote>
  1, 4, 16, 44, 88, 144, 208, 320, 408, 512, 672, 788, 948, 1096, 1288, 1552.
</blockquote>

We have yet to analyze the pattern.

## Here is the game and questions

<style>
  /*PAGE STYLES*/
  .site-content .entry-content{
  	max-width:800px;
  }
  .callout {
    
      background-size: 100px;
      background-image: url("http://boisemathcircles.org/wp-content/uploads/2017/03/left-arrow-e1489246483147.png");
      padding: 20px;
      background-color: #b5e4ee;
      font-size: 20px;
      font-weight: bold;
      background-repeat: no-repeat;
      background-position: left 10px bottom 20px;
      padding-bottom: 50px;
  }
  /*GAME STYLES*/
  #game_board {
  	margin: 0 auto 20px auto;
  	float:left;
  	max-width:540px;
  }
  #game_settings{
  	float:right;
  	margin:0 auto 20px auto;
  	padding:30px 10px 10px 20px;
  	width:170px; /* SAM MODIFY from 210 */
  }
  .land-block{
  	float:left;
  	clear:left;
  }
  .land-box {
  	background: #efefef;
  	border:2px solid #333;
  	float: left;
  	width:70px;
  	height:70px;
  	max-width:70px;
  	max-height:70px;
  }
  .land-box p{
  	display:none;
  }
  .chicken-img {
  	width:70px;
  	height:70px;
  	max-width:70px;
  	max-height:70px;
  }
  .col-0{
  	clear:left;
  }

  .occupied{
  	background-size: 100% 100%;
      background-repeat: no-repeat;
  }
  [data-n="0"]{
  	background-color:#fff;
  }
  [data-n="1"]{
  	background-color:#0f0;
  	background-image: url("/assets/misc/one-chicken.png");					
  }
  [data-n="2"]{
  	background-color:rgb(255, 234, 101);
  	background-image: url("/assets/misc/two-chickens.png");					
  }
  [data-n="3"]{
  	background-color:#f00;
  	background-image: url("/assets/misc/three-chickens.png");					
  }
  /*Theme Fixes*/
  .entry-content ul > li {
  	background:none;
  	padding-left:inherit;
  }
  .entry-content{
  	position:relative;
  }

  /*DROPDOWN*/
  label.dropdown select {
  	padding: 0 10px;
  	background: #f8f8f8;
  	color: #444;
    	font-size:16px !important;
  	border: 1px solid #aaa;
  	border-radius: 0;
  	display: inline-block;
  	-webkit-appearance: none;
  	-moz-appearance: none;
  	appearance: none;
  	cursor: pointer;
  	outline: none;
  }
  label.dropdown select:-moz-focusring {
  	color: transparent;
  	text-shadow: 0 0 0 #444;
  }
  label.dropdown select::-ms-expand {
  	display: none;
  }

  label.dropdown { position: relative; }

  .switch-label{
  	float: left;
      height: 30px;
      display: inline-block;
      font-size: 15px;
      padding: 10px;
  }

  /* TOGGLE SWITCH*/
  #toggle-sound {
    position: absolute;
    margin-left: -9999px;
    visibility: hidden;
  }
  #toggle-sound + label {
   display:inline-block;
    position: relative;
    cursor: pointer;
    outline: none;
    user-select: none;
  }

  input#toggle-sound.cmn-toggle-round + label {
    padding: 2px;
    width: 60px;
    height: 30px;
    background-color: #dddddd;
    border-radius: 30px;
  }
  input#toggle-sound + label:before,
  input#toggle-sound + label:after {
    display: block;
    position: absolute;
    top: 1px;
    left: 1px;
    bottom: 1px;
    content: "";
  }
  input#toggle-sound + label:before {
    right: 1px;
    background-color: #f1f1f1;
    border-radius: 30px;
    transition: background 0.4s;
  }
  input#toggle-sound + label:after {
    width: 28px;
    background-color: #fff;
    border-radius: 100%;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
    transition: margin 0.4s;
  }
  input#toggle-sound:checked + label:before {
    background-color: #09347A;
  }
  input#toggle-sound:checked + label:after {
    margin-left: 30px;
  }



  /*! jQuery UI - v1.8.24 - 2012-09-28
  * https://github.com/jquery/jquery-ui
  * Includes: jquery.ui.core.css, jquery.ui.accordion.css, jquery.ui.autocomplete.css, jquery.ui.button.css, jquery.ui.datepicker.css, jquery.ui.dialog.css, jquery.ui.progressbar.css, jquery.ui.resizable.css, jquery.ui.selectable.css, jquery.ui.slider.css, jquery.ui.tabs.css, jquery.ui.theme.css
  * Copyright (c) 2012 AUTHORS.txt; Licensed MIT, GPL */

  /* Layout helpers
  ----------------------------------*/
  .ui-helper-hidden { display: none; }
  .ui-helper-hidden-accessible { position: absolute !important; clip: rect(1px 1px 1px 1px); clip: rect(1px,1px,1px,1px); }
  .ui-helper-reset { margin: 0; padding: 0; border: 0; outline: 0; line-height: 1.3; text-decoration: none; font-size: 100%; list-style: none; }
  .ui-helper-clearfix:before, .ui-helper-clearfix:after { content: ""; display: table; }
  .ui-helper-clearfix:after { clear: both; }
  .ui-helper-clearfix { zoom: 1; }
  .ui-helper-zfix { width: 100%; height: 100%; top: 0; left: 0; position: absolute; opacity: 0; filter:Alpha(Opacity=0); }


  /* Interaction Cues
  ----------------------------------*/
  .ui-state-disabled { cursor: default !important; }


  /* Icons
  ----------------------------------*/

  /* states and images */
  .ui-icon { display: block; text-indent: -99999px; overflow: hidden; background-repeat: no-repeat; }


  /* Misc visuals
  ----------------------------------*/

  /* Overlays */
  .ui-widget-overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }

  /* IE/Win - Fix animation bug - #4615 */
  .ui-accordion { width: 100%; }
  .ui-accordion .ui-accordion-header { cursor: pointer; position: relative; margin-top: 1px; zoom: 1; }
  .ui-accordion .ui-accordion-li-fix { display: inline; }
  .ui-accordion .ui-accordion-header-active { border-bottom: 0 !important; }
  .ui-accordion .ui-accordion-header a { display: block; font-size: 1em; padding: .5em .5em .5em .7em; }
  .ui-accordion-icons .ui-accordion-header a { padding-left: 2.2em; }
  .ui-accordion .ui-accordion-header .ui-icon { position: absolute; left: .5em; top: 50%; margin-top: -8px; }
  .ui-accordion .ui-accordion-content { padding: 1em 2.2em; border-top: 0; margin-top: -2px; position: relative; top: 1px; margin-bottom: 2px; overflow: auto; display: none; zoom: 1; }
  .ui-accordion .ui-accordion-content-active { display: block; }

  .ui-autocomplete { position: absolute; cursor: default; }	

  /* workarounds */
  * html .ui-autocomplete { width:1px; } /* without this, the menu expands to 100% in IE6 */

  /*
   * jQuery UI Menu 1.8.24
   *
   * Copyright 2010, AUTHORS.txt (http://jqueryui.com/about)
   * Dual licensed under the MIT or GPL Version 2 licenses.
   * http://jquery.org/license
   *
   * http://docs.jquery.com/UI/Menu#theming
   */
  .ui-menu {
  	list-style:none;
  	padding: 2px;
  	margin: 0;
  	display:block;
  	float: left;
  }
  .ui-menu .ui-menu {
  	margin-top: -3px;
  }
  .ui-menu .ui-menu-item {
  	margin:0;
  	padding: 0;
  	zoom: 1;
  	float: left;
  	clear: left;
  	width: 100%;
  }
  .ui-menu .ui-menu-item a {
  	text-decoration:none;
  	display:block;
  	padding:.2em .4em;
  	line-height:1.5;
  	zoom:1;
  }
  .ui-menu .ui-menu-item a.ui-state-hover,
  .ui-menu .ui-menu-item a.ui-state-active {
  	font-weight: normal;
  	margin: -1px;
  }

  .ui-button { display: inline-block; position: relative; padding: 0; margin-right: .1em; text-decoration: none !important; cursor: pointer; text-align: center; zoom: 1; overflow: visible; } /* the overflow property removes extra width in IE */
  .ui-button-icon-only { width: 2.2em; } /* to make room for the icon, a width needs to be set here */
  button.ui-button-icon-only { width: 2.4em; } /* button elements seem to need a little more width */
  .ui-button-icons-only { width: 3.4em; } 
  button.ui-button-icons-only { width: 3.7em; } 

  /*button text element */
  .ui-button .ui-button-text { display: block; line-height: 1.4;  }
  .ui-button-text-only .ui-button-text { padding: .4em 1em; }
  .ui-button-icon-only .ui-button-text, .ui-button-icons-only .ui-button-text { padding: .4em; text-indent: -9999999px; }
  .ui-button-text-icon-primary .ui-button-text, .ui-button-text-icons .ui-button-text { padding: .4em 1em .4em 2.1em; }
  .ui-button-text-icon-secondary .ui-button-text, .ui-button-text-icons .ui-button-text { padding: .4em 2.1em .4em 1em; }
  .ui-button-text-icons .ui-button-text { padding-left: 2.1em; padding-right: 2.1em; }
  /* no icon support for input elements, provide padding by default */
  input.ui-button { padding: .4em 1em; }

  /*button icon element(s) */
  .ui-button-icon-only .ui-icon, .ui-button-text-icon-primary .ui-icon, .ui-button-text-icon-secondary .ui-icon, .ui-button-text-icons .ui-icon, .ui-button-icons-only .ui-icon { position: absolute; top: 50%; margin-top: -8px; }
  .ui-button-icon-only .ui-icon { left: 50%; margin-left: -8px; }
  .ui-button-text-icon-primary .ui-button-icon-primary, .ui-button-text-icons .ui-button-icon-primary, .ui-button-icons-only .ui-button-icon-primary { left: .5em; }
  .ui-button-text-icon-secondary .ui-button-icon-secondary, .ui-button-text-icons .ui-button-icon-secondary, .ui-button-icons-only .ui-button-icon-secondary { right: .5em; }
  .ui-button-text-icons .ui-button-icon-secondary, .ui-button-icons-only .ui-button-icon-secondary { right: .5em; }

  /*button sets*/
  .ui-buttonset { margin-right: 7px; }
  .ui-buttonset .ui-button { margin-left: 0; margin-right: -.3em; }

  /* workarounds */
  button.ui-button::-moz-focus-inner { border: 0; padding: 0; } /* reset extra padding in Firefox */

  .ui-datepicker { width: 17em; padding: .2em .2em 0; display: none; }
  .ui-datepicker .ui-datepicker-header { position:relative; padding:.2em 0; }
  .ui-datepicker .ui-datepicker-prev, .ui-datepicker .ui-datepicker-next { position:absolute; top: 2px; width: 1.8em; height: 1.8em; }
  .ui-datepicker .ui-datepicker-prev-hover, .ui-datepicker .ui-datepicker-next-hover { top: 1px; }
  .ui-datepicker .ui-datepicker-prev { left:2px; }
  .ui-datepicker .ui-datepicker-next { right:2px; }
  .ui-datepicker .ui-datepicker-prev-hover { left:1px; }
  .ui-datepicker .ui-datepicker-next-hover { right:1px; }
  .ui-datepicker .ui-datepicker-prev span, .ui-datepicker .ui-datepicker-next span { display: block; position: absolute; left: 50%; margin-left: -8px; top: 50%; margin-top: -8px;  }
  .ui-datepicker .ui-datepicker-title { margin: 0 2.3em; line-height: 1.8em; text-align: center; }
  .ui-datepicker .ui-datepicker-title select { font-size:1em; margin:1px 0; }
  .ui-datepicker select.ui-datepicker-month-year {width: 100%;}
  .ui-datepicker select.ui-datepicker-month, 
  .ui-datepicker select.ui-datepicker-year { width: 49%;}
  .ui-datepicker table {width: 100%; font-size: .9em; border-collapse: collapse; margin:0 0 .4em; }
  .ui-datepicker th { padding: .7em .3em; text-align: center; font-weight: bold; border: 0;  }
  .ui-datepicker td { border: 0; padding: 1px; }
  .ui-datepicker td span, .ui-datepicker td a { display: block; padding: .2em; text-align: right; text-decoration: none; }
  .ui-datepicker .ui-datepicker-buttonpane { background-image: none; margin: .7em 0 0 0; padding:0 .2em; border-left: 0; border-right: 0; border-bottom: 0; }
  .ui-datepicker .ui-datepicker-buttonpane button { float: right; margin: .5em .2em .4em; cursor: pointer; padding: .2em .6em .3em .6em; width:auto; overflow:visible; }
  .ui-datepicker .ui-datepicker-buttonpane button.ui-datepicker-current { float:left; }

  /* with multiple calendars */
  .ui-datepicker.ui-datepicker-multi { width:auto; }
  .ui-datepicker-multi .ui-datepicker-group { float:left; }
  .ui-datepicker-multi .ui-datepicker-group table { width:95%; margin:0 auto .4em; }
  .ui-datepicker-multi-2 .ui-datepicker-group { width:50%; }
  .ui-datepicker-multi-3 .ui-datepicker-group { width:33.3%; }
  .ui-datepicker-multi-4 .ui-datepicker-group { width:25%; }
  .ui-datepicker-multi .ui-datepicker-group-last .ui-datepicker-header { border-left-width:0; }
  .ui-datepicker-multi .ui-datepicker-group-middle .ui-datepicker-header { border-left-width:0; }
  .ui-datepicker-multi .ui-datepicker-buttonpane { clear:left; }
  .ui-datepicker-row-break { clear:both; width:100%; font-size:0em; }


  /* RTL support */
  .ui-datepicker-rtl { direction: rtl; }
  .ui-datepicker-rtl .ui-datepicker-prev { right: 2px; left: auto; }
  .ui-datepicker-rtl .ui-datepicker-next { left: 2px; right: auto; }
  .ui-datepicker-rtl .ui-datepicker-prev:hover { right: 1px; left: auto; }
  .ui-datepicker-rtl .ui-datepicker-next:hover { left: 1px; right: auto; }
  .ui-datepicker-rtl .ui-datepicker-buttonpane { clear:right; }
  .ui-datepicker-rtl .ui-datepicker-buttonpane button { float: left; }
  .ui-datepicker-rtl .ui-datepicker-buttonpane button.ui-datepicker-current { float:right; }
  .ui-datepicker-rtl .ui-datepicker-group { float:right; }
  .ui-datepicker-rtl .ui-datepicker-group-last .ui-datepicker-header { border-right-width:0; border-left-width:1px; }
  .ui-datepicker-rtl .ui-datepicker-group-middle .ui-datepicker-header { border-right-width:0; border-left-width:1px; }

  /* IE6 IFRAME FIX (taken from datepicker 1.5.3 */
  .ui-datepicker-cover {
      position: absolute; /*must have*/
      z-index: -1; /*must have*/
      filter: mask(); /*must have*/
      top: -4px; /*must have*/
      left: -4px; /*must have*/
      width: 200px; /*must have*/
      height: 200px; /*must have*/
  }
  .ui-dialog { position: absolute; padding: .2em; width: 300px; overflow: hidden; }
  .ui-dialog .ui-dialog-titlebar { padding: .4em 1em; position: relative;  }
  .ui-dialog .ui-dialog-title { float: left; margin: .1em 16px .1em 0; } 
  .ui-dialog .ui-dialog-titlebar-close { position: absolute; right: .3em; top: 50%; width: 19px; margin: -10px 0 0 0; padding: 1px; height: 18px; }
  .ui-dialog .ui-dialog-titlebar-close span { display: block; margin: 1px; }
  .ui-dialog .ui-dialog-titlebar-close:hover, .ui-dialog .ui-dialog-titlebar-close:focus { padding: 0; }
  .ui-dialog .ui-dialog-content { position: relative; border: 0; padding: .5em 1em; background: none; overflow: auto; zoom: 1; }
  .ui-dialog .ui-dialog-buttonpane { text-align: left; border-width: 1px 0 0 0; background-image: none; margin: .5em 0 0 0; padding: .3em 1em .5em .4em; }
  .ui-dialog .ui-dialog-buttonpane .ui-dialog-buttonset { float: right; }
  .ui-dialog .ui-dialog-buttonpane button { margin: .5em .4em .5em 0; cursor: pointer; }
  .ui-dialog .ui-resizable-se { width: 14px; height: 14px; right: 3px; bottom: 3px; }
  .ui-draggable .ui-dialog-titlebar { cursor: move; }

  .ui-progressbar { height:2em; text-align: left; overflow: hidden; }
  .ui-progressbar .ui-progressbar-value {margin: -1px; height:100%; }
  .ui-resizable { position: relative;}
  .ui-resizable-handle { position: absolute;font-size: 0.1px; display: block; }
  .ui-resizable-disabled .ui-resizable-handle, .ui-resizable-autohide .ui-resizable-handle { display: none; }
  .ui-resizable-n { cursor: n-resize; height: 7px; width: 100%; top: -5px; left: 0; }
  .ui-resizable-s { cursor: s-resize; height: 7px; width: 100%; bottom: -5px; left: 0; }
  .ui-resizable-e { cursor: e-resize; width: 7px; right: -5px; top: 0; height: 100%; }
  .ui-resizable-w { cursor: w-resize; width: 7px; left: -5px; top: 0; height: 100%; }
  .ui-resizable-se { cursor: se-resize; width: 12px; height: 12px; right: 1px; bottom: 1px; }
  .ui-resizable-sw { cursor: sw-resize; width: 9px; height: 9px; left: -5px; bottom: -5px; }
  .ui-resizable-nw { cursor: nw-resize; width: 9px; height: 9px; left: -5px; top: -5px; }
  .ui-resizable-ne { cursor: ne-resize; width: 9px; height: 9px; right: -5px; top: -5px;}
  .ui-selectable-helper { position: absolute; z-index: 100; border:1px dotted black; }

  .ui-slider { position: relative; text-align: left; }
  .ui-slider .ui-slider-handle { position: absolute; z-index: 2; width: 1.2em; height: 1.2em; cursor: default; }
  .ui-slider .ui-slider-range { position: absolute; z-index: 1; font-size: .7em; display: block; border: 0; background-position: 0 0; }

  .ui-slider-horizontal { height: .8em; }
  .ui-slider-horizontal .ui-slider-handle { top: -.3em; margin-left: -.6em; }
  .ui-slider-horizontal .ui-slider-range { top: 0; height: 100%; }
  .ui-slider-horizontal .ui-slider-range-min { left: 0; }
  .ui-slider-horizontal .ui-slider-range-max { right: 0; }

  .ui-slider-vertical { width: .8em; height: 100px; }
  .ui-slider-vertical .ui-slider-handle { left: -.3em; margin-left: 0; margin-bottom: -.6em; }
  .ui-slider-vertical .ui-slider-range { left: 0; width: 100%; }
  .ui-slider-vertical .ui-slider-range-min { bottom: 0; }
  .ui-slider-vertical .ui-slider-range-max { top: 0; }
  .ui-tabs { position: relative; padding: .2em; zoom: 1; } /* position: relative prevents IE scroll bug (element with position: relative inside container with overflow: auto appear as "fixed") */
  .ui-tabs .ui-tabs-nav { margin: 0; padding: .2em .2em 0; }
  .ui-tabs .ui-tabs-nav li { list-style: none; float: left; position: relative; top: 1px; margin: 0 .2em 1px 0; border-bottom: 0 !important; padding: 0; white-space: nowrap; }
  .ui-tabs .ui-tabs-nav li a { float: left; padding: .5em 1em; text-decoration: none; }
  .ui-tabs .ui-tabs-nav li.ui-tabs-selected { margin-bottom: 0; padding-bottom: 1px; }
  .ui-tabs .ui-tabs-nav li.ui-tabs-selected a, .ui-tabs .ui-tabs-nav li.ui-state-disabled a, .ui-tabs .ui-tabs-nav li.ui-state-processing a { cursor: text; }
  .ui-tabs .ui-tabs-nav li a, .ui-tabs.ui-tabs-collapsible .ui-tabs-nav li.ui-tabs-selected a { cursor: pointer; } /* first selector in group seems obsolete, but required to overcome bug in Opera applying cursor: text overall if defined elsewhere... */
  .ui-tabs .ui-tabs-panel { display: block; border-width: 0; padding: 1em 1.4em; background: none; }
  .ui-tabs .ui-tabs-hide { display: none !important; }

  /* Component containers
  ----------------------------------*/
  .ui-widget { font-family: Verdana,Arial,sans-serif/*{ffDefault}*/; font-size: 1.1em/*{fsDefault}*/; }
  .ui-widget .ui-widget { font-size: 1em; }
  .ui-widget input, .ui-widget select, .ui-widget textarea, .ui-widget button { font-family: Verdana,Arial,sans-serif/*{ffDefault}*/; font-size: 1em; }
  .ui-widget-content { border: 1px solid #aaaaaa/*{borderColorContent}*/; background: #ffffff/*{bgColorContent}*/ url(images/ui-bg_flat_75_ffffff_40x100.png)/*{bgImgUrlContent}*/ 50%/*{bgContentXPos}*/ 50%/*{bgContentYPos}*/ repeat-x/*{bgContentRepeat}*/; color: #222222/*{fcContent}*/; }
  .ui-widget-content a { color: #222222/*{fcContent}*/; }
  .ui-widget-header { border: 1px solid #aaaaaa/*{borderColorHeader}*/; background: #cccccc/*{bgColorHeader}*/ url(images/ui-bg_highlight-soft_75_cccccc_1x100.png)/*{bgImgUrlHeader}*/ 50%/*{bgHeaderXPos}*/ 50%/*{bgHeaderYPos}*/ repeat-x/*{bgHeaderRepeat}*/; color: #222222/*{fcHeader}*/; font-weight: bold; }
  .ui-widget-header a { color: #222222/*{fcHeader}*/; }

  /* Interaction states
  ----------------------------------*/
  .ui-state-default, .ui-widget-content .ui-state-default, .ui-widget-header .ui-state-default { border: 1px solid #d3d3d3/*{borderColorDefault}*/; background: #e6e6e6/*{bgColorDefault}*/ url(images/ui-bg_glass_75_e6e6e6_1x400.png)/*{bgImgUrlDefault}*/ 50%/*{bgDefaultXPos}*/ 50%/*{bgDefaultYPos}*/ repeat-x/*{bgDefaultRepeat}*/; font-weight: normal/*{fwDefault}*/; color: #555555/*{fcDefault}*/; }
  .ui-state-default a, .ui-state-default a:link, .ui-state-default a:visited { color: #555555/*{fcDefault}*/; text-decoration: none; }
  .ui-state-hover, .ui-widget-content .ui-state-hover, .ui-widget-header .ui-state-hover, .ui-state-focus, .ui-widget-content .ui-state-focus, .ui-widget-header .ui-state-focus { border: 1px solid #999999/*{borderColorHover}*/; background: #dadada/*{bgColorHover}*/ url(images/ui-bg_glass_75_dadada_1x400.png)/*{bgImgUrlHover}*/ 50%/*{bgHoverXPos}*/ 50%/*{bgHoverYPos}*/ repeat-x/*{bgHoverRepeat}*/; font-weight: normal/*{fwDefault}*/; color: #212121/*{fcHover}*/; }
  .ui-state-hover a, .ui-state-hover a:hover { color: #212121/*{fcHover}*/; text-decoration: none; }
  .ui-state-active, .ui-widget-content .ui-state-active, .ui-widget-header .ui-state-active { border: 1px solid #aaaaaa/*{borderColorActive}*/; background: #ffffff/*{bgColorActive}*/ url(images/ui-bg_glass_65_ffffff_1x400.png)/*{bgImgUrlActive}*/ 50%/*{bgActiveXPos}*/ 50%/*{bgActiveYPos}*/ repeat-x/*{bgActiveRepeat}*/; font-weight: normal/*{fwDefault}*/; color: #212121/*{fcActive}*/; }
  .ui-state-active a, .ui-state-active a:link, .ui-state-active a:visited { color: #212121/*{fcActive}*/; text-decoration: none; }
  .ui-widget :active { outline: none; }

  /* Interaction Cues
  ----------------------------------*/
  .ui-state-highlight, .ui-widget-content .ui-state-highlight, .ui-widget-header .ui-state-highlight  {border: 1px solid #fcefa1/*{borderColorHighlight}*/; background: #fbf9ee/*{bgColorHighlight}*/ url(images/ui-bg_glass_55_fbf9ee_1x400.png)/*{bgImgUrlHighlight}*/ 50%/*{bgHighlightXPos}*/ 50%/*{bgHighlightYPos}*/ repeat-x/*{bgHighlightRepeat}*/; color: #363636/*{fcHighlight}*/; }
  .ui-state-highlight a, .ui-widget-content .ui-state-highlight a,.ui-widget-header .ui-state-highlight a { color: #363636/*{fcHighlight}*/; }
  .ui-state-error, .ui-widget-content .ui-state-error, .ui-widget-header .ui-state-error {border: 1px solid #cd0a0a/*{borderColorError}*/; background: #fef1ec/*{bgColorError}*/ url(images/ui-bg_glass_95_fef1ec_1x400.png)/*{bgImgUrlError}*/ 50%/*{bgErrorXPos}*/ 50%/*{bgErrorYPos}*/ repeat-x/*{bgErrorRepeat}*/; color: #cd0a0a/*{fcError}*/; }
  .ui-state-error a, .ui-widget-content .ui-state-error a, .ui-widget-header .ui-state-error a { color: #cd0a0a/*{fcError}*/; }
  .ui-state-error-text, .ui-widget-content .ui-state-error-text, .ui-widget-header .ui-state-error-text { color: #cd0a0a/*{fcError}*/; }
  .ui-priority-primary, .ui-widget-content .ui-priority-primary, .ui-widget-header .ui-priority-primary { font-weight: bold; }
  .ui-priority-secondary, .ui-widget-content .ui-priority-secondary,  .ui-widget-header .ui-priority-secondary { opacity: .7; filter:Alpha(Opacity=70); font-weight: normal; }
  .ui-state-disabled, .ui-widget-content .ui-state-disabled, .ui-widget-header .ui-state-disabled { opacity: .35; filter:Alpha(Opacity=35); background-image: none; }

  /* Icons
  ----------------------------------*/

  /* states and images */
  .ui-icon { width: 16px; height: 16px; background-image: url(images/ui-icons_222222_256x240.png)/*{iconsContent}*/; }
  .ui-widget-content .ui-icon {background-image: url(images/ui-icons_222222_256x240.png)/*{iconsContent}*/; }
  .ui-widget-header .ui-icon {background-image: url(images/ui-icons_222222_256x240.png)/*{iconsHeader}*/; }
  .ui-state-default .ui-icon { background-image: url(images/ui-icons_888888_256x240.png)/*{iconsDefault}*/; }
  .ui-state-hover .ui-icon, .ui-state-focus .ui-icon {background-image: url(images/ui-icons_454545_256x240.png)/*{iconsHover}*/; }
  .ui-state-active .ui-icon {background-image: url(images/ui-icons_454545_256x240.png)/*{iconsActive}*/; }
  .ui-state-highlight .ui-icon {background-image: url(images/ui-icons_2e83ff_256x240.png)/*{iconsHighlight}*/; }
  .ui-state-error .ui-icon, .ui-state-error-text .ui-icon {background-image: url(images/ui-icons_cd0a0a_256x240.png)/*{iconsError}*/; }

  /* positioning */
  .ui-icon-carat-1-n { background-position: 0 0; }
  .ui-icon-carat-1-ne { background-position: -16px 0; }
  .ui-icon-carat-1-e { background-position: -32px 0; }
  .ui-icon-carat-1-se { background-position: -48px 0; }
  .ui-icon-carat-1-s { background-position: -64px 0; }
  .ui-icon-carat-1-sw { background-position: -80px 0; }
  .ui-icon-carat-1-w { background-position: -96px 0; }
  .ui-icon-carat-1-nw { background-position: -112px 0; }
  .ui-icon-carat-2-n-s { background-position: -128px 0; }
  .ui-icon-carat-2-e-w { background-position: -144px 0; }
  .ui-icon-triangle-1-n { background-position: 0 -16px; }
  .ui-icon-triangle-1-ne { background-position: -16px -16px; }
  .ui-icon-triangle-1-e { background-position: -32px -16px; }
  .ui-icon-triangle-1-se { background-position: -48px -16px; }
  .ui-icon-triangle-1-s { background-position: -64px -16px; }
  .ui-icon-triangle-1-sw { background-position: -80px -16px; }
  .ui-icon-triangle-1-w { background-position: -96px -16px; }
  .ui-icon-triangle-1-nw { background-position: -112px -16px; }
  .ui-icon-triangle-2-n-s { background-position: -128px -16px; }
  .ui-icon-triangle-2-e-w { background-position: -144px -16px; }
  .ui-icon-arrow-1-n { background-position: 0 -32px; }
  .ui-icon-arrow-1-ne { background-position: -16px -32px; }
  .ui-icon-arrow-1-e { background-position: -32px -32px; }
  .ui-icon-arrow-1-se { background-position: -48px -32px; }
  .ui-icon-arrow-1-s { background-position: -64px -32px; }
  .ui-icon-arrow-1-sw { background-position: -80px -32px; }
  .ui-icon-arrow-1-w { background-position: -96px -32px; }
  .ui-icon-arrow-1-nw { background-position: -112px -32px; }
  .ui-icon-arrow-2-n-s { background-position: -128px -32px; }
  .ui-icon-arrow-2-ne-sw { background-position: -144px -32px; }
  .ui-icon-arrow-2-e-w { background-position: -160px -32px; }
  .ui-icon-arrow-2-se-nw { background-position: -176px -32px; }
  .ui-icon-arrowstop-1-n { background-position: -192px -32px; }
  .ui-icon-arrowstop-1-e { background-position: -208px -32px; }
  .ui-icon-arrowstop-1-s { background-position: -224px -32px; }
  .ui-icon-arrowstop-1-w { background-position: -240px -32px; }
  .ui-icon-arrowthick-1-n { background-position: 0 -48px; }
  .ui-icon-arrowthick-1-ne { background-position: -16px -48px; }
  .ui-icon-arrowthick-1-e { background-position: -32px -48px; }
  .ui-icon-arrowthick-1-se { background-position: -48px -48px; }
  .ui-icon-arrowthick-1-s { background-position: -64px -48px; }
  .ui-icon-arrowthick-1-sw { background-position: -80px -48px; }
  .ui-icon-arrowthick-1-w { background-position: -96px -48px; }
  .ui-icon-arrowthick-1-nw { background-position: -112px -48px; }
  .ui-icon-arrowthick-2-n-s { background-position: -128px -48px; }
  .ui-icon-arrowthick-2-ne-sw { background-position: -144px -48px; }
  .ui-icon-arrowthick-2-e-w { background-position: -160px -48px; }
  .ui-icon-arrowthick-2-se-nw { background-position: -176px -48px; }
  .ui-icon-arrowthickstop-1-n { background-position: -192px -48px; }
  .ui-icon-arrowthickstop-1-e { background-position: -208px -48px; }
  .ui-icon-arrowthickstop-1-s { background-position: -224px -48px; }
  .ui-icon-arrowthickstop-1-w { background-position: -240px -48px; }
  .ui-icon-arrowreturnthick-1-w { background-position: 0 -64px; }
  .ui-icon-arrowreturnthick-1-n { background-position: -16px -64px; }
  .ui-icon-arrowreturnthick-1-e { background-position: -32px -64px; }
  .ui-icon-arrowreturnthick-1-s { background-position: -48px -64px; }
  .ui-icon-arrowreturn-1-w { background-position: -64px -64px; }
  .ui-icon-arrowreturn-1-n { background-position: -80px -64px; }
  .ui-icon-arrowreturn-1-e { background-position: -96px -64px; }
  .ui-icon-arrowreturn-1-s { background-position: -112px -64px; }
  .ui-icon-arrowrefresh-1-w { background-position: -128px -64px; }
  .ui-icon-arrowrefresh-1-n { background-position: -144px -64px; }
  .ui-icon-arrowrefresh-1-e { background-position: -160px -64px; }
  .ui-icon-arrowrefresh-1-s { background-position: -176px -64px; }
  .ui-icon-arrow-4 { background-position: 0 -80px; }
  .ui-icon-arrow-4-diag { background-position: -16px -80px; }
  .ui-icon-extlink { background-position: -32px -80px; }
  .ui-icon-newwin { background-position: -48px -80px; }
  .ui-icon-refresh { background-position: -64px -80px; }
  .ui-icon-shuffle { background-position: -80px -80px; }
  .ui-icon-transfer-e-w { background-position: -96px -80px; }
  .ui-icon-transferthick-e-w { background-position: -112px -80px; }
  .ui-icon-folder-collapsed { background-position: 0 -96px; }
  .ui-icon-folder-open { background-position: -16px -96px; }
  .ui-icon-document { background-position: -32px -96px; }
  .ui-icon-document-b { background-position: -48px -96px; }
  .ui-icon-note { background-position: -64px -96px; }
  .ui-icon-mail-closed { background-position: -80px -96px; }
  .ui-icon-mail-open { background-position: -96px -96px; }
  .ui-icon-suitcase { background-position: -112px -96px; }
  .ui-icon-comment { background-position: -128px -96px; }
  .ui-icon-person { background-position: -144px -96px; }
  .ui-icon-print { background-position: -160px -96px; }
  .ui-icon-trash { background-position: -176px -96px; }
  .ui-icon-locked { background-position: -192px -96px; }
  .ui-icon-unlocked { background-position: -208px -96px; }
  .ui-icon-bookmark { background-position: -224px -96px; }
  .ui-icon-tag { background-position: -240px -96px; }
  .ui-icon-home { background-position: 0 -112px; }
  .ui-icon-flag { background-position: -16px -112px; }
  .ui-icon-calendar { background-position: -32px -112px; }
  .ui-icon-cart { background-position: -48px -112px; }
  .ui-icon-pencil { background-position: -64px -112px; }
  .ui-icon-clock { background-position: -80px -112px; }
  .ui-icon-disk { background-position: -96px -112px; }
  .ui-icon-calculator { background-position: -112px -112px; }
  .ui-icon-zoomin { background-position: -128px -112px; }
  .ui-icon-zoomout { background-position: -144px -112px; }
  .ui-icon-search { background-position: -160px -112px; }
  .ui-icon-wrench { background-position: -176px -112px; }
  .ui-icon-gear { background-position: -192px -112px; }
  .ui-icon-heart { background-position: -208px -112px; }
  .ui-icon-star { background-position: -224px -112px; }
  .ui-icon-link { background-position: -240px -112px; }
  .ui-icon-cancel { background-position: 0 -128px; }
  .ui-icon-plus { background-position: -16px -128px; }
  .ui-icon-plusthick { background-position: -32px -128px; }
  .ui-icon-minus { background-position: -48px -128px; }
  .ui-icon-minusthick { background-position: -64px -128px; }
  .ui-icon-close { background-position: -80px -128px; }
  .ui-icon-closethick { background-position: -96px -128px; }
  .ui-icon-key { background-position: -112px -128px; }
  .ui-icon-lightbulb { background-position: -128px -128px; }
  .ui-icon-scissors { background-position: -144px -128px; }
  .ui-icon-clipboard { background-position: -160px -128px; }
  .ui-icon-copy { background-position: -176px -128px; }
  .ui-icon-contact { background-position: -192px -128px; }
  .ui-icon-image { background-position: -208px -128px; }
  .ui-icon-video { background-position: -224px -128px; }
  .ui-icon-script { background-position: -240px -128px; }
  .ui-icon-alert { background-position: 0 -144px; }
  .ui-icon-info { background-position: -16px -144px; }
  .ui-icon-notice { background-position: -32px -144px; }
  .ui-icon-help { background-position: -48px -144px; }
  .ui-icon-check { background-position: -64px -144px; }
  .ui-icon-bullet { background-position: -80px -144px; }
  .ui-icon-radio-off { background-position: -96px -144px; }
  .ui-icon-radio-on { background-position: -112px -144px; }
  .ui-icon-pin-w { background-position: -128px -144px; }
  .ui-icon-pin-s { background-position: -144px -144px; }
  .ui-icon-play { background-position: 0 -160px; }
  .ui-icon-pause { background-position: -16px -160px; }
  .ui-icon-seek-next { background-position: -32px -160px; }
  .ui-icon-seek-prev { background-position: -48px -160px; }
  .ui-icon-seek-end { background-position: -64px -160px; }
  .ui-icon-seek-start { background-position: -80px -160px; }
  /* ui-icon-seek-first is deprecated, use ui-icon-seek-start instead */
  .ui-icon-seek-first { background-position: -80px -160px; }
  .ui-icon-stop { background-position: -96px -160px; }
  .ui-icon-eject { background-position: -112px -160px; }
  .ui-icon-volume-off { background-position: -128px -160px; }
  .ui-icon-volume-on { background-position: -144px -160px; }
  .ui-icon-power { background-position: 0 -176px; }
  .ui-icon-signal-diag { background-position: -16px -176px; }
  .ui-icon-signal { background-position: -32px -176px; }
  .ui-icon-battery-0 { background-position: -48px -176px; }
  .ui-icon-battery-1 { background-position: -64px -176px; }
  .ui-icon-battery-2 { background-position: -80px -176px; }
  .ui-icon-battery-3 { background-position: -96px -176px; }
  .ui-icon-circle-plus { background-position: 0 -192px; }
  .ui-icon-circle-minus { background-position: -16px -192px; }
  .ui-icon-circle-close { background-position: -32px -192px; }
  .ui-icon-circle-triangle-e { background-position: -48px -192px; }
  .ui-icon-circle-triangle-s { background-position: -64px -192px; }
  .ui-icon-circle-triangle-w { background-position: -80px -192px; }
  .ui-icon-circle-triangle-n { background-position: -96px -192px; }
  .ui-icon-circle-arrow-e { background-position: -112px -192px; }
  .ui-icon-circle-arrow-s { background-position: -128px -192px; }
  .ui-icon-circle-arrow-w { background-position: -144px -192px; }
  .ui-icon-circle-arrow-n { background-position: -160px -192px; }
  .ui-icon-circle-zoomin { background-position: -176px -192px; }
  .ui-icon-circle-zoomout { background-position: -192px -192px; }
  .ui-icon-circle-check { background-position: -208px -192px; }
  .ui-icon-circlesmall-plus { background-position: 0 -208px; }
  .ui-icon-circlesmall-minus { background-position: -16px -208px; }
  .ui-icon-circlesmall-close { background-position: -32px -208px; }
  .ui-icon-squaresmall-plus { background-position: -48px -208px; }
  .ui-icon-squaresmall-minus { background-position: -64px -208px; }
  .ui-icon-squaresmall-close { background-position: -80px -208px; }
  .ui-icon-grip-dotted-vertical { background-position: 0 -224px; }
  .ui-icon-grip-dotted-horizontal { background-position: -16px -224px; }
  .ui-icon-grip-solid-vertical { background-position: -32px -224px; }
  .ui-icon-grip-solid-horizontal { background-position: -48px -224px; }
  .ui-icon-gripsmall-diagonal-se { background-position: -64px -224px; }
  .ui-icon-grip-diagonal-se { background-position: -80px -224px; }


  /* Misc visuals
  ----------------------------------*/

  /* Corner radius */
  .ui-corner-all, .ui-corner-top, .ui-corner-left, .ui-corner-tl { -moz-border-radius-topleft: 4px/*{cornerRadius}*/; -webkit-border-top-left-radius: 4px/*{cornerRadius}*/; -khtml-border-top-left-radius: 4px/*{cornerRadius}*/; border-top-left-radius: 4px/*{cornerRadius}*/; }
  .ui-corner-all, .ui-corner-top, .ui-corner-right, .ui-corner-tr { -moz-border-radius-topright: 4px/*{cornerRadius}*/; -webkit-border-top-right-radius: 4px/*{cornerRadius}*/; -khtml-border-top-right-radius: 4px/*{cornerRadius}*/; border-top-right-radius: 4px/*{cornerRadius}*/; }
  .ui-corner-all, .ui-corner-bottom, .ui-corner-left, .ui-corner-bl { -moz-border-radius-bottomleft: 4px/*{cornerRadius}*/; -webkit-border-bottom-left-radius: 4px/*{cornerRadius}*/; -khtml-border-bottom-left-radius: 4px/*{cornerRadius}*/; border-bottom-left-radius: 4px/*{cornerRadius}*/; }
  .ui-corner-all, .ui-corner-bottom, .ui-corner-right, .ui-corner-br { -moz-border-radius-bottomright: 4px/*{cornerRadius}*/; -webkit-border-bottom-right-radius: 4px/*{cornerRadius}*/; -khtml-border-bottom-right-radius: 4px/*{cornerRadius}*/; border-bottom-right-radius: 4px/*{cornerRadius}*/; }

  /* Overlays */
  .ui-widget-overlay { background: #aaaaaa/*{bgColorOverlay}*/ url(images/ui-bg_flat_0_aaaaaa_40x100.png)/*{bgImgUrlOverlay}*/ 50%/*{bgOverlayXPos}*/ 50%/*{bgOverlayYPos}*/ repeat-x/*{bgOverlayRepeat}*/; opacity: .3;filter:Alpha(Opacity=30)/*{opacityOverlay}*/; }
  .ui-widget-shadow { margin: -8px/*{offsetTopShadow}*/ 0 0 -8px/*{offsetLeftShadow}*/; padding: 8px/*{thicknessShadow}*/; background: #aaaaaa/*{bgColorShadow}*/ url(images/ui-bg_flat_0_aaaaaa_40x100.png)/*{bgImgUrlShadow}*/ 50%/*{bgShadowXPos}*/ 50%/*{bgShadowYPos}*/ repeat-x/*{bgShadowRepeat}*/; opacity: .3;filter:Alpha(Opacity=30)/*{opacityShadow}*/; -moz-border-radius: 8px/*{cornerRadiusShadow}*/; -khtml-border-radius: 8px/*{cornerRadiusShadow}*/; -webkit-border-radius: 8px/*{cornerRadiusShadow}*/; border-radius: 8px/*{cornerRadiusShadow}*/; }
</style>

<div id="game_settings">
<div class="model-choice pick-num-cells">
<h4>How Many Backyards?</h4>
<select id="pick_gridN" title="Grid Size">
<option value="3">3 by 3</option>
<option selected="selected" value="7">7 by 7</option>
<option value="15">15 by 15</option>
<option value="30">30 by 30</option>
</select>
</div>
<div class="callout">
<p>Click on the Yards to Add Chickens</p>
</div>
<h4>Or Make It "Rain Chickens":</h4>
<p><button id="rain_chickens_middle">Chickens in the Middle</button></p>
<p><button id="rain_chickens_random">Random Chickens</button></p>
<p><button id="stop_chickens">Stop</button> <button id="reset_game">Reset</button></p>
<h4>Sound Effects?</h4>
<div class="switch"><input id="toggle-sound" class="cmn-toggle cmn-toggle-round" type="checkbox" /><label for="toggle-sound"></label></div>
</div>
<div id="game_board"></div>
<table style="width: 100%;">
<tbody>
<tr>
<th></th>
<th>0 chickens</th>
<th>1 chickens</th>
<th>2 chickens</th>
<th>3 chickens</th>
</tr>
<tr>
<td>Number of Yards</td>
<td class="chicken-count-0">0</td>
<td class="chicken-count-1">0</td>
<td class="chicken-count-2">0</td>
<td class="chicken-count-3">0</td>
</tr>
</tbody>
</table>

## Math Questions

<ol>
<li>If one of the yards has 2 or more chickens, is it possible to go back to all yards having less than 2 chickens?</li>
<li>Does the order at which chickens arrive change the result? (or just the locations where they arrive)</li>
<li>How many falling chickens does it take for the locations to stop changing so much?</li>
<li>If chickens always fall in the same spot, how does the total number of chickens relate to the "range" of the chickens?</li>
<li>What percentage of yards end up with 0, 1, 2, or 3 chickens?</li>
<li>Is it possible to add enough chickens to the middle of the neighborhood to result in no chickens in the middle?</li>
<li>Does it matter whether chickens arrive in the "middle" of the neighborhood (versus the yards near the edges)?</li>
<li>What happens if you add chickens to one yard every time?</li>
<li>What happens if you alternate adding chickens between two yards?</li>
<li>Which is better, spreading the chickens out in a consistent way, or letting them fall randomly?</li>
</ol>

## Resources

This activity is an exploration of a class mathematical objects called <a href="http://www.math.cmu.edu/~wes/sandgallery.html">abelian sandpiles</a>. We highly recommend reading <a href="http://nautil.us/issue/23/Dominoes/the-amazing-autotuning-sandpile">Jordan Ellenberg's wonderful article</a> about sandpiles.

In addition, we thank Marcel Salathé for a nice <a href="http://www.natureincode.com/code/various/sandpile.html">outline of the code</a> to implement the "chicken rule".

<script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

<script type="text/javascript">
  (function($) {
  	$(document).ready(function () {
		
  	$( window ).resize(function() {
  	  resize_land_squares();
  	  return false;
  	});
		
  	// SET-UP PARAMETERS
  	var gridN;
	
  	var occ = [];
  	var chicks = 0;
  	var chicks_in_area =0;
  	var chickenN = 10000;	
  	var mad_chicken = new Audio('/assets/misc/Angry-chicken-cut.mp3');

  	function resetGame(){
  		//console.log("resetting the game!");
  		var gridN_pick = document.getElementById("pick_gridN");
   		gridN = gridN_pick.options[gridN_pick.selectedIndex].value;
  		//console.log("grid size = "+gridN);
  		//var chickenN_pick = document.getElementById("pick_chickenN");
   		//chickenN = chickenN_pick.options[chickenN_pick.selectedIndex].value;
  		chicks =0;
  		chicks_in_area=0;
  		occ = Matrix(gridN, gridN, '0');
  		$('.chicken-count-0').html(gridN*gridN);
  		var board = document.getElementById('game_board');
  		board.innerHTML = '';
  		board.appendChild(displayLand(occ));
  		resize_land_squares();
  	}
		
  	// USER INTERFACE

  	$("[id^=pick_]").change(function() {
  		resetGame();
  	});
		
  	resetGame();
		
  	var rain_speed = 300;
  	var rain_timer1, rain_timer2;

  	//User Interface
  	var play_sound = false;
	
  	$('#toggle-sound').click(function(){
  		play_sound = this.checked;
  	});
		
  	$("#rain_chickens_middle").on('click', function(e){
  		e.preventDefault();
		
  		setTimeout(function() {
      		rain_timer1 = setInterval(function() {
       
  				if( chicks < chickenN ){
  					chicks++;
  					$('#chicken_count').html(chicks);
  					add_chicken( Math.floor((gridN-1)/2), Math.floor((gridN-1)/2) );
  					$('#chicken_count_in_area').html(chicks_in_area);
  				}
		
      		}, rain_speed);
  		}, rain_speed);
		
			
  	});
	
  $("#rain_chickens_random").on('click', function(e){
  		e.preventDefault();
		
  		setTimeout(function() {
      		rain_timer2 = setInterval(function() {
       
  				if( chicks < chickenN ){
  					chicks++;
  					$('#chicken_count').html(chicks);
  					add_chicken( getRandomInt(0,gridN-1), getRandomInt(0,gridN-1) );
  					$('#chicken_count_in_area').html(chicks_in_area);
  				}
		
      		}, rain_speed);
  		}, rain_speed);
		
			
  	});

  	$("#stop_chickens").on('click', function(){
  		clearTimeout(rain_timer1); // stop the timer
  		clearTimeout(rain_timer2); // stop the timer
  	});
  		$("#reset_game").on('click', function(){resetGame();});
		
  	$("#game_board").on('click', ".land-box", function(e){
  			e.preventDefault();
  		    if( chicks < chickenN ){
  			    chicks++;
  				$('#chicken_count').html(chicks);
  			    var clicked_x = Number( $(this).attr("data-x") );
                  var clicked_y = Number( $(this).attr("data-y") );
  				add_chicken(clicked_x, clicked_y); 
  				$('#chicken_count_in_area').html(chicks_in_area);
  		    }
             
  			return false;
  	});
	
  	/* FUNCTIONS */
  	function add_chicken(i,ii){
  		var this_cell = $(".row-"+i+"-col-"+ii);
  		var chickens = Number(occ[i][ii]);
		   
  		if (chickens < 3) {
             occ[i][ii]++;
  			chicks_in_area++;
  			this_cell.addClass("occupied");
  			this_cell.attr('data-n',chickens+1)
  			$(".row-"+i+"-col-"+ii+" p").html( chickens + 1 );
          }
          else {
  			//this spot is full!
             occ[i][ii] = chickens - 3;
  			chicks_in_area = chicks_in_area - 3;
  			this_cell.removeClass("occupied");
  			this_cell.attr('data-n',chickens-3);
  			$(".row-"+i+"-col-"+ii+" p").html( chickens - 3 );
  			//var anim_delay = 200;
  			if(play_sound){
  				//anim_delay = 900;
  				mad_chicken.play();
  			}; // play angry chicken
			
  			//setTimeout(function() { 
  				if (i > 0) {
              		add_chicken(i - 1, ii);
           		}
           		if (i < gridN - 1) {
              		add_chicken(i + 1, ii);
           		}
          		if (ii > 0) {
              		add_chicken(i, ii - 1);
           		}
           		if (ii < gridN - 1) {
              		add_chicken(i, ii + 1);
           		}
  			//}, anim_delay);
         
         }
		
  		var chicken_counts = array_freq(flatten(occ) );
  		i_0 = chicken_counts[0].indexOf(0);
  		i_1 = chicken_counts[0].indexOf(1);
  		i_2 = chicken_counts[0].indexOf(2);
  		i_3 = chicken_counts[0].indexOf(3);
  		$(".chicken-count-0").html(i_0>-1 ? chicken_counts[1][i_0]:0);
  		$(".chicken-count-1").html(i_1>-1 ? chicken_counts[1][i_1]:0);
  		$(".chicken-count-2").html(i_2>-1 ? chicken_counts[1][i_2]:0);
  		$(".chicken-count-3").html(i_3>-1 ? chicken_counts[1][i_3]:0);
      }
	
  	// make a list of indices for a matrix
  	function matrix_indices (msize){
  		var inds=[];
  		for (i=1; i<= msize; i++){
  			for (j=1; j<= msize; j++){
  				inds.push(i+","+j);
  			}
  		}
  		return inds;
  	}
	
  	//resize land squares to match width of the land
  	function resize_land_squares(){
  		var land_width = $('#game_board').width();
  		var box_width = Math.floor((land_width - 4*gridN)/gridN);
  		var chicken_width = box_width;
	
  		$('.land-box').height(box_width); 
  		$('.land-box').width(box_width);
  		$('.chicken-img').height(chicken_width).width(chicken_width);

  	}
  	//function to flatten an array (general purpose)
  	function flatten(arr) {
  	  return arr.reduce(function (flat, toFlatten) {
  		return flat.concat(Array.isArray(toFlatten) ? flatten(toFlatten) : toFlatten);
  	  }, []);
  	}
  	//function to count the number of non-empty elements in a flattened array (for calculating number of occupied cells)
  	function countNonEmpty(arr){
  		var cnt = 0;
  		for (var i = 0; i < arr.length; i++) {
  			if (arr[i] !== '') {
  				++cnt;
  			}
  		}
  		return cnt;
  	}
  	//function to compute max of a multidimensional array
  	function getMaxOfArray(numArray) {
  	  return Math.max.apply(null, numArray);
  	}

  	// create an m x n matrix filled with default value d
  	function Matrix(m, n, d){
  		var matrix = [];
  		for(var i=0; i<m; i++) {
  			matrix[i] = [];
  			for(var j=0; j<n; j++) {
  				matrix[i][j] = d;
  			}
  		}
  		return matrix;
  	}
	
	
  	function displayLand(array) {
  		// Create the list element:
  		var land = document.createElement('div');

  		var title = document.createElement('h3');
  		title.innerHTML = "Total Falling Chickens = <span id='chicken_count'>"+chicks+"</span>";
  		var subtitle = document.createElement('h4');
  		subtitle.innerHTML = "Total Chickens in the Neighborhood = <span id='chicken_count_in_area'>"+chicks_in_area+"</span>";
	
  		land.appendChild(title).appendChild(subtitle);
		
  		for(var i = 0; i < array.length; i++) {
  			// Create the row:
  			var row = document.createElement('div');
  			row.className="row-"+i;
  			// Fill the row
  			for(var j = 0; j < array[i].length; j++) {
  				//console.log(i+"-"+j);
  				//create the cell
  				var cell = document.createElement('div');
				
  				var isocc = array[i][j]!=0;
  				cell.className = "land-box "+"row-"+i+"-col-"+j+" col-"+j+(isocc ?' occupied':'');
  				cell.setAttribute("data-x",i);
  				cell.setAttribute("data-y",j);
  				cell.setAttribute( "data-n",array[i][j] );
  				//set the cell contents to the occ value (or empty)
  				cell.innerHTML = '<p>'+(isocc? array[i][j]:'')+'</p>';
				
				
  				// Add the cell to the row:
  				row.appendChild(cell);
  			}
			
  			// Add the row to the land:
  			land.appendChild(row);
  		}
	
  		// Finally, return the constructed list:
  		return land;
  	}
	
	
   //Returns a random integer between min (inclusive) and max (inclusive)
      function getRandomInt(min, max) {
          return Math.floor(Math.random() * (max - min + 1)) + min;
      }
	
  	// count the occurences of an array
  	function array_freq(arr) {
         var a = [], b = [], prev;
         arr = arr.map(function (x) { return parseInt(x, 10)});
         arr.sort();
          for ( var i = 0; i < arr.length; i++ ) {
             if ( arr[i] !== prev ) {
               a.push(arr[i]);
               b.push(1);
             } else {
               b[b.length-1]++;
             }
              prev = arr[i];
          }
    
          return [a, b];
      }
	
  	});
  })(jQuery);
</script>
  
