<template>
    <main>
        <!-- Heading -->
        <header>
            <img src="./assets/pinia-logo.svg" alt="pinia-logo" />
            <h1>Pinia Tasks</h1>
        </header>

        <!-- New Task Form -->
        <div class="new-task-form">
            <TaskForm />
        </div>

        <!-- Navigation filter-->
        <nav class="filter">
            <button @click="filter = 'all'">All Tasks</button>
            <button @click="filter = 'favs'">Fav Tasks</button>
        </nav>

        <!-- Task List -->
        <div class="taskList" v-if="filter === 'all'">
            <p>You have {{ taskStore.totalCount }} left to do.</p>
            <div v-for="task in taskStore.tasks">
                <TaskDetails :task="task" />
            </div>
        </div>
        <div class="taskList" v-if="filter === 'favs'">
            <p>You have {{ taskStore.favCount }} favourite tasks</p>
            <div v-for="task in taskStore.favs">
                <TaskDetails :task="task" />
            </div>
        </div>
    </main>
</template>

<script setup>
    import { ref } from "vue";
    import TaskDetails from "./components/TaskDetails.vue";
    import TaskForm from "./components/TaskForm.vue";

    import { useTaskStore } from "./store/taskStore";

    const taskStore = useTaskStore();

    const filter = ref("all");
</script>
