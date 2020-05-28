<template>
  <q-page class="flex flex-center">
    <img
      alt="Quasar logo"
      src="~assets/quasar-logo-full.svg"
    >
    <q-btn color="white" text-color="black" label="安装App" @click="installApp"></q-btn>
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
