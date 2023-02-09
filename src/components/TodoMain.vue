<template>
  <div>
    <div class="page">
    <header><h1>Vue Fire todo1</h1></header>
    <main>
      <div class="todos">
        <div class="write">
          <input type="text"/>
          <button class="btn add">Add</button>
        </div>
        <ul class="list">
            <ul>
                <li v-for="item in todos" :key="item.text">
                    <i class="far fa-check-square"></i>
                    <strong>{{ item.text }}</strong>
                    
                </li>
            </ul>
        </ul>
      </div>
    </main>
    </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
        todos:[
        {text: '공부하기', state: 'yet'},
        {text: '운동하기', state: 'done'},
        {text: '글쓰기', state: 'done'},
      ]
        }
    }
}
</script>

<style>

</style>