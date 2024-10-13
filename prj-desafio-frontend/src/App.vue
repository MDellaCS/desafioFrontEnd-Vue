<template>
  <div class="container">

    <div class="challenge-container">

      <div id="form-container">

        <userForm @input-changed="handleFormChange" />

      </div>

      <div id="card-container">

        <userCard :userImage="submittedData.image" :userName="submittedData.name"
          :userSurname="submittedData.surname" />

      </div>

    </div>

  </div>
</template>

<script>
import userForm from './components/userForm.vue';
import userCard from './components/userCard.vue';

export default {
  components: {
    userForm,
    userCard,
  },
  data() {
    return {
      submittedData: {
        image: null,
        name: '',
        surname: '',
      },
    };
  },
  methods: {
    handleFormChange(formData) {
      this.submittedData = formData;
    },
  },
};
</script>

<style>
.container {
  display: flex;
  align-items: center;
  justify-content: center;
}

.challenge-container {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  margin: 3rem;
  gap: 3rem;
}

#form-container {
  border: solid 3px #cccccc;
  padding: 1.5rem;
}

#card-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

@media(max-width: 720px) {
  .challenge-container {
    align-items: center;
  }

  #form-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    padding: 1.5rem 0;
  }
}
</style>
