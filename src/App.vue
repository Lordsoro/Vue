<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-md-12">
        <h1>Personas</h1>
      </div>
    </div>

    <div class="row">
      <div class="col-md-12">
        <formulario-persona @add-persona="agregarPersona" />
        <tabla-personas
          :personas="personas"
          @delete-persona="eliminarPersona"
          @actualizarPersona="actualizarPersona"
        />
      </div>
    </div>
  </div>
</template>

<script>
import TablaPersonas from "@/components/TablaPersonas.vue";
import FormularioPersona from "@/components/FormularioPersona.vue";

export default {
  name: "app",
  components: {
    TablaPersonas,
    FormularioPersona,
    TablaPersonas,
  },
  data() {
    return {
      personas: [
        {
          id: 1,
          nombre: "John",
          apellido: "lennon",
          email: "LennyBeatle@liverpool.com",
        },
        {
          id: 2,
          nombre: "Paul",
          apellido: "Mccartney",
          email: "billySehars@liverpool.com",
        },
        {
          id: 3,
          nombre: "Ringo",
          apellido: "starr",
          email: "dingobeatle@liverpool.com",
        },
        {
          id: 4,
          nombre: "George",
          apellido: "Harrison",
          email: "therockpiece@liverpool.com",
        },
      ],
    };
  },
  methods: {
    agregarPersona(persona) {
      let id = 0;
      if (this.personas.length > 0) {
        id = this.personas[this.personas.length - 1].id + 1;
      }
      this.personas = [...this.personas, persona];
    },
    eliminarPersona(id) {
      this.personas = this.personas.filter((persona) => persona.id !== id);
    },
    actualizarPersona(id, personaActualizada) {
      this.personas = this.personas.map((persona) =>
        persona.id === id ? personaActualizada : persona
      );
    },
  },
};
</script>

<style>
button {
  background: #009435;
  border: 1px solid #009435;
}
</style>