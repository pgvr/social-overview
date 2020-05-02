<template>
    <div class="container">
        <div>
            <h1 class="text-6xl">
                PGVR
            </h1>
            <h2 class="text-xl">
                Patrick Goeler
            </h2>
            <div class="flex justify-center">
                <a
                    v-for="(social, index) in socialArray"
                    :key="social.name"
                    :href="social.url"
                    :style="animDelay(index)"
                    :tooltip="social.name"
                    class="hover:text-green-500"
                    target="_blank"
                >
                    <Icon :icon="social.icon" />
                </a>
            </div>
            <div class="flex justify-center items-center">
                <Icon icon="copyright" />
                {{ footer() }}
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from "vue"
import { Component } from "vue-property-decorator"
import socials from "@/static/socials.json"
import Icon from "@/components/Icon.vue"

@Component({ name: "Index", components: { Icon } })
export default class Index extends Vue {
    name = "Index"
    socialArray = socials

    animDelay(i: number) {
        return `animation-delay: ${i * 50}ms`
    }

    iconClass(c: string) {
        return `${c} index-contact-link-icon`
    }

    footer() {
        return `Patrick Goeler ${new Date().getFullYear()}`
    }
}
</script>

<style>
.container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}
</style>
