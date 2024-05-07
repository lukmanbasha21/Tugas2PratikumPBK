<template>
  <div>
    <h2>Edit Profile</h2>
    <div class="input-container">
      <label for="username">Username:</label>
      <input
        type="text"
        id="username"
        v-model="username"
        :class="{ 'input-error': usernameError }"
        :style="{ borderColor: usernameError ? '#ff4d4d' : '#ccc' }"
        @input="checkUsernameValidity"
        placeholder="Enter your username"
      />
      <span v-if="usernameError" class="error-message">{{
        usernameErrorMessage
      }}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      usernameError: false,
      usernameErrorMessage: "",
    };
  },
  methods: {
    checkUsernameValidity() {
      // Contoh validasi sederhana
      if (this.username.length < 6) {
        this.usernameError = true;
        this.usernameErrorMessage =
          "Username should have at least 6 characters.";
      } else {
        this.usernameError = false;
        this.usernameErrorMessage = "";
      }
    },
  },
};
</script>

<style>
body {
  color: pink;
}
.input-container {
  margin-bottom: 20px;
}

label {
  font-size: 1rem;
  color: #333;
  display: block;
  margin-bottom: 5px;
}

input {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  transition: border-color 0.3s ease;
  font-size: 1rem;
}

input:focus {
  outline: none;
  border-color: #66afe9;
}

.input-error {
  border-color: #ff4d4d !important;
}

.error-message {
  color: #ff4d4d;
  font-size: 0.8rem;
}
</style>
