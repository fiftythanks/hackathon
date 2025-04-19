<script setup>
import { watch } from 'vue';

// Define props received from App.vue
const props = defineProps({
  chatId: {
    type: [String, null],
    default: null,
  },
});

// Watch for changes in chatId to fetch messages
watch(
  () => props.chatId,
  (newChatId, oldChatId) => {
    if (newChatId) {
      console.log(`Chat changed to: ${newChatId} from ${oldChatId}. Fetching messages...`);
      // --- TODO: Add logic here to fetch messages for newChatId ---
      // e.g., fetch(`/api/chats/${newChatId}/messages`)
    } else {
      // Clear messages if no chat is selected
    }
  },
);
</script>

<template>
  <div class="chat-window">
    <div v-if="!chatId" class="placeholder">Выберите чат для начала общения</div>
    <div v-else class="chat-content">
      <!-- Message list area -->
      <div class="message-list">
        <!-- Messages will go here -->
        <p>Messages for {{ chatId }} would load here...</p>
      </div>
      <!-- Message input area -->
      <div class="message-input">
        <input type="text" placeholder="Сообщение..." />
        <button>Отправить</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.chat-window {
  flex-grow: 1; /* Take remaining horizontal space */
  display: flex;
  flex-direction: column;
  height: 100%;
  background-color: #f5f5f5;
  color: #2d2d2b;
}

.placeholder {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  text-align: center;
}

.chat-content {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.message-list {
  flex-grow: 1;
  overflow-y: auto;
  padding: 15px;
  /* Add styles for individual messages later */
}

.message-input {
  display: flex;
  padding: 20px 15px;
  background-color: #d9d9d9;
}
.message-input input {
  flex-grow: 1;
  padding: 5px 15px;
  border: none;
  border-radius: 18px;
  background-color: #f5f5f5;
  margin-right: 10px;
}
.message-input button {
  padding: 5px 15px;
  border: none;
  background-color: #fe0032;
  color: white;
  border-radius: 18px;
  cursor: pointer;
}
</style>
