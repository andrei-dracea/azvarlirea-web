<template>
  <div class="teams-list">
    <br />
    <h3 class="title is-4">Echipe din România</h3>

    <div class="columns">
      <div class="team column" v-for="entity in entities" :key="entity.key">
        <p>
          <img :src="entity.frontmatter.logo" class="logo" alt="" />
        </p>
        <p>
          <b>{{ entity.frontmatter.name }}</b>
        </p>

        <span>{{ entity.frontmatter.city }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    entities() {
      return this.$site.pages
        .filter((x) => x.path.startsWith('/teams/'))
        .sort((a, b) => (a.frontmatter.name < b.frontmatter.name ? -1 : 1))
    },
  },
}
</script>

<style lang="scss">
.logo {
  width: 100px;
  height: 100px;
  border: 1px solid $purple;
}
</style>
