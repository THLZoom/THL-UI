<style scope>
.ul-1 li {
  list-style: none;
  width: 1000px;
  text-align: left;
  padding: 3px;
  font-size: 14px;
  cursor: pointer;
}

.ul-1 span {
  display: block;
  width: 100%;
  padding: 6px;
  position: relative;
}

.ul-1 span:hover {
  background: #f5f7fa;
}

.ul-1 ul  {
  padding: 0;
}

.ul-1>.li-1>span {
  text-indent: 10px;
}

.ul-2>.li-2>span {
  text-indent: 30px;
}

.ul-3>.li-3>span {
  text-indent: 50px;
}

.ul-1 input {
  -webkit-appearance: none;  /*去掉input默认样式 */
}
.ul-1 input[type='checkBox'] {
  width: 15px;
  height: 16px;
  border-radius: 2px;
  border: 1px solid #d8dce5;
  vertical-align: bottom;
  margin: 0;
  outline: none;
}
.checkboxOut{
  display: inline-block;
  text-indent: 0;
}
.haschecked{
  background: url('./check.png') no-repeat 0;
}
</style>
<template>
  <ul v-if="data" class="ul-1">
    <li class="li-1" v-for="(item1,key1) in data" :id="item1.id" :class="item1.class" :style="item1.style" :key="item1.uid">
      <span @click.self="ulCollspan">
        <label class="checkboxOut"><input type="checkBox" v-if="checkBox" @click="checkEvent" :name ="item1.uid" v-model="checked"></label> 
        {{item1.label,checked}}
      </span>
      <ul class="ul-2" v-if="item1.children" style="display: none;">
        <li class="li-2" v-for="(item2,key2) in item1.children" :id="item2.id" :class="item2.class" :style="item2.style" :key="item2.uid">
          <span @click.self="ulCollspan">
            <div class="checkboxOut"><input type="checkBox" v-if="checkBox" @click="checkEvent" :name="item2.uid" v-model="checked"></div>
            {{item2.label,checked}}
          </span>
          <ul class="ul-3" v-if="item2.children" style="display: none;">
            <li class="li-3" v-for="(item3,key3) in  item2.children" :id="item3.id" :class="item3.class" :style="item3.style" :key="item3.uid">
              <span>
                <div class="checkboxOut"><input type="checkBox" v-if="checkBox" @click="checkEvent" :name="item3.uid" v-model="checked"></div>
                {{item3.label,checked}}
              </span>
            </li>
          </ul>
        </li>
      </ul>
    </li>
  </ul>

  
</template>

<script>
export default {
  props: {           //组件接收配置参数的对象
    data: {          //需要渲染的数据
      type: Array,   //数据类型为Array
      required: true //必传参数
    },
    checkBox: {      //选择框参数
      type: Boolean, //数据类型为Boolean
      default: false //默认为false
    }
  },
  data() {
    return {
      hasChecked: true
    }
  },
  methods: {
    //ul折叠方法
    ulCollspan (event) {
      const ulNode = event.target.nextElementSibling; //event.target.nextElementSibling 为 ul 节点
      if(ulNode){  
        ulNode.style.display = ulNode.style.display == 'none' ? 'block' : 'none';
      }
    },
    checkEvent (event) {
      this.$emit('checkEvent',event.target.name); //发布事件广播

      let haschecked = event.target.parentNode.className;
      if(haschecked == 'checkboxOut'){
        event.target.parentNode.className += ' haschecked';
      }else{
        event.target.parentNode.className = 'checkboxOut';
      }     
    }    
  },
  computed: {

  }
}
</script>