<template>
  <div id="app">
    Linear Regression Demo :-)
    <b-container class="bv-example-row bv-example-row-flex-cols">
      <b-row>
        <b-col>
          <b-row>
            Line Data
          </b-row>
          <b-row>
            Points Data
          </b-row>
        </b-col>
        <b-col>
          Points + Line Graph
        </b-col>
        <b-col>
          Cost Function Contour Graph
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
    
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
</style>
