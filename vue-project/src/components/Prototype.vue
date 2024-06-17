<script setup lang="ts">
import { defineProps, computed, Teleport, ref } from 'vue';

interface Props {
    firstName: string;
    lastName: string;
    image?: string;
    birthDate?: string;
    phone?: string;
    email?: string
}

const props = defineProps<Props>();

const age = computed(() => {
    if (!props.birthDate) {
        return "0";
    }
    const birthYear = new Date(props.birthDate).getFullYear();
    const currentYear = new Date().getFullYear();
    return currentYear - birthYear;
})
</script>

<template>
    <div ref="cardRef" class="app-card">
    <img class="user-image" :src="image" alt="avatar" />
    <div>
      <div>
        <label> {{ firstName }} {{ lastName }} </label>
      </div>
      <div>
        <div>
          <label> Birth day: </label>
          <span>
            {{ birthDate }}
          </span>
        </div>
        <div>
          <label> Age: </label>
          <span>
            {{ age }}
          </span>
        </div>
        <div>
          <label> Phone number: </label>
          <span>
            {{ phone }}
          </span>
        </div>
        <div>
          <label> Email: </label>
          <span>
            {{ email }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.app-card {
  padding-left: 10px;
  padding-right: 10px;
  padding-top: 5px;
  padding-bottom: 5px;
  background: white;
  box-shadow: 0 0 5px;
  border-radius: 5px;
  border: none;
  font-size: 1.5em;
  transition: 0.3s;
  display: flex;
  align-items: center;
}
.app-card label {
  font-weight: 600;
}
.app-card:hover {
  background: rgba(128, 128, 128, 0.5);
  color: black;
}
.user-image {
  width: 100px;
}
</style>