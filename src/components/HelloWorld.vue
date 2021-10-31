<template>
  <div class="hello">
    <button style="height:80px; width:80px;" @click="addTableElement()">GENERATE TABLE</button>
    <table>
      <tr v-for="ir in rows" :key="ir" style="height:80px" >
        <td v-for="ic in columns" :key="ic" style="width:80px" :id="convertToIndex(ic,ir)"><button style="height:80px; width:80px;">{{convertToIndex(ic,ir)}}</button></td>
      </tr>
    </table>

  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      rows:[],
      columns:[],
      trIndex: 3,
      tdIndex: 3,
      ir:0,
      ic:0,
      tableGenerated: false
    }
  },
  methods: {
    addTableElement(){

      if(!this.tableGenerated){
  
        for(this.ir = 1; this.ir <= this.trIndex; this.ir++) {
          this.rows.push(this.ir);
        }
        for(this.ic = 1; this.ic <= this.tdIndex; this.ic++) {
          this.columns.push(this.ic);
        }
        this.tableGenerated = true;
      }else{
        alert("Table already generated !");
      }
    },
    convertToIndex(num1, num2){

        if(num2 == 1){
          num1 += 0;
        } else if(num2 > 1){
          num1 += this.tdIndex*(num2-1);
        }
      return num1;
    }
  },
  /*mounted () {
    this.addTableElement();
  }*/
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table, tr, td {
  border: 1px solid black;
  border-collapse: collapse;
}
</style>
