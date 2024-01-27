<script setup>
 const props = defineProps(['resultado'])
</script>

<template>
    <section class="result mt-5">
        <h2 class="result-number text-center text-success">
            {{ props.resultado }}
        </h2>
    </section>
</template>

<style scoped>
.result-number {
    font-size: 5rem;
}
</style>