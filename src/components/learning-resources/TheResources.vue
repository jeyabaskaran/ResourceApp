<template>
  <div>
    <base-card>
      <base-button @click="setSelectedTab('stored-resources')" :mode="storedResourceTab">
        Stored Resources
      </base-button>
      <base-button @click="setSelectedTab('add-resources')" :mode="addResourceTab">
        Add Resource
      </base-button>
    </base-card>
    <keep-alive>
    <component :is="selectedTab"></component>
    </keep-alive>
  </div>
</template>

<script>
import AddResources from "./AddResources";
import StoredResources from "./StoredResources.vue";

export default {
  components: {
    AddResources,
    StoredResources,
  },
  data() {
    return {
      selectedTab: "stored-resources",
      storedResources: [
        {
          id: 1,
          title: "Vue Js course",
          description: "Vue js is easy to learn",
          link: "https://cli.vuejs.org/guide/creating-a-project.html#vue-create",
        },
        {
          id: 2,
          title: "Google",
          description: "The more comfortable search engine",
          link: "https://www.google.com",
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResources:this.addResources,
      deleteResource:this.deleteResource
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResources(userInput){
        this.storedResources.unshift(userInput);
        this.selectedTab="stored-resources";
    },
    deleteResource(id){
        console.log(id,'id');
        const findIndex= this.storedResources.findIndex(resource=>resource.id==id);
        console.log(findIndex,'index');
        this.storedResources.splice(findIndex,1);
    }
  },
  computed:{
    storedResourceTab(){
        return this.selectedTab==='stored-resources'? null:'flat';
    },
    addResourceTab(){
   return this.selectedTab==='add-resources'? null:'flat';
    }
  }
};
</script>