<template>
  <div>
    <nav class="navbar">
      <img :src="BlueLogo" alt="Blue Logo" class="logo" />
      <div class="nav-links">
        <span
          class="material-symbols-outlined search-icon"
          @click="openSideView('search')"
        >
          search
        </span>
        <span
          class="material-symbols-outlined profile-icon"
          @click="openSideView('profile')"
        >
          account_circle
        </span>
        <span
          class="material-symbols-outlined cart-icon"
          @click="openSideView('cart')"
        >
          shopping_cart
        </span>
      </div>
    </nav>
    <div class="content">
      <div class="main-content">
        <router-view />
      </div>

      <transition name="slide">
        <SearchSideView
          v-if="activeSideView === 'search'"
          @close="closeSideView"
        />
      </transition>
      <transition name="slide">
        <ProfileSideView
          v-if="activeSideView === 'profile'"
          @close="closeSideView"
        />
      </transition>
      <transition name="slide">
        <CartSideView
          v-if="activeSideView === 'cart'"
          @close="closeSideView"
        />
      </transition>
    </div>
  </div>
</template>


<script setup>
import { ref } from 'vue';
import BlueLogo from '../../images/logos/blue-logo.png';
import SearchSideView from './SearchSideView.vue';
import ProfileSideView from './ProfileSideView.vue';
import CartSideView from './CartSideView.vue';

const activeSideView = ref(null);

const openSideView = (view) => {
  activeSideView.value = view;
};

const closeSideView = () => {
  activeSideView.value = null;
};

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

.material-symbols-outlined {
  font-size: 24px;
  cursor: pointer;
}

.content {
  display: flex;
  height: calc(100vh - 110px);
}

.main-content {
  flex: 1;
  padding: 1rem;
}

</style>
