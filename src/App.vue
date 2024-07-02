<script setup>
import { reactive, ref } from 'vue'
const resultado = ref(false)
function mostrarResultado() {
  resultado.value = true
}

const categoriasForm = reactive({
  nome: '',
  email: '',
  nascimento: '',
  senha: '',
  confirmarSenha: '',
  endereco: '',
  cidade: '',
  estado: '',
  hobbie: [],
  linguagensProg: [],
  biografia: ''
})

const hobbies = [
  { nome: 'Dança' },
  { nome: 'Instrumentos musicais' },
  { nome: 'Esportes' },
  { nome: 'Culinária' }
]

const linguagemProg = [
  { nome: 'HTML' },
  { nome: 'JavaScript' },
  { nome: 'Java' },
  { nome: 'Python' },
  { nome: 'PHP' },
  { nome: 'C++' }
]

const estados = [
  { sigla: 'AC', nomeEstados: 'Acre' },
  { sigla: 'AL', nomeEstados: 'Alagoas' },
  { sigla: 'AP', nomeEstados: 'Amapá' },
  { sigla: 'AM', nomeEstados: 'Amazonas' },
  { sigla: 'BA', nomeEstados: 'Bahia' },
  { sigla: 'CE', nomeEstados: 'Ceará' },
  { sigla: 'DF', nomeEstados: 'Distrito Federal' },
  { sigla: 'ES', nomeEstados: 'Espírito Santo' },
  { sigla: 'GO', nomeEstados: 'Goiás' },
  { sigla: 'MA', nomeEstados: 'Maranhão' },
  { sigla: 'MT', nomeEstados: 'Mato Grosso' },
  { sigla: 'MS', nomeEstados: 'Mato Grosso do Sul' },
  { sigla: 'MG', nomeEstados: 'Minas Gerais' },
  { sigla: 'PA', nomeEstados: 'Pará' },
  { sigla: 'PB', nomeEstados: 'Paraíba' },
  { sigla: 'PR', nomeEstados: 'Paraná' },
  { sigla: 'PE', nomeEstados: 'Pernambuco' },
  { sigla: 'PI', nomeEstados: 'Piauí' },
  { sigla: 'RJ', nomeEstados: 'Rio de Janeiro' },
  { sigla: 'RN', nomeEstados: 'Rio Grande do Norte' },
  { sigla: 'RS', nomeEstados: 'Rio Grande do Sul' },
  { sigla: 'RO', nomeEstados: 'Rondônia' },
  { sigla: 'RR', nomeEstados: 'Roraima' },
  { sigla: 'SC', nomeEstados: 'Santa Catarina' },
  { sigla: 'SP', nomeEstados: 'São Paulo' },
  { sigla: 'SE', nomeEstados: 'Sergipe' },
  { sigla: 'TO', nomeEstados: 'Tocantins' }
]
</script>

<template>
  <main>
    <h1>Formulário</h1>
    <form @submit.prevent="mostrarResultado">
      <div>
        <label for="nome">Nome: </label>
        <input type="text" v-model="categoriasForm.nome" required id="nome" />
        <hr />
        <label for="email">E-mail: </label>
        <input type="text" v-model="categoriasForm.email" required id="email" />
        <hr />
        <label for="senha">Senha: </label>
        <input type="password" v-model="categoriasForm.senha" required id="senha" />
        <hr />
        <label for="confirmarSenha">Confirme sua senha: </label>
        <input
          type="password"
          v-model="categoriasForm.confirmarSenha"
          required
          id="confirmarSenha"
        />
        <div v-if="categoriasForm.confirmarSenha != categoriasForm.senha">
          <alert> A senha confirmada não é igual a senha </alert>
        </div>
        <hr />
        <label for="nascimento">Data de nascimento: </label>
        <input type="date" v-model="categoriasForm.nascimento" required id="nascimento" />
        <hr />
        <label for="endereco">Endereço: </label>
        <input type="text" v-model="categoriasForm.endereco" required id="endereco" />
        <hr />
        <label for="cidade">Cidade: </label>
        <input type="text" v-model="categoriasForm.cidade" required id="cidade" />
        <hr />
        <label for="estados">Estado: </label>
        <select id="estado" v-model="categoriasForm.estado">
          <option selected disabled value="">Selecionar</option>
          <option v-for="estado of estados" :key="estados.sigla" :value="estado.nomeEstados">
            {{ estado.sigla }}
          </option>
        </select>
        <hr />
        <label for="hobbies"> Hobbies:</label>
        <template v-for="hobbie in hobbies" :key="hobbie.nome">
          <input v-model="categoriasForm.hobbie" :value="hobbie.nome" type="checkbox" />
          {{ hobbie.nome }}
        </template>
        <hr />
        <label for="linguagensProg">Linguagens de programação:</label>
        <template v-for="linguagem in linguagemProg" :key="linguagem.nome">
          <input v-model="categoriasForm.linguagensProg" :value="linguagem.nome" type="checkbox" />
          {{ linguagem.nome }}
        </template>
        <hr />
        <label for="biografia">Escreva uma breve biografia: </label>
        <input type="text" v-model="categoriasForm.biografia" />
        <hr />
      </div>
      <button type="submit">Mostrar resultado</button>
    </form>
    <section v-if="resultado">
      <div>
        <p v-for="(value, index) of categoriasForm" :key="index">{{ index }}:{{ value }}</p>
      </div>
    </section>
  </main>
</template>

<style scoped>
h1 {
  font-size: 40px;
  margin: 0%;
  text-align: center;
  padding: 10px;
  background: #9b9b9b;
  color: #ffffff;
}

form {
  padding: 20px;
  margin: 8%;
  background: #b6b6b6;
  border-radius: 10px;
}

input {
  border-radius: 8px;
  margin-left: 2%;
  background: #dfdfdf;
}
</style>
