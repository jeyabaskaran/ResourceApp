<template>
  <div>
    <base-card>
      <form @submit.prevent="submitedData">
        <div class="form-control">
          <label for="title">Title</label>
          <input type="text" name="title" id="title" ref="title" />
        </div>
        <div class="form-control">
          <label for="description">Description</label>
          <textarea
            name="description"
            id="description"
            rows="10"
            ref="description"
          />
        </div>
        <div class="form-control">
          <label for="link">Link</label>
          <input type="url" name="link" id="link" ref="link" />
        </div>
        <div>
          <base-button type="submit">Add Resources</base-button>
        </div>
      </form>
    </base-card>
    <base-dialog v-if="required" title="Invalid Input" @close="closeDialog">
      <template #default>
        <p>Please enter the all input fields.</p>
        <p>Without filling those information may affect your data.</p>
      </template>
    
    </base-dialog>
  </div>
</template>


<script>
import BaseButton from '../UI/BaseButton.vue';
export default {
  components: { BaseButton },
  data() {
    return { required: false };
  },
  inject: ["addResources"],
  methods: {
    submitedData() {
      const userInputValue = {
        id: Math.random(),
        title: this.$refs.title.value,
        description: this.$refs.description.value,
        link: this.$refs.link.value,
      };
      if (
        !userInputValue.link ||
        !userInputValue.title ||
        !userInputValue.description
      ) {
        this.required = true;
      } else {
        this.addResources(userInputValue);
      }
    },
    closeDialog() {
      this.required = false;
    },
  },
};
</script>


<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>