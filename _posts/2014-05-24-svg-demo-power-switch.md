---
layout: post
title: SVG实例之电力开关
date: 2014-05-24 07:08
author: admin
comments: true
categories: [SVG]
tags: [SVG,switch]
---

	<?xml version="1.0" standalone="no"?>
	<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"  width="400" height="200" >
	<script> 
	function lineGClick(evt) {
	
	var lineA = document.getElementById("lineA");
	if( lineA.getAttribute("display")=="none"){
	
	lineA.setAttribute("display","#000000");
	line2.setAttribute("display","none");
	
	}else{
	lineA.setAttribute("display","none");
	line2.setAttribute("display","#000000");
	}
	}
	 </script>
	<defs>
	 <g id="lineG1" >
	  <line id="line1" fill="none" stroke="#000000" stroke-width="4" x1="10" y1="10" x2="10" y2="40"/>
	  <line id="lineA" fill="none" display="none" stroke="#000000" stroke-width="4" x1="10" y1="40" x2="10" y2="70"/>
	  <line id="line2" fill="none" stroke="#000000" stroke-width="4" x1="10" y1="40" x2="35" y2="60"/>
	  <line id="lineB" fill="none" stroke="#000000" stroke-width="4" x1="10" y1="70" x2="10" y2="100"/>
	 </g>
	</defs>
	 
	<text x="10" y="20" fill="red">一个SVG电力开关的例子。点击开关，进行状态转换</text>
	<use x="10" y="30" xlink:href="#lineG1" onclick="lineGClick(evt)"/>
	<a xlink:href="http://www.waylau.com" target="_blank">
	<text x="10" y="180" fill="red">欢迎访问wwww.waylau.com</text>
	  </a>
	</svg>



<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"  width="400" height="200" >
<script> 
function lineGClick(evt) {
var lineA = document.getElementById("lineA");
if( lineA.getAttribute("display")=="none"){
lineA.setAttribute("display","#000000");
line2.setAttribute("display","none");
}else{
lineA.setAttribute("display","none");
line2.setAttribute("display","#000000");
}
}
 </script>
<defs>
 <g id="lineG1" >
  <line id="line1" fill="none" stroke="#000000" stroke-width="4" x1="10" y1="10" x2="10" y2="40"/>
  <line id="lineA" fill="none" display="none" stroke="#000000" stroke-width="4" x1="10" y1="40" x2="10" y2="70"/>
  <line id="line2" fill="none" stroke="#000000" stroke-width="4" x1="10" y1="40" x2="35" y2="60"/>
  <line id="lineB" fill="none" stroke="#000000" stroke-width="4" x1="10" y1="70" x2="10" y2="100"/>
 </g>
</defs>
<text x="10" y="20" fill="red">一个SVG电力开关的例子。点击开关，进行状态转换</text>
<use x="10" y="30" xlink:href="#lineG1" onclick="lineGClick(evt)"/>
<a xlink:href="http://www.waylau.com" target="_blank">
<text x="10" y="180" fill="red">欢迎访问wwww.waylau.com</text>
  </a>
</svg>


<img src="/assets/svg/2014-05-24-svg-demo-power-switch.svg"/>


<img src="/assets/img/wl_white_100.png"/>

<object data="/assets/svg/2014-05-24-svg-demo-power-switch.svg" width="302px" height="302px" type="image/svg+xml">
</object>

解释：

`defs`标签定义了可以重复利用的组件

`use`引用了`defs`所定义的组件，其中`onclick`监听了鼠标点击事件