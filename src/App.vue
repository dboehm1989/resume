<template>
  <div class="container column">
    <app-create-resume @resume="v => resume.push(v)" />

    <app-resume :resume="resume" />

  </div>
  <div class="container">
    <app-comments />
  </div>
</template>

<script>
import AppResume from './components/AppResume/AppResume'
import AppCreateResume from './components/AppCreateResume'
import AppComments from './components/AppComments'

export default {
  data: () => ({
    resume: []
  }),
  components: { AppResume, AppCreateResume, AppComments, }
}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
