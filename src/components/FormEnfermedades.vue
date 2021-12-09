<template>
 <div class="q-pa-md">
    <h3>Enfermedades Cronicas</h3>
    <form
      class="q-gutter-md col-5"
    >
      <q-input
        ref="name"
        filled
        v-model="name"
        label="Your name *"
        hint="Name and surname"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Please type something']"
      />

      <button @click="setData">Finalizar</button>
      <button @click="volver">Back</button>
      
    </form>
 </div>
</template>


<script>
export default {
  name: "FormSalud",
  data () {
    return {
      name: null,

      step: 4
    }
  },

  methods: {
    setData() {
      this.$refs.name.validate()

      if (this.$refs.name.hasError) {
        console.log("Error en el Form");
      }else{
        this.step = 1;
        console.log(this.step);
        this.$emit("getData",this.step);
      }
      },
      volver(){
        this.step = 3;
        this.$emit("getData",this.step);
      }
  }
}
</script>
