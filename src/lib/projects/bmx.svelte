<script>
import CaptionedImage from "./CaptionedImage.svelte";
</script>

<div
  class="flex flex-col xl:flex-row space-y-10 xl:space-y-0 xl:space-x-10 items-center justify-center p-10"
>
  <div class="relative xl:mt-0">
    <img
      src="/projects/bmx/bmx.svg"
      alt="BMX Project Logo"
      class="absolute inset-0 w-16 xl:w-32 xl:-translate-x-1/4 -translate-x-[30%] -translate-y-1/4 z-10"
    />
    <CaptionedImage
      src="/projects/bmx/bmx.png"
      alt="BMX Project"
      caption="This is the BMX project caption"
      classString="w-full max-h-[411px] object-cover"
    />
  </div>
  <div
    class="flex flex-col space-y-5 max-w-[600px] xl:px-0 xl:max-w-[400px] h-full justify-center"
  >
    <div class="flex flex-col space-y-2.5">
      <h1 class="text-4xl text-right" style="color: #cc0000;">Bmx</h1>
    </div>

    <div class="flex flex-col space-y-2.5">
      <h1 class="text-4xl text-right italic" style="color: #cc0000;">PRJ</h1>
    </div>

    <div class="flex flex-col space-y-2.5">
      <h2 class="text-4xl">Engineering</h2>
    </div>

    <div class="flex flex-col space-y-5">
      <h3 class="text-lg">Brief</h3>
      <p class="text-justify text-sm">
        Seventies BMX approached us to explore a new solution for BMX hubs.
        Current Hubs are not durable enough, too expensive, and restrict certain
        tricks such as crank flips.
      </p>
      <h3 class="text-lg">Impact</h3>
      <p class="text-justify text-sm">
        By working directly with BMX athletes and exploring the technologies
        currently available, we were able to create 2 new hubs SHIFTA and
        ELEKTRA. Designs that are lighter, more durable, less inhibiting on the
        riding experience, and are at the forefront of technological capability.
        About to undertake production, SHIFTA and ELEKTRA are pushing the
        boundaries of the sport and giving ultimate freedom to riders to express
        themselves.
      </p>
    </div>
  </div>
</div>
