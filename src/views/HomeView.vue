<script>
export default {
  data() {
    return {
      arr:[],
      obj:{},
      text:'',
      switchBtn:'all',
    }
  },

  mounted() {
    if(localStorage.getItem('news')){
      this.arr = JSON.parse(localStorage.getItem('news'));
    }
  },

  // 預處理拿到的資料,他有暫存的功能,所以我們可以拿整包資料,利用判斷式把我們資料做篩選
  computed:{
    selectnews(){
      this.arr.filter((item)=>{
        if(this.switchBtn === 'all'){
          return this.arr;
        }else if(this.switchBtn === '已完成'){
          return item.checkBox == true;
        }else if(this.switchBtn ==='未完成'){
          return item.checkBox == false;
        }
        })
      }
    },
  
  methods: {

  pushobj() {
    console.log(this.news);
    const id = this.arr.length;
    this.obj = {
      checkBox : false,
      msgSwitch : false,
      news : this.news,
      id : id,
    };
    
    this.arr.push(this.obj);
    localStorage.setItem('news', JSON.stringify(this.arr));

  },
  getInputValue(e) {
    this.news = e.target.value;
  },
  deleteBtn(index) {
    this.arr.splice(index,1);
    localStorage.setItem('news', JSON.stringify(this.arr));
  },

  editBtn(index) {
    // this.arr[index].news =prompt('請輸入');
  this.arr[index].msgSwitch =! this.arr[index].msgSwitch;
  if(this.arr[index].msgSwitch === false) {
    this.arr[index].news = this.aaa;
  }
  else {
    this.aaa = this.arr[index].news; 
  }
  localStorage.setItem('news', JSON.stringify(this.arr));

  },
  editInput(e) {
    this.aaa = e.target.value;
  }
 },
};

</script>
<template>
<div class="body w-screen h-screen flex justify-center items-center bg-neutral-800">
    <div class="w-[80rem] h-[50rem] bg-stone-400 border-4 flex flex-col">
    <div class="add m-2 ml-96">
      <input type="text" class="add-text w-[30rem] rounded-lg text-2xl" @change="(e) => getInputValue(e)">
      <button class="add-Todo w-20 rounded-lg text-2xl ml-8 bg-red-50" @click="pushobj()" type="button">新增</button>
    </div>
    <div class="search-btn m-4 text-2xl">
      <button class="all w-20 rounded-lg text-2xl ml-5 bg-red-50" type="button" data-search="all">全部</button>
      <button class="is-todo w-20 rounded-lg text-2xl ml-5 bg-red-50" type="button" data-search="isTodo">已執行</button>
      <button class="not-todo w-20 rounded-lg text-2xl ml-5 bg-red-50" type="button" data-search="notTodo">未執行</button>
    </div>
    <table class="todo  border-4 text-2xl">
      <thead>
        <tr>
          <th>執行</th>
          <th>事項</th>
          <th>功能</th>
        </tr>
      </thead>
      <tbody class="data-show">
        <tr v-for="( item, index) in arr" :key="index">
          <th><input type="checkbox"></th>
          <th v-if="item.msgSwitch === false">{{ item.news }}</th>
          <th v-else><input type="text" @change="(e) => editInput(e)"></th>
          <th>
            <button class="enter-to-local w-16 rounded-lg text-2xl bg-red-50" type="button" @click="editBtn(index)">編輯</button>
            <button class="enter-to-local w-16 rounded-lg text-2xl bg-red-50" type="button" @click="deleteBtn(index)">刪除</button>
          </th>
        </tr>
      </tbody>
    </table>
    

  </div>
</div>
</template>