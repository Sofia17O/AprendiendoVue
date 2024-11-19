<template>
  <div ref="chatRef" class="flex-1 overflow-y-auto p-4">
    <div class="flex flex-col space-y-2">
      <!-- Messages go here -->
      <ChatBubble v-for="message in messages" :key="message.id" v-bind="message"></ChatBubble>
    </div>
  </div>
</template>

<script setup lang="ts">
// import type { ChatMessage } from '@/interfaces/chat-message.interface';
import ChatBubble from './ChatBubble.vue';
import { ref, watch } from 'vue';

// interface Props {
//   messages: ChatMessage[];
// }

// const { messages } = defineProps<Props>();
const props = defineProps(['messages']);

const chatRef = ref<HTMLDivElement | null>(null);

watch(props.messages, () => {
  setTimeout(() => {
    chatRef.value?.scrollTo({
      top: chatRef.value.scrollHeight,
      behavior: 'smooth',
    });
  }, 100);
});

// watchEffect(async () => {
//   console.log('Mensajes: ' + messages.length);
//   await nextTick();
//   chatRef.value?.scrollTo({
//     top: chatRef.value.scrollHeight,
//     behavior: 'smooth',
//   });
// });
</script>
