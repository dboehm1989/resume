<template>
  <p>
    <button class="btn primary" @click="loadComments">Загрузить комментарии</button>
  </p>
  <div v-if="isCommentsExist" class="card">
    <h2>Комментарии</h2>
    <ul class="list">
      <li class="list-item" v-for="comment in comments" :key="comment.id">
        <div>
          <p><strong>{{ comment.email}}</strong></p>
          <small>{{ comment.body }}</small>
        </div>
      </li>
    </ul>
  </div>
  <div v-else-if="error" class="alert danger">
    <h3>Ошибка!</h3>
    <p>{{ error }}</p>
  </div>
  <div v-if="isLoading" class="loader"></div>
</template>

<script>
export default {
  data: () => ({
    comments: [],
    isLoading: false,
    error: null
  }),
  computed: {
    isCommentsExist () {
      return this.comments.length && !this.isLoading
    }
  },
  methods: {
    loadComments () {
      this.isLoading = true
      this.error = null

      setTimeout(async () => {
        const response = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')

        if (!response.ok) {
          this.error = 'Данные не смогли загрузится!'
          this.isLoading = false
          return
        }

        this.comments = await response.json()
        this.isLoading = false
      }, 1500)
    }
  }
}
</script>

<style>

</style>