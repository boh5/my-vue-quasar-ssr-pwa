<template>
  <q-header elevated class="bg-white text-primary">
    <q-toolbar>
      <div v-if="$q.screen.gt.sm">
        <q-btn flat round dense icon="menu" class="q-mr-sm"/>
        <q-btn flat to="/home" label="主页"/>
        <q-btn flat to="/home" label="主页"/>
        <q-btn flat to="/home" label="主页"/>
        <q-btn flat to="/home" label="主页"/>
        <q-btn flat to="/home" label="主页"/>
      </div>
      <div v-else>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
          icon="menu"
        />
      </div>
      <q-space></q-space>
      <div class="row no-wrap" v-if="$q.screen.gt.sm">
        <q-input dense outlined square v-model="search" placeholder="Search" class="bg-white col"/>
        <q-btn color="grey-3" text-color="grey-8" icon="search" unelevated/>
      </div>
      <q-space></q-space>
      <q-btn flat round dense icon="search" class="q-mr-xs"/>
      <q-btn flat round dense icon="group_add"/>
    </q-toolbar>
  </q-header>
</template>

<script>
import { fabGithub } from '@quasar/extras/fontawesome-v5'

const stringOptions = [
  'quasarframework/quasar',
  'quasarframework/quasar-awesome'
]
export default {
  name: 'MyLayout',
  data () {
    return {
      text: '',
      options: null,
      filteredOptions: []
    }
  },
  methods: {
    filter (val, update) {
      if (this.options === null) {
        // load data
        setTimeout(() => {
          this.options = stringOptions
          this.$refs.search.filter('')
        }, 2000)
        update()
        return
      }
      if (val === '') {
        update(() => {
          this.filteredOptions = this.options.map(op => ({ label: op }))
        })
        return
      }
      update(() => {
        this.filteredOptions = [
          {
            label: val,
            type: 'In this repository'
          },
          {
            label: val,
            type: 'All GitHub'
          },
          ...this.options
            .filter(op => op.toLowerCase().includes(val.toLowerCase()))
            .map(op => ({ label: op }))
        ]
      })
    }
  },
  created () {
    this.fabGithub = fabGithub
  }
}
</script>
