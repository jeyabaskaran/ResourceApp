<template>
  <div>
    <base-card>
      <li>
        <header>
          <h3>{{ title }}</h3>
          <base-button mode="flat" @click="deleteResources(id)">
            Delete
          </base-button>
        </header>
      </li>

      <p>{{ description }}</p> 
      <nav>
        <a :href="link"> View resource </a>
      </nav>
    </base-card>
  </div>
</template>

<script>
export default {
  inject: ["deleteResource"],
  props: ["id", "title", "description", "link"],
  methods: {
    deleteResources(id) {
      this.deleteResource(id);
    },
  },
};
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>