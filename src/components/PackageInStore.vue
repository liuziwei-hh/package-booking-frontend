<template>
  <div>
    <h3>包裹入库</h3>
    <a-form :form="form" @submit="handleSubmit">
      <a-form-item label="运单号" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }">
        <a-input
          placeholder="201907240001"
          v-decorator="[
          'note',
          {rules: [{ required: true, message: 'Please input your Transport-Number!' }]}
        ]"
        />
      </a-form-item>
      <a-form-item label="收件人" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }">
        <a-input
          placeholder="李亚娥"
          v-decorator="[
          'receiver',
          {rules: [{ required: true, message: 'Please input your Receiver-Name!' }]}
        ]"
        />
      </a-form-item>
      <a-form-item label="电话" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }">
        <a-input
          placeholder="18912345678"
          v-decorator="[
          'tel',
          {rules: [{ required: true, message: 'Please input your Tel-Number!' }]}
        ]"
        />
      </a-form-item>
      <a-form-item label="重量" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }">
        <a-input
          placeholder="3KG"
          v-decorator="[
          'weight',
          {rules: [{ required: true, message: 'Please input your Item-Weight!' }]}
        ]"
        />
      </a-form-item>
      <a-button type="primary" html-type="提交">Submit</a-button>
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
