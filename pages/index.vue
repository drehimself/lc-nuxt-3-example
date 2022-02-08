<template>
<div>
  <div>This is the main page</div>
  <Counter />
  <div>
    x: {{ x }}
    y: {{ y }}
  </div>
  <div>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.name }}
      </li>
    </ul>
  </div>
  <div>
    <ul>
      <li v-for="user in users2" :key="user.id">
        {{ user.name }}
      </li>
    </ul>
  </div>

  <div>
    <ul>
      <li v-for="user in users3" :key="user.id">
        {{ user.name }}
      </li>
    </ul>
  </div>

  <div>
    {{ user.name }}
  </div>

  <div>
    <h2>Weather</h2>
    <div>Description: {{ weather.weather[0].description }}</div>
    <div>Temperature: {{ weather.main.temp }} C</div>
  </div>
</div>
</template>

<script setup>
  const {x, y} = useMouse()
  const users = ref([])

  onMounted(() => {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(response => response.json())
      .then(data => users.value = data)
  })

  const { data: users2 } = await useAsyncData('users2', () => $fetch('https://jsonplaceholder.typicode.com/users'))

  const { data : users3 } = await useFetch('https://jsonplaceholder.typicode.com/users')

  const { data : user } = await useFetch('https://jsonplaceholder.typicode.com/users/1' ,{ pick: ['id', 'name', 'email'] })

  const { data : weather } = await useFetch('/api/weather')
</script>
