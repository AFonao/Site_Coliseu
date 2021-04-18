<template>
  <div id="material-kit">
    <div :class="{ 'nav-open': NavbarStore.showNavbar }">
      <router-view name="header" />
      <div>
        <div class="" id="pre-loader" >
            <div class="loader"></div>
        </div>
        <router-view />
      </div>
      <router-view name="footer" />
    </div>
  </div>
</template>
