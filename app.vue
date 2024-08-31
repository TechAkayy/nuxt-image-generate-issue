<script setup lang="ts">
  const src =
    'https://images.unsplash.com/photo-1654870468927-92c943da24fe?crop=entropy&cs=srgb&fm=jpg&ixid=M3wyMDkyMnwwfDF8c2VhcmNofDQ5fHxiYWtlcnklMjBjYWtlfGVufDB8fHx8MTY5NTA5NzYyNXww&ixlib=rb-4.0.3&q=85'
  const height = 500
  const img = useImage()
  const _srcset = computed(() => {
    return img.getSizes(src, {
      sizes: 'xs:100vw sm:100vw md:100vw lg:100vw xl:100vw',
      modifiers: {
        format: 'webp',
        quality: 70,
        height,
      },
    })
  })
</script>

<template>
  <v-img
    :lazy-src="img(src, {width: 10, quality: 70})"
    :src="img(src, {height, quality: 70})"
    :srcset="_srcset.srcset"
    :height="height"
    :sizes="_srcset.sizes"></v-img>
</template>
