<script lang="ts" setup >
    import { computed, ref } from 'vue';
    import TaskForm from './components/TaskForm.vue';
    import FilterButton from './components/FilterButton.vue';
    import TaskList from './components/TaskList.vue';
    import type { Task, TaskFilter } from './types';
    const message = ref('Task App');
    const tasks = ref<Task[]>([]);
    const filter = ref<TaskFilter>('all');

    const totalDone = computed(() => tasks
    .value
    .reduce((total, task) => task.done ? total + 1 : total, 0));
    
    const filteredTasks = computed(() => {
        switch (filter.value) {
            case 'done':
                return tasks.value.filter(task => task.done);
            case 'todo':
                return tasks.value.filter(task => !task.done);
            default:
                return tasks.value;
        }
    });
    function addTask(newTask: string) {
        tasks.value.push({
            id: crypto.randomUUID(),
            title: newTask,
            done: false
        });
    }

    function toggleDone(id: string) {
        const task = tasks.value.find(task => task.id === id);
        if (task) {
            task.done = !task.done;
        }
    }

    function removeTask(id: string) {
        const index = tasks.value.findIndex(task => task.id === id);
        if (index !== -1) {
            tasks.value.splice(index, 1);
        }
    }

    function setFilter(newFilter: TaskFilter) {
        filter.value = newFilter;
    }


</script>

<template>
    <main>
        <h1> {{ message }}</h1>
        <TaskForm @add-task="addTask"/>
        <h3 v-if="!tasks.length">Add tasks to get started</h3>
        <h3 v-else> {{ totalDone }} / {{tasks?.length }} tasks completed</h3>
        <div v-if="tasks.length" class="button-container">
           <FilterButton :currentFilter="filter" @set-filter="setFilter" filter="all"/>
           <FilterButton :currentFilter="filter" @set-filter="setFilter" filter="todo"/>
           <FilterButton :currentFilter="filter" @set-filter="setFilter" filter="done"/>
        </div>
        <TaskList :tasks="filteredTasks" @toggle-done="toggleDone" @remove-task="removeTask"/>
    </main>
</template>

<style >
    main  {
        width: 800px;
        margin: 1rem auto;
    }

    .button-container {
        display: flex;
        justify-content: end;
        gap: 0.5rem;
    }
</style>