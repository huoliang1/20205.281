<template>
      <div class="todo-header">
        <input type="text" placeholder="请输入你的任务名称，按回车键确认" @keyup.enter="addT" v-model="content"/>
      </div>
</template>

<script type="text/ecmascript-6">
export default {
    props:{
        addTodo:Function
    },

    data() {
        return {
            content:'',
        }
    },
    

    methods: {
        addT(){
            // 手机数据做成对象
            let content =this.content
            let id = Date.now()
            let isOver = false
            if(content.trim()){
                let obj ={
                    content,
                    id,
                    isOver
                }

                // this.addTodo(obj)  props 传递数据
                this.$emit('addTodo',obj)  //自定义事件 重子传给父


            }
            this.content = ''
        }
      
    },

}
</script>

<style scoped>
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
}

</style>
