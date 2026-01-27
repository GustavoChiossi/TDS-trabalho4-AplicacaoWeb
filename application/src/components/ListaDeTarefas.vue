<template>
  <div class="container mt-5">
    <h2 class="mb-3">Lista de Tarefas</h2>

    <div class="input-group mb-3">
      <input
        v-model="novaTarefa"
        type="text"
        class="form-control"
        placeholder="Digite uma tarefa"
      />
      <button class="btn btn-primary" @click="adicionarTarefa">
        Adicionar
      </button>
    </div>

    <ul class="list-group">
      <li
        v-for="(tarefa, index) in tarefas"
        :key="index"
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        {{ tarefa }}
        <button class="btn btn-sm btn-danger" @click="removerTarefa(index)">
          Remover
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ListaDeTarefas',
  data() {
    return {
      novaTarefa: '',
      tarefas: []
    }
  },
  methods: {
    adicionarTarefa() {
      if (this.novaTarefa.trim() !== '') {
        this.tarefas.push(this.novaTarefa)
        this.novaTarefa = ''
      }
    },
    removerTarefa(index) {
      this.tarefas.splice(index, 1)
    }
  }
}
</script>

<style scoped>
h2 {
  text-align: center;
}
</style>