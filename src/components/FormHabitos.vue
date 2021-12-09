<template>
  <div class="q-pa-md">
    <h3 style="font-size: 2.2em">Habitos</h3>
    <form class="q-gutter-md col-5">
      <q-select
        ref="cigar"
        filled
        v-model="cigar"
        :options="resp"
        label="Smoker"
        lazy-rules
        :rules="[(val) => !!val || 'Please write something.']"
      />

      <q-select
        ref="alcohol"
        filled
        v-model="alcohol"
        :options="resp"
        label="Alcoholic"
        lazy-rules
        :rules="[(val) => !!val || 'Please write something.']"
      />

      <q-select
        ref="diet"
        filled
        v-model="diet"
        :options="resp"
        label="Diet"
        lazy-rules
        :rules="[(val) => !!val || 'Please write something.']"
      />

      
      <q-select
        ref="exercise"
        filled
        v-model="exercise"
        :options="resp"
        label="Exercise"
        lazy-rules
        :rules="[(val) => !!val || 'Please write something.']"
      />

      <q-select
        ref="sleeping"
        filled
        v-model="sleeping"
        :options="resp"
        label="trouble sleeping"
        lazy-rules
        :rules="[(val) => !!val || 'Please write something.']"
      />

      <q-btn
        @click="setData"
        color="primary"
        text-color="white"
        label="Continuar"
      />
      <q-btn
        @click="volver"
        color="secundary"
        text-color="black"
        label="Back"
      />
      
    </form>
  </div>
</template>

<script>
export default {
  name: "FormHabitos",
  data() {
    return {
      cigar: null,
      alcohol: null,
      diet: null,
      exercise: null,
      sleeping: null,
      resp: [
        {
          label: "Yes",
          value: "Yes",
        },
        {
          label: "No",
          value: "No",
        },
      ],
      step: 2,
    };
  },

  methods: {
    setData() {
      this.$refs.cigar.validate();
      this.$refs.alcohol.validate();
      this.$refs.diet.validate();
      this.$refs.exercise.validate();
      this.$refs.sleeping.validate();

      if (this.$refs.cigar.hasError || 
          this.$refs.alcohol.hasError ||
          this.$refs.diet.hasError ||
          this.$refs.excercise.hasError ||
          this.$refs.sleeping.hasError) {
        console.log("Error en el Form");
      } else {
        this.step++;
        console.log(this.step);
        this.$emit("getData", this.step);
      }
    },
    volver() {
      this.step = 1;
      this.$emit("getData", this.step);
    },
  },
};
</script>
