# Haasonline Charting Engine

## Introduction
Haasonline's Charting Engine (HCE) is a powerful and 100% custom build engine. By combining the advantages of HTML5 canvas and d3.js library we have created a fast, reliable, dynamic and heavily modifiable charting engine with support for touch screens. The HCE supports up to 8 different price chart styles, an orderbook chart on axis, 10 indicators styles, 23 drawing tools, double y-axis and both pre-calculated and in-house indicators can be rendered. Currently, there are 44 in-house indicators supported.

## Features
 - Price chart with 11 different styles
 - Indicator and overlay charts with 15 different styles and endless combinations
 - Backend calculated indicator data supported
 - 39 in-house indicators
 - Mobile friendly
 - Touch friendly
 - Supported browsers: Chrome, Edge, Firefox & Opera
 - Easy to use API
 - Orderbookchart in y-axis
 - Double y-axis for overlaying data
 - 22 drawing tools
 - Im- & export drawing data
 - Take snapshot and convert to BMP
 - Live update supported
 - Fully customizable 


## Initialize
Option list is located [here][1]
```javascript
var options = { 
    wrapperID : "#chart" 
};

var plotter = createPlotter(options);
```

## Plot data
Plot data will empty the container and re-initialize the engine.

Data structure is located [here][0]
```javascript
plotter.plotData(data);
```

## Replot data
Replot data if more efficient if only the (price)data changes.
```javascript
var moveIfLAstTimestampChanged   = true;
var moveToRightDate              = false // or a unix timestamp
plotter.rePlot(data, moveIfLAstTimestampChanged, moveToRightDate);
```

## Clear chart
Clears the chart of any data
```javascript
plotter.clearChart();
```

## Price tick update
Overwrites the last price tick with the data below
```javascript
var data = {
    high   : 100.15
    low    : 99.62
    close  : 100.02
    volume : 1264.26
};
plotter.tickUpdate();
```

## Trade update
Combines the last price tick with the data below
```javascript
var close = 100.02;
var high = 102.26;
var low = 99.3;
var volume = 12.8;
plotter.tradeUpdate(close, high, low, volume);
```

## Move chart to data
The setRightDate allows you to programmaticly controll the charts timerange
```javascript
// rightData should be unix timestamp
var rightDate = 123457866;
plotter.setRightDate(rightDate);
```

## Interaction tool color control
Supported color types:
- string (yellow,blue)
- HEX (#000, #FF0012)
- rgb/rgba (rgb(255,255,255), rgba(123,123,123,0.8))

enumIntercationTool can be found [here][2]

```javascript
plotter.setToolColor("#FF0012");
plotter.setToolFill("#FF0012");
plotter.setToolTextColor("#FF0012");
plotter.setTool(enumInteractionTool.Line)
```

## Get art
Art data structure can be found [here][3]
```javascript
var data = plotter.getArt();
var json = JSON.stringify(data);
```

## Clear art
Clears all art on the chart
```javascript
plotter.clearArt();
```

## Insert art
Problematically insert art into the chart.
enumIntercationTool can be found [here][4]
```javascript
plotter.insertArt(enumIntercationTool, data);
```

## Get last date
Returns the last date of the chart
```javascript
var date = plotter.getLastDate();
```

## Move chart
Move the chart left or right
```javascript
var toTheRight = true;
plotter.moveChart(toTheRight);
```

## Current view
Return the current visible time range
```javascript
// Data structure
var data = {
    leftDate    : // DataTime object
    rightDate   : // DateTime object,
    left        : int, // Left key in timeline data
    right       : int, // Left key in timeline data,
    zoom        : int // Zoom level
}
plotter.moveChart(toTheRight);
```

## Color scheme
Set a new color scheme. After this rePlot the chart to apply the changes
```javascript
plotter.setColorScheme(colorScheme);
```

## Resize chart
The engine automatically reacts to resizing of the windows, but if the container is resized manually this needs to be called to resize the chart.
```javascript
plotter.resizePlot();
```

[0]:https://github.com/Vieuxx/HaasolineCharts/wiki/Data-structure-and-enums
[1]:https://github.com/Vieuxx/HaasolineCharts/wiki/Front-end-options
[2]:https://github.com/Vieuxx/HaasolineCharts/wiki/Front-end-options
