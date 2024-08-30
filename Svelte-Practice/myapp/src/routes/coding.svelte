<script>
    import IntersectionObserver from "svelte-intersection-observer/IntersectionObserver.svelte";
    import { fade } from "svelte/transition";
    import banner from '../assets/coding-img.png'
    import Banneroverlay from "./banneroverlay.svelte";
    export let id = "coding";
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
    @font-face {
        font-family:'CC Primal Scream'; 
        src:url('../fonts/CCPrimalScream.ttf');
    }
    .filler {
        height:500px;
    }
   .trigger {
        text-align:left;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
  
    }
    h1 {
        position: relative;
        right:20%;
        color:white;
        font-family: 'CC Primal Scream';
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
<div class="filler"></div>

<IntersectionObserver {element} bind:intersecting threshold={1} >
    <Banneroverlay></Banneroverlay>
    <div class="trigger " {id} bind:this={element}>
      
        
        <img src={banner} alt="Hands in front of a computer running Visual Studio Code" >
        <p>You're...making the website??</p>
    </div>
  
            
       
  
</IntersectionObserver>