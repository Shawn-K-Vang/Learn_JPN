<template>
    <!--Allow user to add kanji to study-->
    <div>
        <input  type="text" 
                class="todo-input"
                placeholder="Enter Here" 
                v-model="newTodo" 
                @keyup.enter="addTodo">

        <div v-for="(todo, index) in todosFiltered" :key="todo.id" class="todo-item">
            <div class="todo-item-left">
                <input type="checkbox" v-model="todo.completed">
                <div v-if="!todo.editing" @dblclick="editTodo(todo)" class="todo-item-label" :class="{ completed : todo.completed }">{{ todo.title }}</div>
                <input v-else class="todo-item-edit" type="text" v-model="todo.title" @blur="doneEdit(todo)" @keyup.enter="doneEdit(todo)" @keyup.esc="cancelEdit(todo)" v-focus>
            </div>
            <div class="remove-item" @click="removeTodo(index)">&times;</div>
        </div>

        <div class="container">
            <div>
                <label>
                    <input type="checkbox" :checked="!anyRemaining" @change="checkAllTodos">
                    Check All
                </label>
            </div>
            <div>{{ remaining }} items left</div>
        </div>

        <div class="container">
            <div>
                <button v-if="showClearCompletedButton" @click="clearCompleted">
                    Clear Completed
                </button>
            </div>
        </div>
    </div>                  
</template>

<script>
export default {
    data() {
        return {
            idForTodo: 1,
            newTodo: '',
            beforeEdit: '',
            todos: []
        }
    },
    computed: {
        remaining() {
            return this.todos.filter(todo => !todo.completed).length
        },
        anyRemaining() {
            return this.remaining != 0
        },
        todosFiltered() {
            if (this.filter == 'all') {
                return this.todos
            } 
            else if (this.filter == 'active') {
                return this.todos.filter(todo => !todo.completed)
            } 
            else if (this.filter == 'completed') {
                return this.todos.filter(todo => todo.completed)
            }
            return this.todos
        },
        showClearCompletedButton() {
            return this.todos.filter(todo => todo.completed).length > 0
        }
    },
    methods: {
        addTodo() {
            if (this.newTodo.trim().length == 0) {
                return
            }
            this.todos.push({
                id: this.idForTodo,
                title: this.newTodo,
                completed: false,
                editing: false,
            })
            this.newTodo = ''
            this.idForTodo++
        },
        editTodo(todo) {
            this.beforeEdit = todo.title
            todo.editing = true
        },
        doneEdit(todo) {
            if (todo.title.trim() == '') {
                todo.title = this.beforeEdit
            }
            todo.editing = false
        },
        cancelEdit(todo) {
            todo.title = this.beforeEdit
            todo.editing = false
        },
        removeTodo(index) {
            this.todos.splice(index, 1)
        },
        checkAllTodos() {
            this.todos.forEach((todo) => todo.completed = event.target.checked)
        },
        clearCompleted() {
            this.todos = this.todos.filter(todo => !todo.completed)
        }
    },
    directives: {
        focus: {
            inserted: function (el) {
                el.focus()
            }
        }
    }
}
</script>

<style scoped>
  .todo-input {
    width: 50%;
    padding: 1% 1%;
    margin-right: 50%;
    padding-right: .01%;
    font-size: 18px;
    margin-bottom: 16px;
  }
  .todo-item {
    margin-bottom: 1%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    animation-duration: 0.3s;
  }
  .remove-item {
    cursor: pointer;
    margin-right: 50%;
  }
  .todo-item-left { 
    display: flex;
    align-items: center;
  }
  .todo-item-label {
    padding: 10px;
    border: 1px solid gray;
    margin-left: 12px;
  }
  .todo-item-edit {
    font-size: 24px;
    color: gray;
    margin-left: 12px;
    width: 100%;
    padding: 10px;
    border: 1px solid black; 
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
  }
  .completed {
    text-decoration: line-through;
    color: black;
  }
  .container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 15px;
    border-top: 1px solid black;
    padding-top: 2%;
    margin-bottom: 2%;
    margin-right: 50%;
  }
  button {
    font-size: 15px;
    background-color: white;
  }
</style>