<template>
  <div class="home">
  <h1 v-if="showTitle">🏡 Home</h1>
    <transition name="toast">
      <Toast v-if="showToast" />
    </transition>
    <Todos @badValue="triggerToast" />
    <br>
    <h5 className="App-Developers-name">
                Developed by : Anu Gupta
              </h5>
  </div>
</template>

<script>
import { ref } from 'vue'
import Toast from '../components/Toast'
import Todos from '../components/Todos'

export default {
  components: { Toast, Todos },
  setup() {
    const showTitle = ref(true)
    const showToast = ref(false)

    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => showToast.value = false, 3000)
    }

    return { showToast, triggerToast,showTitle }
  }
}
</script>

<style>
  .App-Developers-name {
  text-align: center !important;
}
 
  .toast-enter-active {
    animation: wobble 0.5s ease;
  }
  
  .toast-leave-to {
    opacity: 0;
    transform: translateY(-60px);
  }
  .toast-leave-active {
    transition: all 0.3s ease;
  }

  @keyframes wobble {
    0% { transform: translateY(-100px); opacity: 0 }
    50% { transform: translateY(0px); opacity: 1 }
    60% { transform: translateX(8px); opacity: 1 }
    70% { transform: translateX(-8px); opacity: 1 }
    80% { transform: translateX(4px); opacity: 1 }
    90% { transform: translateX(-4px); opacity: 1 }
    100% { transform: translateX(0px); opacity: 1 }
  }
</style>
