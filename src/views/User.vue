<template>
  <div class="container">
    <form @:submit.prevent="saveChanges">
      <div class="columns">

        <div class="column">
          <div class="field">
            <label class="label">First Name</label>
            <div class="control">
              <input v-model="user.firstName" class="input" type="text" placeholder="Text input">
            </div>
          </div>
          <div class="field">
            <label class="label">Last Name</label>
            <div class="control">
              <input v-model="user.lastName" class="input" type="text" placeholder="Text input">
            </div>
          </div>
        </div>

        <div class="column">
          <div class="field">
            <label class="label">Label</label>
            <div class="control">
              <input v-model="user.company" class="input" type="text" placeholder="Text input">
            </div>
          </div>
          <div class="field">
            <label class="label">Label</label>
            <div class="control">
              <input v-model="user.age" class="input" type="text" placeholder="Text input">
            </div>
          </div>
        </div>

      </div>

      <div class="text-right">
        <button type="submit" class="button is-success">Success</button>
      </div>
    </form>

  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'User',
  props: {
    id: {
      type: String || Number,
      required: true
    }
  },
  data: () => {
    return {
      user: {}
    }
  },
  mounted() {
    axios.get(`http://localhost:3000/users/${this.id}`).then(res => {
      this.user = res.data
    })
  },
  methods: {
    saveChanges() {
      console.log(this.user)
    }
  }
}
</script>

<style scoped>
.container {
  text-align: left;
}
</style>
