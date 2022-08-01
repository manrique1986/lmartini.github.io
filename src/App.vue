<template>
  <div class="container" style="background-image: url('https://picsum.photos/1000/700');">
    <div class="wrapper">
    <div id="profile" class="profile">
      <div class="user-info">
        <div class="user-info_avatar">
          <img src="https://picsum.photos/250/250" alt="" />
        </div>
        <h2>{{ name }}</h2>
        <div class="profile_nav">
          <ul>
            <li
              @click="
                view = 'profile-about';
                active = 'about';
              "
              v-bind:class="{ active: active === 'about' }"
            >
              ABOUT
            </li>
            <li
              @click="
                view = 'profile-posts';
                active = 'posts';
              "
              v-bind:class="{ active: active === 'posts' }"
            >
              WORK EXPERIENCE
            </li>
            <li
              @click="
                view = 'profile-contact';
                active = 'contact';
              "
              v-bind:class="{ active: active === 'contact' }"
            >
              CONTACT
            </li>
          </ul>
        </div>
      </div>
      <div class="content">
        <transition name="slide-fade" mode="out-in">
          <component v-bind:is="view"></component>
        </transition>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
import ProfileAbout from "./components/ProfileAbout.vue";
import ProfileContact from "./components/ProfileContact.vue";
import ProfilePosts from "./components/ProfilePosts.vue";
export default {
  name: "App",
  components: {
    ProfileAbout,
    ProfileContact,
    ProfilePosts
  },
  data() {
    return {
      view: "profile-about",
      active: "about",
      name: "Mark Rigby",
      mycolor: '#'+(Math.random()*0xFFFFFF<<0).toString(16)
    }
  },
  mounted(){
    document.getElementsByClassName("user-info_avatar")[0].style.border = `5px solid ${this.mycolor}`
    document.getElementsByClassName("wrapper")[0].style.background = `linear-gradient(to right bottom, transparent 50%, ${this.mycolor} 50%)`
  }
};
</script>

<style>
*,
*:before,
*:after {
  box-sizing: border-box;
}

body {
  margin: 0;
}

.container {
  background: #fff;
  background-size: cover;
  background-position: top left;
  font-family: "Rubik", sans-serif;
  margin: 0;
}
.container p {
  color: #424242;
  line-height: 1.4;
}
.container h1,
.container h2,
.container h3 {
  text-transform: uppercase;
  letter-spacing: 2px;
}

img {
  max-width: 100%;
}

.wrapper {
  background: linear-gradient(to right bottom, transparent 50%, #009688 50%);
  height: 100vh;
  width: 100%;
}

.profile {
  background-color: #fff;
  box-shadow: 0 20px 75px #00302c;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 3em;
  width: 90%;
  max-width: 800px;
  min-width: 600px;
  margin: 0 auto;
  height: 550px;
}
.profile .user-info {
  width: calc(40% - 15px);
  margin-right: 30px;
  float: left;
}
.profile .user-info h2 {
  font-size: 2em;
  font-weight: 100;
}
.profile .user-info .user-info_avatar {
  border: 5px solid #009688;
}
.profile .user-info img,
.profile .user-info h3 {
  position: relative;
  top: -15px;
  left: -25px;
}
.profile .profile_nav {
  margin-top: 1em;
}
.profile .profile_nav ul {
  list-style: none;
  padding-left: 1em;
  border-left: 3px solid #eaeaea;
}
.profile .profile_nav li {
  margin-top: 0.5em;
  font-size: 1.2em;
  font-weight: bold;
  letter-spacing: 2px;
  transition: 0.2s all;
}
.profile .profile_nav li.active {
  color: #009688;
}
.profile .profile_nav li:hover {
  cursor: pointer;
  color: #009688;
}
.profile .content {
  width: calc(60% - 15px);
  max-height: 100%;
  float: left;
}
.profile .content h3 {
  margin-top: 0;
  font-size: 1.8em;
}
.profile .content .bg-float {
  text-transform: capitalize;
  color: rgba(230, 230, 230, 0.2);
  font-weight: bold;
  position: absolute;
  right: 10px;
  bottom: 0;
  font-size: 12em;
  z-index: -1;
}

.posts {
  list-style: none;
}
.posts li {
  border-bottom: 1px solid #eaeaea;
  margin-bottom: 1em;
  padding: 0.25em;
}
.posts li:after {
  display: table;
  content: "";
  clear: both;
}
.posts img,
.posts h4 {
  display: inline-block;
  margin-right: 1em;
  float: left;
}

.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: opacity 0.1s, transform 0.2s;
}

.slide-fade-enter,
.slide-fade-leave-active {
  opacity: 0;
  transform: translateX(20px);
}
</style>
