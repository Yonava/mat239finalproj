<template>
    <div class="stop-scrolling" style="transition: 7s" :style="parentStyle">
        <div style="transition: 4s" :style="starting">
            <h1>Path Pebbling</h1>
            <hr>
            <h2>Input Number of Vectices:</h2>
            <input type="number" v-model="vectices" />
            <h2>Pebbling Number - {{ minPebbles }}</h2>
            <button @click="engageTour">Start Tour</button>
            <button class="home" v-on:click="$parent.switchPage('')">Home</button>
        </div>
        <div>
            <br><br><br><br><br><br><br>
            <h2 style="transition: 3s" :style="tourTitle">The Path</h2>
            <p style="transition: 3s" :style="tourTitleSub">Presented By Yona Voss-Andreae</p>
            <br><br>
            <h2 style="transition: 3s" :style="a">What is a Path?</h2>
            <div style="max-width: 50vw;">
                <p style="transition: 3s" :style="b">In graph theory, a path graph is a graph in which each vertice 
                    inbetween the endpoints has a degree of 2 chaining the parent vertex and root vertex together.
                </p>
            </div>
            <img :style="extras" style="width: 80vw;" src="../assets/path/9.svg" alt="path graph">
            <div class="main-tour">
                <h2 style="transition: 4s ease-in-out;" :style="d">What is the path graphs pebbling number?</h2>
                <h2 style="transition: 4s ease-in-out; font-weight: bold;" :style="e">2 to the Power of N</h2>
                <h2 style="transition: 4s ease-in-out;" :style="f">Why?</h2>
                <p style="transition: 4s ease-in-out; max-width: 50vw;" :style="g">
                    N represents each edge (aka tollway).
                    The 2 represents doubling the necessary pebbles to ensure successful pebbling. 
                </p>
                <h2 style="transition: 4s ease-in-out;" :style="h">I Am Player 1, What's My Best Move?</h2>
                <p :style="i" style="transition: 4s ease-in-out; max-width: 50vw;">
                    The only sensible strategy for you to take, given a path, is to place the pebbles
                    as far as possible away from the target.
                </p>
                <h2 style="transition: 4s ease-in-out;" :style="j">Does Spreading Out The Pebbles Along The Path Help Me?</h2>
                <p :style="k" style="transition: 4s ease-in-out; max-width: 50vw;">
                    Since each tile the pebbles move comes at a hefty
                    50% tax, pebbles placed closer to the target carry exponentially more weight than those placed
                    father down the path. Due to this, player 1 would gain no additional benefit by dispersing the
                    pebbles throughout the path.
                </p>
            </div>
        </div>
        <br><br><br><br><br><br>
        <h1 :style="extras">Tour Will Exit Automatically</h1>
        <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
    </div>
</template>

<script>
export default {
    data: () => {
        return {
            vectices: 7,
            minPebbles: 64,
            // on the tour
            tourTitle: 'opacity: 0; color: white;',
            tourTitleSub: 'opacity: 0; color: white;',
            starting: '',
            parentStyle: '',
            pagePos: 0,
            a: 'opacity: 0; color: white;',
            b: 'opacity: 0; color: white;',
            c: '',
            d: 'opacity: 0;',
            e: 'opacity: 0;',
            f: 'opacity: 0;',
            g: 'opacity: 0;',
            h: 'opacity: 0;',
            i: 'opacity: 0;',
            j: 'opacity: 0;',
            k: 'opacity: 0;',
            extras: 'display: none;',
        }
    },
    watch: {
        vectices() {
            this.vectices > 1 ? this.minPebbles = 2**(this.vectices-1):this.minPebbles = 'Invalid';
        }
    },
    methods: {
        engageTour() {
            this.tour();
            setInterval(() => {window.scrollTo(0, this.pagePos); this.pagePos += 0.1}, 1);
            this.parentStyle = 'background-color: white; cursor: none;';
            this.starting = 'opacity: 0;';
            this.extras = '';
        },
        tour() {
            setTimeout(() => this.parentStyle = 'background-color: black; cursor: none;', 2000)
            setTimeout(() => this.tourTitle = 'font-size: 40pt; margin: 0px; color: white;', 4000)
            setTimeout(() => this.tourTitleSub = 'font-size: 20pt; margin-top: 0px; color: white', 5000)
            setTimeout(() => this.a = 'color: white;', 10000)
            setTimeout(() => this.b = 'color: white;', 14000)
            setTimeout(() => this.parentStyle = 'background-color: white; cursor: none;', 30000)
            setTimeout(() => this.d = 'opacity: 1', 37200)
            setTimeout(() => this.e = 'opacity: 1', 39400)
            setTimeout(() => this.f = 'opacity: 1', 41300)
            setTimeout(() => this.g = 'opacity: 1', 44600)
            setTimeout(() => this.h = 'opacity: 1', 55800)
            setTimeout(() => this.i = 'opacity: 1', 58000)
            setTimeout(() => this.j = 'opacity: 1', 63000)
            setTimeout(() => this.k = 'opacity: 1', 67000)
            setTimeout(() => this.parentStyle = 'background-color: rgb(255, 200, 200); cursor: none;', 75000)
            setTimeout(() => location.reload(), 90000)
        },
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
    box-shadow: none;
}
h2 {
    font-weight: bold;
}
.stop-scrolling {
    height: 100%;
    overflow: hidden;
}
</style>
