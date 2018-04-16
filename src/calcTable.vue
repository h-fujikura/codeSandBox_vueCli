<template>
  <div>
    <table>
      <tr>
        <th>商品名</th>
        <th>単価</th>
        <th>個数</th>
        <th>行計</th>
        <th></th>
      </tr>
      <tr v-for="(item, index) in items" 
              :key="item.name">
        <td>
          <input type="text" v-model="item.name" >
        </td>
        <td>
          <input type="number" v-model.number="item.tanka" >
        </td>
        <td>
          <input type="number" v-model.number="item.qty" >
        </td>
        <td class="taRight" >
          {{addComma(item.qty * item.tanka)}} 円
        </td>
        <td>
          <button @click="removeData(index)">行削除</button>
        </td>  
      </tr>        
      <tr>
        <td colspan="2">計</td>
        <td class="taRight">{{qtySum}}個</td>
        <td class="taRight">{{addComma(uriageSum)}} 円</td>
        <td></td>
      </tr>
    </table>
    <button @click="addRow">
      行追加
    </button>
</div>  
</template>

<script>
const formatter = new Intl.NumberFormat('ja-JP');
export default {
  name: "App",
  data () {
    return {
      recieveItems: this.items
    }
  },
  props:{
    items: Array 
  },
  methods: {
		removeData(idx) {
			this.items.splice(idx,1)
		},
		addRow(){
      this.items.push(
        {name: '', tanka: null, qty: null }
      )
		},
    addComma(num) {
      return formatter.format(num)
    }
  },
  computed: {
    qtySum() {
      return this.items.reduce((pre, cur) => {
        return  pre + cur.qty
      },0)
    },
    uriageSum() {
      return this.items.reduce((pre, cur) => {
        return  pre + cur.qty * cur.tanka
      },0)
    }  
  }
};
</script>
  <style>
  section {
    border-bottom: 2px solid #42b983;
    padding: 1rem;
  }
  input {
    text-align: right;
    width: 90%;
    font-size: 1rem;
  }
  table,
  td,
  th {
    border: 1px solid #000;
    border-collapse: collapse;
  }
  table {
    table-layout: fixed;
    width: 100%;
    text-align: center;
  }
  td.taRight {
    text-align: right;
  }
</style>