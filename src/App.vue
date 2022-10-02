<script setup lang="ts">
import TheHeader from "@/components/TheHeader.vue";
import EntryEditor from "@/components/EntryEditor.vue";
import EntryCard from "@/components/EntryCard.vue";
import type Entry from "./types/Entry";
import type User from "@/types/User";
import { provide, reactive } from "vue";
import { userInjectionKey } from "@/injectionKeys";
const entries: Entry[] = reactive([]);
const handleCreateEntry = (entry: Entry) => {
  entries.unshift(entry);
};
const user: User = reactive({
  id: 2,
  username: "Kosmos",
  settings: [],
});

provide(userInjectionKey, user);
</script>

<template>
  <main class="container m-auto p-10">
    <TheHeader />
    <EntryEditor @@create="handleCreateEntry" />
    <ul>
      <li v-for="(entry, index) in entries" :key="index">
        <EntryCard :entry="entry" />
      </li>
    </ul>
  </main>
</template>
