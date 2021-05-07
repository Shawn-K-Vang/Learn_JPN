<template>
    <!--PASSING PROP AS A STATIC VALUE-->
    <div class="container">
        <header>
            <!--TEXT INTERPOLATION-->
            <h1>{{title}}</h1>
        </header>
    </div>
</template>

<script>

export default {
    name: 'Header',
    props: {
        title: String,
    },
}
</script>

<style scoped>
    header {
        overflow: hidden;
        display: flex;
        justify-content: space-between;
        align-items: center;
        border: solid 1px;
        padding-left: 2%;
        background-color: orange;
    }
    nav {
        margin-right: 1.5px;
    }
    button {
        margin-right: 20px;
    }
</style>


