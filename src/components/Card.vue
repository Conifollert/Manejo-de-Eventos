<script>

export default{
    props: ["cita", "index"],
}
</script>

<template>
    <div class="mi-card"   :class="{
                'bg-red': cita.gravedad == 3,
                'bg-yellow': cita.gravedad == 2,
                'bg-green': cita.gravedad == 1,
            }">
        <label for="">Paciente</label>
        <p>{{ cita.paciente }}</p>
        <label for="">fecha</label>
        <p>{{ cita.fecha }}</p>
        <label for="">Hora</label>
        <p>{{ cita.hora }}</p>
        <label for="">Motivo</label>
        <p>{{ cita.motivo }}</p>
        <button>Eliminar</button>
        <button @click="$emit('eliminarConsulta', index)">Eliminar</button>
    </div>

</template>

<style scoped>

.mi-card{
    padding: 20px 2vw;
    border-radius: 20px;
    margin: 0px 1vw;
    width: 150px;
}

.mi-card label{
font-weight: bold;
}

.bg-red{
    background: red;
    color: white;
}

.bg-yellow{
    background: yellow;
}

.bg-green{
    background: greenyellow;
}
</style>