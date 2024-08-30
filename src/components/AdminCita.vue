<script>
import FormPaciente from './FormPaciente.vue'
import CardPaciente from './CardPaciente.vue'

export default {
  name: 'AdminCita',
  data() {
    return {
      pacientes: []
    }
  },
  components: {
    FormPaciente,
    CardPaciente
  },
  methods: {
    agregarPaciente(nuevoPaciente) {
      this.pacientes.push(nuevoPaciente)
    },
    removeCard(index) {
      this.pacientes.splice(index, 1)
    }
  }
}
</script>

<template>
  <FormPaciente @submit-form="agregarPaciente" />
  <div v-show="pacientes.length == 0">
    <p :style="{ color: 'red', textAlign: 'center', marginTop: '2rem' }">
      Aún no hay pacientes registrados. Por favor, registra un nuevo paciente.
    </p>
  </div>
  <div class="card-container">
    <CardPaciente
      v-for="(paciente, index) in pacientes"
      :key="index"
      :paciente="paciente.paciente"
      :fecha="paciente.fecha"
      :hora="paciente.hora"
      :gravedad="paciente.gravedad"
      :motivo="paciente.motivo"
      @remove-card="pacientes.splice(index, 1)"
    />
  </div>
</template>
<style>
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
}
</style>
