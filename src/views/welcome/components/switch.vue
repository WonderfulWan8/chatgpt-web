<script setup lang="ts">
const emits = defineEmits<{

  (e: 'changeMsg', value: string): void

}>()

const handleChangeMsg = (type: any) => {
  emits('changeMsg', type)
}
const change = (type: any) => {
  const switchC1 = document.querySelector('#switch-c1') as any
  const switchC2 = document.querySelector('#switch-c2') as any
  const switchCircle = document.querySelectorAll('.switch__circle') as any
  const switchCtn = document.querySelector('#switch-cnt') as any
  switchCtn.classList.add('is-gx')
  setTimeout(() => {
    switchCtn.classList.remove('is-gx')
  }, 1500)
  switchCtn.classList.toggle('is-txr')
  switchCircle[0].classList.toggle('is-txr')
  switchCircle[1].classList.toggle('is-txr')
  switchC1.classList.toggle('is-hidden')
  switchC2.classList.toggle('is-hidden')

  handleChangeMsg(type)
}
</script>

<template>
  <div id="switch-cnt" class="switch">
    <div class="switch__circle" />
    <div class="switch__circle switch__circle--t" />
    <div id="switch-c1" class="switch__container">
      <h2 class="switch__title title">
        Welcome Back !
      </h2>
      <p class="switch__description description">
        To keep connected with us please login with your personal info
      </p>
      <button class="switch__button button switch-btn" @click="change(1)">
        SIGN IN
      </button>
    </div>
    <div id="switch-c2" class="switch__container is-hidden">
      <h2 class="switch__title title">
        Hello Friend !
      </h2>
      <p class="switch__description description">
        Enter your personal details and start journey with us
      </p>
      <button class="switch__button button switch-btn" @click="change(2)">
        SIGN UP
      </button>
    </div>
  </div>
</template>

<style scoped>
.switch {
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 400px;
    padding: 50px;
    z-index: 200;
    transition: 1.25s;
    background-color: #ecf0f3;
    overflow: hidden;
    box-shadow: 4px 4px 10px #d1d9e6, -4px -4px 10px #f9f9f9;
}.switch__circle {
    position: absolute;
    width: 500px;
    height: 500px;
    border-radius: 50%;
    background-color: #ecf0f3;
    box-shadow: inset 8px 8px 12px #d1d9e6, inset -8px -8px 12px #f9f9f9;
    bottom: -60%;
    left: -60%;
    transition: 1.25s;
}
.switch__circle--t {
    top: -30%;
    left: 60%;
    width: 300px;
    height: 300px;
}
.switch__container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    position: absolute;
    width: 400px;
    padding: 50px 55px;
    transition: 1.25s;
}
.title {
    font-size: 34px;
    font-weight: 700;
    line-height: 3;
    color: #181818;
}
.description {
    font-size: 14px;
    letter-spacing: 0.25px;
    text-align: center;
    line-height: 1.6;
}
.switch__button {
    cursor: pointer;
}
.button {
    width: 180px;
    height: 50px;
    border-radius: 25px;
    margin-top: 50px;
    font-weight: 700;
    font-size: 14px;
    letter-spacing: 1.15px;
    background-color: #4B70E2;
    color: #f9f9f9;
    box-shadow: 8px 8px 16px #d1d9e6, -8px -8px 16px #f9f9f9;
    border: none;
    outline: none;
}
.is-hidden {
    visibility: hidden;
    opacity: 0;
    position: absolute;
    transition: 1.25s;
}
</style>
