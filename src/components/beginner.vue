<template>
    <!--Create an introductory level-->
    <div class="Dynamic_content">
        <h1>{{show ? 'Katakana Chart' : 'Hiragana Chart'}}</h1>
        <button v-bind:title="message" @click="display">
            {{show ? 'Hiragana' : 'Katakana'}}
        </button>
        <br><br>
        <div v-if="show"><Katakana/></div>

        <div v-else><Hiragana/></div>
    </div>
</template>

<script>
import Katakana from './Katakana'
import Hiragana from './Hiragana'

export default {
    name: 'Dynamic_Component',
    components: {
        Katakana, Hiragana, 
    },
    //Data properties
    data() {
        return {
            //objects
            show: true,
            message: 'Click to display chart'
        }
    },
    //Methods option - declared functions
    methods: {
        //EVENT LISTENER
        display() {
            // `this` keyword implies to the component instance
            this.show=!this.show
        }
    }
}
</script>

<style scoped>
    .Dynamic_content {
        overflow: hidden;
        border: solid 1px;
        /*CHANGE if ASIDE ELEMENT IS ADDED */
        max-height: auto;
        margin: 0%;
        background-color: azure;
    }
</style>

