<template>
  <v-row>
    <v-col class="text-center">
      <div class="allwindow">
        <div class="hero">
          <img src="@/assets/images/logo-header-web.png" class="herologo" />

          <div class="welcometext">
            <h1>¡Ups!</h1>
            <h1>Respuesta Incorrecta</h1>
            <p>
              Esa respuesta no es correcta... pero, ¿qué tal si lo arreglamos?
              Disfrutando de un almuerzo, o una cena en Ingenio, nos podemos
              poner al día y descubrir la respuesta correcta. ¿Te apuntas? Por
              cierto... ya sabes a quién le toca pagar... 😉
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
  name: "WrongPage",
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
  min-height: 800px;
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
  margin: 5px;
  padding: 5px;
}
</style>
