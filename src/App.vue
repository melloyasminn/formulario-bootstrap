<script setup>
import { reactive, ref } from 'vue'
const resultado = ref(false)
function mostrarResultado() {
  resultado.value = true
}

const categoriasForm = reactive({
  nome: '',
  email: '',
  senha: '',
  confirmarSenha: '',
  nascimento: '',
  endereco: '',
  cidade: '',
  estado: '',
  hobbies: [],
  linguagensProg: [],
  biografia: ''
})

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
        <hr>
        <label for="email">E-mail: </label>
        <input type="text" v-model="categoriasForm.email" required id="email" />
        <hr>
        <label for="senha">Senha: </label>
        <input type="password" v-model="categoriasForm.senha" required id="senha" />
        <hr>
        <label for="confirmarSenha">Confirme sua senha: </label>
        <input type="password" v-model="categoriasForm.confirmarSenha" required id="confirmarSenha" />
        <hr>
        <label for="nascimento">Data de nascimento: </label>
        <input type="date" v-model="categoriasForm.nascimento" required id="nascimento" />
        <hr>
        <label for="endereco">Endereço: </label>
        <input type="text" v-model="categoriasForm.endereco" required id="endereco" />
        <hr>
        <label for="cidade">Cidade: </label>
        <input type="text" v-model="categoriasForm.cidade" required id="cidade" />
        <hr>
        <label for="estados">Estado: </label>
        <select id="estado" v-model="categoriasForm.estado">
              <option selected disabled value="">Selecionar...</option>
              <option v-for="estado of estados" :key="estados.sigla" :value="estado.sigla">
                {{ estado.nome }}
              </option>
          </select>
      </div>
      <button type="submit">Mostrar resultado</button>
    </form>
    <section v-if="resultado">
      <div>
        <p v-for="(value, index) of categoriasForm" :key="index">{{ index }}: {{ value }}</p>
      </div>
    </section>
  </main>
</template>
