<script lang="ts" setup>
import DateDisplay from "./DateDisplay.vue";
import UseEmojis from "@/composables/UseEmojis";
import type Entry from "@/types/Entry";
import { inject } from "vue";
import { userInjectionKey } from "@/injectionKeys";
const { findEmoji } = UseEmojis();
interface Props {
  entry: Entry;
}
const user = inject(userInjectionKey);
defineProps<Props>();
</script>
<template>
  <div class="entry-card">
    <div class="entry-card-body">
      <component width="75" :is="findEmoji(entry.emoji)"></component>
      <div class="entry-text">{{ entry.body }}</div>
    </div>
    <div class="entry-footer">
      <DateDisplay :date="new Date()" class="mr-2" />
      |"
      <span class="ml-2">{{ user?.username || "Anonymous" }}</span>
    </div>
  </div>
</template>
