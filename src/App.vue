<script setup>
import { ref, onMounted, computed } from 'vue';
import ChatSidebar from './components/ChatSidebar.vue';
import ChatWindow from './components/ChatWindow.vue';

// --- State ---

// Reactive array to hold the chat list
// API or WebSocket!
const chatList = ref([
  {
    id: 'chat1',
    name: 'Alice',
  },
  {
    id: 'group1',
    name: 'Vue Developers',
  },
  {
    id: 'chat2',
    name: 'Bob',
  },
  {
    id: 'chat3',
    name: 'Charlie',
  },
  // ... more chats
]);

// Reactive variable to store the ID of the currently selected chat
const selectedChatId = ref(null); // Initially no chat is selected

// --- Methods ---

// Function to update the selected chat ID
function handleSelectChat(chatId) {
  console.log('Selected Chat ID:', chatId);
  selectedChatId.value = chatId;
  // Fetch chat details
}

// --- Lifecycle ---
onMounted(() => {
  // Fetch initial chat list here if needed
  // fetch('/api/chats').then(res => res.json()).then(data => chatList.value = data);
});
</script>

<template>
  <div class="app-layout">
    <ChatSidebar :chats="chatList" :activeChatId="selectedChatId" @select-chat="handleSelectChat" />
    <ChatWindow :chatId="selectedChatId" />
  </div>
</template>

<style>
/* Basic Layout Styling */
.app-layout {
  display: flex;
  height: 100vh; /* Full viewport height */
  background-color: #f5f5f5;
  color: #d9d9d9;
}

/* Ensure components take up space */
/* ChatSidebar will have its own width */
/* ChatWindow should grow */
</style>
