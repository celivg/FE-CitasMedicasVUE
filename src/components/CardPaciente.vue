<script>
export default {
  name: 'CardPaciente',
  props: ['paciente', 'fecha', 'hora', 'gravedad', 'motivo'],
  methods: {
    removeCard() {
      this.$emit('remove-card')
    }
  },
  emits: ['remove-card']
}
</script>

<template>
  <div
    class="card"
    :class="gravedad === 'Leve' ? 'green' : gravedad === 'Medio' ? 'yellow' : 'red'"
  >
    <h4>Paciente:</h4>
    <p>{{ paciente }}</p>
    <h4>Fecha:</h4>
    <p>{{ fecha }}</p>
    <h4>Hora</h4>
    <p>{{ hora }}</p>
    <h4>Gravedad:</h4>
    <p>{{ gravedad }}</p>
    <h4>Motivo:</h4>
    <p>{{ motivo }}</p>

    <button @click="removeCard">Eliminar</button>
  </div>
</template>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  border: 1px solid #ddd;
  border-radius: 10px;
  padding: 1rem;
  margin: 1rem;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  width: 200px;
}

button {
  background-color: #ffffff;
  color: rgb(0, 0, 0);
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

h4 {
  padding-bottom: 3px;
}

p {
  padding-bottom: 7px;
}

.yellow {
  background-color: rgb(247, 247, 129);
}
.green {
  background-color: rgb(140, 226, 140);
}
.red {
  background-color: rgb(238, 125, 125);
}
</style>
