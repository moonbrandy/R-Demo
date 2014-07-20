---
title       : Social Network Analysis
subtitle    : 
author      : 
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : standalone  # {standalone, draft}
ext_widgets : {rCharts: [libraries/nvd3], shiny: [www/shared/datatables]}
---

## The Key Statistical Technique is Social Network Analysis
SNA presents social relationships such as friendship and kinship in graphical form, consisting of nodes and edges.

<img height=350 src='https://raw.githubusercontent.com/lc-ethan/SNA/master/img/slide1.png' alt='slide1'/>

<!---
<img height=350 src="https://dl.dropbox.com/u/7586336/googleVisExamples/gvisObject.png" alt="gvis object structure" />
-->

---

## Connections between Churners and Non-churners 
>  1. Churners **indirectly** connected through non-churners:

>  <div class="centered">
<img class src='https://raw.githubusercontent.com/lc-ethan/SNA/master/img/slide21.png' alt='slide21'/>
</div>

>  2. Churners **directly** connected:

>  <div class="centered">
<img src='https://raw.githubusercontent.com/lc-ethan/SNA/master/img/slide22.png' alt='slide22'/>
</div>

---

## Prioritising Customers with a High Propensity to Churn
<div class="centered">
<img src='https://raw.githubusercontent.com/lc-ethan/SNA/master/img/slide3.png' alt='slide3'/>
</div>


---

## Visualization of the Whole Network
<div class="centered">
<img src='https://raw.githubusercontent.com/lc-ethan/SNA/master/img/tk.png' alt='tk'/>
</div>


---

## Key Network Attributes
>  1. Degree
>  2. Betweenness
>  3. Closeness

---

## Network Metrics

![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1.png) 

---

## Network Metrics (Degree)
<link rel='stylesheet' href=http://nvd3.org/assets/css/nv.d3.css>
<script type='text/javascript' src=http://ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js></script>
<script type='text/javascript' src=http://d3js.org/d3.v3.min.js></script>
<script type='text/javascript' src=http://timelyportfolio.github.io/rCharts_nvd3_tests/libraries/widgets/nvd3/js/nv.d3.min-new.js></script>
<script type='text/javascript' src=http://nvd3.org/assets/lib/fisheye.js></script> 
 <style>
  .rChart {
    display: block;
    margin-left: auto; 
    margin-right: auto;
    width: 900px;
    height: 500px;
  }  
  </style>
<div id = 'chart1' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawchart1()
    });
    function drawchart1(){  
      var opts = {
 "dom": "chart1",
"width":    900,
"height":    500,
"x": "Degree",
"y": "Network",
"group": "Customer_Number",
"type": "scatterChart",
"id": "chart1" 
},
        data = [
 {
 "Degree":              7,
"Between": 13.18333333333,
"Close": 0.04545454545455,
"Network":              1,
"Customer_Number": "1" 
},
{
 "Degree":              4,
"Between":           2.85,
"Close": 0.03846153846154,
"Network": 0.5959669015376,
"Customer_Number": "2" 
},
{
 "Degree":              3,
"Between":            1.5,
"Close": 0.03703703703704,
"Network": 0.4149750037346,
"Customer_Number": "3" 
},
{
 "Degree":              3,
"Between": 0.3333333333333,
"Close": 0.03703703703704,
"Network": 0.5221817028602,
"Customer_Number": "4" 
},
{
 "Degree":              4,
"Between":            3.1,
"Close":           0.04,
"Network": 0.6511386619306,
"Customer_Number": "5" 
},
{
 "Degree":              6,
"Between": 11.81666666667,
"Close": 0.04347826086957,
"Network": 0.7649989537905,
"Customer_Number": "6" 
},
{
 "Degree":              6,
"Between": 11.21666666667,
"Close": 0.04347826086957,
"Network": 0.7324521248701,
"Customer_Number": "7" 
},
{
 "Degree":              2,
"Between": 1.366666666667,
"Close": 0.03030303030303,
"Network": 0.1761776508546,
"Customer_Number": "8" 
},
{
 "Degree":              3,
"Between": 5.116666666667,
"Close": 0.03448275862069,
"Network": 0.2957184396746,
"Customer_Number": "9" 
},
{
 "Degree":              5,
"Between": 9.483333333333,
"Close": 0.04166666666667,
"Network": 0.551460227067,
"Customer_Number": "10" 
},
{
 "Degree":              6,
"Between": 4.366666666667,
"Close": 0.04166666666667,
"Network": 0.9310412091675,
"Customer_Number": "11" 
},
{
 "Degree":              6,
"Between":            9.9,
"Close": 0.04545454545455,
"Network": 0.8821970441163,
"Customer_Number": "12" 
},
{
 "Degree":              5,
"Between": 5.066666666667,
"Close": 0.04347826086957,
"Network": 0.7764372908811,
"Customer_Number": "13" 
},
{
 "Degree":              2,
"Between":              0,
"Close": 0.03333333333333,
"Network": 0.3574729884077,
"Customer_Number": "14" 
},
{
 "Degree":              4,
"Between":            7.7,
"Close": 0.03846153846154,
"Network": 0.574146919453,
"Customer_Number": "15" 
} 
]
  
      if(!(opts.type==="pieChart" || opts.type==="sparklinePlus" || opts.type==="bulletChart")) {
        var data = d3.nest()
          .key(function(d){
            //return opts.group === undefined ? 'main' : d[opts.group]
            //instead of main would think a better default is opts.x
            return opts.group === undefined ? opts.y : d[opts.group];
          })
          .entries(data);
      }
      
      if (opts.disabled != undefined){
        data.map(function(d, i){
          d.disabled = opts.disabled[i]
        })
      }
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .width(opts.width)
          .height(opts.height)
          
        if (opts.type != "bulletChart"){
          chart
            .x(function(d) { return d[opts.x] })
            .y(function(d) { return d[opts.y] })
        }
          
         
        chart
  .tooltipContent( function(key, x, y, e){
  return '<b>Customer Number</b>: ' + e.point.Customer_Number
} )
  .color( d3.scale.category10().range() )
  .transitionDuration( 350 )
  .showDistY( true )
  .showDistX( true )
  .size( 1 )
  .sizeRange( [100,100] )
          
        chart.xAxis
  .tickFormat( d3.format(' .02f') )
  .axisLabel("Degree")

        
        
        chart.yAxis
  .tickFormat( d3.format(' .02f') )
  .axisLabel("Network")
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>

---

## Network Metrics (Betweenness)

<div id = 'chart2' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawchart2()
    });
    function drawchart2(){  
      var opts = {
 "dom": "chart2",
"width":    900,
"height":    500,
"x": "Between",
"y": "Network",
"group": "Customer_Number",
"type": "scatterChart",
"id": "chart2" 
},
        data = [
 {
 "Degree":              7,
"Between": 13.18333333333,
"Close": 0.04545454545455,
"Network":              1,
"Customer_Number": "1" 
},
{
 "Degree":              4,
"Between":           2.85,
"Close": 0.03846153846154,
"Network": 0.5959669015376,
"Customer_Number": "2" 
},
{
 "Degree":              3,
"Between":            1.5,
"Close": 0.03703703703704,
"Network": 0.4149750037346,
"Customer_Number": "3" 
},
{
 "Degree":              3,
"Between": 0.3333333333333,
"Close": 0.03703703703704,
"Network": 0.5221817028602,
"Customer_Number": "4" 
},
{
 "Degree":              4,
"Between":            3.1,
"Close":           0.04,
"Network": 0.6511386619306,
"Customer_Number": "5" 
},
{
 "Degree":              6,
"Between": 11.81666666667,
"Close": 0.04347826086957,
"Network": 0.7649989537905,
"Customer_Number": "6" 
},
{
 "Degree":              6,
"Between": 11.21666666667,
"Close": 0.04347826086957,
"Network": 0.7324521248701,
"Customer_Number": "7" 
},
{
 "Degree":              2,
"Between": 1.366666666667,
"Close": 0.03030303030303,
"Network": 0.1761776508546,
"Customer_Number": "8" 
},
{
 "Degree":              3,
"Between": 5.116666666667,
"Close": 0.03448275862069,
"Network": 0.2957184396746,
"Customer_Number": "9" 
},
{
 "Degree":              5,
"Between": 9.483333333333,
"Close": 0.04166666666667,
"Network": 0.551460227067,
"Customer_Number": "10" 
},
{
 "Degree":              6,
"Between": 4.366666666667,
"Close": 0.04166666666667,
"Network": 0.9310412091675,
"Customer_Number": "11" 
},
{
 "Degree":              6,
"Between":            9.9,
"Close": 0.04545454545455,
"Network": 0.8821970441163,
"Customer_Number": "12" 
},
{
 "Degree":              5,
"Between": 5.066666666667,
"Close": 0.04347826086957,
"Network": 0.7764372908811,
"Customer_Number": "13" 
},
{
 "Degree":              2,
"Between":              0,
"Close": 0.03333333333333,
"Network": 0.3574729884077,
"Customer_Number": "14" 
},
{
 "Degree":              4,
"Between":            7.7,
"Close": 0.03846153846154,
"Network": 0.574146919453,
"Customer_Number": "15" 
} 
]
  
      if(!(opts.type==="pieChart" || opts.type==="sparklinePlus" || opts.type==="bulletChart")) {
        var data = d3.nest()
          .key(function(d){
            //return opts.group === undefined ? 'main' : d[opts.group]
            //instead of main would think a better default is opts.x
            return opts.group === undefined ? opts.y : d[opts.group];
          })
          .entries(data);
      }
      
      if (opts.disabled != undefined){
        data.map(function(d, i){
          d.disabled = opts.disabled[i]
        })
      }
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .width(opts.width)
          .height(opts.height)
          
        if (opts.type != "bulletChart"){
          chart
            .x(function(d) { return d[opts.x] })
            .y(function(d) { return d[opts.y] })
        }
          
         
        chart
  .tooltipContent( function(key, x, y, e){
  return '<b>Customer Number</b>: ' + e.point.Customer_Number
} )
  .color( d3.scale.category10().range() )
  .transitionDuration( 350 )
  .showDistY( true )
  .showDistX( true )
  .size( 1 )
  .sizeRange( [100,100] )
          
        chart.xAxis
  .tickFormat( d3.format(' .02f') )
  .axisLabel("Degree")

        
        
        chart.yAxis
  .tickFormat( d3.format(' .02f') )
  .axisLabel("Network")
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>

---

## Network Metrics (Closeness)

<div id = 'chart3' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawchart3()
    });
    function drawchart3(){  
      var opts = {
 "dom": "chart3",
"width":    900,
"height":    500,
"x": "Close",
"y": "Network",
"group": "Customer_Number",
"type": "scatterChart",
"id": "chart3" 
},
        data = [
 {
 "Degree":              7,
"Between": 13.18333333333,
"Close": 0.04545454545455,
"Network":              1,
"Customer_Number": "1" 
},
{
 "Degree":              4,
"Between":           2.85,
"Close": 0.03846153846154,
"Network": 0.5959669015376,
"Customer_Number": "2" 
},
{
 "Degree":              3,
"Between":            1.5,
"Close": 0.03703703703704,
"Network": 0.4149750037346,
"Customer_Number": "3" 
},
{
 "Degree":              3,
"Between": 0.3333333333333,
"Close": 0.03703703703704,
"Network": 0.5221817028602,
"Customer_Number": "4" 
},
{
 "Degree":              4,
"Between":            3.1,
"Close":           0.04,
"Network": 0.6511386619306,
"Customer_Number": "5" 
},
{
 "Degree":              6,
"Between": 11.81666666667,
"Close": 0.04347826086957,
"Network": 0.7649989537905,
"Customer_Number": "6" 
},
{
 "Degree":              6,
"Between": 11.21666666667,
"Close": 0.04347826086957,
"Network": 0.7324521248701,
"Customer_Number": "7" 
},
{
 "Degree":              2,
"Between": 1.366666666667,
"Close": 0.03030303030303,
"Network": 0.1761776508546,
"Customer_Number": "8" 
},
{
 "Degree":              3,
"Between": 5.116666666667,
"Close": 0.03448275862069,
"Network": 0.2957184396746,
"Customer_Number": "9" 
},
{
 "Degree":              5,
"Between": 9.483333333333,
"Close": 0.04166666666667,
"Network": 0.551460227067,
"Customer_Number": "10" 
},
{
 "Degree":              6,
"Between": 4.366666666667,
"Close": 0.04166666666667,
"Network": 0.9310412091675,
"Customer_Number": "11" 
},
{
 "Degree":              6,
"Between":            9.9,
"Close": 0.04545454545455,
"Network": 0.8821970441163,
"Customer_Number": "12" 
},
{
 "Degree":              5,
"Between": 5.066666666667,
"Close": 0.04347826086957,
"Network": 0.7764372908811,
"Customer_Number": "13" 
},
{
 "Degree":              2,
"Between":              0,
"Close": 0.03333333333333,
"Network": 0.3574729884077,
"Customer_Number": "14" 
},
{
 "Degree":              4,
"Between":            7.7,
"Close": 0.03846153846154,
"Network": 0.574146919453,
"Customer_Number": "15" 
} 
]
  
      if(!(opts.type==="pieChart" || opts.type==="sparklinePlus" || opts.type==="bulletChart")) {
        var data = d3.nest()
          .key(function(d){
            //return opts.group === undefined ? 'main' : d[opts.group]
            //instead of main would think a better default is opts.x
            return opts.group === undefined ? opts.y : d[opts.group];
          })
          .entries(data);
      }
      
      if (opts.disabled != undefined){
        data.map(function(d, i){
          d.disabled = opts.disabled[i]
        })
      }
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .width(opts.width)
          .height(opts.height)
          
        if (opts.type != "bulletChart"){
          chart
            .x(function(d) { return d[opts.x] })
            .y(function(d) { return d[opts.y] })
        }
          
         
        chart
  .tooltipContent( function(key, x, y, e){
  return '<b>Customer Number</b>: ' + e.point.Customer_Number
} )
  .color( d3.scale.category10().range() )
  .transitionDuration( 350 )
  .showDistY( true )
  .showDistX( true )
  .size( 1 )
  .sizeRange( [100,100] )
          
        chart.xAxis
  .tickFormat( d3.format(' .02f') )
  .axisLabel("Degree")

        
        
        chart.yAxis
  .tickFormat( d3.format(' .02f') )
  .axisLabel("Network")
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>

---

## Better Visualization of the Whole Network
<div class="centered">
<img src='https://raw.githubusercontent.com/lc-ethan/SNA/master/img/tk2.png' alt='tk2'/>
</div>

---

## SNA Animation
<div class="centered">
<img src='https://raw.githubusercontent.com/lc-ethan/SNA/master/img/SNA.gif' />
</div>









---
