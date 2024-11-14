---
title: "My blog post with charts"
scripts: 
  - "rrtAlgorithm.js"
  - "aStarAlgorithm.js"
  - "customgrid.js"
  - "rrtStarAlgorithm.js"
---


<html lang = "en">
<head>
    <meta charset = "UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/style.css">
    <section class="header2">
        <h1>Motion Planning: Custom High Resolution Grid</h1>
        <p>Set start and goal locations, obstacles, and visualize the RRT, A* or Informed RRT* algorithm</p>
    </section>    
</head>
<body>

    <div class="selection">
    <h2>Choose an algorithm:</h2>
    <select class= "choose-algorithm" name= "choose-algorithm">
        <option value="RRT">RRT Algorithm</option>
        <option value="AStar">A* Algorithm</option>
        <option value="RRTStar">Informed RRT* Algorithm</option>
    </select>
    <button id="runAlgorithm"> Go! </button>
   </div>

   <div class = "reset">
    <button id="resetGrid" onClick="window.location.reload(true)"> Reset Grid </button>
   </div>

   <div class="results">
    <h3 id="algoresults">[View Results]</h3>
   </div>

   <div class = "canvas">
   <canvas id="myCanvas" width="1000" height="650" style="border:1px solid #FF0000;">
    </canvas>
   </div>

   <button id="setStart"> Set Start Location </button>
   <h3 id="startCoords">0 0</h3>
   <button id="setGoal"> Set Goal Location </button>
   <h3 id="goalCoords">0 0</h3>
   <button id="setObstacles"> Set Obstacles </button>
   <button id="returnHome"> Home Page </button>
   
   <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js" type="text/javascript"></script>
   <script src="js/customgrid.js" type="module"></script>

</body>
</html>
