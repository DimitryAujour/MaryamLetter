<script>
    import { fade, fly } from 'svelte/transition';
    import { elasticOut } from 'svelte/easing';
  
    export let receiver = "John Doe";
    export let message = "Hello! This is the content of your letter.";
  
    let isOpen = false;
  
    function toggleLetter() {
      isOpen = !isOpen;
    }
  </script>
  
  <div class="letter-container">
    {#if !isOpen}
      <div class="closed-letter" in:fade={{ duration: 300 }}>
        <h2>{receiver}</h2>
        <button on:click={toggleLetter}>Open the letter</button>
      </div>
    {:else}
      <div class="open-letter" in:fly={{ y: 200, duration: 500, easing: elasticOut }}>
        <div class="paper">
          <p>{message}</p>
        </div>
        <button on:click={toggleLetter}>Close the letter</button>
      </div>
    {/if}
  </div>
  
  <style>
    .letter-container {
        font-size: 1.3rem;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
  
    .closed-letter, .open-letter {
      background-color: #f0f0f0;
      padding: 20px;
      border-radius: 10px;
      text-align: center;
    }
  
    .closed-letter {
      width: 300px;
      height: 30%;
    }
  
    .open-letter {
      width: 300px;
    }
  
    .paper {
      background-color: white;
      padding: 20px;
      margin-bottom: 20px;
      border-radius: 5px;
    }
  
    button {
      background-color: greenyellow;
      border: none;
      color: white;
      padding: 10px 20px;
      text-align: center;
      text-decoration: none;
      display: inline-block;
      font-size: 2rem;
      margin: 4px 2px;
      cursor: pointer;
      border-radius: 5px;
    }
  </style>