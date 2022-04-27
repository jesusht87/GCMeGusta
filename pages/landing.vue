<template>
  <v-row>
    <v-col v-if="proposition.show" class="text-center">
      <div class="allwindow">
        <div class="hero">
          <img src="@/assets/images/logo-header-web.png" class="herologo" />

          <div class="welcometext">
            <h1>¿Aceptas el reto?</h1>
            <p>
              En ocasiones, quienes más cerca tenemos, son quienes menos
              conocemos. Compañeros de trabajo, hermanos, amigos de toda la
              vida...
            </p>
            <p>
              Pero, en Ingenio, creemos de verdad en invitarte a sentir de nuevo
              en conexión con tu entorno. Con tu familia, con tus amigos, con
              tus compañeros de trabajo... y estamos decididos a poner el marco
              ideal para ello, en un municipio único, lleno de contrastes,
              naturaleza, Historia, tradiciones y curiosidades para descubrir y
              sentir.
            </p>
            <br />
            <h3>
              ¿Te animas a descubrir si conoces bien a
              {{ proposition.sendername }}?
            </h3>
            <h4>
              Si ganas, {{ proposition.sendername }} te invita a comer en
              Ingenio, y así compartiréis un gran rato juntos. Y si pierdes, te
              toca invitar a tí... y así, descubrirás mejor a tu amig@.
            </h4>
          </div>

          <img src="@/assets/images/arrow-down.png" class="arrow-landing" />
          <div>
            <v-card elevation="2" outlined shaped class="questioncard">
              <v-card-title>{{ proposition.question }}</v-card-title>
              <v-btn class="buttons" @click="finishWrong()">{{
                proposition.wronganswertwo
              }}</v-btn>
              <v-btn class="buttons" @click="finishOk()">{{
                proposition.rightanswer
              }}</v-btn>
              <v-btn class="buttons" @click="finishWrong()">{{
                proposition.wronganswerone
              }}</v-btn>
            </v-card>
          </div>
        </div>
      </div>
    </v-col>
    <v-col v-else>
      <div class="allwindow">
        <div class="hero">
          <img src="@/assets/images/logo-header-web.png" class="herologo" />

          <div class="welcometext">
            <h1>{{ proposition.receivername }} ya contestó...</h1>
            <p>
              Y su respuesta fué {{ textresult }}. Así que ya sabes... ¿a quíen
              le toca invitar?
            </p>
            <div class="selectorDiv">
              <v-btn
                class="buttons"
                href="https://turismoingenio.com/restaurantes-ingenio/"
                block
                >🍲 Ver Restaurantes</v-btn
              >
              <v-btn
                class="buttons"
                href="https://drive.google.com/file/d/1KKm_Pfw14wCJKldDJK0oeo-F4Jg011ID/view?usp=sharing"
                block
                >🗺 Ruta: Un día en Ingenio</v-btn
              >
              <v-btn class="buttons" href="https://turismoingenio.com" block
                >♾ Ver TurismoIngenio.com</v-btn
              >
            </div>
          </div>
        </div>
      </div>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "LandingPage",
  data() {
    return {
      proposition: [],
      textresult: "",
    };
  },
  async mounted() {
    // Charging data from back-end about the proposition
    const propId = this.$route.query.id;
    const response = await this.$axios.get("/proposition/" + propId);
    this.proposition = response.data[0];
    // Checks if proposition have been answered true or false
    if ((this.proposition.success = true)) {
      this.textresult = "correcta ☺️";
    } else {
      this.textresult = "errónea 😱";
    }
  },
  methods: {
    async finishOk() {
      const propId = this.$route.query.id;
      await this.$axios.put("/proposition/" + propId, {
        success: true,
        show: false,
      });
      window.location.href = "/right";
    },
    async finishWrong() {
      const propId = this.$route.query.id;
      await this.$axios.put("/proposition/" + propId, {
        success: false,
        show: false,
      });
      window.location.href = "/wrong";
    },
  },
};
</script>

<style scoped>
.hero {
  text-align: center;
}
.herologo {
  max-width: 150px;
  margin-top: 15px;
}
.allwindow {
  background-image: url("@/assets/images/background.jpg");
  background-size: cover;
  height: auto;
  min-height: 700px;
  padding: 10px;
}
.welcometext {
  margin: 15px;
  padding: 25px;
  background-color: rgba(255, 255, 255, 0.7);
  border-radius: 5px;
  color: black;
}
.arrow-landing {
  width: 150px;
}
.questioncard {
  margin: 15px;
  padding: 25px;
}
.buttons {
  margin: 15px;
  padding: 5px;
}
</style>
