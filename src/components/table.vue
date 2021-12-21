<template>
  <div class="Mytable">{{ title }}</div>
  <div class="demo01">
    <form action="#" class="Myfrom">
      <label for="">请输入快递重量(kg)：</label>
      <input
        type="text"
        :placeholder="iptVue"
        v-model="num"
        style="color: #3c3c3c"
        :onfocus="clearData"
        :onblur="clearData"
      />
      <div class="Value">
        <label for="" :style="{ fontSize: fsize + 'px' }">邮费：</label>
        <input
          v-model="result"
          type="text"
          style="height: 30px; margin-left: 85px"
        />
      </div>
      <div id="Computed">
        <input class="ipt" type="button" value="计算邮费" @click="getResult" />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      result: null,
      num: null,
      iptVue: '例如22',
    }
  },
  methods: {
    getResult() {
      if (typeof this.num !== Number) {
        alert('请输入大于零的数字')
        this.num = null
        return
      }
      if (this.num == 0 || this.num == null) {
        this.result = null
        alert('请输入大于零的数字')
        this.num = null
        return
      }
      this.num <= 1
        ? (this.result = 10 + '元')
        : (this.result = (this.num - 1) * 5 + 10 + '元')
      this.num = null
    },
    clearData() {
      this.iptVue === '' ? (this.iptVue = '请输入') : (this.iptVue = '')
    },
  },
  name: 'Table',
  props: {
    title: {
      type: String,
      default: 'MyTable',
    },
    fsize: {
      type: Number,
      default: 30,
    },
  },
}
</script>

<style lang="less" scoped>
// 首页
.Mytable {
  position: fixed;
  top: 0;
  left: 0;
  text-align: center;
  width: 100%;
  height: 45px;
  font-size: 20px;
}
// 计算表格
.demo01 {
  margin-top: 45px;
  height: 250px;
  text-align: center;
  .Myfrom {
    font-size: 18px;
  }
  .Value {
    label {
      color: red;
      position: relative;
      left: 95px;
    }
  }
  #Computed {
    padding: 10px 0;
    .ipt {
      border-radius: 8px 8px 8px 8px;
      color: blue;
      margin-left: 170px;
    }
  }
}
</style>
