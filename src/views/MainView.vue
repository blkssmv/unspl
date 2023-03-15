<template>
  <div class="home">
    <!-- <AuthorizationForm /> -->
    <ImageList/>
  
  </div>
    

  
</template>

<script>
// @ is an alias to /src
import AuthorizationForm from '@/components/AuthorizationForm.vue';
import ImageList from "@/components/ImageList.vue"

export default {
  name: 'MainView',
  components: {
    AuthorizationForm,
    ImageList
  },
  data() {
    return {
    
    }
  },
  
}
</script>

