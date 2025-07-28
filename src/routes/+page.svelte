<script lang="ts">
   import GradualSpacing from '$lib/components/ui/svelte-motion/gradual-spacing.svelte';
   import GlobalHeroSection from './components/global-hero-section.svelte';
   import Input from './components/input.svelte';
</script>

<svelte:head>
   <title>CHIDO AI</title>

   <meta
      name="description"
      content="La IA es el pincel; la visión sigue siendo humana."
   />
   <meta property="og:url" content="https://chido-ai.com" />
   <meta property="og:type" content="website" />
   <meta property="og:title" content="CHIDO AI | Automatización con IA" />
   <meta
      property="og:description"
      content="La IA es el pincel; la visión sigue siendo humana."
   />

   <meta property="og:image" content="https://chido-ai.com/preview.jpeg" />

   <link rel="preconnect" href="https://fonts.googleapis.com" />
   <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="" />
   <link
      href="https://fonts.googleapis.com/css2?family=Roboto+Slab:wght@100..400&display=swap"
      rel="stylesheet"
   />
   <script
      type="module"
      src="https://unpkg.com/@splinetool/viewer@1.10.37/build/spline-viewer.js"
   >
   </script>
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
         class="text-white text-center text-2xl md:text-4xl lg:text-7xl max-w-[1020px]"
         style="font-family: 'Roboto Slab'; font-weight: 900;"
      >
         La IA es el pincel; la visión sigue siendo humana.
      </h1>

      <GradualSpacing
         words="Automatización con IA"
         className="text-white text-xs md:text-lg lg:text-2xl"
         textStyle="font-family: 'Roboto Slab"
      />

      <Input />
   </div>
   <GlobalHeroSection />
</main>
