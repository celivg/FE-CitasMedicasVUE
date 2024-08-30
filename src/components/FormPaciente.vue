<script>
export default {
  name: 'FormPaciente',
  data() {
    return {
      paciente: '',
      fecha: '',
      hora: '',
      gravedad: '',
      optionGravedad: ['Leve', 'Medio', 'Grave'],
      motivo: '',
      pacientes: []
    }
  },
  methods: {
    addPaciente() {
      this.$emit('submit-form', {
        paciente: this.paciente,
        fecha: this.fecha,
        hora: this.hora,
        gravedad: this.gravedad,
        motivo: this.motivo
      })

      //para limpiar el form:
      this.paciente = ''
      this.fecha = ''
      this.hora = ''
      this.gravedad = ''
      this.motivo = ''
    },
    isFormValid() {
      return this.paciente && this.fecha && this.hora && this.gravedad && this.motivo
    }
  },
  emits: ['submit-form']
}
</script>

<template>
  <form @submit.prevent="addPaciente">
    <div class="form-box">
      <div class="form-group">
        <label for="paciente" :style="{ color: paciente === '' ? 'red' : 'black' }">Paciente</label>
        <input type="text" id="paciente" v-model="paciente" />
      </div>

      <div class="form-group">
        <label for="fecha" :style="{ color: fecha === '' ? 'red' : 'black' }">Fecha</label>
        <input type="date" id="fecha" v-model="fecha" />
      </div>

      <div class="form-group">
        <label for="hora" :style="{ color: hora === '' ? 'red' : 'black' }">Hora</label>
        <input type="time" id="hora" v-model="hora" />
      </div>

      <div class="form-group">
        <label for="gravedad" :style="{ color: motivo === '' ? 'red' : 'black' }">Gravedad</label>
        <select id="gravedad" v-model="gravedad">
          <option v-for="(option, idx) in optionGravedad" :key="idx">{{ option }}</option>
        </select>
      </div>

      <div class="form-group">
        <label for="motivo" :style="{ color: motivo === '' ? 'red' : 'black' }">Motivo</label>
        <input type="text" v-model="motivo" />
      </div>
    </div>

    <div>
      <button class="btn" type="submit" :disabled="!isFormValid()">Agregar</button>
    </div>
  </form>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 3rem;
  border: 1px solid #ccc;
  border-radius: 15px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.form-group {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-box {
  display: flex;
  gap: 2rem;
}

label {
  margin-bottom: 0.5rem;
  font-weight: bold;
}

.btn {
  margin-top: 2rem;
  padding: 1rem 2.5rem;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.btn:disabled {
  background-color: #f1f1f5;
  cursor: not-allowed;
}
</style>
