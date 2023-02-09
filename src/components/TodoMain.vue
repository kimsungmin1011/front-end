<template>
  <div>
    <div class="page">
    <header><h1>Vue Fire todo1</h1></header>
    <main>

      <div class="todos">
        <div class="write" v-if="writeState==='add'"> <!--등록-->
          <input ref="writeArea" type="text" v-model="addItemText"/>
          <button @click="addItem" class="btn add">Add</button>
        </div>

        <div class="write" v-else> <!--수정-->
            <input ref="writeArea" type="text" v-model="editItemText"/>
          <button @click="editSave" class="btn add">Save</button>
        </div>

        <ul class="list">
            <ul>
                <li v-for="(item,i) in todos" :key="item.text">
                    <i @click="checkItem(i)" :class="[item.state === 'yet'?'far':'fas', 'fa-check-square']"></i>
                    <strong>{{ item.text }}</strong>     
                    <span>
                        <b>
                            <a href="" @click.prevent="editShow(i)">Edit</a>
                            <a href="" @click.prevent="delShow(i)">Del</a>
                        </b>
                    </span>
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
        writeState:'add',
        crrEditItem: '',
        addItemText: '',
        editItemText:'',
        todos:[
        {text: '공부하기', state: 'yet'},
        {text: '운동하기', state: 'done'},
        {text: '글쓰기', state: 'done'},
      ]
        }
    },
    methods: {
        addItem() {
            if (this.addItemText==='') return;
            this.todos.push({text: this.addItemText, state: 'yet'});
            this.addItemText = '';
        },
        checkItem(i) {
            if (this.todos[i].state==='yet') 
                {this.todos[i].state==='done'
            } else if (this.todos[i].state==='done') 
                {this.todos[i].state==='yet'}
        },
        editShow(index) {
            this.crrEditItem=index;
            this.writeState='edit';
            this.editItemText=this.todos[index].text
        },
        editSave() {
            this.todos[this.crrEditItem].text = this.editItemText;
            this.writeState='add'
        },
        delShow(index) {
            this.todos.splice(index, 1)
        },
        
    },
    mounted() {
        this.$refs.writeArea.focus();
    }
}
</script>

<style>

</style>