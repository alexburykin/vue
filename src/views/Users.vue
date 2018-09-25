<template>
  <table class="table is-bordered is-striped is-fullwidth is-hoverable">
    <thead>
      <tr>
        <th>Avatar</th>
        <th>First name</th>
        <th>Last name</th>
        <th>Company</th>
        <th>Age</th>
        <th>Email</th>
        <th>Phone</th>
        <th>Copy</th>
        <th>Edit</th>
        <th>Delete</th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="user of users"
        :key="user.id">
        <td>
          <div class="image is-48x48">
            <img
              :src="user.picture"
              class="is-rounded"
              alt="">
          </div>
        </td>
        <td>{{ user.firstName | uppercase }}</td>
        <td>{{ user.lastName | uppercase }}</td>
        <td>{{ user.company }}</td>
        <td>{{ user.age }}</td>
        <td>{{ user.email }}</td>
        <td>{{ user.phone }}</td>
        <td>
          <button class="button is-info" disabled>Copy</button>
        </td>
        <td>
          <button class="button is-primary">
            <router-link :to="{name: 'user', params: {id: user.id}}" >Edit</router-link>
          </button>
        </td>
        <td>
          <button class="button is-danger">Danger</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import axios from 'axios'
// import copy from 'v-copy'

export default {
  name: 'UsersList',
  components: {
    // 'users-list': usersListComponent
  },
  directives: {
    // copy
  },
  filters: {
    uppercase: function(value) {
      if (!value) return ''
      value = value.toString()
      return value.toUpperCase()
    }
  },
  data: () => {
    return {
      users: []
    }
  },
  mounted() {
    this.getUsers()
  },
  methods: {
    getUsers() {
      axios.get('http://localhost:3000/users').then(res => {
        this.users = res.data
      })
    }
  }
}
</script>
