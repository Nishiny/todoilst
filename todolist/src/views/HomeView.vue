<script setup>

</script>

<template>
 <div>
    <div class="add">
      <input type="text" id="" class="add-text">
      <button class="add-Todo" type="button">新增</button>
    </div>
    <div class="search-btn">
      <button class="all" type="button" data-search="all">全部</button>
      <button class="is-todo" type="button" data-search="isTodo">已執行</button>
      <button class="not-todo" type="button" data-search="notTodo">未執行</button>
    </div>
    <table class="todo">
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
    <button class="enter-to-local" type="button">存進local</button>
  </div>
</template>
