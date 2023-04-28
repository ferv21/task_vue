<script setup>
import { reactive } from 'vue';


  const estado = reactive ({
    operacao :'adicao',
    numero1:0,
    numero2:0,
  })


  const adicionar = () => {
    const {numero1,numero2} =  estado;
    return parseInt(numero1) + parseInt(numero2);
  }

  const subtrair = () => {
    const {numero1,numero2} =  estado;
    return  numero1 - numero2;
  }

  const multiplicar = () => {
    const {numero1,numero2} =  estado;
    return numero1 * numero2;
  }

  const dividir = () => {
    const {numero1,numero2} =  estado;
    return (numero1 / numero2).toFixed(2);
  }
  

  const escolherOperacao = () =>{
    const {operacao} = estado;
    switch(operacao){
      case 'subtracao':
        return subtrair();
      case 'multiplicacao':
        return multiplicar();
      case 'divisao':
        return dividir();  
      default:
        return adicionar();   
  }
  }
</script>

<template>
  <div class="container">
    <div class="row">
      <h1>Calculdora Aritmética</h1>
      <div class="col-md-2">
      <input @keyup="evento => estado.numero1 = evento.target.value" type="number" class="form-control mb-3">
      <input @keyup="evento => estado.numero2 = evento.target.value" type="number" class="form-control">
    </div>
      <div class="col-md-2">
        <select @change="evento => estado.operacao = evento.target.value" class="form-control">
          <option value="adicao">Adição</option>
          <option value="subtracao">Subtração</option>
          <option value="multiplicacao">Multiplicação</option>
          <option value="divisao">Divisão</option>
        </select>
      </div>
      <p>Resultado: {{ escolherOperacao() }}</p>
    </div>
  </div>
  
</template>

<style scoped>

</style>
