<template>
  <div>
    <b-row>
      <h5>Line Data</h5>
    </b-row>
    <b-row class="mb-2">
      <span>m = </span>
      <b-col class="col-lg-6">
        <b-form-input
          @input="update"
          v-model="input.m"
          type="number"
          step="0.1"
          size="sm"
        ></b-form-input>
      </b-col>
    </b-row>
    <b-row class="mb-2">
      <span>b = </span>
      <b-col class="col-lg-6">
        <b-form-input
          @input="update"
          v-model="input.b"
          type="number"
          step="0.1"
          size="sm"
        ></b-form-input>
      </b-col>
    </b-row>
    <b-row>
      <h5>Points Data</h5>
      <table class="table table-sm table-bordered col-sm-9">
        <tr>
          <th>x</th>
          <th>y</th>
        </tr>
        <tr v-for="(point, index) in points" :key="index">
          <td>
            {{ point.x }}
          </td>
          <td>
            {{ point.y }}
          </td>
          <td class="col-sm-1">
            <button class="btn btn-sm btn-danger" @click="removePoint(index)">
              <font-awesome-icon icon="trash-alt" size="sm"></font-awesome-icon>
            </button>
          </td>
        </tr>
        <tr>
          <td>
            <b-form-input
              v-model="newPoint.x"
              type="number"
              step="0.1"
              size="sm"
            ></b-form-input>
          </td>
          <td>
            <b-form-input
              v-model="newPoint.y"
              type="number"
              step="0.1"
              size="sm"
            ></b-form-input>
          </td>
          <td>
            <button class="btn btn-sm btn-success" @click="addPoint">
              <font-awesome-icon icon="plus"></font-awesome-icon>
            </button>
          </td>
        </tr>
      </table>
    </b-row>
  </div>
</template>

<script>
export default {
  name: "SideBarInput",
  props:{
    m: Number,
    b: Number,
    points: Array,
  },
  data() {
    return {
      newPoint: { x: 0, y: 0 },
      input: {
        m: this.m || 1,
        b: this.b || 0,
      },
    }
  },
  methods: {
    addPoint() {
      this.points.push(this.newPoint);
      this.newPoint = { x: 0, y: 0 };
      this.$emit("pointsChanged", this.points);
    },
    removePoint(index) {
      this.points.splice(index, 1);
    },
    update() {
      this.input.m = parseFloat(this.input.m) || 0;
      this.input.b = parseFloat(this.input.b) || 0;
      this.$emit("input", this.input);
    },
  },
};
</script>