<template>
  <div>
    <h3>预约取件</h3>
    <a-form :form="form" @submit="handleSubmit">
      <a-form-item label="运单号" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }">
        <a-input
          placeholder="201907250002"
          v-decorator="[
          'note',
          {rules: [{ required: true, message: 'Please input your Transport-Number!' }]}
        ]"
        />
      </a-form-item>
      <a-form-item label="取件时间" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }">
        <a-input
          placeholder="2019-07-26 18:10:00"
          v-decorator="[
          'receiver',
          {rules: [{ required: true, message: 'Please input your Receiver-Name!' }]}
        ]"
        />
      </a-form-item>
      <a-button type="primary" html-type="submit">预约</a-button>&nbsp;&nbsp;&nbsp;&nbsp;
      <a-button type="primary" html-type="reset">取消</a-button>
    </a-form>
  </div>
</template>

<script>
import Vue from "vue";
import Antd from "ant-design-vue";
import "ant-design-vue/dist/antd.css";
Vue.config.productionTip = false;
Vue.use(Antd);

export default {
  data() {
    return {
      formLayout: "horizontal",
      form: this.$form.createForm(this)
    };
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log("Received values of form: ", values);
        }
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  text-align: center;
}
</style>
