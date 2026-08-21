<template>
  <div>
    <h1>Minhas Tarefas</h1>
    
    <input
      v-model="novaTarefa"
      type="text"
      placeholder="Digite uma tarefa..."
      @keyup.enter="adicionarTarefa"
    />
    <button @click="adicionarTarefa">Adicionar</button>

    <ul>
      <li v-for="tarefa in tarefas" :key="tarefa.id">
        <span
          @click="alternarConcluida(tarefa.id)"
          :class="{ riscado: tarefa.concluida }"
        >
          {{ tarefa.texto }}
        </span>
        <button @click="removerTarefa(tarefa.id)">Remover</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      novaTarefa: '',
      tarefas: [],
      proximoId: 1,
    };
  },
  methods: {
    adicionarTarefa() {
      if (this.novaTarefa.trim() === '') return;

      this.tarefas.push({
        id: this.proximoId++,
        texto: this.novaTarefa,
        concluida: false,
      });

      this.novaTarefa = '';
    },
    alternarConcluida(id) {
      const tarefa = this.tarefas.find(t => t.id === id);
      if (tarefa) tarefa.concluida = !tarefa.concluida;
    },
    removerTarefa(id) {
      this.tarefas = this.tarefas.filter(t => t.id !== id);
    },
  },
};
</script>

<style scoped>
input {
  padding: 8px;
  margin-right: 10px;
}

button {
  padding: 8px 12px;
}

li {
  list-style: none;
  margin: 10px 0;
}

span {
  cursor: pointer;
  margin-right: 10px;
}

.riscado {
  text-decoration: line-through;
  color: gray;
}
</style>
