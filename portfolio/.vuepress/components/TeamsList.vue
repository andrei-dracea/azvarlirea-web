<template>
  <div class="teams-list">
    <div class="team">
      <p>
        <b>{{ post.frontmatter.title }}</b>
      </p>

      <span v-if="post.frontmatter.city">{{ post.frontmatter.city }}</span>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    posts() {
      return this.$site.pages
        .filter(
          (x) => x.path.startsWith('/works/') && !x.frontmatter.works_index
        )
        .sort(
          (a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date)
        )
    },
  },
}
</script>

<style scoped>
.post {
  position: relative;
  width: 100%;
  height: 70vh;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  margin-bottom: 5vw;
  cursor: pointer;
}
</style>
