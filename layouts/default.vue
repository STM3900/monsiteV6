<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>
::-webkit-scrollbar {
  width: 8px;
  background: #ffffff;
  border-left: 1px solid #ffffff;
  border-radius: 10px;
}

::-webkit-scrollbar-track {
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  background: rgb(200, 200, 200);
  border-left: 0px solid #ffffff;
  border-radius: 3px;
}

html {
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

body {
  margin: 0;
  font-family: "Quicksand", sans-serif;
}

.part {
  padding-left: 20%;
  padding-right: 20%;
}

.border-part {
  padding: 40px !important;

  box-shadow: 15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;
  border-radius: 15px;
}

/*transition aled*/
.page-enter-active,
.page-leave-active {
  transition: opacity 0.5s;
}
.page-enter,
.page-leave-to {
  opacity: 0;
}

.layout-enter-active,
.layout-leave-active {
  transition: opacity 0.5s;
}
.layout-enter,
.layout-leave-to {
  opacity: 0;
}

.slide-bottom-enter-active,
.slide-bottom-leave-active {
  transition: opacity 0.4s ease-in-out, transform 0.4s ease-in-out;
}
.slide-bottom-enter,
.slide-bottom-leave-to {
  opacity: 0;
  transform: translateY(-25px);
}
.bounce-enter-active {
  transform-origin: top;
  animation: bounce-in 0.8s;
}
.bounce-leave-active {
  transform-origin: top;
  animation: bounce-out 0.5s;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}
@keyframes bounce-out {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(0);
  }
}

/* responsive */
@media screen and (max-width: 1570px) {
  .part {
    padding-left: 15%;
    padding-right: 15%;
  }
}

@media screen and (max-width: 1360px) {
  .part {
    padding-left: 10%;
    padding-right: 10%;
  }
}

@media screen and (max-width: 918px) {
  .part {
    padding-left: 5%;
    padding-right: 5%;
  }
}
</style>
