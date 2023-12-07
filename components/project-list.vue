<template>
  <p class="mb-10">Taking a look at my Github Projects!</p>

  <section v-if="pending">Loading...</section>
  <section v-else-if="error">Something went wrong... Try again!</section>
  <section v-else>
    <ul class="grid grid-cols-1 gap-4">
      <li
        v-for="repository in data.entries"
        :key="repository.API"
        class="border border-gray-200 rounded-sm p-4 hover:bg-gray-100 font-mono"
      >
        <a :href="repository.Link" target="_blanck">
          <div class="flex items-center justify-between text-sm">
            <div class="font-semibold">{{ repository.API }}</div>
            <div>{{ repository.Category }} *</div>
          </div>
          <p>
            {{ repository.Description }}
          </p>
        </a>
      </li>
    </ul>
  </section>
</template>

<script setup>
const { error, pending, data } = await useFetch(
  "https://api.publicapis.org/entries"
);
</script>
