<template>
    <ul>
    <learning-resource-vue v-for="resource in resources" 
    :key="resource.id"
    :id="resource.id"
    :title="resource.title"
    :description="resource.description"
    :link="resource.link"
    >
    </learning-resource-vue>
</ul> 
</template>

<script>
import LearningResourceVue from './LearningResource.vue';

export default{
    components:{
        LearningResourceVue
    },
    inject:['resources']
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
