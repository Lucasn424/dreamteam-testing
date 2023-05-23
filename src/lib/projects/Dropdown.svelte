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
  
    .dropdown-content h3 {
      font-size: 1.125rem; /* equivalent to text-lg */
    }
  
    .dropdown-content p {
      text-align: justify;
      font-size: 0.875rem; /* equivalent to text-sm */
    }
  </style>
  
  <button on:click={toggleDropdown}>{buttonText}</button>
  
  {#if isOpen}
    <div class="dropdown-content open">
      <h3 class="text-lg">{dropdownContent.title}</h3>
      <p class="text-justify text-sm">{dropdownContent.text}</p>
    </div>
  {/if}