<template>
  <div>
    <NuxtLink to="/">index</NuxtLink>
    <NuxtLink to="/main">main</NuxtLink>
    <div>해더 {{ $route.name }}</div>
    <slot />
  </div>
</template>
