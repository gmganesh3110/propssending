<template>
  <div>
    <h2>Parent Component</h2>
    <p>Shared message: {{ sharedMessage }}</p>
    <h3>Child 1 to Parent Message{{ child1parent}}</h3>
    <h3>Child 2 to Parent Message{{ child2parent }}</h3>
    <ChildA :sharedMessage="sharedMessage" @childEvent="handleChildEvent1" @siblingEvent1="siblingEvent1" :child2message="child2message" />
    <ChildB :sharedMessage="sharedMessage" :child1message="child1message" @childEvent="handleChildEvent2"  @siblingEvent2="siblingEvent2" />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import ChildA from './ChildA.vue';
import ChildB from './ChildB.vue';

const sharedMessage = ref('Hello from Parent');
const child2message = ref('');
const child1message = ref('');
const child1parent=ref('')
const child2parent=ref('')

const handleChildEvent1 = (message) => {
  child1parent.value=message
};

const handleChildEvent2 = (message) => {
  child2parent.value=message
};

const siblingEvent1 = (message) => {
  child1message.value = message;
};

const siblingEvent2 = (message) => {
  child2message.value = message;
};

</script>
