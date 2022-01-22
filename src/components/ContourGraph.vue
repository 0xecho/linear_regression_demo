<template>
  <div>

    <div class="contour_graph">
    </div>
    
  </div>
</template>

<script>
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
  methods: {
    drawGraph() {
      // TODO: draw a contour graph
      // with the `right` data from points
      // and the mean squared error cost function
      // also mark the current m and b values on the graph as a circle point
    }
  },
  mounted() {
    this.drawGraph();
  },
};
</script>