---
layout: post
title: SVG &lt;marker&gt;创建箭头
date: 2014-05-29 07:08
author: admin
comments: true
categories: [SVG]
tags: [SVG,marker,arrow]
---
 
SVG 中&lt;line&gt;并没有箭头，可以通过&lt;marker&gt;进行扩展。

先定义一个箭头

    <defs>
        <marker id="arrow"
                viewBox="0 0 10 10" refX="0" refY="5"
                markerUnits="strokeWidth" markerWidth="3" markerHeight="10"
                orient="auto"
                >
            <path d="M 0 0 L 10 5 L 0 10 z" fill="yellow" stroke="black"/>
        </marker>
    </defs>

其中`orient="auto"`设置箭头的方向为自动适应线条的方向。

而后，画line ,line的`marker-end`引用上面定义好的`arrow`即可

    <line x1="0" y1="0" x2="200" y2="200"  stroke="red" stroke-width="5" marker-end="url(#arrow)"  />
效果如下：

<svg width="4cm" height="4cm" viewBox="0 0 400 400">
<desc>Markers,一个箭头实例，更多例子访问www.waylau.com</desc>
<defs>
<marker id="arrow"
viewBox="0 0 10 10" refX="0" refY="5"
markerUnits="strokeWidth" markerWidth="3" markerHeight="10"
orient="auto"
>
<path d="M 0 0 L 10 5 L 0 10 z" fill="yellow" stroke="black"/>
</marker>
</defs>

<line x1="0" y1="0" x2="200" y2="200"  stroke="red" stroke-width="5" marker-end="url(#arrow)"  />
<path d="M75,100 c25,-75 50,50 100,0 s50,-50 150,50"
  stroke="purple" stroke-width="5" fill="none"
  marker-start="url(#arrow)"
  marker-mid="url(#arrow)"
  marker-end="url(#arrow)" />
</svg>

完整代码如下：
	
	<svg width="4cm" height="4cm" viewBox="0 0 400 400">
	    <desc>Markers,一个箭头实例，更多例子访问www.waylau.com</desc>
	    <defs>
	        <marker id="arrow"
	                viewBox="0 0 10 10" refX="0" refY="5"
	                markerUnits="strokeWidth" markerWidth="3" markerHeight="10"
	                orient="auto"
	                >
	            <path d="M 0 0 L 10 5 L 0 10 z" fill="yellow" stroke="black"/>
	        </marker>
	    </defs>
	    <!-- First row -->
	    <line x1="0" y1="0" x2="200" y2="200"  stroke="red" stroke-width="5" marker-end="url(#arrow)"  />
	    <!-- Second row -->
	    <path d="M75,100 c25,-75 50,50 100,0 s50,-50 150,50"
	          stroke="purple" stroke-width="5" fill="none"
	          marker-start="url(#arrow)"
	          marker-mid="url(#arrow)"
	          marker-end="url(#arrow)" />
	</svg>
