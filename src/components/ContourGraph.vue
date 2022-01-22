<template>
  <div>

    <div class="contour_graph">
    </div>
    
  </div>
</template>

<script>
import * as d3 from 'd3';
import {contours} from 'd3-contour';

export default {
  name: "ContourGraph",
  props:{
    points: {
      type: Array,
      required: true
    },
    width: Number,
    height: Number,
    m: Number,
    b: Number,
  },
  data() {
    return {
      minM: 0,
      maxM: 10,
      minB: 0,
      maxB: 10,
    }
  },
  methods: {
    drawGraph() {
      // TODO: draw a contour graph
      // with the `right` data from points
      // and the mean squared error cost function
      // also mark the current m and b values on the graph as a circle point
      const n = this.maxM-this.minM, 
      m = this.maxM-this.minM,
      values = new Array(n * m);
      for (let i = this.minM; i < this.maxM; i++) {
        for (let j = this.minB; j < this.maxB; j++) {
          values[i * m + j] = this.costFunction(i, j);
        }
      }
      // fit 350x350 square to the screen
      let contour = contours()
        .size([n,m]) (values)
      let svg = d3.select(".contour_graph")
        .append("svg")
        .attr("width", this.width)
        .attr("height", this.height)
        .style("border", "1px solid black")
           
           
      svg.selectAll("path")
        .data(contour)
        .enter()
        .append("path")
        .attr("d", d3.geoPath())
        .style("fill", "none")
        .style("stroke", "black")
        .style("stroke-width", "1px")
      
      // TODO: Not sure d3 is the best way to do this, need to reevaluate shit
      
      
    },
    costFunction(m, b) {
      let sum = 0;
      for (let i = 0; i<this.points.length; i++) {
        sum += Math.pow(this.points[i].x - (m*this.points[i].y + b), 2)
      }
      return sum / this.points.length
    },
  },
  mounted() {
    this.drawGraph();
  },
};
</script>

<style scoped>
svg {
  width: 100%;
}
</style>