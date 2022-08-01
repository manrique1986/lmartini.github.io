<template>
  <div>
    <h3>Work Experience</h3>
    <ul class="posts">
      <li v-for="n in 3" :key="n">
        <img src="https://picsum.photos/75/75" alt="" class="tn" />
        <h4>Job Title</h4>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ProfilePosts",
};
</script>
