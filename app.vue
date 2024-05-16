<script setup>
const version = 2 + 1
const message = ref('Nuxt')

useHead({
  titleTemplate: '%s - Meta Tags Example'
})

const nav = [
  {
    label: 'Home',
    to: '/',
  },
  {
    label: 'External',
    to: '/external',
  },
  {
    label: 'Component',
    to: '/component',
  },
  {
    label: 'About',
    to: '/about',
  },
  { label: 'Custom', to: '/custom' },
  { label: 'Dynamic', to: '/dynamic' },
  { label: 'Other', to: '/other' },
]

const counter = useState('counter', () => Math.round(Math.random() * 1000))
const sameCounter = useState('counter')

function hello () {
  sayHello(message.value)
}
</script>

<template>
  <div>
    Hello Nuxt {{ version }}!
    <NuxtExample1 dir="features/auto-imports">
      <h1>Demo with auto imports</h1>
      <form class="flex gap-2" @submit.prevent="hello">
        <CustomInput v-model="message" />
        <UButton type="submit">Hello</UButton>
      </form>
    </NuxtExample1>

    <NuxtExample2 dir="features/state-management">
      <p>Counter: {{ counter }}</p>
      <div class="flex gap-2 my-4">
        <UButton @click="counter--">-</UButton>
        <UButton @click="counter++">+</UButton>
      </div>
      <p>Same Counter: {{ sameCounter }}</p>
    </NuxtExample2>

    <NuxtExample dir="features/data-fetching" :nav="nav" file="pages/index.vue">
      <NuxtLoadingIndicator />
      <NuxtLayout class="layouts">
        <NuxtPage />
      </NuxtLayout>
      <div class="flex items-center gap-4 mt-4">
        <UButton color="white" @click="setPageLayout('default')">
          layouts/default.vue
        </UButton>
        <UButton color="white" @click="setPageLayout('custom')">
          layouts/custom.vue
        </UButton>
        <UButton color="white" @click="setPageLayout('other')">
          layouts/other.vue
        </UButton>
        <UButton color="white" @click="setPageLayout(false)">
          Remove layout
        </UButton>
      </div>
      <!-- Show Nuxt progress indicator on page change

      <NuxtPage />-->
    </NuxtExample>

    <NuxtWelcome />
  </div>
</template>

<style scoped>
.hello {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 3rem;
  padding: 2rem;
}
</style>
