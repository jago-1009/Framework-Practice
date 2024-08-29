<script>
	import Footer from "./footer.svelte";
import Navbar from "./navbar.svelte";
import { onMount } from "svelte";
import HeroAttack from '../assets/Hero-Attack.png'
import HeroOfThe from '../assets/Hero-Of-The.png';
import HeroFrontEndDev from '../assets/Hero-Front-End-Developer.png';
import { slide } from "svelte/transition";
import {backIn} from 'svelte/easing';
import HeroSignature from '../assets/Hero-Signature.png'
	
let ready=false;

onMount(() => { 
    requestAnimationFrame(()=>{
        setTimeout(()=>{
            ready = true
        }, 0)
    })
 }) // Adjust the delay as needed})
</script>
<style>
    .hero-signature {
        position: absolute;
        top:5%;
    }
    body {
        height: 100%;
        background-color: #000000;
    }
    .hero-overlay {
        position: absolute;
        opacity: 20%;
        z-index: 2;
        width:95%;
        height:822px;
        background-image: url('../assets/Hero-Grain-Overlay.gif');
        background-size:contain;
    }
   .hero {
    position: relative;
    z-index: 1;
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
   img {
    max-width: 100%;
    margin: 0 auto;
   }
   @media screen and (max-width:1024px) {
    .hero {
        background-image: url('../assets/Hero-Background-laptop.png');
        height:600px;
        
    }
   }
   @media screen and (max-width:700px) {
    .hero {
        height: 600px;
    }
   }
   @media screen and (max-width:500px) {
    .hero {
        height:430px;
    }
   }
   @media screen and (max-width:400px) {
    .hero {
        height:350px;
    }
   }
   @media screen and (max-width:350px) {
    .hero {
        height:300px;
    }
   }
</style>
<body>
<Navbar></Navbar>
<div class="hero-overlay"></div>

<div class="hero">
    <img src={HeroSignature} alt="Jacob Garwood presents" class="hero-signature">
    {#if ready==true}
    <img src={HeroAttack} alt="Attack" transition:slide|global={{delay:300}}>
    <img src={HeroOfThe} alt="Of The" transition:slide={{delay:900}}>
    <img src={HeroFrontEndDev} alt="FrontEndDeveloper" transition:slide={{delay:1500}}>
    {/if}
</div>
<Footer></Footer>
</body>