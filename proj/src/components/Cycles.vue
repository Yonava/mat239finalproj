<template>
    <div class="stop-scrolling" style="transition: 7s" :style="parentStyle">
        <div style="transition: 4s" :style="starting">
            <h1>Cycle Pebbling</h1>
            <hr>
            <h2>Input Number of Vectices:</h2>
            <input type="number" v-model="vectices" />
            <h2>Pebbling Number - {{ minPebbles }}</h2>
            <button @click="engageTour">Start Tour</button>
            <button class="home" v-on:click="$parent.switchPage('')">Home</button>
        </div>
        <div>
            <br><br><br><br><br><br><br>
            <h2 style="transition: 3s" :style="tourTitle">The Cycle</h2>
            <p style="transition: 3s" :style="tourTitleSub">Presented By Yona Voss-Andreae</p>
            <br><br>
            <h2 style="transition: 3s" :style="a">What is a Cycle Graph?</h2>
            <div style="max-width: 50vw;">
                <p style="transition: 3s" :style="b">In graph theory, a cycle graph is a graph in which each 
                Vertice has exactly a degree of 2.</p>
            </div>
            <img :style="extras" style="width: 25vw;" src="../assets/cycle/8.svg" alt="path graph">
            <div class="main-tour">
                <h2 style="transition: 4s ease-in-out;" :style="d">What is the Cycles Pebbling Number?</h2>
                <p style="transition: 4s ease-in-out;" :style="e">While I am not entirely certain
                    on an equation that can scale to any graph and hold true, my running theory is
                    <b>(2 to the N) / 2 + 1</b> for an even number of vertices and
                    <b>(2 to the N) / 2</b> for an odd number of vertices.
                </p>
                <h2 style="transition: 4s ease-in-out;" :style="f">Why?</h2>
                <p style="transition: 4s ease-in-out; max-width: 50vw;" :style="g">
                    When conceptualizing what a cycle is, I believe the best way to distill it is to look at the cycle
                    as two paths joined together to form a whole. With that in mind, if we split the cycle in half
                    we can see 2 distinct paths. In the equation <b>(2 to the N) / 2 + 1</b>, we take a regular
                    path (2 to the N), divide that by 2 and add 1 extra pebble to ensure that player 1
                    cannot win by piling all the pebbles on the Vertice farthest from the target along with moving 2 pebbles
                    to each adjacent Vertice (taking away a single pebble necessary for player 2).
                </p>
                <h2 style="transition: 4s ease-in-out;" :style="h">I Am Player 1, What's My Best Move?</h2>
                <p :style="i" style="transition: 4s ease-in-out; max-width: 50vw;">
                    Like with the path graph, placing pebbles further from the target diminishes the pebbles ultimate value.
                    Splitting pebbles between paths may be positive at first, however, you must keep in mind
                    that every pebble you move closer to the target Vertice is a donation to player 2 that I'm sure
                    they would be very grateful for!
                </p>
                <h2 style="transition: 4s ease-in-out;" :style="j">Unsolved...</h2>
                <p :style="k" style="transition: 4s ease-in-out; max-width: 50vw;">
                    The cycle graph posed as the most challenging graph to find an equation for. Be it because there are
                    different equations at play for cycles with odd number vertices juxtaposed to even sums of vertices, or
                    that when I tried to scale it, the problem became much harder to grasp, which came with it uncertainty.
                    I have thought long and hard about pebbling the cycle, I hope to find a satisfying answer to this
                    specific graph type, but unfortunately, as of the end of the semester that hasn't materialized.
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
            minPebbles: 128,
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
            this.vectices > 1 ? this.minPebbles = (2**(this.vectices-1))/2+1:this.minPebbles = 'Invalid';
        }
    },
    methods: {
        engageTour() {
            this.tour();
            setInterval(() => {window.scrollTo(0, this.pagePos); this.pagePos += 0.075}, 1);
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
            setTimeout(() => this.parentStyle = 'background-color: white; cursor: none;', 27000)
            setTimeout(() => this.d = 'opacity: 1', 33200)
            setTimeout(() => this.e = 'opacity: 1', 49400)
            setTimeout(() => this.f = 'opacity: 1', 51300)
            setTimeout(() => this.g = 'opacity: 1', 54600)
            setTimeout(() => this.h = 'opacity: 1', 55800)
            setTimeout(() => this.i = 'opacity: 1', 68000)
            setTimeout(() => this.j = 'opacity: 1', 73000)
            setTimeout(() => this.k = 'opacity: 1', 87000)
            setTimeout(() => this.parentStyle = 'background-color: rgb(255, 200, 200); cursor: none;', 125000)
            setTimeout(() => location.reload(), 140000)
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