<template>
  <div>
    <div v-for="(todo , index) in todos" :key="todo.title">
      <b-field class="is-pulled-left">
        <b-checkbox size="is-large" @input=checkbox(index)>
          <strike v-if="todo.completed">{{ todo.title }}</strike>
          <span v-else>{{ todo.title }}</span>
        </b-checkbox>
      </b-field>
      <a class="delete is-pulled-right" @click=DELETE_TODO(index)></a>
      <div class="is-clearfix"></div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'

export default {
  computed: {
    ...mapGetters(['todos'])
  },
  methods: {
    ...mapActions(['DELETE_TODO',
      'checkbox'])
  }
}
</script>
