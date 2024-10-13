<template>
  <h1>{{ title }}</h1>
  <p>Wellcome...</p>
  <Teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Ninja Giveaway!</h1>
      <p>Grab your ninja swag for half price!</p>
    </Modal>
  </Teleport>

  <Teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Sign up to the newsletter</h1>
      <p>For updates and promo codes</p>
    </Modal>
  </Teleport>

  <button @click.alt="toggleModal">open modal (alt)</button>
  <button @click="toggleModalTwo">open modal</button>
  <!-- <input type="text" ref="name" />
  <button @click="handleClick">click me</button> -->
</template>

<script>
// challenge
//   - create an extra button to open a different modal
//   - use the same component but pass in a different template (slot)
//   - use a different method (e.g. toggleModalTwo) and data (e.g. showModalTwo)

import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My First Vue App",
      // header: "Sign up for the Giveaway!",
      // text: "Grab your ninja swag for half price!",
      showModal: false,
      showModalTwo: false,
    };
  },

  methods: {
    // handleClick() {
    //   console.log(this.$refs.name);
    //   this.$refs.name.classList.add("active");
    //   this.$refs.name.focus();
    // },

    toggleModal() {
      this.showModal = !this.showModal;
    },

    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app,
.modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
