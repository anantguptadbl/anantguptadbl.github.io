---
layout: post
title:  "Creating Interactive Maps using HighCharts"
date:   2019-06-21 
categories: 
---

## HighCharts
Highcharts is an awesome plotting library that helps in creating dynamic HTML charts, with less effort compared to D3.JS

The following are the steps to be followed for a simple implementation of plotting certain coordinates on a map

## Creating the HTML File
The HTML file that we create will have the following components

### HTML 
``` html
<script src="https://cdnjs.cloudflare.com/ajax/libs/proj4js/2.3.6/proj4.js"></script>
<script src="https://code.highcharts.com/maps/highmaps.js"></script>
<script src="https://code.highcharts.com/maps/modules/exporting.js"></script>
<script src="https://code.highcharts.com/maps/modules/offline-exporting.js"></script>
<script src="https://code.highcharts.com/mapdata/countries/gb/gb-all.js"></script>
<script src="https://code.highcharts.com/mapdata/countries/in/in-all.js"></script>
<input type="file" id="myFile" multiple size="50" onchange="myFunction()">

<div id="container"></div>
```

### STYLE/CSS
``` css
<style>
#container {
    height: 680px;
    min-width: 310px;
    max-width: 800px;
    margin: 0 auto;
}
.loading {
    margin-top: 10em;
    text-align: center;
    color: gray;
}
</style>
```

### JAVASCRIPT
``` html
<script type="text/javascript">
// Upload the file

function myFunction(){
  var x = document.getElementById("myFile");
  var txt = "";
  if ('files' in x) {
    if (x.files.length == 0) {
      txt = "Select one or more files.";
    } else {
      for (var i = 0; i < x.files.length; i++) {
        txt += "<br><strong>" + (i+1) + ". file</strong><br>";
        var file = x.files[i];
        if ('name' in file) {
          txt += "name: " + file.name + "<br>";
        }
        if ('size' in file) {
          txt += "size: " + file.size + " bytes <br>";
        }
      }
    }
  } 
  else {
    if (x.value == "") {
      txt += "Select one or more files.";
    } else {
      txt += "The files property is not supported by your browser!";
      txt  += "<br>The path of the selected file: " + x.value; // If the browser does not support the files property, it will return the path of the selected file instead. 
    }
  }
  document.getElementById("demo").innerHTML = txt;
}

// Initiate the chart
Highcharts.mapChart('container', {

    chart: {
        map: 'countries/in/in-all'
    },

    title: {
        text: 'Highmaps basic lat/lon demo'
    },

    mapNavigation: {
        enabled: true
    },

    tooltip: {
        headerFormat: '',
        pointFormat: '<b>{point.name}</b><br>Lat: {point.lat}, Lon: {point.lon}'
    },

    series: [{
        // Use the gb-all map with no data as a basemap
        name: 'Basemap',
        borderColor: '#A0A0A0',
        nullColor: 'rgba(200, 200, 200, 0.3)',
        showInLegend: false
    }, {
        name: 'Separators',
        type: 'mapline',
        nullColor: '#707070',
        showInLegend: false,
        enableMouseTracking: false
    }, {
        // Specify points using lat/lon
        type: 'mappoint',
        name: 'Cities',
        color: Highcharts.getOptions().colors[1],
		data:[{'name': 'KO5490_1KM', 'lat': 28.477778000000004, 'lon': 77.129722},
 {'name': 'City1', 'lat': 28.5375, 'lon': 77.271694},
 {'name': 'City2', 'lat': 28.910079999999997, 'lon': 77.10876}]
     }]
});
```

### Combine all the above 3 in order into a single HTML File

<img src="https://raw.githubusercontent.com/anantguptadbl/anantguptadbl.github.io/master/images/Chart1.png" style="float: left; margin-right: 10px;" />

### Important Configurations

#### Map
In the line
``` javascript
chart: {
        map: 'countries/in/in-all'
    },
 ```
 We are mentioning the region in/in-all which means India. The list of all such regions is present here
 http://code.highcharts.com/mapdata/?_ga=2.240186051.15578447.1561097806-1754947431.1560948026
 
 #### Tooltip
 In the following code
 ```
 tooltip: {
        headerFormat: '',
        pointFormat: '<b>{point.name}</b><br>Lat: {point.lat}, Lon: {point.lon}'
    },

 ```
We are using three variables from the list of Dicts **lat** **lon** and **name**. You can add as many as you want here
