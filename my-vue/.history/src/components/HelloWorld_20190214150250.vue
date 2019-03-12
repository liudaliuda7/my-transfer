<template>
  <div class="hello">
    <transfer :title="title" :from_data='fromData' :to_data='toData' :defaultProps="{label:'label'}" @addBtn='add' @removeBtn='remove' :mode='mode' height='540px' filter openAll>
    </transfer>
  </div>
</template>


<script>
import transfer from './transfer.vue' 
export default {
    name: "HelloWorld",
    data(){
      return{
        title: ["可选账户列表", "已选账户列表"],
        mode: "transfer", // transfer addressList,
        fromData:[
          {
        id: 1,
        pid: 0,
        label: '一级 1',
        children: [
            {
                id: 4,
                pid: 1,
                label: '二级 1-1',
                children: [
                    {
                        id: 9,
                        pid: 4,
                        label: '三级 1-1-1'
                    },
                    {
                        id: 10,
                        pid: 4,
                        label: '三级 1-1-2'
                    }
                ]
            }
        ]
    }, 
    {
        id: 2,
        pid: 1,
        label: '一级 2',
        children: [
            {
                id: 5,
                pid: 2,
                label: '二级 2-1'
            }, 
            {
                id: 6,
                // pid: 2,
                label: '二级 2-2'
            }
        ]
    }, 
    {
        id: 3,
        // pid: 2,
        label: '一级 3',
        children: [
            {
                id: 7,
                // pid: 3,
                label: '二级 3-1'
            }, 
            {
                id: 8,
                // pid: 3,
                label: '二级 3-2'
            }
        ]
    }
            
        ],
        toData:[]
      }
    },
    methods:{
      // 切换模式 现有树形穿梭框模式transfer 和通讯录模式addressList
      changeMode() {
        if (this.mode == "transfer") {
          this.mode = "addressList";
        } else {
          this.mode = "transfer";
        }
      },
      // 监听穿梭框组件添加
      add(fromData,toData,obj){
        // 树形穿梭框模式transfer时，返回参数为左侧树移动后数据、右侧树移动后数据、移动的{keys,nodes,halfKeys,halfNodes}对象
        // 通讯录模式addressList时，返回参数为右侧收件人列表、右侧抄送人列表、右侧密送人列表
        // console.log("fromData:", fromData);
        // console.log("toData:", toData);
        console.log("obj:", obj);
      },
      // 监听穿梭框组件移除
      remove(fromData,toData,obj){
        // 树形穿梭框模式transfer时，返回参数为左侧树移动后数据、右侧树移动后数据、移动的{keys,nodes,halfKeys,halfNodes}对象
        // 通讯录模式addressList时，返回参数为右侧收件人列表、右侧抄送人列表、右侧密送人列表
        // console.log("fromData:", fromData);
        // console.log("toData:", toData);
        console.log("obj:", obj);
      },

      leftCheckChange(nodeObj, treeObj){
          console.log(nodeObj)
          console.log(treeObj)
      }
    },
    components:{ transfer } // 注册
  
}
</script>
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
