<template>
  <q-layout view="hHh lpR fFf">

    <Header></Header>

    <q-drawer show-if-aboveside="left">
      <!-- drawer content -->
    </q-drawer>
    <q-drawer show-if-aboveside="right">
      <!-- drawer content -->
    </q-drawer>

    <q-page-container>
      <div class="row">
        <div class="col-md-8 col-sm-12 col-xs-12">
          <router-view/>
        </div>
        <div class="col-md-4 col-sm-12 col-xs-12">
          <RightSideBar></RightSideBar>
        </div>
      </div>
      <Footer></Footer>
    </q-page-container>
    <ToolBar></ToolBar>
  </q-layout>
</template>

<script>
import Header from 'components/Header'
import RightSideBar from 'components/RightSideBar'
import Footer from 'components/Footer'
import ToolBar from 'components/ToolBar'

export default {
  components: {
    ToolBar,
    Footer,
    RightSideBar,
    Header
  },
  data () {
    return {
      right: true
    }
  },
  methods: {
    clickRight () {
      this.right = !this.right
    }
  }
}
</script>
