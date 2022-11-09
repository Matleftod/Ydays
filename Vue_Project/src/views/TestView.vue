<template>
  <div class="test">
    <h1>This is the test page</h1>
    <h2>This is how to use ref :</h2>
    <input type="text" ref="name" />
    <button @click="handleClick">Click me</button>
    <br />
    <button @click="toggleModal">Open modal</button>
    <button @click="toggleModal2">Open modal 2</button>
    <teleport to="#modals" v-if="showModal">
      <Modal theme="sale" @close="toggleModal">
        <template v-slot:links>
          <a href="#">sign up now</a>
          <a href="#">more info</a>
        </template>
        <h1>Ninja Giveaway !</h1>
        <p>Grab your ninja swag for half price ;)</p>
      </Modal>
    </teleport>
    <teleport to="#modals" v-if="showModal2">
      <Modal theme="" @close="toggleModal2">
        <template v-slot:links>
          <a href="#">sign up now</a>
          <a href="#">more info</a>
        </template>
        <h1>Ninja Giveaway 2 !</h1>
        <p>Grab your ninja swag 2 for half price ;)</p>
      </Modal>
    </teleport>
  </div>
</template>

<style></style>

<script lang="ts">
import Modal from "../components/Modal.vue";

export default {
  data() {
    return {
      showModal: false,
      showModal2: false,
    };
  },
  methods: {
    handleClick() {
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2;
    },
  },
  components: { Modal },
};
</script>
