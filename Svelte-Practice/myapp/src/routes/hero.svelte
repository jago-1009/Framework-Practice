<script>
    import Banneroverlay from "./banneroverlay.svelte";
    import { fade,slide } from "svelte/transition";
    import HeroAttack from '../assets/Hero-Attack.png'
    import HeroOfThe from '../assets/Hero-Of-The.png';
    import HeroFrontEndDev from '../assets/Hero-Front-End-Developer.png';
    import HeroSignature from '../assets/Hero-Signature.png'
    import { onMount } from "svelte";
//---VARIABLE DECLARATIONS---
let components=['about','lightning','laptop-hand','scream','coding','success','theend']
let ready=false;
let startingTime = 300
let newTime;
let componentNum=0
export const smoothScroll = (id) => {
    const element = document.getElementById(id)
    if (element) { 
        window.scrollTo({
            top: element.getBoundingClientRect().top + window.scrollY - 20,
            behavior: 'smooth'})
            componentNum++
    };
    console.log(components[componentNum])
    console.log(componentNum)
}
// ---FUNCTIONS---
function updateTime(time) {
    newTime = time + 600
    return newTime;
}
//---ONMOUNT FUNCTION---
onMount(() => { 
    ready = true
 }) 

</script>

<style>
     .hero-signature {
        position: absolute;
        top:5%;
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
   img {
    max-width: 100%;
    margin: 0 auto;
   }
   i {
    cursor: pointer;
    color:black;
    font-size: 42px;
    text-align: center;
    width:60px;
    height:60px;
    background-color: var(--light-gray);
    border-radius: 30px;
    position: sticky;
    display: flex;
    align-items: center;
    justify-content: center;
    left:80%;
    top:20px;
    bottom:35%;
    text-decoration: none;
    z-index: 99 !important;
   }

   @media screen and (max-width:1024px) {
    .hero {
        background-image: url('../assets/Hero-Background-laptop.png');
        height:660px;
        
    }
   }
   /* @media screen and (max-width:1300px) {
    i {
        left:40%;
    }
   } */
   @media screen and (max-width:700px) {
    .hero {
        height: 600px;
    }
   }
   @media screen and (max-width:500px) {
    .hero {
        height:550px;
    }
   }
   @media screen and (max-width:400px) {
    .hero {
        height:450px;
    }
   }
   @media screen and (max-width:350px) {
    .hero {
        height:400px;
    }
   }
    @media screen and (max-width:1024px) {
        i{
            font-size:24px;
            width:40px;
            height:40px;
        }
    }

</style>
<Banneroverlay></Banneroverlay>
{#if ready==true}
<div class="hero" transition:fade={{delay:startingTime}}>
    
   
    <img src={HeroSignature} alt="Jacob Garwood presents" class="hero-signature" transition:fade|global={{delay:startingTime}}>
    <img src={HeroAttack} alt="Attack" transition:slide|global={{delay:updateTime(startingTime)}}>
    <img src={HeroOfThe} alt="Of The" transition:slide={{delay:updateTime(newTime)}}>
    <img src={HeroFrontEndDev} alt="FrontEndDeveloper" transition:slide={{delay:updateTime(newTime)}}>

    
</div>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
<i on:click|preventDefault={() => smoothScroll(components[componentNum])} class="fa-solid fa-arrow-down-long" transition:fade={{delay:updateTime(newTime) + 800}}></i>

{/if}
