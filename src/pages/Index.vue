<template>
  <q-page class="">
    啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      deferredPrompt: null
    }
  },
  mounted () {
    this.listenInstall()
  },
  methods: {
    installApp () {
      this.deferredPrompt.prompt()
      this.deferredPrompt.userChoice.then((choiceResult) => {
        if (choiceResult.outcome === 'accepted') {
          console.log('User accepted the A2HS prompt')
        } else {
          console.log('User dismissed the A2HS prompt')
        }
        this.deferredPrompt = null
      })
    },
    listenInstall () {
      window.addEventListener('beforeinstallprompt', (e) => {
        this.deferredPrompt = e
      })
    }
  }
}
</script>
