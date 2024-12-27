<template>
  <nav class="navbar">
    <img :src="BlueLogo" alt="Blue Logo" class="logo" />
    <div class="nav-links">
      <LinkBtn
        :path="'/'"
        :buttonText="'Home'">
      </LinkBtn>
      <LinkBtn
        :path="'/second-page'"
        :buttonText="'Second Page'">
      </LinkBtn>
      <!-- Add more navigation links here -->
    </div>
  </nav>
</template>

<script setup>
import LinkBtn from '../components/RouterBtn.vue';
import BlueLogo from '../../images/logos/blue-logo.png';
// import YellowLogo from '../../images/logos/yellow-square-logo.png';
</script>

<style scoped>
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem;
  height: 110px;
  background-color: #00a6ce;
  border-bottom: 1px solid #ddd;
}

.logo {
  height: 90px;
  object-fit: contain;
}

.nav-links {
  display: flex;
  gap: 1rem;
}
</style>
