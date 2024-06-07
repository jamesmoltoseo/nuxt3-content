<template>
    <div>
        <h1>{{ doc.title }}</h1>
        <nuxt-content :document="doc" />
    </div>
</template>

<script setup>
import { useAsyncData } from 'nuxt/app'
import { useContent } from '@nuxt/content'

const { params } = useRoute()
const { data: doc } = await useAsyncData(() => useContent(params.slug).fetch())
</script>