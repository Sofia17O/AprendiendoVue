<template>
  <div class="bg-gray-100 h-screen flex flex-col max-w-lg mx-auto">
    <div class="bg-blue-500 p-4 text-white flex justify-between items-center">
      <span>Nose😶‍🌫️</span>
    </div>

    <!-- ChatMessges -->
    <ChatMessages :messages="messages"></ChatMessages>

    <!-- MessageBox -->
    <MessageBox @send-message="onMessage($event)"></MessageBox>
  </div>
</template>

<script setup lang="ts">
import ChatMessages from '@/components/Chat/ChatMessages.vue';
import MessageBox from '@/components/Chat/MessageBox.vue';
import { useChat } from '@/composables/useChat';

const { messages, onMessage } = useChat();
</script>
