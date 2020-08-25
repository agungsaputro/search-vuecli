<template>
    <div>
        <div class="h-100 w-full flex items-center justify-center bg-teal-lightest">
            <div>
                <div class="grid gap-4 grid-cols-3 grid-rows-3" >
                    <div>
                        <a v-bind:href="url" target="_blank">
                                <img class="w-full p-4" v-bind:src="thumbnailUrl">
                                <div class="px-auto text-center py-4">
                                    <div class="text-base mb-2">{{title}}</div>
                                </div>
                                <p>
                                    <Label v-for="tech in post.tech" :tech="tech" :key="tech" />
                                </p>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Label from './Label.vue'

export default {
    name: 'Results',
    props: ['title', 'url', 'thumbnailUrl', 'id'],
    components: {Label}
}
</script>