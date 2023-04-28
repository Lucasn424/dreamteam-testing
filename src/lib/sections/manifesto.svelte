<script lang="ts">
  import { OnMount } from "fractils";
  import { fly, fade, scale } from "svelte/transition";
  import { spring } from "svelte/motion";

  let manifesto = spring(0, {
    stiffness: 0.005,
    damping: 0.1,
  });

  let manifesto_open = false;

  $: {
    if (manifesto_open) manifesto.set(100);
    else manifesto.set(0);
  }

  function stopPulseAnimation() {
    const circElement = document.querySelector('.circ');
    circElement.classList.add('stop-pulse');
}
</script>

<div class="relative flex w-full flex-col items-center min-h-screen"> 
  <svg
    xmlns="http://www.w3.org/2000/svg"
    class="absolute inset-0 -z-50 w-screen h-screen"
  >
    <defs>
      <clipPath id="manifesto_clip">
        <circle cx="50%" cy="75%" r={$manifesto + 5 + "%"} />
      </clipPath>
    </defs>
  </svg>

  <svg
    xmlns="http://www.w3.org/2000/svg"
    class="absolute inset-0 -z-50 w-screen h-screen"
  >
    <defs>
      <clipPath id="manifesto_button_clip">
        <circle cx="50%" cy="75%" r={(100 - $manifesto) / 21 + "%"} />
      </clipPath>
    </defs>
  </svg>

  <OnMount>
    <div class="sticky top-0 left-0 w-full h-screen z-40">
      <!-- <div
        class="gradient circ absolute top-0 left-0 w-full h-screen flex items-center justify-center z-40"
        style="clip-path: url(#manifesto_clip); transform-origin: 50% 75%;"
        in:scale={{ duration: 1000, delay: 2000}}
      /> -->

      <svg xmlns="http://www.w3.org/2000/svg" class="circ absolute top-0 left-0 w-screen h-screen flex items-center justify-center z-40"  style="clip-path: url(#manifesto_clip); transform-origin: 50% 75%;"
      in:scale={{ duration: 1000, delay: 2000}}>
        <defs>
           <linearGradient id='a' gradientUnits='objectBoundingBox' x1='0' y1='0' x2='1' y2='1'>
              <stop offset='0' stop-color='#FF7B89'>
                 <animate attributeName="stop-color"
                    values="#FF7B89;" dur="10s" repeatCount="indefinite">
                 </animate>
              </stop>
              <stop offset='0.5' stop-color='#00FFED'>
                 <animate attributeName="stop-color"
                    values="#00FFED" dur="10s" repeatCount="indefinite">
                 </animate>
              </stop>
              <stop offset='1' stop-color='#FF7B89'>
                 <animate attributeName="stop-color"
                    values="#FF7B89;" dur="10s" repeatCount="indefinite">
                 </animate>
              </stop>
              <animateTransform attributeName="gradientTransform" type="rotate" from="0 .5 .5" to="360 .5 .5"
                 dur="10s" repeatCount="indefinite" />
           </linearGradient>
           <linearGradient id='b' gradientUnits='objectBoundingBox' x1='0' y1='1' x2='1' y2='1'>
              <stop offset='0' stop-color='#00FFED'>
                 <animate attributeName="stop-color"
                    values="#00FFED;" dur="10s" repeatCount="indefinite">
                 </animate>
              </stop>
              <stop offset='1' stop-color='#FF7B89' stop-opacity="1">
                 <animate attributeName="stop-color"
                    values="#FF7B89;" dur="10s" repeatCount="indefinite">
                 </animate>
              </stop>
              <animateTransform attributeName="gradientTransform" type="rotate" values="360 .5 .5;0 .5 .5" class="ignore"
                 dur="10s" repeatCount="indefinite" />
           </linearGradient>
        </defs>
        <rect fill='url(#a)' width='100%' height='100%' />
        <rect fill='url(#b)' width='100%' height='100%' />
     </svg>

      <div
      class="circle absolute top-0 left-0 w-full h-full flex items-center justify-center z-40 cursor-pointer"
      on:click={() => {
        manifesto_open = !manifesto_open;
        stopPulseAnimation();
    }}
      style="background: black; clip-path: url(#manifesto_button_clip); transform-origin: 50% 75%;"
      in:scale={{ duration: 2000, delay: 3000}}
    />

      <div
        class="absolute left-1/2 top-3/4 -translate-x-1/2 -translate-y-1/2"
        in:fly={{ y: 250, duration: 1500, delay: 1700 }}
      >
        <p class="pt-64 xl:pt-41">Manifesto</p>
      </div>
    </div>
  </OnMount>

  <div
    class="{manifesto_open &&
      'text-black'} absolute top-0 flex flex-col w-full h-screen items-center justify-center space-y-8 px-4 xl:px-32"
  >
    <OnMount>
      <h1 class="z-40" in:fade={{ duration: 1000, delay: 0 }}>
        Design is more than beauty.
      </h1>
      <h1 class="z-40" in:fade={{ duration: 1000, delay: 1000 }}>
        Engineering is more than science.
      </h1>
    </OnMount>
  </div>

  {#if manifesto_open}
    <div
      class="text-black flex flex-col w-full h-screen items-center justify-center space-y-8 px-4 xl:px-32 z-40"
    >
      <h1>We know diversity determines innovative futures.</h1>
      <h1>We know design engineering can change the world.</h1>
    </div>

    <div
      class="text-black flex flex-col w-full h-screen items-center justify-center space-y-8 px-4 xl:px-32 z-40"
    >
      <h1>We are tomorrow's designers, engineers, makers and thinkers.</h1>
      <h1>We think freely; paving new ways of thinking and doing.</h1>
    </div>

    <div
      class="text-black flex flex-col w-full h-screen items-center justify-center space-y-8 px-4 xl:px-32 z-40"
    >
      <h1>We engineer the future; incubating tomorrow's change-makers.</h1>
      <h1>
        We are fearlessly optimistic; radical futures need radical action.
      </h1>
    </div>

    <div
      class="text-black flex flex-col w-full h-screen items-center justify-center space-y-8 px-4 xl:px-32 z-40"
    >
      <h1>We are defined by innovation.</h1>
      <h1>We are defining design engineering.</h1>
    </div>
  {/if}
</div>

<style>
  .circle:hover {
    transform: scale(0.9);
    transition-duration: 0.01s;
    transform-origin: 50% 75%;
  }

  .circ {
	transform: scale(1);
	animation: pulse 3s infinite;
  animation-delay: 2500ms;
  transform-origin: 50% 75%;
  }

  @keyframes pulse {
	0% {
		transform: scale(1);
	}

	60% {
		transform: scale(1.15);
	}

	100% {
		transform: scale(1);
	}
}

.stop-pulse {
    animation: none !important;
}

</style>
