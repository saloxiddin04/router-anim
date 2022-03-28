<template>
  <nav>
    <div class="link">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/contact">Contact</router-link>
    </div>
    <a href="#">Hello world</a>
  </nav>
  <transition name="router-anim">
    <router-view/>
  </transition>
</template>

<style>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";

  body {
    background: rgb(233,233,233);
    font-family: Arial, Helvetica, sans-serif;
  }
  html, body {
    height: calc(100% - 50px);
  }

  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  nav a {
    text-decoration: none;
    color: #000;
    font-weight: 700;
  }

  .router-link-active {
    color: green;
  }

  #app {
    background: #fff;
    width: 95%;
    margin: auto;
    padding: 30px;
    border-radius: 10px;
    height: calc(60% - 50px);
    position: relative;
  }

  .page {
    width: 100%;
  }

  .router-anim-enter-active {
    animation: coming 1s;
    animation-delay: 0.5s;
    opacity: 0;
  }

  .router-anim-leave-active {
    animation: going 1s;
  }

  @keyframes going {
    from {
      transform: translateX(0);
    }
    to {
      transform: translateX(-50px);
      opacity: 0;
    }
  }

  @keyframes coming {
    from {
      transform: translateX(-50px);
      opacity: 0;
    }
    to {
      transform: translateX(0);
      opacity: 1;
    }
  }
</style>
