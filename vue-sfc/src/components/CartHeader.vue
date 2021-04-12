<template>
    <h1>{{ upperTitle }}</h1>
</template>
<script>
export default {
    data: function() {
        return {
            title: "Vue Cart"
        }
    },
    computed: {
        upperTitle: function() {
            return this.title.toUpperCase();
        }
    }
}
</script>

<style scoped>
    h1 {
        font-size: 2.0em;
        color: blue;
    }
</style>
