<template>
  <div>
    <h3>Child Component 2</h3>
    <p>Received shared message: {{ sharedMessage }}</p>
    <h3>Child 1 Message: {{ child1message }}</h3>
    <button @click="sendToParent">Send to Parent</button>
    <button @click="sendToSibling">Send to Sibling</button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

// Props and emits for communication
const { sharedMessage, child1message } = defineProps(['sharedMessage', 'child1message']);
const emit = defineEmits();

// Methods to send events to the parent and sibling
const sendToParent = () => {
  emit('childEvent', 'Message from Child Component 2');
};

const sendToSibling = () => {
  emit('siblingEvent2', 'Message from Child Component 2 to Sibling');
};
</script>
