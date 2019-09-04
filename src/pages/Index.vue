<template>
  <Layout>

    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <g-image alt="Example image" src="~/favicon.png" width="135" />

    <h1 class="bg-red-500">Hello, world!</h1>

    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur excepturi labore tempore expedita, et iste tenetur suscipit explicabo! Dolores, aperiam non officia eos quod asperiores
    </p>

    <p class="home-links">
      <a href="https://gridsome.org/docs" target="_blank" rel="noopener">Gridsome Docs</a>
      <a href="https://github.com/gridsome/gridsome" target="_blank" rel="noopener">GitHub</a>
    </p>

    <div class="container mx-auto flex flex-wrap">
      <div class="w-1/2 h-1/2 flex" v-for="edge in $page.photos.edges" :key="edge.node.id">
        <g-image :src="edge.node.display_url"/>
      </div>
    </div>

  </Layout>
</template>

<page-query>
query InstagramPhotos {
  photos: allInstagramPhoto {
    edges {
      node {
        id
        display_url
        edge_liked_by {
          count
        }
        edge_media_to_comment {
          count
        }
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  },
  created() {
    // console.log(this.$page)
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
