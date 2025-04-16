<template>
  <div id="container-principal" class="d-flex justify-content-center align-items-center">
    <div class="text-center">
      <h1>{{ titulo }}</h1>
      <div class="input-group mt-3 mb-3">
        <div class="input-group-prepend">
          <div class="input-group-text">
            <input type="text" class="form-control" placeholder="Digite algo..." aria-label="Input group example"
              v-model="Novatarefa" />
          </div>
        </div>
      </div>
      <div class="d-flex gap-3">
        <div>
          <button id="botao-limpar" class="btn btn-secondary btn-sm" @click="adicionarTarefa">Adicionar Tarefa</button>

        </div>
        <div>
          <button class="btn btn-warning btn-sm" @click="limparTarefa">Limpar Lista</button>
        </div>
      </div>

      <h2>{{ Subtitulo }}</h2>
      <ul>
        <li v-for="tarefa in listaTarefas" :key="tarefa">
          {{ tarefa }} <button @click="excluirItemLista(tarefa)">X</button>
        </li>
      </ul>
    </div>
  </div>
</template>


<script>
export default {
  name: 'TodoList',
  data() {
    return {
      Novatarefa: '',
      listaTarefas: [],
      titulo: 'ToDo for You',
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
<style scoped>
#container-principal {
  height: 100vh;
  background-color: #d1cbc0;

}

.text-center {
  border: solid, 0px, black;
  border-radius: 10px;
  padding: 15vh;
  background-color: #c8e3c5;
}

#botao-limpar {}
</style>
