<template>
  <div>
    <b-row>
      <h5>Line Data</h5>
    </b-row>
    <b-row class="mb-2">
      <span>m = </span>
      <b-col class="col-lg-6">
        <b-form-input
          v-model="m"
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
          v-model="b"
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
  data() {
    return {
      m: 1,
      b: 0,
      points: [
        { x: 1, y: 1 },
        { x: 2, y: 3 },
        { x: 3, y: 3 },
        { x: 4, y: 5 },
        { x: 5, y: 4 },
        { x: 6, y: 7 },
        { x: 7, y: 6 },
        { x: 8, y: 8 },
        { x: 9, y: 10 },
        { x: 10, y: 9 },
      ],
      newPoint: { x: 0, y: 0 },
    }
  },
};
</script>