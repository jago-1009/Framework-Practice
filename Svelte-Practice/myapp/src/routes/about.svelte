<script>
    import IntersectionObserver from "svelte-intersection-observer/IntersectionObserver.svelte";
    import { fade } from "svelte/transition";
    import aboutBanner from '../assets/about-banner.png'
    import Banneroverlay from "./banneroverlay.svelte";
	import Filler from "./filler.svelte";
    export let id = "about";
    export let intersecting;
    let element;
   // Debounce function to limit how often the intersection update is processed
   function debounce(func, wait) {
        let timeout;
        return function(...args) {
            clearTimeout(timeout);
            timeout = setTimeout(() => func.apply(this, args), wait);
        };
    }

    const handleIntersection = debounce((entry) => {
        intersecting = entry.isIntersecting;
    }, 100); // Adjust the debounce wait time as needed
</script>
<style>
    .filler {
        height:500px;
    }
    .about-trigger {
        text-align:left;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
  
    }
    h1 {
        position: relative;
        width: 100%;
        color:white;
        font-family: 'CC Primal Scream';
        opacity: 1; /* Ensure visible */
        text-align: left;

    }
   
    img {
        width:100%;
    }
    p {
        color:var(--subtitle-yellow);
        font-style: italic;
        border:1px black;
        position: relative;
        display: flex;
        font-size:32px;
        font-family:Arial, Helvetica, sans-serif;
       text-shadow: 2px 2px black;
        bottom:10%;
    }
    @media screen and (max-width:1024px) {
        p{
            font-size:24px
        }
    }
    @media screen and (max-width:600px) {
        p {
            font-size: 16px;
        }
    }
    @media screen and (max-width:400px) {
        p {
            font-size: 12px;
        }
    }
</style>
<Filler></Filler>

<IntersectionObserver {element} bind:intersecting threshold={1} >
    
    <div class="about-trigger " {id} bind:this={element}>
      
        <h1 transition:fade>One dark night in the office...</h1>
        <img src={aboutBanner} alt="Man sitting at a desk" >
        <p>I need to make a website, but I don't know how!</p>
    </div>
  
            
       
  
</IntersectionObserver>