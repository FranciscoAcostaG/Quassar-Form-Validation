<template>
  <div class="q-pa-md row justify-center">
    <q-stepper
      v-model="step"
      ref="stepper"
      contracted
      color="primary"
      animated
      class="col-10"
    >
      <q-step
        :name="1"
        title="Select campaign settings"
        icon="settings"
        :done="step > 1"
      >
        <FormDatos @getData="getData" />
      </q-step>

      <q-step
        :name="2"
        title="Create an ad group"
        icon="create_new_folder"
        :done="step > 2"
      >
        <FormHabitos @getData="getData" />
      </q-step>

      <q-step :name="3" title="Create an ad" icon="create_new_folder">
        <FormSalud @getData="getData" />
      </q-step>

      <q-step :name="4" title="Create an ad" icon="create_new_folder">
        <FormEnfermedades @getData="getData" />
      </q-step>

      <!--<template v-slot:navigation>
        <q-stepper-navigation>
          <q-btn v-on:click="next" color="primary" :label="step === 4 ? 'Finish' : 'Continue'" />
          <q-btn v-if="step > 1" flat color="primary" @click="$refs.stepper.previous()" label="Back" class="q-ml-sm" />
        </q-stepper-navigation>
      </template>-->
    </q-stepper>
  </div>
</template>

<script>
import FormSalud from "../components/FormSalud.vue";
import FormHabitos from "../components/FormHabitos.vue";
import FormDatos from "../components/FormDatos.vue";
import FormEnfermedades from "../components/FormEnfermedades.vue";

export default {
  components: { FormSalud, FormHabitos, FormDatos, FormEnfermedades },
  data() {
    return {
      step: 1,
    };
  },
  methods: {
    getData(data) {
      this.step = data;
    },
    next() {
      switch (this.step) {
        case 1:
          console.log("Caso 1");
          break;
        case 2:
          console.log("Caso 2");
          break;
        case 3:
          console.log("Caso 3");
          break;
        case 4:
          console.log("Caso 4");
          break;
        case 5:
          console.log("Caso 5");
          this.step = 1;
          break;
        default:
          console.log("No caso");
          this.step = 1;
          break;
      }
    },
  },
};
</script>