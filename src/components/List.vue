<template>
    <ul class="list">
        <Item v-for="(note, index) in value"  v-model="notes[index]" :key="index" v-on:clickDeliteButton="filterFun(index)" v-on:clickEdit="clickEdit(index)"/>
    </ul>
</template>

<script>
import Item from './Item.vue'


export default {
    name: 'List',
  components: {
    Item
  },
  props: {
    value:Array
  },
  methods: {
        filterFun(indexNote) {
          this.$emit('deleteNote', indexNote)
        },
    },
  computed:{
    notes: {
      get() {
        return this.value;
      },
      set(value) {
        this.$emit('input', value);
      },
    },
  },
}
</script>
