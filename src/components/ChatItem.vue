<script setup>
import avatarSrc from '@/icons/user.svg';

// Define props received from ChatSidebar.vue
const props = defineProps({
  chat: {
    type: Object,
    required: true,
  },
  isActive: {
    type: Boolean,
    default: false,
  },
});
</script>

<template>
  <li class="chat-item" :class="{ active: isActive }">
    <div class="avatar"><img :src="avatarSrc" /></div>
  </li>
</template>

<style scoped>
.chat-item {
  display: flex;
  align-items: center;
  flex-direction: center;
  padding: 10px;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.chat-item:hover {
  background-color: #fe0032; /* Hover effect */
}

.chat-item.active {
  background-color: #fe0032; /* Active chat highlight */
}

.avatar {
  width: 45px;
  height: 45px;
  border-radius: 50%;
  background: #e8e8e8;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
