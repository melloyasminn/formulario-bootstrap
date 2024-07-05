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

const data = ref('')

function confirmSenha() {
  if (categoriasForm.confirmarSenha == categoriasForm.senha) {
    mostrarResultado
    data.value =
      categoriasForm.nascimento.slice(8, 11) +
      '/' +
      categoriasForm.nascimento.slice(5, 7) +
      '/' +
      categoriasForm.nascimento.slice(0, 4)
  } else {
    alert('As senhas informadas não são iguais!')
  }
}
</script>

<template>
  <main>
    <h1>Formulário</h1>
    <form @submit.prevent="mostrarResultado">
      <div>
        <label for="nome">Nome: </label>
        <input type="text" v-model="categoriasForm.nome" required id="nome" minlength="3"/>
        <hr />
        <label for="email">E-mail: </label>
        <input type="email" v-model="categoriasForm.email" required id="email" />
        <hr />
        <label for="senha">Senha: </label>
        <input type="password" v-model="categoriasForm.senha" required id="senha" minlength="4"/>
        <hr />
        <label for="confirmarSenha">Confirme sua senha: </label>
        <input
          type="password"
          v-model="categoriasForm.confirmarSenha"
          required
          id="confirmarSenha" minlength="4"
        />
        <div v-if="categoriasForm.confirmarSenha != categoriasForm.senha"></div>
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
        <label for="biografia" >Escreva uma breve biografia: </label>
        <input type="text" v-model="categoriasForm.biografia" minlength="10" maxlength="50" required/>
        <hr />
      </div>
      <button type="submit" @click="confirmSenha">Mostrar resultado</button>
    </form>
    <section v-if="resultado">
      <div>
        <p>Nome: {{ categoriasForm.nome }}</p>
        <hr />
        <p>E-mail: {{ categoriasForm.email }}</p>
        <hr />
        <p>Senha: {{ categoriasForm.senha }}</p>
        <hr />
        <p>Data de nascimento: {{ data }}</p>
        <hr />
        <p>Endereço: {{ categoriasForm.endereco }}</p>
        <hr />
        <p>Cidade {{ categoriasForm.cidade }}</p>
        <hr />
        <p>Estado: {{ categoriasForm.estado }}</p>
        <hr />
        <p>Hobbies: {{ categoriasForm.hobbie }}</p>
        <hr />
        <p>Linguagens de programação: {{ categoriasForm.linguagensProg }}</p>
        <hr />
        <p>Biografia: {{ categoriasForm.biografia }}</p>
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
  border: white;
}

section {
  padding: 20px;
  margin: 8%;
  background: #797979;
  border-radius: 10px;
  color: white;
}

button {
  border: white;
  padding: 1%;
  border-radius: 8px;
}
</style>
