<template>
  <div>
    <input
      type="text"
      class="form-control bg-dark text-white"
      placeholder="New Task.."
      v-model="inputValue"
      @keydown.enter="newItem"
    />
  </div>
</template>

<script>
export default {
  props: ["setText"],
  data() {
    return {
      inputValue: "",
    };
  },
  methods: {
    newItem() {
      let randomNumber = Math.floor(Math.random() * 100);

      if (!this.inputValue.length == 0) {
        this.$emit("exportItem", {
          id: randomNumber,
          text: this.inputValue,
          isCompleted: false,
        });
      }

      this.inputValue = "";
    },
  },
  watch: {
    setText() {
      this.inputValue = this.setText;
    },
  },
};
</script>

<style scoped>
.form-control {
  height: 50px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.234);
  border-top: 3px solid rgba(0, 0, 0, 0.234);
  border-left: 2px solid rgba(0, 0, 0, 0.234);
  border-right: none;
}

.form-control:focus {
  border-color: #9ecaed;
  box-shadow: 0 0 10px #9ecaed;
}
</style>
