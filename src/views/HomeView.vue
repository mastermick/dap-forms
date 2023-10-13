<template>
  <div class="d-flex justify-content-center">
    <form class="d-flex flex-column form-floating m-4">
      <h1 class="form-floating m-4">Gegevens Onderneming</h1>
      <div class="form-floating m-4">
        <input type="text" class="form-control" id="naam" placeholder="Naam onderneming" v-model="formData.naam">
        <label for="naam">Naam onderneming</label>
      </div>
      <div class="form-floating m-4">
        <input type="text" class="form-control" id="kvk" placeholder="KvK-nummer" v-model="formData.kvk">
        <label for="kvk">KvK-nummer</label>
      </div>
      <div class="form-floating m-4">
        <input type="text" class="form-control" id="straat" placeholder="Straatnaam" v-model="formData.straat">
        <label for="straat">Straatnaam</label>
      </div>
      <div class="form-floating m-4">
        <input type="text" class="form-control" id="postcode" placeholder="Postcode" v-model="formData.postcode">
        <label for="postcode">Postcode</label>
      </div>
      <div class="form-floating m-4">
        <input type="text" class="form-control" id="nummer" placeholder="Nummer" v-model="formData.nummer">
        <label for="nummer">Nummer</label>
      </div>
      <div class="form-floating m-4">
        <input type="text" class="form-control" id="plaats" placeholder="Plaatsnaam" v-model="formData.plaats">
        <label for="plaats">Plaatsnaam</label>
      </div>
      <button @click.prevent="submitForm" class="btn btn-primary ">Submit</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const formData = ref({
  naam: '',
  kvk: '',
  straat: '',
  postcode: '',
  nummer: '',
  plaats: '',
});

const submitForm = async () => {


  const data = {
    naam: formData.value.naam,
    kvk: formData.value.kvk,
    straat: formData.value.straat,
    postcode: formData.value.postcode,
    nummer: formData.value.nummer,
    plaats: formData.value.plaats,
  };


  try {
    const response = await fetch(apiUrl, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(data),
    });

    if (response.ok) {

      console.log('Form data submitted successfully');
    } else {

      console.error('Server returned an error:', response.status, response.statusText);
    }
  } catch (error) {

    console.error('Error:', error);
  }
};
</script>

<style scoped>
form {
  margin: 0 auto;
  width: 50vw;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f4f4f4;
}
</style>