<template>
  <v-container fluid>
    <v-row align="center" justify="center">
      <v-col v-if="notfinished" cols="12" mb-10>
        <form class="formtext">
          <v-text-field v-model="sendername" label="Tu Nombre" required />

          <v-text-field
            v-model="receivername"
            label="El nombre de tu amigo/a"
            required
          />

          <v-text-field
            v-model="question"
            label="¿Qué le preguntamos a tu amigo/a?"
            required
          />

          <v-text-field
            v-model="rightanswer"
            label="Pon aquí la respuesta correcta"
            required
          />

          <v-text-field
            v-model="wronganswerone"
            label="Pon aquí una respuesta falsa..."
            required
          />

          <v-text-field
            v-model="wronganswertwo"
            label="Y aquí otra respuesta falsa para despistarle aún más..."
            required
          />

          <v-btn block class="mb-4" @click="submit()"> Registrar </v-btn>
          <v-btn @click="clear"> Borrar Campos </v-btn>
        </form>
      </v-col>
      <v-col v-else>
        <v-card width="400">
          <v-card-title class="white--text mt-8">
            <p class="ml-3">¡Ya sólo tienes que enviarlo!</p>
          </v-card-title>

          <v-card-text>
            <v-btn
              block
              color="green"
              :href="linkmessage + baseurl + '/landing?id=' + responseid"
            >
              💬 Enviar por WhatsApp
            </v-btn>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "StartQuiz",
  data: () => ({
    sendername: "",
    receivername: "",
    question: "",
    rightanswer: "",
    wronganswerone: "",
    wronganswertwo: "",
    show: true,
    linkmessage:
      "whatsapp://send?text=A%20veces%2C%20lo%20que%20tenemos%20m%C3%A1s%20cerca%20es%20lo%20que%20m%C3%A1s%20desconocemos...%20%C2%BFte%20atreves%20a%20responder%20esta%20pregunta%20sobre%20m%C3%AD%3F%20Si%20aciertas%2C%20te%20invito%20a%20comer%20en%20Ingenio.%20Y%20si%20pierdes...%20te%20toca%20invitarme...%20%C2%BFaceptas%20el%20reto%3F%20%F0%9F%98%8D%20 - ",
    baseurl: "http://localhost:3000",
    notfinished: true,
    responseid: "",
  }),
  methods: {
    async submit() {
      try {
        await this.$axios
          .post("/proposition", {
            sendername: this.sendername,
            receivername: this.receivername,
            question: this.question,
            rightanswer: this.rightanswer,
            wronganswerone: this.wronganswerone,
            wronganswertwo: this.wronganswertwo,
            show: true
          })
          .then((response) => {
            this.responseid = response.data._id;
            this.notfinished = false;
          });
      } catch (err) {}
    },
    clear() {},
  },
};
</script>

<style scoped>
.formtext {
  text-align: center;
  color: black;
}
.formtext {
  color: black;
}
</style>
