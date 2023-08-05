<template>
    <header>
        <nav class="container">
            <div class="logo">
                <img src="../assets/logo.png" alt="logo" />

            </div>
            <ul class="nav-routes">
                <li >
                    <RouterLink to="/">To-Do Page</RouterLink>
                </li>
                <li>
                    <RouterLink to="/about">About</RouterLink>
                </li>
            </ul>
        </nav>
    </header>
</template>

<script setup>
import { RouterLink } from 'vue-router';
</script>

<style lang="scss" scoped>
img {
    width: 150px;
    cursor: pointer;
}
header {
  background-color: #F3CBAC;
  nav {
    display: flex;
    align-items: center;
    padding: 25px 16px;

    .branding {
      display: flex;
      align-items: center;
      gap: 8px;
      img {
        max-width: 50px;
      }

      h1 {
        font-size: 24px;
      }
    }

    .nav-routes {
      display: flex;
      flex: 1;
      justify-content: flex-end;
      gap: 12px;
      list-style: none;

      a {
        text-decoration: none;
        color:  black;
        &:hover{
          font-weight: bold;
          color: rgb(243, 243, 243)
        }
      }

     
    }
  }
}

</style>