<template>
  <div class="hello">
    <button style="height: 80px; width: 80px" @click="generateGrid()">
      GENERATE GRİD
    </button>
    <table cellpadding="0" cellspacing="0">
      <tr v-for="ir in rows" :key="ir">
        <td
          v-for="ic in columns"
          :key="ic"
          style="height: 80px; width: 80px"
          :id="convertToIndex(ic, ir)"
        >
          <div style="width: 100%; height: 100%">
            <button
              style="width: 100%; height: 100%"
              :id="convertToIndex(ic, ir)"
            >
              {{ convertToIndex(ic, ir) }}
            </button>
          </div>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      rows: [],
      columns: [],
      trSize: 4,
      tdSize: 4,
      ir: 0,
      ic: 0,
      tableGenerated: false,
    };
  },
  methods: {
    generateGrid() {
      if (!this.tableGenerated) {
        for (this.ir = 1; this.ir <= this.trSize; this.ir++) {
          this.rows.push(this.ir);
        }
        for (this.ic = 1; this.ic <= this.tdSize; this.ic++) {
          this.columns.push(this.ic);
        }
        this.tableGenerated = true;
      } else {
        alert("Grid already generated !");
      }
    },
    convertToIndex(num1, num2) {
      num1 += this.tdSize * (num2 - 1);
      return num1;
    },
  },
  /*mounted () {
    this.addTableElement();
  }*/
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table,
tr,
td {
  border: 1px solid black;
  border-collapse: collapse;
}
</style>
