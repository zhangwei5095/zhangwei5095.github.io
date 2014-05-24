---
layout: post
title: SVG实例之电力开关
date: 2014-05-24 07:08
author: admin
comments: true
categories: [SVG]
tags: [SVG,switch]
---

先上源码
		
	<svg  width="400" height="200" >
	<script> 
		<![CDATA[
		 function lineGClick(evt) {
	 
				var lineA = document.getElementById('lineA');
				if( lineA.getAttribute("display")=="none"){
					
		 		lineA.setAttribute('display','#000000');
				line2.setAttribute('display','none');
		
				}else{
					lineA.setAttribute('display','none');
					line2.setAttribute('display','#000000');
				}
	    }
	  ]]> 
		</script>
	<defs>
	 <g id='lineG1' >
	  <line id='line1' fill="none" stroke="#000000" stroke-width="4" x1="10" y1="10" x2="10" y2="40"/>
	  <line id='lineA' fill="none" display="none" stroke="#000000" stroke-width="4" x1="10" y1="40" x2="10" y2="70"/>
	  <line id='line2' fill="none" stroke="#000000" stroke-width="4" x1="10" y1="40" x2="40" y2="70"/>
	  <line id='lineB' fill="none" stroke="#000000" stroke-width="4" x1="10" y1="70" x2="10" y2="100"/>
	 </g>
	</defs>
	<use x='100' y='100' xlink:href="#lineG1" onclick="lineGClick(evt)"/>
	 <text x="100" y="20" font-size="15" >
	    点击开关，进行状态转换</text>
	</svg>

效果：

<svg  width="400" height="200" >
<script> 
<![CDATA[
function lineGClick(evt) {

var lineA = document.getElementById('lineA');
if( lineA.getAttribute("display")=="none"){

lineA.setAttribute('display','#000000');
line2.setAttribute('display','none');

}else{
lineA.setAttribute('display','none');
line2.setAttribute('display','#000000');
}
}
]]> 
</script>
<defs>
 <g id='lineG1' >
  <line id='line1' fill="none" stroke="#000000" stroke-width="4" x1="10" y1="10" x2="10" y2="40"/>
  <line id='lineA' fill="none" display="none" stroke="#000000" stroke-width="4" x1="10" y1="40" x2="10" y2="70"/>
  <line id='line2' fill="none" stroke="#000000" stroke-width="4" x1="10" y1="40" x2="40" y2="70"/>
  <line id='lineB' fill="none" stroke="#000000" stroke-width="4" x1="10" y1="70" x2="10" y2="100"/>
 </g>
</defs>
<use x='100' y='100' xlink:href="#lineG1" onclick="lineGClick(evt)"/>
 <text x="100" y="20" font-size="15" >
  点击开关，进行状态转换</text>
</svg>

解释：

`defs`标签定义了可以重复利用的组件

`use`引用了`defs`所定义的组件，其中`onclick`监听了鼠标点击事件