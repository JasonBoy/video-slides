<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue'
import party from 'party-js'

const props = defineProps({
  count: {
    default: 0,
  },
  nav: {}
})

const counter = ref(props.count)

const showPartyEffect = () => {
    party.confetti(document.getElementById('party-btn'), {
	    count: party.variation.range(20, 40),
    });
}

let btn

onMounted(() => {
  console.log('mouted')
  showPartyEffect()
  btn = document.getElementById('party-btn')
  btn && btn.addEventListener('click',  showPartyEffect)
  // console.log(props.nav)
})
onBeforeUnmount(() => {
  btn && btn.removeEventListener('click',  showPartyEffect)
})
</script>

<template>
  <div>
    <button
      id="party-btn"
      border="r gray-400 opacity-50"
      p="2"
      font="mono"
      hover:bg="gray-400 opacity-20"
      style="outline: none;"
    >
      <slot>
        🙌 Thank You 🙌  
      </slot>
    </button>
  </div>
</template>
