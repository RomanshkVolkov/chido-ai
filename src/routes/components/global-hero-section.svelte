<script>
   import AnimatedGlobe from './animated-globe.svelte';
   import { onMount } from 'svelte';

   let mounted = $state(false);
   let reducedMotion = $state(false);

   onMount(() => {
      mounted = true;
      // Check for reduced motion preference
      reducedMotion = window.matchMedia(
         '(prefers-reduced-motion: reduce)',
      ).matches;
   });
</script>

<section
   class="relative min-h-screen bg-[#060d12] overflow-hidden flex items-center justify-center"
>
   <!-- Animated background gradient -->
   <div class="absolute inset-0"></div>

   <!-- Starfield background -->
   <div class="absolute inset-0">
      {#each Array(100) as _, i}
         <div
            class="absolute w-1 h-1 bg-white rounded-full opacity-30"
            style="
          left: {Math.random() * 100}%; 
          top: {Math.random() * 100}%;
          animation-delay: {Math.random() * 3}s;
        "
            class:animate-pulse={!reducedMotion}
         ></div>
      {/each}
   </div>

   <!-- Main Globe Container -->
   <div class="relative z-10 flex items-center justify-center w-full h-full">
      {#if mounted}
         <AnimatedGlobe {reducedMotion} />
      {/if}
   </div>

   <!-- Content Overlay -->
   <div class="absolute inset-0 z-20 flex items-center justify-center">
      <div class="text-center space-y-8 px-4 sm:px-6 lg:px-8 max-w-4xl mx-auto">
         <!-- Main Headline -->
         <div class="space-y-4">
            <h1
               class="text-4xl sm:text-5xl lg:text-7xl font-bold text-white leading-tight"
            >
               <span
                  class="block opacity-0 animate-fade-in-up"
                  style="animation-delay: 0.5s; animation-fill-mode: forwards;"
               >
                  Global AI
               </span>
               <span
                  class="block bg-gradient-to-r from-blue-400 via-cyan-400 to-emerald-400 bg-clip-text text-transparent opacity-0 animate-fade-in-up"
                  style="animation-delay: 0.8s; animation-fill-mode: forwards;"
               >
                  Solutions
               </span>
            </h1>

            <p
               class="text-xl sm:text-2xl text-gray-300 max-w-2xl mx-auto leading-relaxed opacity-0 animate-fade-in-up"
               style="animation-delay: 1.1s; animation-fill-mode: forwards;"
            >
               Connecting intelligence worldwide through advanced automation and
               cutting-edge technology
            </p>
         </div>

         <!-- CTA Section -->
         <div
            class="flex flex-col sm:flex-row gap-4 justify-center items-center opacity-0 animate-fade-in-up"
            style="animation-delay: 1.4s; animation-fill-mode: forwards;"
         >
            <button
               class="group relative px-8 py-4 bg-gradient-to-r from-blue-500 to-cyan-500 text-white font-semibold rounded-full hover:from-blue-600 hover:to-cyan-600 transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-xl"
            >
               <span class="relative z-10">Get Started</span>
               <div
                  class="absolute inset-0 bg-gradient-to-r from-blue-400 to-cyan-400 rounded-full blur opacity-30 group-hover:opacity-50 transition-opacity duration-300"
               ></div>
            </button>

            <button
               class="px-8 py-4 border-2 border-gray-600 text-gray-300 font-semibold rounded-full hover:border-gray-400 hover:text-white transition-all duration-300 backdrop-blur-sm bg-gray-900/30"
            >
               Learn More
            </button>
         </div>

         <!-- Feature Cards -->
         <div
            class="grid grid-cols-1 md:grid-cols-3 gap-6 mt-16 opacity-0 animate-fade-in-up"
            style="animation-delay: 1.7s; animation-fill-mode: forwards;"
         >
            <div
               class="backdrop-blur-md bg-white/10 rounded-2xl p-6 border border-white/20 hover:bg-white/15 transition-all duration-300"
            >
               <div
                  class="w-12 h-12 bg-gradient-to-r from-blue-400 to-cyan-400 rounded-lg flex items-center justify-center mb-4 mx-auto"
               >
                  <svg
                     class="w-6 h-6 text-white"
                     fill="none"
                     stroke="currentColor"
                     viewBox="0 0 24 24"
                  >
                     <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M13 10V3L4 14h7v7l9-11h-7z"
                     ></path>
                  </svg>
               </div>
               <h3 class="text-lg font-semibold text-white mb-2">
                  Lightning Fast
               </h3>
               <p class="text-gray-300 text-sm">
                  Advanced algorithms processing at unprecedented speeds
               </p>
            </div>

            <div
               class="backdrop-blur-md bg-white/10 rounded-2xl p-6 border border-white/20 hover:bg-white/15 transition-all duration-300"
            >
               <div
                  class="w-12 h-12 bg-gradient-to-r from-emerald-400 to-teal-400 rounded-lg flex items-center justify-center mb-4 mx-auto"
               >
                  <svg
                     class="w-6 h-6 text-white"
                     fill="none"
                     stroke="currentColor"
                     viewBox="0 0 24 24"
                  >
                     <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 9v-9m0-9v9"
                     ></path>
                  </svg>
               </div>
               <h3 class="text-lg font-semibold text-white mb-2">
                  Global Reach
               </h3>
               <p class="text-gray-300 text-sm">
                  Seamless connectivity across all continents and time zones
               </p>
            </div>

            <div
               class="backdrop-blur-md bg-white/10 rounded-2xl p-6 border border-white/20 hover:bg-white/15 transition-all duration-300"
            >
               <div
                  class="w-12 h-12 bg-gradient-to-r from-purple-400 to-pink-400 rounded-lg flex items-center justify-center mb-4 mx-auto"
               >
                  <svg
                     class="w-6 h-6 text-white"
                     fill="none"
                     stroke="currentColor"
                     viewBox="0 0 24 24"
                  >
                     <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                     ></path>
                  </svg>
               </div>
               <h3 class="text-lg font-semibold text-white mb-2">
                  Secure & Reliable
               </h3>
               <p class="text-gray-300 text-sm">
                  Enterprise-grade security with 99.9% uptime guarantee
               </p>
            </div>
         </div>
      </div>
   </div>
</section>
