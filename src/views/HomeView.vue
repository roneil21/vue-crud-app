<template>
    <main>
        <h1>Todo List</h1>
        <CreateTodo @create-todo="createTodo" />
        <ul class="todo-list" v-if="todoList.length > 0">
            <li>
                <TodoItem v-for="(todo, index) in todoList" :todo="todo" :index="index"
                    @toggle-complete="toggleTodoComplete" @edit-todo="toggleEditTodo" @update-todo="toggleUpdateTodo"
                    @delete-todo="toggleDelete" />
            </li>
        </ul>
        <p class="todos-msg" v-else>
            <span>Add something on your list</span>
            <Icon icon="lucide:list-x" width="22" />
        </p>

        <p class="todos-msg" v-if="todoCompleted && todoList.length > 0">
            <Icon icon="noto:party-popper" width="22" />
            <span>
                Congratulations! You've Completed you To-Do List
            </span>
        </p>
    </main>
</template>

<script setup>
import CreateTodo from '../components/CreateTodo.vue';
import { uid } from "uid";
import { ref, watch, computed } from "vue";
import TodoItem from '../components/TodoItem.vue';
import { Icon } from '@iconify/vue';
const todoList = ref([]);

watch(todoList, () => {
    setTodoLocalStorage();
},
    {
        deep: true
    }
);

const todoCompleted = computed(() => {
    return todoList.value.every((todo) => todo.isCompleted);
});

const setTodoLocalStorage = () => {
    localStorage.setItem('todoList', JSON.stringify(todoList.value))
};
const fetchTodoList = () => {
    const savedTodoList = JSON.parse(localStorage.getItem('todoList'));
    if (savedTodoList) {
        todoList.value = savedTodoList;
    }
};
fetchTodoList();


const createTodo = (todo) => {
    todoList.value.push({
        id: uid(),
        todo,
        isCompleted: null,
        isEditing: null,
    });

};

const toggleTodoComplete = (currentTodo) => {
    todoList.value[currentTodo].isCompleted = !todoList.value[currentTodo].isCompleted;

};
const toggleEditTodo = (currentTodo) => {
    todoList.value[currentTodo].isEditing = !todoList.value[currentTodo].isEditing;

};
const toggleUpdateTodo = (currentTodoValue, currentTodo) => {
    todoList.value[currentTodo].todo = currentTodoValue;

};
const toggleDelete = (todoId) => {
    todoList.value = todoList.value.filter((todo) => todo.id !== todoId);

};
</script>

<style lang="scss" scoped>
main {
    display: flex;
    flex-direction: column;
    max-width: 500px;
    width: 100%;
    margin: 0 auto;
    padding: 40px 16px;

    h1 {
        margin-bottom: 16px;
        text-align: center;
    }

    .todo-list {
        display: flex;
        flex-direction: column;
        list-style: none;
        margin-top: 24px;
        gap: 20px;
    }

    .todos-msg {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 8px;
        margin-top: 24px;
    }
}
</style>
