<template>
  <div>
    <!-- <div class="panelRow">
      <div>{{i18n['label']}}：</div>
      <el-input
        style="width:90%; font-size:12px"
        :disabled="readOnly"
        :value="model.label"
        @input="(value) => {onChange('label', value)}"
      />
    </div>-->
    <!-- <div class="panelRow">
            <el-checkbox @change="(value) => onChange('hideIcon', value)"
                         :disabled="readOnly"
                         :value="!!model.hideIcon">{{i18n['hideIcon']}}</el-checkbox>
    </div>-->
    <!-- <div class="panelRow">
      <div>{{i18n['jobId']}}：</div>
      <el-input
        style="width:90%; font-size:12px"
        :disabled="readOnly"
        :value="model.jobId"
        @input="(value) => {onChange('jobId', value)}"
      />
    </div>-->
    <div class="panelRow">
      <div>请选择任务：</div>
      <el-select
        style="width:90%; font-size:12px"
        placeholder="请选择"
        :disabled="readOnly"
        :value="model.jobId"
        :filterable="true"
        :filter-method="(input, option) => option.props.children.toLowerCase().indexOf(input.toLowerCase()) >= 0"
        @change="onJobChange"
      >
        <el-option v-for="item in jobs" :key="item.id" :label="item.name" :value="item.id" />
      </el-select>
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
    },
    jobs: {
      type: Array,
      default: () => []
    }
  },
  computed: {
    jobMap() {
      const map = {};
      this.jobs.forEach(v => {
        map[v.id] = v.name;
      });
      return map;
    }
  },
  methods: {
    onJobChange(id) {
      this.onChange("jobId", id);
      this.onChange("label", this.jobMap[id]);
    }
  }
};
</script>
