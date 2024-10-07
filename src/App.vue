<template>
  
  <div class="container">
    <h1>Calculadora Aritmética</h1>

    <h2>Digite dois valores nos campos abaixo</h2>
    <input class="input-group-text" type="number" v-model.number="primeiroValor" placeholder="Primeiro valor">
    <br>
    <hr>
    <input class="input-group-text" type="number" v-model.number="segundoValor" placeholder="Segundo valor">
    <br>
    <hr>
    <div>
      <h2>Selecione uma das operações</h2>
      <select class="form-select" v-model="operacoes" id="operations">
        <option value="adicao">Adição</option>
        <option value="subtracao">Subtração</option>
        <option value="divisao">Divisão</option>
        <option value="multiplicacao">Multiplicação</option>
      </select>
    </div>
    <br>
    <hr>
    <div>
      <h2>Resultado: {{ resultado }}</h2>
    </div>

  </div>
</template>

<script>
import  {evaluate} from 'mathjs';

export default {
  data() {
    return{
      primeiroValor: 0,
      segundoValor: 0,
      operacoes: 'adicao'
    };
  },
  computed: {
    resultado(){
      const expression = `${this.primeiroValor}${this.getOperator()} ${this.segundoValor}`;
      try {
        return evaluate(expression);
      } catch (error) {
        return 'Erro de cálculo';
      }
    }
  },
  methods: {
    getOperator(){
      switch (this.operacoes){
        case 'adicao':
          return '+';
      
        case 'subtracao':
          return '-';
      
        case 'divisao':
          return '/';
      
        case 'multiplicacao':
          return '*';
        
          default:
          return '';
      }
    }
  }
};


</script>

<style></style>
