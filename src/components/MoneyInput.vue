<template>
  <div class="money">
    <input type="text" v-model="money">
    <p>{{ moneyNum}}</p>
  </div>
</template>

<script>
export default {
  name: 'moneyinput',
  data () {
    return {
      money: "",
      moneyNum: 0,
      maxValue: 9999999
    }
  },
  methods: {
    formatMoney: function(number){
      if(!number){
        return '';
      }
      // 拿到整数部分
      let i = parseInt(number.toFixed(2), 10);
      let dec = number - i;
      // 整除3的时候补上一个分隔符
      let j = (j = i.length) > 3 ? j % 3 : 0; //拿到余数，从0到余数开始加分隔符
      return "$" + (j ? i.toString().substr(0, j) + "," : "") + i.toString().substr(j).replace(/(\d{3})(?=\d)/g, "$1" + ",") + (dec != 0 ? parseFloat(dec.toFixed(2)).toString().slice(1) : "");
    },

    toNumber: function(str) {
      return str.replace(/^\$/, '').replace(/,/g, '');
    },
    saveNum: function(input){

      // 存值为数字
      input == '' ? this.moneyNum = 0 :this.moneyNum = parseFloat(this.toNumber(this.money));

      // 限制最大值
      this.moneyNum = this.moneyNum > this.maxValue ? this.maxValue : this.moneyNum;
      //防止输入.的时候更新数据
      if(input.substr(input.length - 1) == "."){
        return;
      }
      // 把数值格式化以后还原到input框内
      this.money = this.formatMoney(this.moneyNum);
    }
  },
  watch: {
    money: 'saveNum'
    }
  }

</script>

<style>
input {
  text-align: right;
}
</style>
