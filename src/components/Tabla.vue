<script>
export default{
    props: ["consultas"],

    data(){
        return{
            consulta: this.consultas
        }
    },
    methods: {
        
        eliminarConsulta(i) {
        this.consulta.splice(i,1);
    },
   }
};

</script>

<template>
    <table border="regde">
        <thead>
            <tr>
                <th>Paciente</th>
                <th>Hora</th>
                <th>Fecha</th>
                <th>Gravedad</th>
                <th>Motivo</th>
            </tr>
        </thead>

        <tbody>
            <tr v-for="({paciente, fecha, hora, motivo, gravedad}, i) in consulta"
            :key="i"
            :class="{
                'bg-red': gravedad == 3,
                'bg-yellow': gravedad == 2,
                'bg-green': gravedad == 1,
            }"

            >
            <td>{{ paciente }}</td>
            <td>{{ hora }}</td>
            <td>{{ fecha }}</td>
            <td>{{ motivo }}</td>

            <button @click="eliminarConsulta(i)">Eliminar</button>
            </tr>
        </tbody>
    </table>
</template>

<style>
td,
th{
    padding: 10px;
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