<template>
    <h1>{{ titulo }}</h1>
    <input type="text" v-model="Novatarefa">
    <button @click="adicionarTarefa" >Adicionar Tarefa</button>
    <ul>
        <li v-for="Novatarefa in listaTarefas" :key="Novatarefa">{{ Novatarefa }}</li>
    </ul>
</template>

<script>
export default {
    name: "TodoList",
    data() {
        return{
            Novatarefa: "",
            listaTarefas: [],
            titulo:"ToDo with Vue!!"
        }
    },
    methods: {
        adicionarTarefa() {
           this.listaTarefas.unshift(this.Novatarefa)
           this.Novatarefa = "";
        }
    },
}

</script>