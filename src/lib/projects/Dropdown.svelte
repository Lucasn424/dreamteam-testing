<script>
    export let buttonText = 'Toggle Dropdown';
    export let dropdownContent = '';
  
    let isOpen = false;
  
    function toggleDropdown() {
      isOpen = !isOpen;
    }
  </script>
  
  <style>
    .dropdown-content {
      display: none;
    }
  
    .dropdown-content.open {
      display: block;
    }
  </style>
  
  <button on:click={toggleDropdown}>{buttonText}</button>
  
  {#if isOpen}
    <div class="dropdown-content open">
      <p>{dropdownContent}</p>
    </div>
  {/if}