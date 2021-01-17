<template>
  <div class="card card-w70">
    <template v-if="isResumeExist">
      <template v-for="item in resume" :key="item.id">
        <component :is="getComponent(item)" :value="item.value" />
      </template>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeTitle from './ResumeTitle'
import ResumeSubtitle from './ResumeSubtitle'
import ResumeAvatar from './ResumeAvatar'
import ResumeText from './ResumeText'

export default {
  props: {
    resume: {
      type: Array,
      required: true
    }
  },
  computed: {
    isResumeExist() {
      return this.resume.length
    },
  },
  methods: {
    getComponent({type}) {
      return `resume-${type}`
    }
  },
  components: {
    ResumeTitle, ResumeSubtitle, ResumeAvatar, ResumeText
  }
}
</script>

<style>

</style>