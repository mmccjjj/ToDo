<script>
export default{
    data() {
        return {
            counter: 0
        }
    },
    methods: {
        countUp(){
            this.counter++
        }
    },

computed:{
    counterText(){
        return "Neue Zahl "+ this.counter
    }
}
}
</script>

<template>
    <button @click="$event => countUp()" class="action">
        <slot>Action! {{ counterText}}</slot>
    </button>
</template>


<style scoped>
.action{
 background-color: yellow;
}
</style>
