
<script>
import Tabla from "./components/Tabla.vue";
import miCard from "./components/Card.vue";

export default{
  name: "App",
  data(){
    return{
      consultas: [],
     consulta: {},
    };
  },

  methods: {
    agregarConsulta(){
      const {consulta} = this;
      this.consultas.push(consulta);
      this.consulta = {};
    },

    eliminarConsulta(i) {
      this.consultas.splice(1,1);
    },
  },

 components: {
  Tabla,
  miCard
  }, 
};
</script>

<template>
  <div id="app">
    <form @submit..prevent="agregarConsulta">
      <main>
        <div>
          <label :class="{'text-red': !consulta.paciente}">Paciente</label>
          <input v-model="consulta.paciente">
        </div>

        <div>
          <label :class="{'text-red': !consulta.fecha}">Fecha</label>
          <input type="date"v-model="consulta.fecha">
        </div>

        <div>
          <label :class="{'text-red': !consulta.hora}">Hora</label>
          <input type="time" v-model="consulta.hora">
        </div>

        <div>
          <label :class="{'text-red': !consulta.gravedad}">Gravedad</label>
          <select v-model="consulta.gravedad">
            <option value="1">Baja</option>
            <option value="2">Media</option>
            <option value="3">Alta</option>
          </select>
        </div>
        <div>
          <label :class="{'text-red': !consulta.motivo}">Motivo</label>
          <input v-model="consulta.motivo">
        </div>
      </main>

      <button :disabled="
      !consulta.paciente ||
      !consulta.fecha ||
      !consulta.hora ||
      !consulta.gravedad ||
      !consulta.motivo 
      ">
      Agregar
      </button>
    </form>

    <div class="consultas">
      <p class="text-red" v-if="!consultas.length">
        Aún no hay consultas registradas
      </p>

      <!-- <div class="citas" v-else>
        <miCard v-for="(consulta, i) in consultas" :cita="consulta" :index="i" :key="i" @eliminarConsulta="eliminarConsulta" />
      </div> -->
     <Tabla v-else :consultas="consultas" @eliminarConsulta="eliminarConsulta"/>
    </div>
  </div>
</template>

<style>
#app{
  font-family: Avenir, Helvertica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.text-red{
  color: red;
}

form{
  border: right 3px;
  border-radius: 10px;
  padding: 10px;
  margin: auto;
  width: 650px;
}

form main{
  display: flex;
  justify-content: center;
  gap: 10px
}

form div{
  display: flex;
  flex-direction: column;
  text-align: center;
  gap: 5px;
}

form label{
  font-weight: bold;
}

form select
form input{
  height: 20px;
  box-sizing: border-box;
}

form button{
  margin-top: 20px;
}

.consultas{
  margin: 20px auto;
  width: fit-content;
}

.citas{
  display: flex;
  justify-content: center;
}
</style>