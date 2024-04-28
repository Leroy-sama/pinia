<template>
    <div class="task">
        <h3>{{ task.title }}</h3>
        <div class="icons">
            <i
                class="fa-solid fa-trash"
                @click="taskStore.deleteTasks(task.id)"
            ></i>
            <i
                :class="{ active: task.isFav }"
                class="fa-solid fa-star"
                @click="taskStore.toggleFav(task.id)"
            ></i>
        </div>
    </div>
</template>

<script setup>
    import { useTaskStore } from "../store/taskStore";
    const props = defineProps(["task"]);

    const taskStore = useTaskStore();
</script>
