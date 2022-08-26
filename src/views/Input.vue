<template>
  <el-form ref="$form" :model="model" label-position="left" label-width="100px" size="small">
    <el-form-item :rules="rules.dan_hang_wen_ben" prop="dan_hang_wen_ben" label="MES码*">
      <el-input v-model="model.dan_hang_wen_ben" placeholder="请扫描二维码" autofocus clearable></el-input>
    </el-form-item>
    <el-row :gutter="20" type="flex" justify="start" align="top" tag="div">
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-form-item :rules="rules.input_1660101555747" prop="input_1660101555747" label="任务代号">
          <el-input v-model="model.input_1660101555747" placeholder="生产批次号" readonly clearable disabled></el-input>
        </el-form-item>
      </el-col>
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-form-item :rules="rules.input_1660101586507" prop="input_1660101586507" label="图号">
          <el-input v-model="model.input_1660101586507" placeholder="图号" readonly clearable disabled></el-input>
        </el-form-item>
      </el-col>
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-form-item :rules="rules.input_1660101628068" prop="input_1660101628068" label="编号">
          <el-input v-model="model.input_1660101628068" placeholder="编号" readonly clearable disabled></el-input>
        </el-form-item>
      </el-col>
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-form-item :rules="rules.input_1660109607063" prop="input_1660109607063" label="校试人员">
          <el-input v-model="model.input_1660109607063" placeholder="姓名" readonly clearable></el-input>
        </el-form-item>
      </el-col>
    </el-row>
    <el-form-item :rules="rules.input_1660195074572" prop="input_1660195074572" label="仪表码*">
      <el-input v-model="model.input_1660195074572" placeholder="请扫描仪表码" clearable></el-input>
    </el-form-item>
    <el-row :gutter="20" type="flex" justify="start" align="top" tag="div">
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-form-item :rules="rules.input_1660195160921" prop="input_1660195160921" label="仪表信息">
          <el-input v-model="model.input_1660195160921" placeholder="仪表名称型号" readonly clearable></el-input>
        </el-form-item>
      </el-col>
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-form-item :rules="rules.input_1660195193065" prop="input_1660195193065" label="仪表编号">
          <el-input v-model="model.input_1660195193065" placeholder="仪表编号" readonly clearable></el-input>
        </el-form-item>
      </el-col>
    </el-row>
    <el-divider></el-divider>
    <el-form-item :rules="rules.radio_group_1660101308666" prop="radio_group_1660101308666" label="测试结果*">
      <el-radio-group v-model="model.radio_group_1660101308666" text-color="#ffffff" fill="#409EFF" :class="['111']">
        <el-radio v-for="(item, $index) in radio_group_1660101308666_data" :key="item.value" :label="item.value" :border="!!item.border" :disabled="!!item.disabled">{{item.label}}</el-radio>
      </el-radio-group>
    </el-form-item>
    <el-divider></el-divider>
    <el-row :gutter="20" type="flex" justify="start" align="top" tag="div">
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-form-item :rules="rules.select_group_1660197056199" prop="select_group_1660197056199" label="故障现象">
          <el-select v-model="model.select_group_1660197056199" placeholder="请选择" :style="{width: '100%'}">
            <el-option-group v-for="(group, $groupIndex) in select_group_1660197056199_data" :key="group.label" :label="group.label" :disabled="!!group.disabled">
              <el-option v-for="(item, $index) in (group.data || [])" :key="item.value" :label="item.label" :value="item.value" :disabled="!!item.disabled"></el-option>
            </el-option-group>
          </el-select>
        </el-form-item>
      </el-col>
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-form-item :rules="rules.select_1660205609943" prop="select_1660205609943" label="故障原因">
          <el-select v-model="model.select_1660205609943" multiple placeholder="请选择" :style="{width: '100%'}">
            <el-option v-for="(item, $index) in select_1660205609943_data" :key="item.value" :label="item.label" :value="item.value" :disabled="!!item.disabled"></el-option>
          </el-select>
        </el-form-item>
      </el-col>
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-form-item :rules="rules.select_1660197828650" prop="select_1660197828650" label="故障位号类别">
          <el-select v-model="model.select_1660197828650" multiple placeholder="请选择" :style="{width: '100%'}">
            <el-option v-for="(item, $index) in select_1660197828650_data" :key="item.value" :label="item.label" :value="item.value" :disabled="!!item.disabled"></el-option>
          </el-select>
        </el-form-item>
      </el-col>
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-form-item :rules="rules.input_1660352715875" prop="input_1660352715875" label="故障位号序号">
          <el-input v-model="model.input_1660352715875" placeholder="请输入" clearable></el-input>
        </el-form-item>
      </el-col>
    </el-row>
    <el-row :gutter="20" type="flex" justify="start" align="top" tag="div">
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">

      </el-col>
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-form-item :rules="rules.select_tree_1660196912242" prop="select_tree_1660196912242" label="维修人">
          <j-el-select-tree data.sync="model.select_tree_1660196912242" :tree-data="select_tree_1660196912242_tree_data" highlight-current :style="{width: '100%'}"></j-el-select-tree>
        </el-form-item>
      </el-col>
    </el-row>
    <el-row :gutter="20" type="flex" justify="start" align="top" tag="div">
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-button size="small" type="primary" icon="el-icon-check" @click="submit">提 交</el-button>
      </el-col>
      <el-col :span="12" :offset="0" :push="0" :pull="0" tag="div">
        <el-button size="small" type="primary" icon="el-icon-check" @click="submit">暂存</el-button>
      </el-col>
    </el-row>
  </el-form>
</template>

<script>
export default {
  name: "Input.vue",

// import JElSelectTree from "./JElSelectTree";


  components: {
    // JElSelectTree,

  },
  data() {
    return {
      forms: ['$form'],
      model: {
        dan_hang_wen_ben: '',
        input_1660101555747: '',
        input_1660101586507: '',
        input_1660101628068: '',
        input_1660109607063: '',
        input_1660195074572: '',
        input_1660195160921: '',
        input_1660195193065: '',
        radio_group_1660101308666: '1',
        select_group_1660197056199: '',
        select_1660205609943: [],
        select_1660197828650: [],
        input_1660352715875: '',
        select_tree_1660196912242_label: '',
        select_tree_1660196912242: ''
      },
      rules: {
        dan_hang_wen_ben: [],
        input_1660101555747: [],
        input_1660101586507: [],
        input_1660101628068: [],
        input_1660109607063: [],
        input_1660195074572: [],
        input_1660195160921: [],
        input_1660195193065: [],
        radio_group_1660101308666: [],
        select_group_1660197056199: [],
        select_1660205609943: [],
        select_1660197828650: [],
        input_1660352715875: [],
        select_tree_1660196912242: []
      },
      radio_group_1660101308666_data: [{
        label: '合格',
        value: '1',
        disabled: false,
        border: false
      }, {
        label: '不合格',
        value: '2',
        disabled: false,
        border: false
      }],
      select_group_1660197056199_data: [{
        label: '',
        disabled: false,
        data: [{
          label: '有源滤波器76.3kHz信号无输出',
          value: '1-1',
          disabled: false
        }, {
          label: '解调器电路3.5dB增益调不上去',
          value: '1-2',
          disabled: false
        }, {
          label: '解调器电路方波无输出',
          value: '1-3',
          disabled: false
        }, {
          label: '微机复位信号无',
          value: '1-4',
          disabled: false
        }, {
          label: '微机应答信号无',
          value: '1-5',
          disabled: false
        }, {
          label: '阻抗不可调',
          value: '1-6',
          disabled: false
        }, {
          label: '相位不可调',
          value: '1-7',
          disabled: false
        }, {
          label: '功率监测波形异常',
          value: '1-8',
          disabled: false
        }, {
          label: '电压驻波比波形异常',
          value: '1-9',
          disabled: false
        }, {
          label: '驻波比报警波形异常',
          value: '1-10',
          disabled: false
        }, {
          label: '保护电路异常',
          value: '1-11',
          disabled: false
        }, {
          label: '其他',
          value: '1-12',
          disabled: false
        }]
      }],
      select_1660205609943_data: [{
        label: '缺焊',
        value: '1',
        disabled: false
      }, {
        label: '漏焊',
        value: '2',
        disabled: false
      }, {
        label: '虚焊',
        value: '3',
        disabled: false
      }, {
        label: '连焊',
        value: '4',
        disabled: false
      }, {
        label: '器件失效',
        value: '5',
        disabled: false
      }, {
        label: '其他',
        value: '6',
        disabled: false
      }],
      select_1660197828650_data: [{
        label: 'A',
        value: '1',
        '': false
      }, {
        label: 'B',
        value: '2',
        '': false
      }, {
        label: 'C',
        value: '3',
        '': false
      }, {
        label: 'D',
        value: '4',
        '': false
      }, {
        label: 'E',
        value: '5',
        '': false
      }, {
        label: 'K',
        value: '6',
        '': false
      }, {
        label: 'L',
        value: '7',
        '': false
      }, {
        label: 'N',
        value: '8',
        '': false
      }, {
        label: 'R',
        value: '9',
        '': false
      }, {
        label: 'T',
        value: '10',
        '': false
      }, {
        label: 'Y',
        value: '11',
        '': false
      }, {
        label: 'V',
        value: '12',
        '': false
      }, {
        label: 'XP',
        value: '13',
        '': false
      }, {
        label: 'JMP',
        value: '14',
        '': false
      }],
      select_tree_1660196912242_tree_data: [{
        label: '校试一班',
        value: '1',
        disabled: true,
        leaf: undefined,
        children: [{
          label: '刘毅',
          value: '111',
          disabled: false,
          leaf: undefined,
          children: []
        }, {
          label: '王谦',
          value: '123',
          disabled: false,
          leaf: undefined,
          children: []
        }, {
          label: '刘莉',
          value: '2',
          disabled: false,
          leaf: undefined,
          children: []
        }]
      }, {
        label: '校试二班',
        value: 2,
        disabled: true,
        leaf: undefined,
        children: [{
          label: '胡润新',
          value: 21,
          disabled: false,
          leaf: undefined,
          children: []
        }, {
          label: '2-2',
          value: 22,
          disabled: true,
          leaf: undefined,
          children: []
        }]
      }],
      submit_loading: false
    };
  },
  computed: {

  },
  methods: {
    submit() {
      Promise.all(this.forms.map(form => this.$refs[form].validate()))
          .then(() => {
            this.submit_loading = true;
            // TODO demo
            console.log(this.model);
            setTimeout(() => {
              this.submit_loading = false;
            }, 3000);
          });
    },
  },
  created() {

  }
}
</script>

<style scoped>

</style>