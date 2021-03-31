<template>
  <div class="wrapper">
    <div class="container">
      <Navbar :logo="$site.themeConfig.logo" :sticky="$route.path === '/'" />
    </div>

    <div class="container">
      <!-- Works list -->
      <div
        v-if="$route.path === '/'"
        :style="{
          marginTop: '14vw',
        }"
      >
        <Content />
      </div>

      <!-- Single project view -->
      <div v-if="isSingleProject">
        <SingleProjectHeader
          :title="$page.frontmatter.title"
          :year="$page.frontmatter.year.toString()"
          :categories="$page.frontmatter.categories"
        />
        <Content />
      </div>

      <!-- Journal list -->
      <div v-if="$route.path === '/journal/'" class="journal-list">
        <Content />
      </div>
    </div>

    <div class="container">
      <Footer />
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    isSingleProject() {
      const worksRoute = '/works/'
      const path = this.$route.path
      if (path.includes('works') && path.length >= worksRoute.length + 1) {
        return true
      }
    },
  },
  updated() {
    // unwrap all images from paragraph tags so we can have
    // different widths inside the content.

    document.querySelectorAll('p img').forEach((image) => {
      var wrapper = image.parentNode
      let children = wrapper.children
      let fragment = document.createDocumentFragment()

      Array.from(children).forEach((child) => {
        fragment.appendChild(child)
      })

      wrapper.parentNode.replaceChild(fragment, wrapper)
    })
  },
}
</script>

<style lang="scss">
@import '@theme/../styles/base.scss';
</style>
