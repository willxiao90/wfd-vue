<template>
  <div>
    <div class="panelRow">
      <div>{{i18n['label']}}：</div>
      <el-input
        style="width:90%; font-size:12px"
        :disabled="readOnly"
        :value="model.label"
        @input="(value) => {onChange('label', value)}"
      />
    </div>
    <!-- <div class="panelRow">
            <el-checkbox @change="(value) => onChange('hideIcon', value)"
                         :disabled="readOnly"
                         :value="!!model.hideIcon">{{i18n['hideIcon']}}</el-checkbox>
    </div>-->
    <div class="panelRow">
      <div>{{i18n['id']}}：</div>
      <el-input
        style="width:90%; font-size:12px"
        :disabled="readOnly"
        :value="model.id"
        @input="(value) => {onChange('id', value)}"
      />
    </div>
  </div>
</template>
<script>
export default {
  inject: ["i18n"],
  props: {
    model: {
      type: Object,
      default: () => ({})
    },
    onChange: {
      type: Function,
      default: () => {}
    },
    readOnly: {
      type: Boolean,
      default: false
    }
  }
};
</script>
