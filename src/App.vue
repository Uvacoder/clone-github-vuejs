<template>
  <div>
    <SocialLinks />
    <HomePage
      @ShowView="Show_View"
      @getUser="get_User"
      v-if="viewShow === true"
    />
    <CloneGitHub
      @ShowView2="Show_View"
      @resetUser="get_User"
      :user="user"
      v-else
    />
  </div>
</template>

<script>
import SocialLinks from './components/SocialLinks.vue'
import HomePage from './components/HomePage.vue'
import CloneGitHub from './components/CloneGitHub.vue'

export default {
  name: 'App',
  components: {
    SocialLinks,
    HomePage,
    CloneGitHub
  },
  data() {
    const savedView = localStorage.getItem('view')
    const savedUser = localStorage.getItem('user')

    return {
      viewShow: savedView ? savedView : true,
      user: savedUser ? savedUser : ''
    }
  },
  methods: {
    Show_View() {
      this.viewShow = !this.viewShow
    },
    get_User() {
      const text = document.getElementById('jujuju')
      if (this.user === '') {
        this.user = text.value
      } else {
        this.user = ''
      }
    }
  },
  watch: {
    viewShow(val) {
      localStorage.setItem('view', val)
    },
    user(val) {
      localStorage.setItem('user', val)
    },
    mounted() {
      alert(this.user)
    }
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;

  text-decoration: none;
  list-style-type: none;
}
html,
body {
  width: 100%;
}
body,
body i,
body h2,
body h3,
body h4,
body strong {
  color: #161b22;
  background-color: #fff;
}

body.dark,
body.dark i,
body.dark button,
body.dark strong,
body.dark h2,
body.dark h3,
body.dark h4 {
  background-color: #161b22;
  color: #fff;
}
</style>
