<script>
import User from "./components/User.vue";
export default {
  components: { User },
  data() {
    return {
      users: [],
      error: "",
      userName: "",
      userPass: "",
      userEmail: "",
    };
  },
  /* Методы */
  methods: {
    insertData(val) {
      this.userName = val;
    },
    sendData() {
      if (this.userName == "") {
        this.error = "Имя не введено!";
        // alert(this.error);
        return;
      } else if (this.userPass == "") {
        this.error = "Пароль не введен!";
        // alert(this.error);
        return;
      } else if (this.userEmail == "") {
        this.error = "Почта не введена!";
        // alert(this.error);
        return;
      }

      this.error = "";
      this.users.push({
        name: this.userName,
        password: this.userPass,
        email: this.userEmail,
      });
    },
    deleteUser(index) {
      this.users.splice(index, 1);
    },
  },
};
</script>

<template>
  <form action="#" className="forms">
    <!-- Первый вариант -->
    <input
      type="text"
      @input="insertData($event.target.value)"
      placeholder="Имя"
    />
    <!-- Второй вариант -->
    <input type="password" v-model="userPass" placeholder="Пароль" />
    <input type="email" v-model="userEmail" placeholder="Почта" />
  </form>

  <div>
    <p>{{ userName }}</p>
    <p>{{ userPass }}</p>
    <p>{{ userEmail }}</p>
    <p>{{ error }}</p>
  </div>

  <form action="#">
    <button @click="sendData()">Отправить</button>
  </form>

  <!-- <div>
    <p>{{ users }}</p>
  </div> -->
  <!-- Цикл перебор -->
  <div v-if="users.length == 0" className="user">Нет пользователей</div>
  <div v-if="users.length != 0" className="user">
    Количество пользователей: {{ users.length }}
  </div>

  <div v-for="(el, index) in users" :key="index">
    <p>{{ el }}</p>
  </div>

  <User
    v-for="(el, index) in users"
    :key="index"
    :user="el"
    :index="index"
    :deleteUser="deleteUser"
  />
</template>

<style scoped>
/* .forms {
  display: flex;
  flex-direction: column;
  background: #000;
} */

.forms input {
  display: block;
  height: 30px;
  width: 25%;
  margin-bottom: 10px;
  border: 1px solid silver;
  border-radius: 5px;
  padding-left: 5px;
  font-size: 14px;
  font-weight: 400;
  /* outline: none; */
}

.forms input:last-child {
  margin-bottom: 0;
}

button {
  background-color: #6cd670;
  width: 100px;
  height: 30px;
  border: none;
  border-radius: 10px;
  font-size: 16px;
  opacity: 0.9;
  font-weight: 500;
  cursor: pointer;
  transition: transform 0.3s ease;
}

button:hover {
  transform: translateY(-5px);
  opacity: 0.8;
  border: 1px solid black;
}

.user {
  width: 500px;
  margin-top: 20px;
  border: 1px solid silver;
  background: #e3e3e3;
  color: #222;
  padding: 20px;
  border-radius: 5px;
}
</style>
