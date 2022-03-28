<template>
  <li class="item">
    <input class="todo" type="text" v-model="element.name" :readonly="isReadonly">
    <button class="btn " v-on:click="edit">{{ textButton }}</button>
    <div class="btn danger" @click="removeClick">Удалить</div>
  </li>
</template>

<script>
export default {
  props: {
    value: Object
  },
  data() {
    return {
      isReadonly: true,
      textButton: 'Редактировать',
      localValue: ''
    }
  },
  computed: {
    element: {
      get() {
        return this.value;
      },
      set(value) {
        this.$emit('input', value);
      },
    },
  },
  methods: {
    removeClick() {
      this.$emit("clickDeliteButton")

    },
    edit() {
      this.isReadonly = !this.isReadonly
      if (this.isReadonly) {
        this.textButton = 'Редактировать'
      } else {
        this.textButton = 'Сохранить'
      }
    },
  },

}
</script>

<style>
.todo:read-only {
  border: none;
}
</style>