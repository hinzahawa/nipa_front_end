<template>
  <div id="form-ex">
    <b-container class="bv-example-row mb-1">
      <b-row>
        <b-col class="mb-2" cols="12"><h5>จำนวนเงิน: (THB)</h5></b-col>
      </b-row>
      <b-row>
        <b-col class="mb-3" cols="12">
          <b-form-input type="number" v-model="money" placeholder="กรุณากรอกเลข (บาท)"></b-form-input>
        </b-col>
      </b-row>
      <b-row>
        <b-col class="mb-3" cols="12">
          <h5>แปลงสกุลเงินหน่วยเป็น</h5>
        </b-col>
      </b-row>
      <b-row>
        <b-col class="mb-3" cols="12">
          <b-form-select v-model="selected1" :options="options1"></b-form-select><br>
        </b-col>
      </b-row>
      <b-row>
        <b-col class="mb-3" cols="12">
          <b-button  variant="success" @click="cal()">คำนวน</b-button>
        </b-col>
      </b-row>
      <b-row>
        <b-col class="mb-3" cols="12">
          <h5 id="result">ผลลัพธ์ : {{sum}}</h5>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  name: 'ExchangeMoney',
  data () {
    return {
      data: {},
      money: '',
      selected1: null,
      selected2: null,
      options1: [
        { value: null, text: 'กรุณาเลือกสกุลเงินที่จะแปลง' }
      ],
      sum: 0
    }
  },
  methods: {
    getcurrency () {
      this.axios.get('http://localhost:3000/getcurrency').then((response) => {
        console.log(response.data)
        response.data.forEach(element => {
          this.options1.push({ value: element.currency_id, text: element.currency_name_th })
        })
      })
    },
    cal () {
      this.data = {
        money: this.money,
        ex1: this.selected1,
        ex2: this.selected2
      }
      this.axios.post('http://localhost:3000/exchangemoney', this.data).then((response) => {
        this.sum = response.data.sum
      })
    }
  },
  created () {
    this.getcurrency()
  }
}
</script>
<style lang="css" scoped>
  .custom-select {
    width: 35%;
  }
  .form-control {
    display: inline-block;
    width: 30%
  }
  #form-ex{
    position: relative;
    top: 10%;
  }
  #result{
    background-color: white;
    display: inline;
  }
</style>
