<template>
  <v-row>
    <v-col cols="6">
      <v-container class="input-text-area">
        <v-textarea
          label="Input Json String"
          v-model="input"
          :hint="hint"
          rows="20"
        >
        </v-textarea>
      </v-container>
    </v-col>
    <v-col cols="6">
      <v-container class="output-text-area">
        <v-textarea
          label="Converted Json Object"
          v-model="output"
          readonly
          rows="20"
        ></v-textarea>
      </v-container>
    </v-col>
  </v-row>
</template>
<script>
export default {
  data() {
    return {
      hint: '"{\\"name\\":\\"John\\"}"', // "{\"name\":\"John\"}"
      input: "",
      output: "",
    };
  },
  watch: {
    input(val) {
      try {
        this.output = JSON.parse(val);
      } catch {
        this.output = "invalid json string";
      }
    },
  },
};
</script>
<style scoped>
.input-text-area {
  border: 4px solid blue;
}
.output-text-area {
  border: 4px solid red;
}
</style>
