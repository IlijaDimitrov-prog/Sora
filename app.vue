<template>
  <Html :lang="htmlAttrs.lang" :dir="htmlAttrs.dir">

  <Head>
    <Title>{{ $t('app_title') }}</Title>
    <template v-for="link in head.link" :key="link.id">
      <Link :id="link.id" :rel="link.rel" :href="link.href" :hreflang="link.hreflang" />
    </template>
  </Head>

  <Body class="bg-white dark:bg-gray-900">
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </Body>

  </Html>
</template>
<script setup lang="ts">
const { t } = useI18n()

const head = useLocaleHead({
  addDirAttribute: true,
  identifierAttribute: "id",
  addSeoAttributes: true,
})

useSeoMeta({
  ogTitle: t('seo.ogTitle'),
  description: t('seo.description'),
  ogDescription: t('seo.ogDescription'),
  ogImage: '/logo.png',
  twitterCard: 'summary_large_image',
})

const htmlAttrs = computed(() => head.value.htmlAttrs!)
</script>
