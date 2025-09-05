<script lang="ts">
   // import Globe from 'globe.gl';
   import { onMount } from 'svelte';

   let { reducedMotion = false } = $props();

   let mounted = $state(false);

   const sourceSplineURL = '';

   const N = 20;
   const arcsData = [...Array(N).keys()].map(() => ({
      startLat: (Math.random() - 0.5) * 180,
      startLng: (Math.random() - 0.5) * 360,
      endLat: (Math.random() - 0.5) * 180,
      endLng: (Math.random() - 0.5) * 360,
      color: [
         ['red', 'white', 'blue', 'green'][Math.round(Math.random() * 3)],
         ['red', 'white', 'blue', 'green'][Math.round(Math.random() * 3)],
      ],
   }));

   onMount(() => {
      if (typeof window !== 'undefined') {
         const globeContainer = document.getElementById('globeViz')!;
         new Globe(globeContainer)
            .globeImageUrl(
               '//cdn.jsdelivr.net/npm/three-globe/example/img/earth-night.jpg',
            )
            .arcsData(arcsData)
            .arcColor('color')
            .arcDashLength(() => Math.random())
            .arcDashGap(() => Math.random())
            .arcDashAnimateTime(() => Math.random() * 4000 + 500);
      }
   });
</script>

<div
   class="relative h-[1020px] w-[700px] md:h-auto md:w-96 sm:w-[500px] lg:w-[80vw] overflow-visible"
>
   <!-- Main Globe -->
   <div
      class="relative h-full flex items-center justify-center overflow-visible"
   >
      <!-- Center place -->

      <div id="globeViz" class=" bg-transparent!"></div>
      <!-- <spline-viewer
         url="https://prod.spline.design/o0EFdfY56DM9hrzW/scene.splinecode"
         width="900"
         height="900"
         class="scale-50 translate-y-[200px] md:w-auto md:translate-y-[300px] lg:scale-100 lg:translate-y-[500px]"
      ></spline-viewer> -->

      <!-- Floating Clouds -->
      {#if mounted}
         <div class="absolute inset-0 pointer-events-none">
            {#each Array(8) as _, i}
               <div
                  class="absolute w-8 h-4 bg-white/30 rounded-full blur-sm"
                  class:animate-float={!reducedMotion}
                  style="
              left: {20 + Math.random() * 60}%; 
              top: {20 + Math.random() * 60}%;
              animation-delay: {i * 0.5}s;
              animation-duration: {3 + Math.random() * 2}s;
            "
               ></div>
            {/each}
         </div>
      {/if}

      <!-- Orbital Particles -->
      {#if mounted}
         <div class="absolute inset-0 pointer-events-none">
            {#each Array(12) as _, i}
               <div
                  class="absolute w-2 h-2 bg-cyan-400 rounded-full opacity-60"
                  class:animate-orbit={!reducedMotion}
                  style="
              animation-delay: {i * 0.3}s;
              animation-duration: {8 + Math.random() * 4}s;
            "
               ></div>
            {/each}
         </div>
      {/if}
   </div>
</div>

<style>
   @keyframes globe-rotate {
      from {
         transform: rotateY(0deg);
      }
      to {
         transform: rotateY(360deg);
      }
   }

   @keyframes spin-slow {
      from {
         transform: rotate(0deg);
      }
      to {
         transform: rotate(360deg);
      }
   }

   @keyframes float {
      0%,
      100% {
         transform: translateY(0px) translateX(0px);
      }
      25% {
         transform: translateY(-10px) translateX(5px);
      }
      50% {
         transform: translateY(-5px) translateX(-5px);
      }
      75% {
         transform: translateY(-15px) translateX(3px);
      }
   }

   @keyframes orbit {
      0% {
         transform: rotate(0deg) translateX(200px) rotate(0deg);
         opacity: 0;
      }
      10% {
         opacity: 1;
      }
      90% {
         opacity: 1;
      }
      100% {
         transform: rotate(360deg) translateX(200px) rotate(-360deg);
         opacity: 0;
      }
   }

   .animate-globe-rotate {
      animation: globe-rotate 25s linear infinite;
   }

   .animate-spin-slow {
      animation: spin-slow linear infinite;
   }

   .animate-float {
      animation: float ease-in-out infinite;
   }

   .animate-orbit {
      animation: orbit linear infinite;
   }

   .shadow-inner-strong {
      box-shadow: inset 0 0 50px rgba(0, 0, 0, 0.3);
   }

   /* Respect reduced motion preferences */
   @media (prefers-reduced-motion: reduce) {
      .animate-globe-rotate,
      .animate-spin-slow,
      .animate-float,
      .animate-orbit {
         animation: none;
      }
   }

   .animate-fade-in-up {
      tin: fade-in-up 0.8s ease-out;
   }
</style>
