<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <slot></slot>
      <div class="action">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  props: ["theme"],
  methods: {
    closeModal() {
      this.$emit("close");
    }
  },
};
</script>

<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
  color: black;
  text-align: center;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}

.modal.sale {
  background: crimson;
  color: white;
}

.modal.sale h1 {
  color: white;
}

.modal.sale .action {
  color: white;
}

.modal.sale .action a {
  color: white;
}

.modal .action {
  text-align: center;
  margin: 30px 0 10px 0;
}

.modal .action a {
  color: #333;
  padding: 8px;
  border: 1px solid #eee !important;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}
</style>
