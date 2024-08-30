<script>
    import Filler from "./filler.svelte";
    import LightningGif from '../assets/Lightning-Image.gif'
    import { fade } from "svelte/transition";
    import Banneroverlay from "./banneroverlay.svelte";
    import IntersectionObserver from "svelte-intersection-observer/IntersectionObserver.svelte";
    export let id="lightning"
    export let intersecting;
    let element;
</script>
<style>
    img {
        width:100%;
    }
    h1 {
        position: relative;
        width:100%;
        color:white;
        font-family: 'CC Primal Scream';
        text-align: left;
    }
    div {
        display: flex;
        align-items: center;
        justify-content: space-evenly;
        flex-direction: column;
    }
</style>
<Filler></Filler>

<IntersectionObserver {element} bind:intersecting threshold={1} >
    <Banneroverlay></Banneroverlay>
<div class="lightning-trigger " {id} bind:this={element}>
<h1>Suddenly!</h1>
<img src={LightningGif} alt="Lightning Strikes a building" transition:fade={{delay:900}}>


</div>

</IntersectionObserver>