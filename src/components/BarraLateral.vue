<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="Logo Alura Tracker" />
    </h1>
    <button class="button" @click="alterarTema">
      <i :class="iconeBotao" style="size:1.5rem"></i>
      {{textoBotao}}
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BarraLateral",
  emits: ['aoTemaAlterado'],
  data(){
    return {
      modoEscuroAtivo: false
    }
  },
  computed:{
    textoBotao(){
      if(this.modoEscuroAtivo)
        return 'Ativar modo escuro'
      return 'Desativar modo escuro'
    },
    iconeBotao(){
      if(this.modoEscuroAtivo)
        return 'fa-solid fa-moon'
      return 'fa-solid fa-sun'
    }
  },
  methods: {
    alterarTema(){
      this.modoEscuroAtivo = !this.modoEscuroAtivo
      this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
    }
  }
});
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
