<template>
  <label>
    Predefined instance:<br />
    <select v-model="_value">
      <option disabled :value="null">Custom</option>
      <option
        v-for="instance in instances"
        :value="instance.value"
        :key="instance.text"
      >
        {{ instance.text }}
      </option>
    </select>
  </label>
</template>

<script>
export default {
  props: {
    value: Object,
  },
  computed: {
    instances() {
      return [
        {
          text: "Regular",
          value: { wght: 400, opsz: 18, GRAD: 0, wdth: 100, ROND: 0 },
        },
        {
          text: "Medium",
          value: { wght: 500, opsz: 18, GRAD: 0, wdth: 100, ROND: 0 },
        },
        {
          text: "Bold",
          value: { wght: 700, opsz: 18, GRAD: 0, wdth: 100, ROND: 0 },
        },
        {
          text: "Text Regular",
          value: { wght: 400, opsz: 17, GRAD: 0, wdth: 100, ROND: 0 },
        },
        {
          text: "Text Medium",
          value: { wght: 500, opsz: 17, GRAD: 0, wdth: 100, ROND: 0 },
        },
        {
          text: "Text Bold",
          value: { wght: 700, opsz: 17, GRAD: 0, wdth: 100, ROND: 0 },
        },
      ];
    },
    _value: {
      get() {
        for (const instance of this.instances) {
          if (
            Object.entries(instance.value).every(
              ([tag, userValue]) => this.value[tag] === userValue
            )
          ) {
            return instance.value;
          }
        }
        return null;
      },
      set(value) {
        this.$emit("input", { ...value });
      },
    },
  },
};
</script>

<style>
</style>
