---
layout: project
type: project
image: images/cholera.jpg
title: Cholera Project
permalink: projects/cholera
date: 2018
labels:
  - Javascript
  - CSS
  - Plot.ly
summary: Data Visualization Project 1
---


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Pump and Death Locations</title>
  <head>
    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.2.2/semantic.min.css">
  </head>
</head><nav class="ui stackable menu">
  <a style="padding-top: 8px; padding-left: 50px;" href="https://mserai.github.io/projects/cholera">About</a>
  <div style="padding-top: 8px; padding-left: 200px"><p>Stars represent pumps. Circles represent deaths. The bigger and darker the circle, the more deaths at each location.</p></div>
  </nav>
<body>
<div class="ui fluid container">
<div id="map"></div>
</div>
<script>
  /*1. Read in choleraDeathLocations.csv and ...*/
  Plotly.d3.csv('https://raw.githubusercontent.com/mserai/Cholera/master/choleraDeathLocations.csv', function(err, rows){
    Plotly.d3.csv('https://raw.githubusercontent.com/mserai/Cholera/master/choleraPumpLocations.csv', function(err1, rows1) {
      function unpack(rows, key) {
        return rows.map(function (row) { return row[key];
        });
      }
      var pumpY = [];
      var pumpX = [];
      /*Grab*/
      pumpY.push(Object.keys(rows1[0])[0]);
      pumpX.push(Object.keys(rows1[0])[1]);
      for (var i = 0; i < rows1.length; i++) {
        pumpX.push(rows1[i]["x"]);
        pumpY.push(rows1[i]["y"]);
      }
      var colors = [[0, 'rgb(256,0,0)'],[0.25,'rgb(200, 36, 36)'],[0.5,'rgb(132, 73, 73)'],[0.75,'rgb(73, 0, 0)'],[1,'rgb(0,0,0)']];
      /*2. Show a map of the locations of the deaths...*/
      var plots = [{
        type: 'scattermapbox',
        mode: 'markers',
        text: unpack(rows, 'Deaths'),
        lon: unpack(rows, 'pumpLong'),
        lat: unpack(rows, 'pumpLat'),
        marker: {
          color: unpack(rows, 'Deaths'),
          colorscale: colors,
          cmin: 0,
          cmax: 10,
          reversescale: false,
          opacity: unpack(rows, 'Deaths'),
          size: unpack(rows, 'Deaths'),
          sizeref: .25,
        },
        name: 'Death(s)'
      }];
      /* of pumps*/
      var plot = [{
        type: 'scattermapbox',
        mode: 'markers',
        lon: unpack(rows1, 'x'),
        lat: unpack(rows1, 'y'),
        marker: {
          symbol: 'star',
          size: 20,
          color: 'rgb(0,0,256)',
        },
        name: 'Pump'
      }];
      layout = {
        height: 1000,
        width: 2000,
        dragmode: 'zoom',
        title: 'Pumps and Deaths',
        mapbox: {
          center: {
            lat: 51.510413,
            lon: -0.132347
          },
          domain: {
            x: [0, 1],
            y: [0, 1]
          },
          style: 'light',
          zoom: 15.3
        },
        margin: {
          r: 0,
          t: 0,
          b: 0,
          l: 0,
          pad: 0
        },
        showlegend: true
      };
      Plotly.setPlotConfig({
        mapboxAccessToken: 'pk.eyJ1IjoibXNlcmFpIiwiYSI6ImNqbTl1NWJ5ajAwMW8zcG1yNjY5emc5NnMifQ.Ig1yRjY3fv_Babaz0TbVOw'
      });
      /*Go*/
      Plotly.newPlot('map', plot, layout);
      Plotly.plot('map', plots, layout);
    })
  });
</script>
</body>
</html>
