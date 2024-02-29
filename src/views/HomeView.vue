<script>
export default {
  data() {
    return {
      
    }
  },

  methods: {

 },
};

</script>

<template>
<div class="body w-screen h-screen flex justify-center items-center bg-neutral-800">
    <div class="w-[80rem] h-[50rem] bg-stone-400 border-4 flex flex-col">
    <div class="add m-2 ml-96">
      <input type="text" id="" class="add-text w-[30rem] rounded-lg text-2xl">
      <button class="add-Todo w-20 rounded-lg text-2xl ml-8 bg-red-50" type="button">新增</button>
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
        
      </tbody>
    </table>
    <button class="enter-to-local w-32 rounded-lg text-2xl bg-red-50" type="button">存進local</button>
    <button class="enter-to-local w-32 rounded-lg text-2xl bg-red-50" type="button">新增</button>
    <button class="enter-to-local w-32 rounded-lg text-2xl bg-red-50" type="button">刪除</button>

  </div>
</div>
</template>