<template>
  <div class="px-5 flex flex-col gap-3">
    <Button class="w-full sm:max-w-48">
      <LucidePlus />
      Add new article
    </Button>
    <main>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-x-4 p-2">
        <ArticleCard :key="i" v-for="i in Array.from({length: 5}).keys()" title="5 tips to create a modern app UI Design" summary="lorem ipsum awodkaowkdakwKDkw daowdk apowkda kwdoak dwakdaw dwoa" />
      </div>
    </main>
  </div>
</template>

<script lang="ts" setup>

</script>

<style>

</style>