<template>
  <div id="app">
    Linear Regression Demo :-)
    <b-container>
      <b-row>
        <b-col class="col-md-2">
          <SideBarInput :points="points" v-model="lineData" @pointsChanged="pointsChanged"/>
        </b-col>
        <b-col>
          <div class="graph">
          </div>
        </b-col>
        <b-col>
          Cost Function Contour Graph
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import SideBarInput from './components/SideBarInput.vue'
import * as d3 from 'd3';

export default {
  name: 'App',
  components: {
    SideBarInput,
  },
  data(){
    return {
      points: [
        {x: 100, y: 100},
      ],
      lineData: {
        m: 1,
        b: 0
      },
      width: 500,
      height: 500,
    }
  },methods: {
    drawGraph() {
      d3.select(".graph").
        selectAll("*").
        remove();
      let svg = d3.select(".graph")
        .append("svg")
        .attr("width", this.width)
        .attr("height", this.height)
        .style("border", "1px solid black")

      this.points.forEach(point => {
        svg
          .append("circle")
          .attr("cx", (point.x))
          .attr("cy", this.width-(point.y))
          .attr("r", 3)
          .style("fill", "red")
          .style("stroke", "black")
          .style("stroke-width", "1px")
      });
      
      // add line for mx + b
      svg
        .append("line")
        .attr("x1", 0)
        .attr("y1", this.width - (this.lineData.m * 0 + this.lineData.b))
        .attr("x2", this.width)
        .attr("y2", this.width - (this.lineData.m * this.width + this.lineData.b))
        .style("stroke", "black")
        .style("stroke-width", "1px")
    },
    pointsChanged(points) {
      this.points = points;
      this.drawGraph();
    },

  },
  mounted() {
    this.drawGraph();
  },
  watch: {
    lineData: {
      handler() {
        this.drawGraph();
      },
      deep: true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type=number] {
  -moz-appearance: textfield;
}
</style>
