<template>
    <div class="h-100 w-full flex items-center justify-center bg-teal-lightest" :key="results">
        <Results v-for="result in results" :item="result" :key="result" />
    </div>
</template>

<script>
import Results from './Results'
export default {
    name: 'ResultGrid',
    components: {Results},
    props: ['results'],
}
</script>