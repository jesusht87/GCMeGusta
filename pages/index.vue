<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <div class="allwindow">
        <div class="hero">
          <img src="@/assets/images/logo-header-web.png" class="herologo" />

          <div class="welcometext">
            <h1>¿Aceptas el reto?</h1>
            <p>
              En ocasiones, quienes más cerca tenemos, son quienes menos
              conocemos. Compañeros de trabajo, hermanos, amigos de toda la
              vida... a veces la rutina nos lleva, y no nos deja tiempo para charlar y conocer mejor a quienes nos rodean.
            </p>
            <p>
              Por eso, Ingenio te invita a parar, a descubrir, a sentir. Y para ello, te
              proponemos un juego: Envía a tus amig@s y conocid@s este sencillo
              test donde escribirás una pregunta sobre tu vida, y 3 posibles
              respuestas. Si logran acertar, te tocará invitar a una comida o
              cena en Ingenio. Pero si pierden (y no olvides poner respuestas
              que les despisten 😈), les tocará invitarte a tí.
            </p>
            <p>
              Sea como sea, les deseamos que disfruten de una comida o cena
              juntos, en el marco incomparable del municipio de Ingenio.
            </p>
            <img src="@/assets/images/arrow-down.png" class="arrow-landing" />
          </div>
        </div>
      </div>
            <Startquiz />
    </v-col>
  </v-row>
</template>

<script>
import Startquiz from "../components/startquiz.vue";
export default {
  name: "IndexPage",
  components: { Startquiz },
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
