<template>
  <aside :class="[is_expanded ? 'is-expanded' : '']">
    <div class="logo">
      <img src="../assets/logo.png" alt="Vue Logo" />
    </div>
    <div class="menu-toggle-wrap">
      <button class="menu-toggle" @click="ToggleMenu">
        <span class="material-icons material-icons-round"> double_arrow </span>
      </button>
    </div>

    <h3>Menu</h3>
    <div class="menu">
      <router-link class="button" to="/">
        <span class="material-icons material-icons-round"> home </span>
        <span class="text">Home</span>
      </router-link>
      <router-link class="button" to="/about">
        <span class="material-icons material-icons-round"> home </span>
        <span class="text">About</span>
      </router-link>
    </div>
  </aside>
</template>

<script setup>
import { ref } from "vue";
const is_expanded = ref(false);

const ToggleMenu = () => {
  is_expanded.value = !is_expanded.value;
};
</script>

<style lang="scss" scoped>
aside {
  display: flex;
  flex-direction: column;
  width: calc(2rem + 2rem);
  min-height: 100vh;
  overflow: hidden;
  padding: 1rem;

  background-color: var(--dark);
  color: var(--light);

  transition: 0.2s ease-out;

  .logo {
    margin-bottom: 1rem;
    img {
      width: 2rem;
    }
  }

  .menu-toggle-wrap {
    display: flex;
    justify-content: flex-end;
    margin-bottom: 1rem;
    position: relative;

    top: 0;
    transition: 0.2s ease-out;

    .menu-toggle {
      transition: 0.2s ease-out;
      .material-icons-round {
        font-size: 2rem;
        color: white;
      }
    }

    .menu-toggle:hover {
      .material-icons-round {
        transform: scale(1.2);
        color: green;
      }
    }
  }

  @media (max-width: 768px) {
    position: fixed;
    z-index: 99;
  }
}

h3,
.button .text {
  opacity: 0;
  transition: 0.3s ease-out;
}

.menu {
  margin: 0 -1rem;
  .button {
    display: flex;
    align-items: center;
    text-decoration: none;

    padding: 0.5rem 1rem;
    transition: 0.2 ease-out;
  }
}

.is-expanded {
  width: var(--sidebar-width);

  .menu-toggle-wrap {
    top: -3.5rem;
    .menu-toggle {
      transform: rotate(180deg);
    }
  }

  h3,
  .button .text {
    opacity: 1;
  }
}
</style>