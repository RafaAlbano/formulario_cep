<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: {},
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const { data } = await axios.get(url);
      this.endereco = data;
    },
  },
};
</script>
<template>
  <div>
    <h1>Buscar Cep</h1>
    <form @submit.prevent="buscar" class="form_1">
      <input type="text" v-model="cep" />
      <button type="submit">Buscar</button>
    </form>
    <form class="form_2">
      <label for="rua">Rua</label>
      <input name="numero" type="text" v-model="endereco.numero" />
      <label for="bairro">Bairro</label>
      <input for="bairro" type="text" v-model="endereco.bairro" />
      <label for="localidade">Cidade</label>
      <input for="localidade" type="text" v-model="endereco.localidade" />
      <label for="uf">Uf</label>
      <input for="uf" type="text" v-model="endereco.uf" />
      <label for="complemento">Complemento</label>
      <input name="complemento" type="text" v-model="endereco.logradouro" />
    </form>
    {{ endereco }}
  </div>
</template>
<style>
* {
  padding: 0;
  margin: 0;
  border: 0;
  box-sizing: border-box;
}
label {
  font-family: "Times New Roman", Times, serif;
  color: rgb(26, 65, 88);
}
.form_1 {
  display: flex;
  text-align: center;
  flex-direction: column;
  margin: 5% 30%;
}
.form_2 {
  display: flex;
  text-align: center;
  flex-direction: column;
  margin: 5% 30%;
}
h1 {
  text-align: center;
  font-family: Georgia, "Times New Roman", Times, serif;
  color: rgb(48, 112, 150);
}
input {
  border-radius: 5px;
}
button {
  border: 2px solid rgb(0, 162, 255);
  color: rgb(48, 41, 41);
  border-radius: 5px;
  height: 5%;
  display: flex;
  justify-content: center;
  background-color: white;
  font-weight: bold;
  margin: 7px 30%;
}
input {
  border: 2px solid rgb(127, 161, 180);
  color: rgb(26, 65, 88);
  border-radius: 5px;
}
body {
  background: linear-gradient(to left , white, rgb(148, 177, 233));
}
</style>
