<template>
  <div ref="container">
    <img
      width="200"
      src="https://media-public.canva.com/MADE6lOJ6h0/1/thumbnail_large-1.png"
      alt=""
    />
    <img
      ref="roleta"
      width="300"
      src="https://media-public.canva.com/RTx-w/MADzv3RTx-w/1/tl.png"
      alt=""
    />
    <img
      width="200"
      src="https://media-public.canva.com/bujNU/MAFEIBbujNU/1/tl.png"
      alt=""
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      isTeste: true,
      elapsedTime: 0,
    };
  },
  mounted() {
    // Armazena a referência do componente em uma variável
    var vm = this;
    var start = new Date();
    // Armazena o retorno do setInterval em uma variável
    this.intervalId = setInterval(function () {
      vm.$refs.roleta.style.transform = 'rotate(360deg)';

      // Para a roleta aleatoriamente em um ângulo
      setTimeout(function () {
        var randomAngle = Math.floor(Math.random() * 360);
        vm.$refs.roleta.style.transform = 'rotate(' + randomAngle + 'deg)';
      }, 3000); // 3000 é o tempo em milissegundos que a roleta leva para parar
    }, 0); // 0 é o tempo em milissegundos para a execução da função

    var end = new Date();
    // Calcula a diferença entre as duas datas em milissegundos
    this.elapsedTime = end - start;

    if (this.elapsedTime == 1000) {
      clearInterval(this.intervalId);
      console.log(this.elapsedTime);
    }
  },
};
</script>

<style>
#container {
  width: 100%;
  height: 100%;
}
</style>
