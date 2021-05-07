<template>
    <div class="Hiragana_div">
        <img src="../assets/hiragana_chart.png" alt="hiragana chart"/>
        <!--<ul>
            <li v-for="image in images" :key="image">
                <img :src="image.img" :alt="image.alt">
            </li> IMAGES ARE NOT DISPLAYING
        </ul>-->
        <img src="../assets/hiragana_mod_1.png" alt="hiragana mod 1"/>
        <img src="../assets/hiragana_mod_2.png" alt="hiragana mod 2"/>
        <img src="../assets/hiragana_mod_3.png" alt="hiragana mod 3"/>
        <img src="../assets/hiragana_dakuten.png" alt="hiragana dakuten"/>
    </div>
</template>

<script>
export default {
    name: 'Hiragana',
    data () {
        return {
            images: [
                { img: '../assets/hiragana_mod_1.png', alt: '1' },
                { img: '../assets/hiragana_mod_2.png', alt: '2' },
                { img: '../assets/hiragana_mod_3.png', alt: '3' },
                { img: '../assets/hiragana_mod_4.png', alt: '4' },
            ]
        }
    }
}
</script>

<style scoped>
</style>

