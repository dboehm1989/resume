<template>
  <form class="card card-w30" @submit.prevent="updateResume">
    <div class="form-control">
      
      <label for="type">Тип блока</label>
      <select id="type" v-model="form.type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model.trim="form.value"></textarea>
    </div>

    <button class="btn primary" :disabled="isValueNotValid">Добавить</button>
  </form>
</template>

<script>
export default {
  emits: {
    resume(obj) {
      const isObject = obj instanceof Object
      if (!isObject) {
        console.warn('Wrong type format in resume emit');
      }
      return isObject
    }
  },
  data: () => ({
    form: {
      id: 0,
      type: 'title',
      value: ''
    }
  }),
  computed: {
    isValueNotValid () {
      return this.form.value.length < 4
    }
  },
  methods: {
    updateResume() {
      this.form.id++
      this.$emit('resume', {...this.form})
      this.resetForm()
    },
    resetForm() {
      this.form.type = 'title'
      this.form.value = ''
    }
  }
}
</script>

<style>

</style>