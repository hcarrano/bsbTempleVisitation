<template>
  <div  class="hbg-nav ">
    <nav class="navbar navbar-expand-lg navbar-light bg-light  "    >
      <div class="container-fluid"  >
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarTogglerDemo01" aria-controls="navbarTogglerDemo01" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarTogglerDemo01">
          <ul class="nav me-auto mb-2 mb-lg-0 justify-content-end">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="https://www.vindeacristo.org/" target="_blank" >Conheça Mais</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Voltar</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
  <div>
    <img class="img-fluid " style="max-width: auto; height: auto" alt="Background" src=".\assets\bg_brasilia.png" >
    <HelloWorld msg="Templo de Brasília - Visitação"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0;

}

</style>
