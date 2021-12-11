<template>
    <div>
        <h1>Path Pebbling</h1>
        <hr>
        <h2>Input Number of Vectors:</h2>
        <input type="number" v-model="vectors" />
        <h2>Pebbling Number - {{ minPebbles }}</h2>
        <button class="home" v-on:click="$parent.switchPage('')">Home</button>
    </div>
</template>

<script>
export default {
    data: () => {
        return {
            vectors: 0,
            minPebbles: 'Invalid',
        }
    },
    watch: {
        vectors() {
            this.vectors > 1 ? this.minPebbles = 2**(this.vectors-1):this.minPebbles = 'Invalid';
        }
    }
}
</script>

<style scoped>
button {
    padding: .5%;
    width: 20vw;
}
button:hover {
    background-color: lightcoral;
}
h2 {
    font-weight: normal;
}

</style>
