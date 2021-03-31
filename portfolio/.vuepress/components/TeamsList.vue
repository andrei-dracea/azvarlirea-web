<template>
  <div class="teams-list">
    <div class="team" v-for="entity in entities" :key="entity.title">
      <p>
        <b>{{ entity.frontmatter.title }}</b>
      </p>

      <span>{{ entity.frontmatter.city }}</span>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    teams() {
      return this.$site.pages
        .filter(
          (x) => x.path.startsWith('/teams/') && !x.frontmatter.works_index
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
