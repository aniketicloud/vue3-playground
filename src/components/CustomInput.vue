<template>
  <div class="entry-item">
    <label for="signInName">Email Address</label>
    <div class="error itemLevel" aria-hidden="true" role="alert">
      <p></p>
    </div>
    <input
      type="text"
      id="signInName"
      name="Email Address"
      title="Please enter a valid Email Address"
      aria-label="Email Address"
    />
  </div>
</template>

<script>
export default {
  name: "CustomInput",
  data() {
    return {
      emailInput: null,
      emailLabel: null,
    };
  },
  mounted() {
    const emailInput = document.getElementById("signInName");
    const emailLabel = document.querySelector('label[for="signInName"]');

    // emailInput.placeholder = "Some Place";
    this.emailInput = emailInput;
    this.emailLabel = emailLabel;

    this.focusHandler();
  },
  methods: {
    focusHandler() {
      this.emailInput.addEventListener("focus", () => {
        this.emailLabel.classList.add("input-focused");
        setTimeout(() => {
          this.emailInput.placeholder = "Some Place";
        }, 200);
      });
      this.emailInput.addEventListener("blur", () => {
        this.emailLabel.classList.remove("input-focused");
        this.emailInput.placeholder = "";
      });
    },
  },
};
</script>

<style scoped>
.entry-item {
  position: relative;
}
label[for="signInName"] {
  background-color: white;
  color: red;
  position: absolute;
  top: 12px;
  left: 10px;
}
label[for="signInName"].input-focused {
  color: green;
  transition: 0.3s all ease-in;
  transform: translate(0, -100%) scale(1);
  left: 3px;
}

#signInName {
  padding: 12px 16px;
  font-size: 14px;
  border: 1px solid #c8cbd0;
}
</style>
