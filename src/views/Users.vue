<template>
  <div class="main">

    <div class="columns">
      <div class="column has-text-left">
        <h1 class="title">Users Table</h1>
      </div>

      <div class="column has-text-right">
        <button class="button is-primary">
          <router-link :to="{name: 'addUser' }" >Add User</router-link>
        </button>
      </div>
    </div>

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

    <div class="columns">
      <div class="column">
        <nav class="pagination is-centered" role="navigation" aria-label="pagination">
          <a class="pagination-previous">Previous</a>
          <a class="pagination-next">Next page</a>
          <ul class="pagination-list">
            <li><a class="pagination-link" aria-label="Goto page 1">1</a></li>
            <li><span class="pagination-ellipsis">&hellip;</span></li>
            <li><a class="pagination-link" aria-label="Goto page 45">45</a></li>
            <li><a class="pagination-link is-current" aria-label="Page 46" aria-current="page">46</a></li>
            <li><a class="pagination-link" aria-label="Goto page 47">47</a></li>
            <li><span class="pagination-ellipsis">&hellip;</span></li>
            <li><a class="pagination-link" aria-label="Goto page 86">86</a></li>
          </ul>
        </nav>
      </div>
      <div class="column">
        <div class="dropdown is-active">
          <div class="dropdown-trigger">
            <button class="button" aria-haspopup="true" aria-controls="dropdown-menu">
              <span>Users per page</span>
              <span class="icon is-small">
                <i class="fas fa-angle-down" aria-hidden="true"></i>
              </span>
            </button>
          </div>
          <div id="dropdown-menu" class="dropdown-menu" role="menu">
            <div class="dropdown-content">
              <span class="dropdown-item">Dropdown item</span>
              <a class="dropdown-item">
                Other dropdown item
              </a>
              <a href="#" class="dropdown-item is-active">
                Active dropdown item
              </a>
              <a href="#" class="dropdown-item">
                Other dropdown item
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>


  </div>
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

<style lang="sass" scoped>
.main
  padding: 10px 20px
</style>
