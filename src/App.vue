<template>
  <v-app>
    <v-main class="global-background">
      <v-container fill-height class="justify-content-center">
        <v-row justify="center">
          <v-col v-for="(card, i) in cards" :key="i" cols="auto" class="ml-5">
            <data-card v-bind="card" />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import "@/assets/global.scss";
import DataCard from "@/components/DataCard.vue";
export default {
  name: "App",
  data: () => ({
    cards: [
      {
        data: {
          value: 2500000,
          type: "Conversões",
        },
        icon: "mdi-email-outline",
        color: {
          avatar: "#BBDFFF",
          icon: "#1E93FF",
        },
        helper: "Conversão é a ação do envio de qualquer formulário",
      },
      {
        data: {
          value: 965321,
          type: "Leads",
        },
        icon: "mdi-account-outline",
        color: {
          avatar: "#E7C1FF",
          icon: "#CB79FF",
        },
        helper:
          "Lead é um contato individual do cliente ao enviar formulários.",
      },
      {
        data: {
          value: "R$ 10",
          type: "Custo por lead",
        },
        icon: "mdi-currency-usd",
        color: {
          avatar: "#BFF0CC",
          icon: "#4ED574",
        },
        helper:
          "É o cálculo do investimento utilizado pela quantidade de leads gerados no período.",
      },
    ],
  }),
  components: {
    DataCard,
  },
};
</script>
