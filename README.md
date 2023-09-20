# RealTimeData

This is a simple real-time chart that demonstrates how to use Chart.js to create a line chart that updates in real time.

### Prerequisites

To run this project, you will need the following:

- Node.js installed on your system
- A code editor such as Visual Studio Code



### Usage

The chart will automatically start updating in real time. You can change the data that is being plotted by editing the `data` array in the `index.js` file.

### Code Explanation

The code for this project is relatively simple. Let's go through it step by step.

#### HTML

The HTML file for this project is very simple. It just includes the necessary HTML elements and links to the JavaScript and CSS files.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Real-Time Chart</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div id="div">
      <canvas id="realTimeChart"></canvas>
    </div>

    <script src="index.js"></script>
  </body>
</html>
```

#### CSS

The CSS file for this project is also very simple. It just sets the width and height of the chart.

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
canvas {
  max-width: 100%;
  height: auto;
}
#div {
  width: 500px;
  height: 500px;
}
```

#### JavaScript

The JavaScript file for this project is where the magic happens. This is where we create the chart and update it in real time.

```javascript
const ctx = document.getElementById("realTimeChart").getContext("2d");
let chart;
const initialData = {
  labels: [],
  datasets: [
    {
      label: "Price",
      data: [],
      borderColor: "rgba(75, 192, 192, 1)",
      borderWidth: 1,
      fill: false,
    },
  ],
};
const chartConfig = {
  type: "line",
  data: initialData,
  options: {
    scales: {
      x: {
        type: "linear",
        position: "bottom",
        title: {
          display: true,
          text: "Time",
        },
      },
      y: {
        beginAtZero: true,
        title: {
          display: true,
          text: "Price",
        },
      },
    },
    animation: false,
  },
};
chart = new Chart(ctx, chartConfig);
function addData() {
  const newData = Math.random() * 500;
  chart.data.labels.push(chart.data.labels.length);
  chart.data.datasets[0].data.push(newData);
  chart.update();
}
setInterval(addData, 1000);
```
