<script lang="ts">
   import GlobalHeroSection from './components/global-hero-section.svelte';
   import Input from './components/input.svelte';
</script>

<svelte:head>
   <link rel="preconnect" href="https://fonts.googleapis.com" />
   <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="" />
   <link
      href="https://fonts.googleapis.com/css2?family=Roboto+Slab:wght@100..400&display=swap"
      rel="stylesheet"
   />
</svelte:head>

<main class="relative">
   <div
      class="z-50 absolute inset-0 flex justify-between py-2 px-4 md:px-7 md:py-4"
   >
      <!-- left -->
      <div>
         <span class="text-white text-2xl font-bold">CHIDO AI</span>
      </div>

      <!-- center -->
      <div></div>

      <!-- right -->
      <div>
         <button
            class="text-white border border-white py-2 px-4 rounded-xl bg-gradient-to-r from-neutral-900 to-purple-900/40 hover:to-purple-900/10 transition-all duration-300 cursor-pointer"
         >
            Get Started
         </button>
      </div>
   </div>
   <div
      class="z-50 absolute flex w-full flex-col items-center justify-start gap-4 inset-0 top-48 font-semibold"
   >
      <h1
         class="text-white text-2xl md:text-4xl lg:text-7xl max-w-[1020px]"
         style="font-family: 'Roboto Slab'; font-weight: 900;"
      >
         Impulsa tus flujos de trabajo con Inteligencia Artificial
      </h1>
      <p
         class="text-white text-base md:text-lg lg:text-2xl"
         style="font-family: 'Roboto Slab';"
      >
         Diseño, Desarrollo y Automatización de Procesos Inteligentes
      </p>

      <Input />
   </div>
   <GlobalHeroSection />
</main>
