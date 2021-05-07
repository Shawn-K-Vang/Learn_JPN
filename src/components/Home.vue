<template>
    <!--Create a home default page-->
    <div class="home">
        <h1 v-bind:style="{color: colorName}">
            Welcome to the Home Page!
        </h1>
    </div>
</template>
<script>
export default {
    name: 'Home',
    data() {
        return {
            colorName: 'lightgreen'
        }
    }
}
</script>
<style scoped>
    .home {
        border: solid 1px;
        background-color: azure;
    }
</style>

