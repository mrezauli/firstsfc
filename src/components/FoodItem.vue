<template>
    <div v-on:click="countClicks">
        <!-- <h2>{{ name }}</h2>
        <p>{{ message }}</p> -->
        <h2>
            {{ foodName }}
            <img src="/img_quality.svg" v-show="isFavorite">
        </h2>
        <p>{{ foodDesc }}</p>
        <p id="red">You have clicked me {{ clicks }} times.</p>
        <button v-on:click="toggleFavorite">Favorite</button>
    </div>
</template>

<script>
export default {
    // props: [
    //     'foodName',
    //     'foodDesc',
    //     'isFavorite'
    // ],
    props: {
        foodName: {
            type: String,
            required: true
        },
        foodDesc: {
            type: String,
            required: false,
            default: 'This is the default description.',
            validator: function (value) {
                if (20 < value.length && value.length < 50) {
                    return true;
                }
                else {
                    return false;
                }
            }
        },
        isFavorite: {
            type: Boolean,
            required: false,
            default: false
        }
    },
    data() {
        return {
            name: 'Apples',
            message: 'I like apples',
            clicks: 0,
            //foodIsFavorite: this.isFavorite
        }
    },
    emits: ['toggle-favorite'],
    methods: {
        countClicks() {
            this.clicks++;
        },
        toggleFavorite() {
            // this.foodIsFavorite = !this.foodIsFavorite;
            this.$emit('toggle-favorite', this.foodName);
        }
    }
};
</script>

<style>
#red {
    font-weight: bold;
    color: rgb(144, 12, 12);
}

img {
    height: 1.5em;
    float: right;
}
</style>