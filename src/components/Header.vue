<template>
  <q-header elevated class="bg-white text-primary" height-hint="50">
    <q-toolbar v-if="$q.screen.gt.sm">
      <!-- 大图标 -->
      <div class="q-pr-lg">
        <a href="#">
          <img height="32" src="https://cdn.quasar.dev/img/layout-gallery/logo-google-play.png">
        </a>
      </div>
      <!-- 导航 -->
      <q-btn class="text-h5" flat to="/home" label="主页"/>
      <q-btn class="text-h5" flat to="/home" label="主页"/>
      <q-btn class="text-h5" flat to="/home" label="主页"/>
      <q-btn class="text-h5" flat to="/home" label="主页"/>
      <q-btn class="text-h5" flat to="/home" label="主页"/>
      <!-- 搜索框 -->
      <div class="row no-wrap q-ml-lg">
        <q-input dense outlined square v-model="search" placeholder="Search" class="bg-white col"/>
        <q-btn color="grey-3" text-color="grey-8" icon="search" unelevated/>
      </div>
      <q-space></q-space>
      <!-- 用户信息 -->
      <div v-if="user">
        <q-btn flat dense :label="user.username" icon="fas fa-user"/>
      </div>
      <!-- 登录提示 -->
      <div v-else>
        <q-btn flat dense label="登录/注册" icon="fas fa-sign-in-alt" @click="redirectLogin"/>
      </div>
    </q-toolbar>

    <q-toolbar v-else>
      <div class="q-pr-lg">
        <a href="#">
          <img height="32" src="~assets/sad.svg">
        </a>
      </div>
      <q-space></q-space>
      <div class="q-mr-sm">
        <q-btn
          flat
          dense
          round
          @click="mobileNav = !mobileNav"
          aria-label="Menu"
          icon="menu"
        />
      </div>
      <q-drawer
        v-model="mobileNav"
        :breakpoint="500"
        overlay
        bordered
        content-class="bg-grey-3"
      >
        <q-scroll-area class="fit">
          <q-list v-for="(menuItem, index) in menuList" :key="index">

            <q-item clickable :active="menuItem.label === 'Outbox'" v-ripple>
              <q-item-section avatar>
                <q-icon :name="menuItem.icon"/>
              </q-item-section>
              <q-item-section>
                {{ menuItem.label }}
              </q-item-section>
            </q-item>

            <q-separator v-if="menuItem.separator"/>

          </q-list>
        </q-scroll-area>
      </q-drawer>
      <!-- 用户信息 -->
      <div v-if="user">
        <q-btn flat dense :label="user.username" icon="fas fa-user"/>
      </div>
      <!-- 登录提示 -->
      <div v-else>
        <q-btn flat dense label="登录/注册" icon="fas fa-sign-in-alt" @click="redirectLogin"/>
      </div>
    </q-toolbar>
  </q-header>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      user: {
        username: 'john'
      },
      mobileNav: false,
      menuList: [
        {
          icon: 'inbox',
          label: 'Inbox',
          separator: true
        },
        {
          icon: 'send',
          label: 'Outbox',
          separator: false
        },
        {
          icon: 'delete',
          label: 'Trash',
          separator: false
        },
        {
          icon: 'error',
          label: 'Spam',
          separator: true
        },
        {
          icon: 'settings',
          label: 'Settings',
          separator: false
        },
        {
          icon: 'feedback',
          label: 'Send Feedback',
          separator: false
        },
        {
          icon: 'help',
          iconColor: 'primary',
          label: 'Help',
          separator: false
        }
      ]
    }
  },
  methods: {
    redirectLogin () {
      //
    }
  }
}
</script>
