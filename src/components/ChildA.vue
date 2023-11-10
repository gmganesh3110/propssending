<template>
  <div>
    <h3>Child Component 1</h3>
    <p>Received shared message: {{ sharedMessage }}</p>
    <h3>Child 2 Message: {{ child2message }}</h3>
    <button @click="sendToParent">Send to Parent</button>
    <button @click="sendToSibling">Send to Sibling</button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

// Props and emits for communication
const { sharedMessage, child2message } = defineProps(['sharedMessage', 'child2message']);
const emit = defineEmits();

// Methods to send events to the parent and sibling
const sendToParent = () => {
  emit('childEvent', 'Message from Child Component 1');
};

const sendToSibling = () => {
  emit('siblingEvent1', 'Message from Child Component 1 to Sibling');
};
</script>
