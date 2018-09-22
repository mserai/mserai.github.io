
---
layout: projects
type: project
image: images/cholera.jpg
title: Cholera Project
permalink: projects/choleraC
date: 2018
labels:
  - Javascript
  - CSS
  - Plot.ly
summary: Data Visualization Project 1 Part C
---
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Cholera Deaths</title>
</head>
<head>
  <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.2.2/semantic.min.css">
</head>
<!--4. Allow the user-->
<nav class="ui stackable menu">
  <a style="padding-top: 8px; padding-left: 50px;" href="https://mserai.github.io/projects/cholera">About</a>
</nav>
<body>
<div class="ui fluid container">
  <div id="table"style="padding-left: 450px; width: 600px"></div>
</div>
<div id="summary"style="padding-bottom: 10px">
  <p align="center">This table represents the number of cholera attacks and death per date.
  </p>
  <p align="center">The total number of attacks and deaths up to the date is displayed on the two rightmost columns.
  </p>
</div>
<div>
  <div class="ui fluid container">
    <div style="border-style: solid"></div>
  </div>
</div>
<div class="ui fluid container">
  <div id="plots"style="margin: 100px"></div>
</div>
  <div id="summary2"style="padding-bottom: 10px">
    <p align="center">This line chart represents the number of cholera attacks, deaths, total attacks, and total deaths per date.
    </p>
  </div>
<div>
  <div class="ui fluid container">
    <div style="border-style: solid"></div>
  </div>
</div>
<script>
  /*1. Read in the choleraDeaths.tsv data file*/
  Plotly.d3.tsv("https://raw.githubusercontent.com/mserai/Cholera/master/choleraDeaths.tsv", function(err, rows){
    function unpack(row, key) {
      return row.map(function(row) { return row[key]; });
    }
    var header = Plotly.d3.keys(rows[0]);
    var headerData = [];
    var cellData = [];
    var totalAttack = ["1"];
    var totalDeath = ["1"];
    /*Grab*/
    for (i = 0; i < header.length; i++) {
      headerValue = [header[i]];
      headerData[i] = headerValue;
      cellValue = unpack(rows, header[i]);
      cellData[i] = cellValue;
    }
    for (i = 0; i < cellData[1].length; i++) {
      var dateValue = cellData[1][i].split(' ')[0];
      cellData[1][i] = dateValue;
    }
    for(i = 1; i< cellData[1].length; i++){
      totalAttack[i] = parseInt(cellData[1][i], 10) + parseInt(totalAttack[i-1], 10);
      totalAttack[i] = totalAttack[i].toString();
      totalDeath[i] = parseInt(cellData[2][i], 10) + parseInt(totalDeath[i-1], 10);
      totalDeath[i] = totalDeath[i].toString();
    }
    headerData.push(["Total Attacks"]);
    headerData.push(["Total Deaths"]);
    cellData.push(totalAttack);
    cellData.push(totalDeath);
    /*2. Create a Plot.ly table of attacks...*/
    var tableData = [{
      type: 'table',
      columnwidth: [50,50,50,50,50],
      columnorder: [0,1,2,3,4],
      header: {
        values: headerData,
        align: "center",
        font: {family: "Helvetica", size: 11, color: "white"},
        line: {color: 'rgb(50, 50, 50)',width: 1, },
        fill: {color: ['green']}
      },
      cells: {
        values: cellData,
        align: "center",
        font: {family: "Helvetica", size: 11, color: ["black"]},
        line: {color: "black", width: 1},
        fill: {color: ['rgb(144, 238, 144)','white']}
      }
    }];
    /*3. Create a line chart showing...*/
    trace1 = {
      x: cellData[0],
      y: cellData[1],
      mode: 'lines',
      name: 'Attacks per Day'
    };
    trace2 = {
      x: cellData[0],
      y: cellData[2],
      mode: 'lines',
      name: 'Deaths per Day'
    };
    trace3 = {
      x: cellData[0],
      y: totalAttack,
      mode: 'lines',
      name: 'Total Attacks'
    };
    trace4 = {
      x: cellData[0],
      y: totalDeath,
      mode: 'lines',
      name: 'Total Deaths'
    };
    var plotsData = [trace1, trace2, trace3, trace4];
    /* Titles*/
    var tableTitle = {
      title: "Table of Cholera Attacks and Deaths"
    };
    var plotsTitle = {
      title: 'Cholera Attacks and Deaths by Date',
      yaxis: {
        title: 'Attacks and Deaths per day'
      }
    };
    /*Go*/
    Plotly.plot('table', tableData, tableTitle);
    Plotly.plot('plots', plotsData, plotsTitle);
  });
</script>
</body>
