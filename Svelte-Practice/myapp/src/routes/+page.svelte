<script>
	import Footer from "./footer.svelte";
import Navbar from "./navbar.svelte";
import { onMount } from "svelte";
import HeroAttack from '../assets/Hero-Attack.png'
import HeroOfThe from '../assets/Hero-Of-The.png';
import HeroFrontEndDev from '../assets/Hero-Front-End-Developer.png';
import { slide } from "svelte/transition";
import {backIn} from 'svelte/easing';
	
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
    h1 {
        color: white;
    }
    body {
        height: 100%;
        background-color: #000000;
    }
   .hero {
    width:100%;
    height:822px;
    background-image: url('../assets/Hero-Background.png');
    background-size: contain;
    background-repeat: no-repeat;
    display: flex;
    align-items: center;
    justify-content: center;
   flex-direction: column;
   }
</style>
<body>
<Navbar></Navbar>
<div class="hero">
    {#if ready==true}
    <img src={HeroAttack} alt="Attack" transition:slide|global={{delay:300, easing:backIn}}>
    <img src={HeroOfThe} alt="Of The" transition:slide={{delay:900}}>
    <img src={HeroFrontEndDev} alt="FrontEndDeveloper" transition:slide={{delay:1500}}>
    {/if}
</div>
<Footer></Footer>
</body>