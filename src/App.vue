<template>
  <div id="app">
    Linear Regression Demo :-)
    <b-container>
      <b-row>
        <b-col class="col-md-2">
          <SideBarInput />
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
import SideBarInput from './components/SideBarInput.vue'

export default {
  name: 'App',
  components: {
    SideBarInput
  },
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
