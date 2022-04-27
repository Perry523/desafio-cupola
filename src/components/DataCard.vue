<template>
  <v-card width="240px" class="pl-0 pa-5 pb-8 rounded-lg elevation-1">
    <v-row justify="end" class="mb-n4">
      <v-tooltip top color="black" content-class="tooltip-top">
        <template v-slot:activator="{ on, attrs }">
          <v-icon v-bind="attrs" v-on="on" size="18"
            >mdi-information-outline</v-icon
          >
        </template>
        <span>{{ helper }}</span>
      </v-tooltip>
    </v-row>
    <v-row class="pa-3 pl-8">
      <v-avatar class="mr-3" size="55" :color="`${color.avatar}`"
        ><v-icon size="23" :color="color.icon">{{ icon }}</v-icon></v-avatar
      >
      <div class="d-flex flex-column">
        <div class="data-value-font-size font-weight-medium">
          {{ formatedDataValue }}
        </div>
        <div class="font-weight-light mt-n1 grey--text text-subtitle-1">
          {{ data.type }}
        </div>
      </div>
    </v-row>
  </v-card>
</template>

<script>
export default {
  name: "DataCard",
  props: {
    color: {
      type: Object,
      default: () => {},
    },
    data: {
      type: Object,
      default: () => {},
    },
    icon: {
      type: String,
      default: "",
    },
    helper: {
      type: String,
      default: "",
    },
  },
  computed: {
    formatedDataValue() {
      if (typeof this.data.value === String) return this.data.value;
      const stringDataValue = this.data.value.toString();
      if (stringDataValue.length >= 7) {
        const [firstDigit, secondDigit] = stringDataValue;
        return `${firstDigit}.${secondDigit} M`;
      }
      return stringDataValue.replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    },
  },
};
</script>
<style scoped>
.data-value-font-size {
  font-size: 2rem;
  line-height: 1.2;
}
</style>
