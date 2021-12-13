<template>
  <div>
    <ul class="users">
      <li class="user" v-for="user in users" :key="user.id">
        <h4 class="user__title">{{ user.name }}</h4>
        <a class="user__email" :href="`mailto:${user.email}`">
          {{ user.email }}</a
        >
        <a class="user__phone" :href="`tel:${user.phone.replace(/[^\d]/g, '')}`"
          >{{ user.phone }}
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: "",
    };
  },
  methods: {
    async signIn() {
      const res = await fetch("https://jsonplaceholder.typicode.com/users");

      const data = await res.json();

      this.users = data;
    },
  },
  mounted() {
    this.signIn();
  },
};
</script>