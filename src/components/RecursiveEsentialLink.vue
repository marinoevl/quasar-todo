<script setup>

const props = defineProps({
  title: {
    type: String,
    required: true
  },

  caption: {
    type: String,
    default: ''
  },

  link: {
    type: String,
    default: '#'
  },

  icon: {
    type: String,
    default: ''
  },

  level: {
    type: String,
    default: ''
  },

  children: []
})
</script>

<template>
  <div>
    <div v-if="props.children.length == 0">
      <q-item clickable v-ripple :inset-level="props.level">
        <q-item-section>{{props.title}}</q-item-section>
      </q-item>
    </div>
    <div v-else>
      <div v-if="props.children.length > 0">
        <!-- {{children}} -->
        <q-expansion-item
          expand-separator
          icon="mail"
          :label="props.title"
          :caption="props.caption"
          :header-inset-level="props.level"
          default-closed>
          <RecursiveEsentialLink
            v-for="child in props.children"
            :key="child"
            v-bind="child">
          </RecursiveEsentialLink>
        </q-expansion-item>
      </div>
      <div v-else>
        <q-item clickable v-ripple :inset-level="level">
          <q-item-section>{{title}}</q-item-section>
        </q-item>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
