<template>
  <div class="row q-mb-sm">
    <q-input
      outlined
      :value="name"
      :rules="[(val) => !!val || 'Field is required']"
      :modelValue="name"
      @update:modelValue="(event) => $emit('update:name', event)"
      autofocus
      ref="name"
      label="Task name"
      class="col"
    >
      <template v-slot:append>
        <q-icon
          v-if="name"
          @click="$emit('update:name', '')"
          name="close"
          class="cursor-pointer"
        />
      </template>
    </q-input>
  </div>
</template>

<script>
export default {
  props: ["name"],
};
</script>

<style>
</style>