<template >
  <AppHeader @open-login-modal="isLoginOpen = true"/>
  <div class="flex m-auto">
    <router-view></router-view>
  </div>
  <LoginModal v-if="isLoginOpen" @close-login="isLoginOpen = false"/>
</template>

<script>
import AppHeader from '@/components/AppHeader.vue';
import LoginModal from '@/components/LoginModal.vue';

export default {
  data() {
    return {
      isLoginOpen: false
    }
  },
  components: {
    AppHeader,
    LoginModal,
  }
}
</script>
