<template>
  <div class="q-pa-md">
    <h3 style="font-size: 2.2em;">Datos Personales</h3>
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

      <q-input
        ref="lastname"
        filled
        v-model="lastname"
        label="Your last name *"
        hint="Last Name"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Please type something']"
      />

      <q-input 
        ref="date"
        filled
        type="date"
        v-model="date"
        hint="Native date"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Please enter a date']"
     
      />

      
      <q-input
        ref="height"
        filled
        type="number"
        v-model="height"
        label="Your height"
        mask="#.##"
        fill-mask="0"
        reverse-fill-mask
        hint="Example: 1.60"
        lazy-rules
        :rules="[(val) => !!val || 'Please write something. Example: 1.60',
                 (val) => (val.length > 3 && val.length < 5) || 'Example: 1.60']"
     
      />

      <q-input
        ref="weight"
        v-model.number="weight"
        type="number"
        filled
        label="Your weight"
        mask="###"
        hint="Example: 60 kg"
        suffix="kg"
        lazy-rules
        :rules="[(val) => !!val || 'Please write something. Example: 90 kg',
                 (val) => (val > 10 && val < 635) || 'Enter a correct weight between 10 to 635']"
     
    />

    <q-input
        ref="telephone"
        filled
        v-model="telephone"
        label="Telephone"
        mask="(###) ### - ####"
        hint="Mask: (###) ### - ####"

        lazy-rules
        :rules="[(val) => !!val || 'Please write something.',
        (val) => (val.length > 15 && val.length < 18 ) || 'Enter a valid telephone']"
     
      />

    <q-input
        ref="phone"
        filled
        v-model="phone"
        label="Phone"
        mask="(##) #### - ####"
        hint="Mask: (##) #### - ####"

        lazy-rules
        :rules="[(val) => !!val || 'Please write something.',
        (val) => (val.length > 15 && val.length < 18 ) || 'Enter a valid phone']"
     
      />

      <q-select
        ref="blood"
        filled
        v-model="blood"
        :options="options"
        label="Standard"
        hint="Type Blood"
         lazy-rules
        :rules="[(val) => !!val || 'Please write something.']"
     
      />

      <q-btn @click="setData" color="primary" text-color="white" label="Continuar" />
    </form>
  </div>
</template>


<script>
export default {
  name: "FormSalud",
  data () {
    return {
      name: null,
      lastname: null,
      date: null,
      height: null,
      weight: null,
      telephone: null,
      phone: null,
      blood: null,
      options: [
        {
          label: 'O negativo',
          value: 'oNegativo',
        },
        {
          label: 'O positivo',
          value: 'oPositivo',
        },
        {
          label: 'A negativo',
          value: 'aNegativo',
        },
        {
          label: 'A positivo',
          value: 'aPositivo',
        },
        {
          label: 'B negativo',
          value: 'bNegativo',
        },
        {
          label: 'B positivo',
          value: 'bPositivo',
        },
        {
          label: 'AB negativo',
          value: 'abNegativo',
        },
        {
          label: 'AB positivo',
          value: 'abPositivo',
        }],
      step: 1
    }
  },

  methods: {
     setData() {
      this.$refs.name.validate()
      this.$refs.lastname.validate()
      this.$refs.date.validate()
      this.$refs.height.validate()
      this.$refs.weight.validate()
      this.$refs.telephone.validate()
      this.$refs.phone.validate()
      this.$refs.blood.validate()

      if (this.$refs.name.hasError || 
          this.$refs.lastname.hasError  ||
          this.$refs.date.hasError ||
          this.$refs.height.hasError ||
          this.$refs.weight.hasError ||
          this.$refs.telephone.hasError ||
          this.$refs.phone.hasError ||
          this.$refs.blood.hasError) {
        console.log("Error en el Form");
      }else{
        this.step++;
        console.log(this.step);
        this.$emit("getData",this.step);
      }
    },
  }
}
</script>
