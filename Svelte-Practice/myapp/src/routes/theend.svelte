<script>
    import Filler from "./filler.svelte";
    import Banneroverlay from "./banneroverlay.svelte";
    import IntersectionObserver from "svelte-intersection-observer/IntersectionObserver.svelte";
    import { fade } from "svelte/transition";
    export let id = "theend";
    export let intersecting;
    let element;

</script>
<style>
    h1 {
        color:white;
        position: relative;
        font-size:64px;
        text-align: center;
        font-family: 'CC Primal Scream';
        display: flex;
       bottom:20%;
        align-items: center;
        justify-content: center;
        
    }
    .hero {
    position: relative;
   
    width:100%;
    height:822px;
    background-image: url('../assets/Hero-Background.png');
    background-repeat: no-repeat;
    display: flex;
    align-items: center;
    justify-content: center;
   flex-direction: column;
   background-size: 100%;
   }
</style>

<Filler></Filler>
<IntersectionObserver {element} bind:intersecting threshold={1} >
    <Banneroverlay></Banneroverlay>
    <div class="hero" transition:fade={{delay:600}} {id}>
        <h1 transition:fade={{delay:1200}}>The End!</h1>



</div>
<Filler></Filler>
</IntersectionObserver>