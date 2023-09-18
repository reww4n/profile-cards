<script setup>
import axios from 'axios'
import { ref, onMounted} from 'vue'
import Card from './components/Card.vue'

const apiUrl = "https://gorest.co.in/public/v2/users"
const users = ref([])
const usersImg = ref([
  "https://mott.pe/noticias/wp-content/uploads/2016/07/Estas-fotograf%C3%ADas-capturaron-la-belleza-de-los-paisajes-de-Finlandia-e-Islandia-Mikko-Lagerstedt-1.1.jpg",
  "https://www.phototourbarcelona.com/wp-content/uploads/2020/05/3-1.jpg",
  "https://cdn-7.nikon-cdn.com/Images/Learn-Explore/Photography-Techniques/2016/Tony-Sweet-Landscapes/Media/Tony-Sweet-landscape-boat-01.jpg",
  "https://ecologiahoy.net/wp-content/uploads/2019/07/1-1-718x477.jpg"
])

const extractData = () => {
  axios.get(apiUrl)
  .then(response => {
    users.value = response.data
    console.log(this.users)
  })
  .catch(error => {
    console.log('Ni modo: ', error)
  });
}

onMounted(() => {
  extractData()
})
</script>

<template>
  <div class="w-full pt-5 pb-5 grid grid-cols-3 grid-flow-row gap-5 justify-items-center responsive-cards">
    <Card
      v-for="(user, index) in users"
      :key="user.id"
      :name="user.name"
      :gender="user.gender"
      :email="user.email"
      :id="user.id"
      :status="user.status"
      :image="usersImg[index % usersImg.length]"
    >
    </Card>
  </div>
</template>

<style>
  @media (max-width: 1280px) {
    .responsive-cards {
      grid-template-columns: repeat(2, minmax(0, 1fr));
    }
  }

  @media (max-width: 800px) {
    .responsive-cards {
      grid-template-columns: repeat(1, minmax(0, 1fr));
    }
  }
</style>