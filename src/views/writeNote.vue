<template>
  <div class="noteBook">
    <div class="left">
      <div class="leftList-top" @click="addNewNote">添加新笔记</div>
      <div class="leftList">
        <div class="list-item" @click="showNote(index)" v-for="(note,index) in noteList" :key="index">
          <div class="title">{{note.noteTitle}}</div>
          <div class="delect"  @click.stop="delectNote(index)"><img src="../assets/删除.png"  height="20px"></div>
        </div>
      </div>
    </div>
    <div class="middle">
        <div class="noteHeader"><div>标题</div><input type="text" v-model="titleValue"></div>
        <div id="main">
          <mavon-editor v-model="value"/>
        </div>
    </div>
  </div>
</template>
<script type="text/ecmascript-6">
export default {
  data() {
    return {
      noteList: [
        {
          noteTitle: '第一条',
          noteMain: '这是第一条',
        },
        {
          noteTitle: '第二条',
          noteMain: '这是第二条',
        },
        {
          noteTitle: '第三条',
          noteMain: '这是第三条',
        },
      ],
      value: '',
      titleValue: '',
      key: '',
    }
  },
  watch: {
    titleValue(newVal,oldVal){
        // console.log(newVal,oldVal);
        if(newVal==''){
          // console.log('删除成功变成空不需要赋值')
          return;
        }else{
          this.noteList[this.key].noteTitle=newVal;
        }
    },
    value(newVal,oldVal){
        // console.log(newVal,oldVal);
        if(newVal==''){
          // console.log('删除成功变成空不需要赋值')          
          return;
        }else{
          this.noteList[this.key].noteMain=newVal;
        }
    }
  },
  components: {

  },
  methods: {
    addNewNote(){
      this.noteList.push({noteTitle:'这是新的一条',noteMain:'这是新的一条'})
    },
    delectNote(id){
      console.log(id)
      this.noteList.splice(id,1);
      this.titleValue='';
      this.value='';
    },
    showNote(id){
      this.value=this.noteList[id].noteMain;
      this.titleValue=this.noteList[id].noteTitle;
      this.key=id;
    },
  }
}
</script>

<style scoped lang="scss">
.noteBook{
  height: 100%;
  width: 100%;
}
.left{
  height: 100%;
  width: 200px;
  border: 1px solid #2ecc7c;
  float: left;
}
.left .leftList-top{
  height: 100px;
  line-height: 100px;
  color: #ffffff;
  font-size: 18px;
  background: #2ecc7c;
}
.left .leftList .list-item{
  position: relative;
  height: 50px;
  line-height: 50px;
  background: #f3f3f3;
}
.left .leftList .list-item .title{
  position: absolute;
  left: 50px;
  width: 100px;
  overflow: hidden;
  text-overflow:ellipsis;
  white-space: nowrap;
}
.left .leftList .list-item .delect{
  position: absolute;
  right: 10px;
  top: 3px;
}
.middle{
  float: left;
}
.noteHeader{
  height: 50px;
  text-align: left;
}
.noteHeader input{
  border:0;
  font-size: 18px;
  font-weight: bold;
}
</style>
