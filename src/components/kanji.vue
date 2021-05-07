<template>
    <!--Create a kanji table of notes-->
    <div class="Kanji_chart">
        <h1>Learn Kanji</h1>
        <div class="container">
            <ul class="">
                <li v-for="post in posts" :key="post.id" @click="selectedPost = post">
                    <button>{{ post.title }}</button>
                </li>
            </ul>
            <div>
                <div v-if="selectedPost">
                    <div class="first_table">
                        <table border=1px> 
                            <tr>
                                <td colspan="10"><strong>{{ selectedPost.lvl1 }}</strong></td>
                            </tr>
                            <tr>
                                <td>{{selectedPost.char10}}</td>
                                <td>{{selectedPost.char8}}</td>
                                <td>{{selectedPost.char9}}</td>
                                <td>{{selectedPost.char7}}</td>
                                <td>{{selectedPost.char6}}</td>
                                <td>{{selectedPost.char5}}</td>
                                <td>{{selectedPost.char4}}</td>
                                <td>{{selectedPost.char3}}</td>
                                <td>{{selectedPost.char2}}</td>
                                <td>{{selectedPost.char1}}</td>
                            </tr>
                            <tr>
                                <td>{{selectedPost.hira10}}</td>
                                <td>{{selectedPost.hira9}}</td>
                                <td>{{selectedPost.hira8}}</td>
                                <td>{{selectedPost.hira7}}</td>
                                <td>{{selectedPost.hira6}}</td>
                                <td>{{selectedPost.hira5}}</td>
                                <td>{{selectedPost.hira4}}</td>
                                <td>{{selectedPost.hira3}}</td>
                                <td>{{selectedPost.hira2}}</td>
                                <td>{{selectedPost.hira1}}</td>
                            </tr>
                            <tr>
                                <td>{{selectedPost.define10}}</td>
                                <td>{{selectedPost.define9}}</td>
                                <td>{{selectedPost.define8}}</td>
                                <td>{{selectedPost.define7}}</td>
                                <td>{{selectedPost.define6}}</td>
                                <td>{{selectedPost.define5}}</td>
                                <td>{{selectedPost.define4}}</td>
                                <td>{{selectedPost.define3}}</td>
                                <td>{{selectedPost.define2}}</td>
                                <td>{{selectedPost.define1}}</td>
                            </tr>
                        </table>
                    </div>
                    
                    <div class="second_table">
                        <table border=1px>
                            <tr>
                                <td colspan="10"><strong>{{ selectedPost.lvl2 }}</strong></td>
                            </tr>
                            <tr>
                                <td>{{selectedPost.char20}}</td>
                                <td>{{selectedPost.char19}}</td>
                                <td>{{selectedPost.char18}}</td>
                                <td>{{selectedPost.char17}}</td>
                                <td>{{selectedPost.char16}}</td>
                                <td>{{selectedPost.char15}}</td>
                                <td>{{selectedPost.char14}}</td>
                                <td>{{selectedPost.char13}}</td>
                                <td>{{selectedPost.char12}}</td>
                                <td>{{selectedPost.char11}}</td>
                            </tr>
                            <tr>
                                <td>{{selectedPost.hira20}}</td>
                                <td>{{selectedPost.hira19}}</td>
                                <td>{{selectedPost.hira18}}</td>
                                <td>{{selectedPost.hira17}}</td>
                                <td>{{selectedPost.hira16}}</td>
                                <td>{{selectedPost.hira15}}</td>
                                <td>{{selectedPost.hira14}}</td>
                                <td>{{selectedPost.hira13}}</td>
                                <td>{{selectedPost.hira12}}</td>
                                <td>{{selectedPost.hira11}}</td>
                            </tr>
                            <tr>
                                <td>{{selectedPost.define20}}</td>
                                <td>{{selectedPost.define19}}</td>
                                <td>{{selectedPost.define18}}</td>
                                <td>{{selectedPost.define17}}</td>
                                <td>{{selectedPost.define16}}</td>
                                <td>{{selectedPost.define15}}</td>
                                <td>{{selectedPost.define14}}</td>
                                <td>{{selectedPost.define13}}</td>
                                <td>{{selectedPost.define12}}</td>
                                <td>{{selectedPost.define11}}</td>
                            </tr>
                        </table>
                    </div><!--
                    <h1>TABLE</h1>
                    <div class="first_table">
                        <table border=1px>
                            <tr>
                                <td><strong>Meaning</strong></td>
                                <td><strong>Hiragana</strong></td>
                                <td><strong>Kanji</strong></td>
                            </tr>
                            <tr v-for="kanji in kanjis.slice(0, 10)" :key="kanji.id">
                                <td>{{kanji.define}}</td>
                                <td>{{kanji.hiragana}}</td>
                                <td>{{kanji.char}}</td>
                            </tr>
                        </table>
                    </div>
                    <div class="second_table">
                        <table border=1px>
                            <tr>
                                <td><strong>Meaning</strong></td>
                                <td><strong>Hiragana</strong></td>
                                <td><strong>Kanji</strong></td>
                            </tr>
                            <tr v-for="kanji in kanjis.slice(10, 20)" :key="kanji.id">
                                <td>{{kanji.define}}</td>
                                <td>{{kanji.hiragana}}</td>
                                <td>{{kanji.char}}</td>
                            </tr>
                        </table>
                    </div>-->
                </div>
                <strong v-else>
                    <br>
                    Select any level to view.
                </strong>
            </div>
            <Study v-bind:selectedPost="selectedPost"/>
        </div>
    </div>
</template>

<script>
import charsData from '/src/Kanji.json'
import Study from './StudySet'

export default {
    components: {
        Study
    },
    data() {
        return {
            posts: charsData,
            selectedPost: null,
            kanjis: []
        }
    },
    mounted() {
        fetch('http://localhost:3000/Kanjis')
            .then(res=> res.json())
            .then(data => this.kanjis = data)
            .catch(err => console.log(err.message))
    }
}
</script>

<style scoped>
    .Kanji_chart {
        border: solid 1px;
        background-color: aliceblue;
    }
    table {
        padding: 2px;
        margin: 0px auto;
        float: right;
        border-radius: 5px;
    }
    tr td {
        padding: 9px;
    }
    .first_table {
        display: inline-block;
        position: relative;
        border: solid 1px;
        margin: 1% 0.5% 1%;
        border-radius: 5px;
    }
    .second_table {
        display: inline-block;
        border-radius: 5px;
        position: relative;
        border: solid 1px;
        margin: 1% 0.5% 1%;
    }
    ul {
        margin: auto 1px;
    }
    li {
        display: inline-flex;
        padding: 2px;
    }
</style>