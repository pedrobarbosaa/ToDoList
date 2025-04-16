<template>
  <h1>{{ titulo }}</h1>
  <input type="text" v-model="Novatarefa" />
  <button @click="adicionarTarefa">Adicionar Tarefa</button>
  <button @click="limparTarefa">Limpar Lista</button>

  <h2>{{ Subtitulo }}</h2>
  <ul>
    <li v-for="tarefa in listaTarefas" :key="tarefa">
      {{ tarefa }} <button @click="excluirItemLista(tarefa)">X</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'TodoList',
  data() {
    return {
      Novatarefa: '',
      listaTarefas: [],
      titulo: 'ToDo with Vue!!',
      Subtitulo: 'Lista de Tarefas',
    }
  },
  methods: {
    adicionarTarefa() {
      if (this.Novatarefa == '') {
        alert('Digite uma tarefa')
        return
      } else {
        this.listaTarefas.unshift(this.Novatarefa)
        this.Novatarefa = ''
        return this.listaTarefas
      }
    },
    excluirItemLista(tarefaExcluir) {
      const index = this.listaTarefas.indexOf(tarefaExcluir)
      if (index > -1) {
        this.listaTarefas.splice(index, 1)
        return this.listaTarefas
      } else {
        alert('Tarefa não encontrada')
      }
    },
    limparTarefa() {
      if (this.listaTarefas != '') {
        this.listaTarefas = []
      }
    },
  },
}
</script>
