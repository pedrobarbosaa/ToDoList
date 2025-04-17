<template>
  <div id="container-principal" class="d-flex justify-content-center align-items-center">
    <div class="text-center">
      <h1 class="titulo-principal">{{ titulo }}</h1>
      <div class="input-group mt-4 mb-3">
        <div class="input-group-prepend">
          <div class="input-group-text">
            <input type="text" class="form-control" placeholder="Digite algo..." aria-label="Input group example"
              v-model="Novatarefa" />
          </div>
        </div>
      </div>
      <div class="d-flex gap-3 align-items-center justify-content-center">
        <div>
          <button class="btn btn-secondary btn-sm" @click="adicionarTarefa">Adicionar Tarefa</button>

        </div>
        <div>
          <button class="btn btn-warning btn-sm" @click="limparTarefa">Limpar Lista</button>
        </div>
      </div>

      <div class="mt-3">
        <h2 class="titulo-secundario">{{ Subtitulo }}</h2>
        <ul>
          <li v-for="tarefa in listaTarefas" :key="tarefa">
            {{ tarefa }} <button @click="excluirItemLista(tarefa)">X</button>
          </li>
        </ul>
      </div>
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
  background-color: gradient(to bottom, #99c3a6, #f0f0f0);
  background: -webkit-linear-gradient(90deg, #6dc488, #009eba, #3f65af);

}

.text-center {
  border: solid, 0px;
  border-radius: 10px;
  padding: 15vh;
  background-color: #99c3a6;
  opacity: 90%;
  box-shadow: 0px 0px 10px #000;
}

.titulo-principal {
  font-size: 40px;
  color: #254f9f;
}

.titulo-secundario {
  font-size: 30px;
  color: #254f9f;
}

.form-control{
  width: 300px;
  height: 40px;
  border-radius: 5px;
  border: none;
  background-color: #f0f0f0;
}

ul{
  list-style-type: none
}
</style>
