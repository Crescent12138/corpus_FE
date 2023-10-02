<template>
<el-card class="box-card">
  <div  :key="show_text" class="text item">
    {{show_text }}
  </div>
  <button @click="splitCorpus">点击执行函数</button>

</el-card>
</template>
<script>
import { createSimpleExpression } from '@vue/compiler-core';
import {postRequest} from '../api/paper'
export default {
  data() {
    return {
      text:"hello world txt ok hhh",
      show_text:"",
      text_list:[],
      numbers :1,
    };
  },
  mounted() {
    this.getSimulation();
    
    console.log(this.text_list)
  },
  created(){
    // this.text_list = this.text.split(" ")
    // console.log(this.text_list)
  },
  methods:{
    getSimulation(){
        postRequest('/paper/simulation',{}).then((data) =>{
            // console.log(data);
            // console.log(this.text);
            // console.log(data.data.data[0].text);
            this.text = data.data.data[0].text;
            this.text_list = this.text.split("  ")
            // console.log(this.text);
        });
    },
    sleep(ms) {
        return new Promise(resolve => setTimeout(resolve, ms));
    },
    async run(){
        this.show_text = ""
        for (var i = 0 ; i < this.text.length;i++){
            this.show_text+= this.text[i];
            await this.sleep(200);
        }
    },
    async splitCorpus(){
       
        this.show_text = ""
        var i = this.numbers
        for(var j = 0 ; j < i ; j++){
            this.show_text += this.text_list[j]
        }
        for (var j = 0 ; j < this.text_list[i].length;j++){
            this.show_text+= this.text_list[i][j];
            await this.sleep(200);
        }
        for(var j = 0 ; j < 3 ; j++){
            this.show_text += "_"
            await this.sleep(200);
        }
        if(this.numbers == this.text_list.length - 1) this.numbers = 0;
        else
        this.numbers ++
    }
  },
  function: {
    
    
    
}
}
</script>
<style>
  .text {
    font-size: 14px;
  }

  .item {
    padding: 18px 0;
  }

  .box-card {
    width: 480px;
  }

</style>