<script>
  export let src;
  export let alt;
  export let caption;
  export let classString = '';
  let isHovered = false;

  function handleFocus() {
    isHovered = true;
  }

  function handleBlur() {
    isHovered = false;
  }
</script>

<style>
  .container {
    position: relative;
    display: inline-block;
  }

  .caption {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.7);
    color: white;
    padding: 8px;
    text-align: center;
    font-size: 14px;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.2s;
  }

  .show-caption {
    opacity: 1;
  }
</style>

<div
  class="container {classString}"
  on:mouseover={handleFocus}
  on:mouseout={handleBlur}
  on:focus={handleFocus}
  on:blur={handleBlur}
  tabindex="0"
>
  <img {src} {alt} />
  <div class="caption" class:show-caption={isHovered}> {caption} </div>
</div>