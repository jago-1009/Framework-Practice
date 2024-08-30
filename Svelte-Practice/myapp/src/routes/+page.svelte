<script>
//---IMPORT STATEMENTS---
import Footer from "./footer.svelte";
import About from "./about.svelte";
import Hero from "./hero.svelte";
import Filler from "./filler.svelte";
import Lightning from "./lightning.svelte";
import Laptophand from "./laptophand.svelte";
import Scream from "./scream.svelte";
import Coding from "./coding.svelte";
import Success from "./success.svelte";
import TheEnd from "./theend.svelte";
//---VARIABLE DECLARATIONS---
let intersectAbout;
let intersectLightning;
let intersectHand;
let intersectScream;
let intersectCoding;
let intersectSuccess;
</script>
<style global>
    :root {
        --light-gray: #cccccc;
        --subtitle-yellow:#F3CE32;
    }
   
    body {
        height: 100%;
        background-color: #000000;
    }
    p {
        color:var(--light-gray);
        font-style: italic;
        border:1px black;
        position: relative;
        display: flex;
        font-size:32px;
        font-family:Arial, Helvetica, sans-serif;
       text-shadow: 2px 2px black;
        bottom:100px;
    }
    
</style>
<body>
<Hero></Hero>
<Filler></Filler>
<About id="about" intersecting={intersectAbout}></About>
<Lightning id="lightning" intersecting={intersectLightning}></Lightning>
<Laptophand id="laptop-hand" intersecting={intersectHand}></Laptophand>
<Scream id="scream" intersecting={intersectScream}></Scream>
<Coding id="coding" intersecting={intersectCoding}></Coding>
<Success id="success" intersecting={intersectSuccess}></Success>
<TheEnd></TheEnd>
<Footer></Footer>
</body>