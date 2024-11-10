<template> 
  <div class="container mt-3 items-center">
    <img src="../assets/img/International_Pokémon_logo.svg.png" class="img-fluid logo" alt="Pokémon Logo">
  </div>
  <div class="container mt-3 border rounded-3 pokemon-card-container">
    <div v-if="inGame" class="row">
      <PokemonCard @results="handleResults"/>
    </div>
    <div v-else>
      <div v-if="showResults" class="results-section">
        <p class="results-title">¡Estos son los resultados!</p>
        <ul class="results-list">
          <li>Correctas: {{ results.corrects }}</li>
          <li>Skips: {{ results.skips }} <span v-if="results.skips===20">Buen trabajo, skipeando todo</span></li>
          <li>Errores: {{ results.errors }}</li>
        </ul>
      </div>
      <button v-if="!showResults" @click="startGame" class="start-btn">¡Empezar!</button>
      <button v-else @click="startGame" class="start-btn restart-btn">¡Reiniciar!</button>
    </div>
  </div>
</template>

<script>
import PokemonCard from './PokemonCard.vue'
export default {
  name: 'PokemonContainer',
  components: {
    PokemonCard
  },
  data() {
    return {
      inGame: false,
      showResults: false,
      results: {},
    };
  },
  methods: {
    handleResults(result) {
      this.results = result;
      this.inGame = false;
      this.showResults = true;
    },
    startGame() {
      this.inGame = true;
      this.showResults = false;
    }
  }
};
</script>

<style scoped>
/* Logo */
.logo {
  display: block;
  margin: 0 auto;
  max-width: 100%;
  height: auto;
}

/* Contenedor de la tarjeta Pokémon */
.pokemon-card-container {
  background-color: #f8f8f8;
  padding: 20px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  border-radius: 12px;
}

/* Título de resultados */
.results-title {
  font-size: 24px;
  font-weight: bold;
  color: #ffcb05;
  text-align: center;
  margin-bottom: 15px;
}

/* Lista de resultados */
.results-list {
  list-style-type: none;
  padding: 0;
  font-size: 18px;
  font-family: 'Arial', sans-serif;
  text-align: center;
}

.results-list li {
  padding: 5px;
}

/* Botones */
.start-btn {
  background-color: #ffcb05;
  color: #3d7dca;
  padding: 10px 20px;
  border: none;
  font-size: 18px;
  font-weight: bold;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  width: 100%;
  margin-top: 10px;
}

.start-btn:hover {
  background-color: #e6b800;
}

.restart-btn {
  background-color: #e60000;
  color: white;
}

.restart-btn:hover {
  background-color: #cc0000;
}

/* Ajustes para mejorar el diseño móvil */
@media (max-width: 768px) {
  .results-title {
    font-size: 20px;
  }
  .results-list li {
    font-size: 16px;
  }
  .start-btn {
    font-size: 16px;
    padding: 8px 16px;
  }
}
</style>

<!-- <template>
  <div class="container mt-3 items-center">
    <img src="../assets/img/International_Pokémon_logo.svg.png" class="img-fluid" alt="">
  </div>
  <div class="container mt-3 border rounded-3">
    <div v-if="inGame" class="row">
      <PokemonCard @results="handleResults"/>
    </div>
    <div v-else>
      <div v-if="showResults">
        <p>estos son los resultados:</p>
        <ul>
          <li>Correctas: {{ results.corrects }}</li>
          <li>Skips: {{ results.skips }}</li>
          <li>Errores: {{ results.errors }}</li>
        </ul>
      </div>
      <button v-if="!showResults" @click="startGame">start</button>
      <button v-else @click="startGame">Re Start</button>
    </div>
  </div>
</template>

<script>
import PokemonCard from './PokemonCard.vue'
export default {
  name: 'PokemonContainer',
  components: {
    PokemonCard
  },
  data() {
    return {
      inGame:false,
      showResults:false,
      results:{
      },
    };
  },
  methods:{
    handleResults(result){
      this.results=result;
      this.inGame=false;
      this.showResults=true;
    },
    startGame(){
      this.inGame=true
    }
  }
};
</script>
<style scoped>
</style> -->