---
layout: project2
type: project
image: images/cholera.jpg
title: Cholera Project
permalink: projects/choleraB
date: 2018
labels:
  - Javascript
  - CSS
  - Plot.ly
summary: Data Visualization Project Part B
---
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Census and Age Data</title>
</head>
<head>
  <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.2.2/semantic.min.css">
</head>
<nav class="ui stackable menu">
  <a style="padding-top: 8px; padding-left: 50px;" href="https://mserai.github.io/projects/cholera">About</a>
</nav>
<body>
<div class="ui fluid container">
  <div id="table"style="padding-left: 500px; width: 400px"></div>
</div>
<div id="summary"style="padding-bottom: 10px">
  <p align="center">This table represents the age ranges of male and female fatalities due to cholera.
  </p>
</div>
<div>
  <div class="ui fluid container">
    <div style="border-style: solid"></div>
  </div>
</div>
<div class="ui fluid container">
  <div id="table1"style="padding-left: 500px; width: 400px"></div>
</div>
<div id="summary2"style="padding-bottom: 10px">
  <p align="center">This table represents the census age data of males and females at the time.
  </p>
</div>
<div>
  <div class="ui fluid container">
    <div style="border-style: solid"></div>
  </div>
</div>
<div id="mBar"></div>
<div id="summary3"style="padding-bottom: 10px">
  <p align="center">This bar chart represents the male age categories of fatalities due to cholera.
  </p>
</div>
<div>
  <div class="ui fluid container">
    <div style="border-style: solid"></div>
  </div>
</div>
<div id="fBar"></div>
<div id="summary4"style="padding-bottom: 10px">
  <p align="center">This bar chart represents the female age categories of fatalities due to cholera.
  </p>
</div>
<div>
  <div class="ui fluid container">
    <div style="border-style: solid"></div>
  </div>
</div>
<div id = "mPie"style="padding-left: 500px"></div>
<div id="summary5"style="padding-bottom: 10px">
  <p align="center">This pie chart represents the census age data of males at the time.
  </p>
</div>
<div>
  <div class="ui fluid container">
    <div style="border-style: solid"></div>
  </div>
</div>
<div id = "fPie"style="padding-left: 500px"></div>
<div id="summary6"style="padding-bottom: 10px">
  <p align="center">This pie chart represents the census age data of females at the time.
  </p>
</div>
<div>
  <div class="ui fluid container">
    <div style="border-style: solid"></div>
  </div>
</div>
<div id="mBar1"></div>
<div id="summary7"style="padding-bottom: 10px">
  <p align="center">This bar chart represents the census age data of males at the time.
  </p>
</div>
<div>
  <div class="ui fluid container">
    <div style="border-style: solid"></div>
  </div>
</div>
<div id="fBar1"></div>
<div id="summary8"style="padding-bottom: 10px">
  <p align="center">This pie chart represents the census age data of females at the time.
  </p>
</div>
<div>
  <div class="ui fluid container">
    <div style="border-style: solid"></div>
  </div>
</div>
<div id = "tPie"style="padding-left: 500px"></div>
<div id="summary9"style="padding-bottom: 10px">
  <p align="center">This pie chart represents the census age data of total males vs. total females at the time.
  </p>
</div>
<script>
  /*1. Read in naplesCholeraAgeSexData.tsv...*/
  Plotly.d3.tsv("https://raw.githubusercontent.com/mserai/Cholera/master/naplesCholeraAgeSexData.tsv", function(err, rows) {
    /*4. Read in UKcensus1851.csv...*/
    Plotly.d3.csv("https://raw.githubusercontent.com/mserai/Cholera/master/UKcensus1851.csv", function (err1, rows1) {
      function unpack(rows, key) {
        return rows.map(function (row) { return row[key];});
      }
      var header = Plotly.d3.keys(rows[0]);
      var header1 = Plotly.d3.keys(rows1[0]);
      var headerData = [];
      var cellData = [];
      var headerData1 = [];
      var cellData1 = [];
      /*Grab*/
      for (i = 0; i < header.length; i++) {
        headerValue = [header[i]];
        headerData[i] = headerValue;
        cellValue = unpack(rows, header[i]);
        cellData[i] = cellValue;
      }
      for (i = 0; i < header1.length; i++) {
        headerValue1 = [header1[i]];
        headerData1[i] = headerValue1;
        cellValue1 = unpack(rows1, header1[i]);
        cellData1[i] = cellValue1;
      }
      for (i = 0; i < cellData[1].length; i++) {
        var ageValue = cellData[1][i].split(' ')[0];
        cellData[1][i] = ageValue;
      }
      for (i = 0; i < cellData1[1].length; i++) {
        var ageValue1 = cellData1[1][i].split(' ')[0];
        cellData1[1][i] = ageValue1;
      }
      var mValues = cellData1[1].slice(0);
      var fValues = cellData1[2].slice(0);
      /*2. Show a table of age categories...*/
      var tableData = [{
        type: 'table',
        columnwidth: [30, 30, 30],
        columnorder: [0, 1, 2],
        header: {
          values: headerData,
          align: "center",
          font: { family: "Helvetica", size: 11, color: "white" },
          line: { color: 'rgb(50, 50, 50)', width: 1, },
          fill: { color: ['green'] }
        },
        cells: {
          values: cellData,
          align: "center",
          font: { family: "Helvetica", size: 11, color: ["black"] },
          line: { color: "black", width: 1 },
          fill: { color: ['rgb(144, 238, 144)', 'white'] }
        }
      }];
      /*5. Show a table of the census age*/
      var tableData1 = [{
        type: 'table',
        columnwidth: [30, 30, 30],
        columnorder: [0, 1, 2],
        header: {
          values: headerData1,
          align: "center",
          font: { family: "Helvetica", size: 11, color: "white" },
          line: { color: 'rgb(50, 50, 50)', width: 1, },
          fill: { color: ['green'] }
        },
        cells: {
          values: cellData1,
          align: "center",
          font: { family: "Helvetica", size: 11, color: ["black"] },
          line: { color: "black", width: 1 },
          fill: { color: ['rgb(144, 238, 144)', 'white'] }
        }
      }];
      /*3. Show a bar chart of cage categories...*/
      var mBarData = [
        {
          x: cellData[0],
          y: cellData[1],
          type: 'bar'
        }
      ];
      var fBarData = [
        {
          x: cellData[0],
          y: cellData[2],
          type: 'bar'
        }
      ];
      /*7. Show a bar chart of the census age*/
      var mBarData1 = [
        {
          x: cellData1[0],
          y: cellData1[1],
          type: 'bar'
        }
      ];
      var fBarData1 = [
        {
          x: cellData1[0],
          y: cellData1[2],
          type: 'bar'
        }
      ];
      /*6. Show a pie chart of the census age*/
      var mPieData = [{
        values: mValues,
        labels: cellData1[0],
        type: 'pie'
      }];
      var fPieData = [{
        values: fValues,
        labels: cellData1[0],
        type: 'pie'
      }];
      function sum(a,b){
        return parseInt(a, 10) + parseInt(b, 10);
      }
      /*Add um up*/
      var tMales = mValues.reduce(sum, 0);
      var tFemales = fValues.reduce(sum, 0);
      var totals = [tMales, tFemales];
      /*8. Show a pie chart for the overall...*/
      var tPieData = [{
        values: totals,
        labels: ['Male', 'Female'],
        type: 'pie'
      }];
      /*Titles*/
      var fPieTitle = {
        title: 'Female Age Data',
        height: 500,
        width: 500
      };
      var mPieTitle = {
        title: 'Male Age Data',
        height: 500,
        width: 500
      };
      var tableTitle = {
        title: "Table of Fatalities by Sex and Age group"
      };
      var tableTitle1 = {
        title: "Table of Census Age"
      };
      var mBarTitle = {
        title: "Male Fatalities"
      };
      var fBarTitle = {
        title: "Female Fatalities"
      };
      var mBarTitle1 = {
        title: "Male Census Age"
      };
      var fBarTitle1 = {
        title: "Female Census Age"
      };
      var tPieTitle = {
        title: "Total Males vs Females",
        height: 500,
        width: 500
      };
      /*Go*/
      Plotly.plot('table', tableData, tableTitle);
      Plotly.plot('table1', tableData1, tableTitle1);
      Plotly.newPlot('mPie', mPieData, mPieTitle);
      Plotly.newPlot('fPie', fPieData, fPieTitle);
      Plotly.newPlot('mBar', mBarData, mBarTitle);
      Plotly.newPlot('fBar', fBarData, fBarTitle);
      Plotly.newPlot('mBar1', mBarData1, mBarTitle1);
      Plotly.newPlot('fBar1', fBarData1, fBarTitle1);
      Plotly.newPlot('tPie', tPieData, tPieTitle);
    });
  });
</script>
</body
