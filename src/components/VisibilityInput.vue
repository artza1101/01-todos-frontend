<template>
  <div>
    <b-field class="is-pulled-right">
      <b-radio-button v-model="visibility"
        native-value="all">
        <span>All ( {{ coutAll }} )</span>
      </b-radio-button>
      <b-radio-button v-model="visibility"
        native-value="active">
        <span>Active ( {{coutActive}} )</span>
      </b-radio-button>
      <b-radio-button v-model="visibility"
        native-value="completed">
        <span>Completed ( {{coutCompleted}} )</span>
      </b-radio-button>
    <button class="button is-dark" @click="CLEAR_TODO">
      <b-icon icon="check"></b-icon>
      <span>Clear</span>
    </button>
    </b-field>
  </div>
</template>

<script>
import { store } from '@/store'
import { mapGetters, mapActions } from 'vuex'
export default {
  computed: {
    visibility: {
      get: function () {
        return store.state.visibility
      },
      set: function (newValue) {
        store.dispatch('changeVisibility', newValue)
      },
      ...mapGetters(['todos', 'visibility'])
    },
    coutCompleted () {
      if (this.todos) {
        return this.todos.filter(todo => todo.completed === true).length
      } else {
        return 0
      }
    }
  },
  coutActive () {
  },
  methods: {
    ...mapActions(['CLEAR_TODO'])
  }
}
</script>
