<template>
    <!--Create navigation buttons-->
    <div class="container">
        <br>
        <div class="Main_content">
            <div id="dynamic-component">
                <button
                    v-for="tab in tabs"
                    v-bind:key="tab"
                    v-on:click="currentTab = tab">
                    {{ tab }}
                </button>
                <component v-bind:is="currentTabComponent"></component>
            </div>
        </div>
    </div>
</template>

<script>
import tab_beginner from './beginner'
import tab_home from './Home'
import tab_kanji from './kanji'

export default {
    name: 'Body',
    components: {
        tab_beginner, tab_home, tab_kanji,
    },
    data() {
        return {
            currentTab: 'Home',
            tabs: ['Home', 'Beginner', 'Kanji']
        }
    },
    computed: {
        currentTabComponent() {
            return 'tab_' + this.currentTab.toLowerCase()
        }
    }
}
</script>

<style scoped>
    .container {
        overflow: hidden;
        background-color: aquamarine;
    }
    .Main_content {
        border-radius: 5px;
        border: solid 1px;
        margin: 0.5%;
        background-color: aqua;
        margin-bottom: 2%;
    }
</style>

