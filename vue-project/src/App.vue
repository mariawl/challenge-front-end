<template>
  <div>
    <h1>Lista de Contatos</h1>
    <ul>
      <li v-for="contato in contatos" :key="contato.id" @click="exibirContato(contato.id)">
        <img :src="contato.avatar_url" :alt="contato.name">
        <p>{{ contato.name }}</p>
      </li>
    </ul>
    <div v-if="contatoSelecionado">
      <h2>{{ contatoSelecionado.name }}</h2>
      <img :src="contatoSelecionado.avatar_url" :alt="contatoSelecionado.name">
      <p>Email: {{ contatoSelecionado.email }}</p>
      <p>Telefone: {{ contatoSelecionado.phone }}</p>
    </div>
  </div>
</template>

<script>
import contatosData from './data/Contatos.json';

export default {
  data() {
    return {
      contatos: contatosData,
      contatoSelecionado: null,
    };
  },
  methods: {
    exibirContato(contatoId) {
      this.contatoSelecionado = this.contatos.find(contato => contato.id === contatoId);
    },
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
  cursor: pointer;
}

img {
  width: 50px;
  height: 50px;
  margin-right: 10px;
  border-radius: 50%;
}
</style>
