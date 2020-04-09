---
title: Solver for Flow game
layout: post
categories: project
excerpt: A javascript solver for popular mobile phone game <i>Flow</i>
icon: /assets/flowSolver/flowSolver.png
---


<style>

.mapElement {
fill:rgb(240,240,240);
stroke:white;
stroke-width:2;
}
span {
display: inline-block;
width: 20px;
}

</style>

<p id = "input">
Size:  <input> <span class ="range" id="range"></span><button>reset</button> 
</p>

<p><button onclick="preset(1)">preset 1</button> <button onclick="preset(2)">preset 2</button><button onclick="preset(3)">preset 3</button><button onclick="preset(4)">preset 4</button></p>
<svg class = "map">
</svg>
<br>
<br>
<svg class = "colorButtons">
</svg>
<p>
<button onclick="solve()">solve!</button>
</p>
<p id="message"> </p>
<script src="/assets/flowSolver/d3.v3.min.js" charset="utf-8"></script>
<script src="/assets/flowSolver/flowSolver.js"></script>
<script src="/assets/flowSolver/flowSolver_solve.js"></script>

[github](https://github.com/ctawong/flowSolver)
