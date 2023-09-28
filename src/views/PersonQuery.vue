


<template>
  <div class="container">
    <!-- <Heads>

    </Heads> -->
    <el-form ref="form" :model="form" label-position="left" label-width="100px">
      <el-row>
        <el-col :span="10">
          <div></div>
        </el-col>
        <el-col :span="11">
          <el-form-item label="姓名" placeholder="请输入姓名">
            <div class='left'>
              <el-input v-model="form.name" style="width: 60%;float: left;"></el-input>
            </div>
          </el-form-item>
        </el-col>

        <el-col :span="11">
          <el-form-item label="年龄">
            <el-input v-model="form.age" placeholder="输入年龄" style="width: 60%;float: left;"></el-input>
          </el-form-item>
        </el-col>
      </el-row>

      <el-row>
        <el-col :span="11">
          <el-form-item label="出生日期">
            <el-date-picker v-model="form.date1" type="date" placeholder="选择日期" style="width: 60%;float: left;">
            </el-date-picker>
          </el-form-item>
        </el-col>

        <el-col :span="11">
          <el-form-item label="性别">
            <el-select label="性别" v-model="form.sex" placeholder="性别" style="width: 60%;float: left;">
              <el-option label="男" value="man"></el-option>
              <el-option label="女" value="woman"></el-option>
            </el-select>
          </el-form-item>
        </el-col>
      </el-row>

      <el-row>
        <el-col :span="11">
          <el-form-item label="籍贯">
            <el-input v-model="form.birthplace" style="width: 60%;float: left;" placeholder="请输入出生地"></el-input>
          </el-form-item>
        </el-col>
        <el-col :span="11">
          <el-form-item label="来中国时间">
            <el-date-picker v-model="form.date2" type="date" placeholder="选择日期" style="width: 60%;float: left;">
            </el-date-picker>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row>
        <el-col :span="11">
          <el-form-item label="受教育时长" label-position="left">
            <el-input v-model="form.last_year" placeholder="请输入教育时长" style="width: 60%;float: left;"></el-input>
          </el-form-item>
        </el-col>
        <el-col :span="11">
          <el-form-item label="教育程度">
            <el-select v-model="value7" placeholder="请选择" style="width: 60%;float: left;">
              <el-option v-for="item in options2" :key="item.value" :label="item.label" :value="item.value">
              </el-option>
            </el-select>
          </el-form-item>
        </el-col>
      </el-row>
      <div>
        <el-form-item label="是否存在以下障碍:" label-width="150px" style="width: 60%;float: left;">
          <el-checkbox-group v-model="checkList">
            <el-checkbox label="视力障碍"></el-checkbox>
            <el-checkbox label="听力障碍"></el-checkbox>
            <el-checkbox label="语言障碍"></el-checkbox>
            <el-checkbox label="学习障碍"></el-checkbox>
          </el-checkbox-group>
        </el-form-item>
      </div>
      <br />
      <div>
        <el-divider></el-divider>
        <h1 style="text-align: left; font-weight: bold; font-family: SimSun">
          请你给你所习得的语言做一个评估:
        </h1>
      </div>
      <br />
      <el-row>
        <el-col :span="11">
          <el-form-item label="习得顺序" label-width="auto">
            <el-select v-model="value1" multiple placeholder="请选择" style="width: 60%;float: left;">
              <el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value">
              </el-option>
            </el-select>
          </el-form-item>
        </el-col>

        <el-col :span="11">
          <!-- <p>（2）请按习得顺序列出您所掌握的所有语言：</p> -->
          <el-form-item label="主次顺序" label-width="auto">
            <el-select v-model="value2" multiple placeholder="请选择" style="width: 60%;float: left;">
              <el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value">
              </el-option>
            </el-select>
          </el-form-item>
        </el-col>
      </el-row>
      <div>
        <h1 style="text-align: left; font-weight: bold; font-family: SimSun">
          请列出您目前接触每种语言的时间百分比（总和为100%）：
        </h1>
        <div>
          <el-row>
            <el-col :span="24">
              <el-form-item label="" label-position="left">
                <br />
                <el-checkbox-group v-model="selectedOptions">
                  <el-form-item v-for="(option, index) in value1" :key="option" :label="option">
                    <br />
                    <el-slider v-model="value3[index]" style="width: 60%;float: left;"></el-slider>
                  </el-form-item>
                  <!-- <el-checkbox v-for="(option, index) in value1" :key="index" :label="option"></el-checkbox> -->
                </el-checkbox-group>
              </el-form-item>
            </el-col>


          </el-row>
        </div>
        <h1 style="text-align: left; font-weight: bold; font-family: SimSun">
          如果要阅读一篇您未掌握的语言的材料，您更想用您所掌握的哪几种语言来阅读，请写出您选择每种语言的概率:
        </h1>
        <div>
          <el-row>
            <el-col :span="24">
              <el-form-item label="" label-position="left">
                <br />
                <el-checkbox-group v-model="selectedOptions">
                  <el-form-item v-for="(option, index) in value1" :key="option" :label="option">
                    <br />
                    <el-slider v-model="value4[index]" style="width: 60%;float: left;"></el-slider>
                  </el-form-item>
                  <!-- <el-checkbox v-for="(option, index) in value1" :key="index" :label="option"></el-checkbox> -->
                </el-checkbox-group>
              </el-form-item>
            </el-col>

            <!-- <el-col :span="18"> </el-col> -->
          </el-row>
        </div>
        <h1 style="text-align: left; font-weight: bold; font-family: SimSun">
          当您和一个语言能力与您完全匹配的人交流时，您更想用您所掌握的哪几种语言交流，请写出您选择每种语言的概率：
        </h1>
        <div>
          <el-row>
            <el-col :span="24">
              <el-form-item label="" label-position="left">
                <br />
                <el-checkbox-group v-model="selectedOptions">
                  <el-form-item v-for="(option, index) in value1" :key="option" :label="option">
                    <br />
                    <el-slider v-model="value5[index]" style="width: 60%;float: left;"></el-slider>
                  </el-form-item>
                  <!-- <el-checkbox v-for="(option, index) in value1" :key="index" :label="option"></el-checkbox> -->
                </el-checkbox-group>
              </el-form-item>
            </el-col>

            <!-- <el-col :span="11"> </el-col> -->
          </el-row>
        </div>
        <h1 style="text-align: left; font-weight: bold; font-family: SimSun">
          请列出您所认同的各种文化，并在0-10的数值范围内标出您对每种文化认同程度。
        </h1>

        <el-row>
          <el-col :span="24">
            <el-form-item label="" label-position="left">
              <br />
              <el-checkbox-group v-model="selectedOptions">
                <el-form-item v-for="(option, index) in value6" :key="option.key">
                  <el-col :span="4">
                    <el-select v-model="value6[index].key" placeholder="请选择">
                      <el-option v-for="item in options3" :key="item.value" :label="item.label" :value="item.value">
                      </el-option>
                    </el-select>
                  </el-col>
                  <el-col :span="1">
                    <div>&nbsp;</div>
                  </el-col>
                  <el-col :span="14">
                    <el-slider v-model="value6[index].val" style="width: 60%;float: left;" :step="1" show-stops
                      max="10"></el-slider>
                  </el-col>
                </el-form-item>

                <!-- <el-checkbox v-for="(option, index) in value1" :key="index" :label="option"></el-checkbox> -->
              </el-checkbox-group>
              <el-col :span="12">
                <el-button type="primary" round @click="addOption">添加</el-button>
                <el-button type="danger" round @click="removeOption">刪除</el-button>
              </el-col>
            </el-form-item>
          </el-col>

          <el-col :span="11"> </el-col>
        </el-row>

        <el-row>
          <el-col :span="8">
            <div style="font-family: SimSun ;font-weight: bold; ">
              <el-form-item label="汉语是你的:" label-position="left">
                <el-radio-group v-model="form.chinese_number">
                  <el-radio :label="3">母语</el-radio>
                  <el-radio :label="6">第二语言</el-radio>
                  <el-radio :label="9">第三语言</el-radio>
                  <el-radio :label="12">第四语言</el-radio>
                </el-radio-group>
              </el-form-item>
            </div>
          </el-col>

        </el-row>
        <el-row>
          <el-col :span="6">
            <el-form-item label="您从几岁开始学汉语？" label-width="160px">
              <el-input v-model="form.learn_chinese_age" style="width:140px ;float: left;" />

            </el-form-item>
          </el-col>
          <el-col :span="4">
            <el-form-item label="您学了几年汉语？" label-width="160px">
              <el-input v-model="form.learn_chinese_time" style="width:140px ;float: left;" />
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>
          <el-col :span="6">
            <el-form-item label="几岁开始学习口语" label-width="160px">
              <el-input v-model="form.oral_age" style="width:140px ;float: left;" />
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="几岁说得流畅" label-width="160px">
              <el-input v-model="form.talk_well_age" style="width:140px ;float: left;" />
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="几岁开始学习阅读" label-width="160px">
              <el-input v-model="form.learning_read_age" style="width:140px ;float: left;" />
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="几岁读的流畅" label-width="160px">
              <el-input v-model="form.read_well_age" style="width:140px ;float: left;" />
            </el-form-item>
          </el-col>
        </el-row>
        <h1 style="text-align: left; font-weight: bold; font-family: SimSun">
          请在表格中写出您在每种环境中度过的时间（年/月）
        </h1>
        <el-row>
          <el-col :span="4">
            <el-form-item label="使用汉语的国家" label-width="160px">
              <el-input v-model="form.chinese_country_year" placeholder="年" style="width:140px ;float: left;" />
            </el-form-item>
          </el-col>
          <el-col :span="4">
            <el-form-item label="" label-width="0px">
              <el-input v-model="form.chinese_country_month" placeholder="月" style="width:140px ;float: left;" />
            </el-form-item>
          </el-col>
          <el-col :span="4">
            <el-form-item label="使用汉语的家庭" label-width="160px">
              <el-input v-model="form.chinese_family_year" placeholder="年" style="width:140px ;float: left;" />
            </el-form-item>
          </el-col>
          <el-col :span="4">
            <el-form-item label="" label-width="0px">
              <el-input v-model="form.chinese_family_month" placeholder="月" style="width:140px ;float: left;" />
            </el-form-item>
          </el-col>
          <el-col :span="4">
            <el-form-item label="使用汉语的学校" label-width="160px">
              <el-input v-model="form.chinese_school_year" placeholder="年" style="width:140px ;float: left;" />
            </el-form-item>
          </el-col>
          <el-col :span="4">
            <el-form-item label="" label-width="0px">
              <el-input v-model="form.chinese_school_month" placeholder="月" style="width:140px ;float: left;" />
            </el-form-item>
          </el-col>
        </el-row>
        <h1 style="text-align: left; font-weight: bold; font-family: SimSun">
          请在1-10的范围内，标出您的汉语口语能力、理解能力和阅读能力：
        </h1>
        <el-row>
          <el-col :span="20">
            <el-form-item label="口语" label-width="300px">
              <el-slider v-model="form.chinese_oral"  :marks="marks" max="10" style="width: 80%;float: left;"/>
            </el-form-item>
          </el-col>
        </el-row>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">立即创建</el-button>
          <el-button>取消</el-button>
        </el-form-item>
      </div>
    </el-form>
  </div>
</template>

<script>
import Heads from "../components/Head.vue";

export default {

  data() {
    return {
      
      marks: ({
        0: '不会',
        1: '很差',
        2: '差',
        3: "勉强",
        4: "尚可",
        5: {
          style: {
            color: '#1989FA',
          },
          label: '一般',
        },
        6: "较好",
        7: "良好",
        8: "很好",
        9: "优秀",
        10: "精通",
      }),
      checkList: [],
      options: [
        { value: "英语", label: "英语" },
        { value: "汉语", label: "汉语" },
        { value: "日语", label: "日语" },
        { value: "俄语", label: "俄语" },
        { value: "法语", label: "法语" },
      ],
      options2: [
        { value: "高中及以下", label: "高中及以下" },
        { value: "大专", label: "大专" },
        { value: "本科", label: "本科" },
        { value: "硕士", label: "硕士" },
        { value: "博士", label: "博士" },
      ],
      options3: [
        { value: "中国文化", label: "中国文化" },
        { value: "美国文化", label: "美国文化" },
        { value: "基督文化", label: "基督文化" },
        { value: "嘻哈文化", label: "嘻哈文化" },
        { value: "躺平文化", label: "躺平文化" },
      ],
      form: {
        name: "",
        region: "",
        date1: "",
        date2: "",
        delivery: false,
        type: [],
        resource: "",
        last_year: "",
        desc: "",
        chinese_number: "",
        learn_chinese_age: "",
        learn_chinese_time: "",
        chinese_oral:"",
      },
      value1: [],
      value2: [],
      value3: [],
      value4: [],
      value5: [],
      value6: [
        {
          key: "",
          val: 0,
        },
      ],
      value7: [],
    };
  },
  methods: {
    onSubmit() {
      console.log("submit!");
    },
    addOption() {
      this.value6.push({
        key: "",
        val: 0,
      });
    },
    removeOption() {
      if (this.value6.length > 0) {
        this.value6.pop();
      }
    },
  },
};
</script>

<style scoped>
.el-row {
  margin-bottom: 20px;
}

.form-input {
  width: 30%;
}

.mid {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* .el-form-item {
  margin-right: 10px; /* 调整 label 右侧的间距 */
/* } */
.container {
  font-family: "Helvetica Neue";
  line-height: 1.3;
}

.el-form-item {
  margin-bottom: 10px;
  margin-right: 10px;
}

.left {
  text-align: left;
}

.el-slider {
  margin-top: 0;
  margin-left: 12px;
}
</style>
