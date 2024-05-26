<template>
  <div className="user">
    <button @click="deleteUser(index)" class="userCreateBtn">X</button>
    <div class="userInfo">
      <p>Name: {{ user.name }}</p>
      <p>Password: {{ user.password }}</p>
      <p>Email: {{ user.email }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
      requied: true,
    },
    index: {
      type: Number,
      requied: true,
    },
    deleteUser: {
      type: Function,
      requied: true,
    },
  },
};
</script>

<style scoped>
button {
  border: 1;
  border-radius: 5px;
  padding: 3px 5px;
  /* background: #d66c75;
  color: #7f1629; */
  font-weight: bold;
  cursor: pointer;
  transition: transform 500ms ease;
  float: right;
}

button:hover {
  transform: translateY(-5px);
}
</style>
