<template>
    <div class="stop-scrolling" style="transition: 7s" :style="parentStyle">
        <div style="transition: 4s" :style="starting">
            <h1>Complete Graph Pebbling</h1>
            <hr>
            <h2>Input Number of Vectors:</h2>
            <input type="number" v-model="vectices" />
            <h2>Pebbling Number - {{ vectices }}</h2>
            <button @click="engageTour">Start Tour</button>
            <button class="home" v-on:click="$parent.switchPage('')">Home</button>
        </div>
        <div>
            <br><br><br><br><br><br><br>
            <h2 style="transition: 3s" :style="tourTitle">The Complete Graph</h2>
            <p style="transition: 3s" :style="tourTitleSub">Presented By Yona Voss-Andreae</p>
            <br><br>
            <h2 style="transition: 3s" :style="a">What is a complete graph?</h2>
            <div style="max-width: 50vw;">
                <p style="transition: 3s" :style="b">In graph theory, a complete graph is a graph in which each vertice interlinks which each other vertice.</p>
            </div>
            <img style="width: 25vw;" src="../assets/complete/10.svg" alt="path graph">
            <div class="main-tour">
                <h2 style="transition: 4s ease-in-out;" :style="d">What is the complete graphs pebbling number?</h2>
                <h2 style="transition: 4s ease-in-out;" :style="e">n</h2>
                <h2 style="transition: 4s ease-in-out;" :style="f">Why?</h2>
                <p style="transition: 4s ease-in-out; max-width: 50vw;" :style="g">
                    The n represents each vertice.
                    Because player 1 can't place a pebble on the target tile, after
                    perfectly spreading out all n-1 pebbles, they are forced to place a second pebble on a single vertex
                    allowing player 2 to win.
                </p>
                <h2 style="transition: 4s ease-in-out;" :style="h">I am player 1, what's my best move here?</h2>
                <p :style="i" style="transition: 4s ease-in-out; max-width: 50vw;">
                    Given a complete graph, place one pebble on each non-target vertex until you have no option
                    but to place two pebbles on a single vertice, thereby granting player 1 a victory.
                </p>
            </div>
        </div>
        <br><br><br><br><br><br>
        <h1>Tour Will Exit Automatically</h1>
        <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
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
        }
    },
    methods: {
        engageTour() {
            this.tour();
            setInterval(() => {window.scrollTo(0, this.pagePos); this.pagePos += 0.1}, 1);
            this.parentStyle = 'background-color: white; cursor: none;';
            this.starting = 'opacity: 0;';
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
            setTimeout(() => this.parentStyle = 'background-color: rgb(255, 200, 200); cursor: none;', 65000)
            setTimeout(() => location.reload(), 80000)
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