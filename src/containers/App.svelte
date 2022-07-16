<script>
  let time = 0;

  let counter = 0;
  let count = 0;

  let text = "";

  function seconds() {
    setTimeout(function () {
      time++;
      console.log(time);
      return time, seconds();
    }, 1000);
  }

  function one() {
    counter++;
    console.log("C: " + counter);
  }

  function two() {
    count++;
  }
</script>

<div class="contend">
  <section>
    <h1>Instrucciones:</h1>
    <p on:mouseleave|once={seconds}>
      estas instruciones son solo una perdida de tiempo...
    </p>

    {#if time >= 10}
      <p>
        y solo de muestan el uso del atributo "on:mouseleave" en <a
          href="https://svelte.dev/tutorial/dom-events    ">svelte.js</a
        >.
      </p>
      <div class="grid">
        <div on:click|once={one}>haz click plis...</div>

        {#if counter >= 1}
          <div>
            <button on:dblclick|once={one}>haora haz doble clik</button>
          </div>
        {/if}

        {#if counter >= 2}
          <div on:drag|once={one}>
            arrastrame<progress min="0" max="5" value={counter} />
          </div>
        {/if}

        {#if counter >= 3}
          <div>
            escribe en el input <input
              type="text"
              on:focus|once={one}
              bind:value={text}
            />
          </div>
        {/if}

        {#if counter >= 4}
          <div>
            <p>pasa sobre el texto que escribiste:</p>
            <p on:mousemove|once={one}>{text}</p>
          </div>
        {/if}

        {#if counter >= 5}
          <div on:mousemove|once={one}>
            <p>
              mira: tu score: {time} y baja usando solo el escrold "te estare vigilando"
            </p>
          </div>
        {/if}

        {#if counter >= 6}
          {#if counter >= 6}
            <div class="down" on:mousemove|once={one}>
              <p>baja mas</p>
            </div>
          {/if}

          {#if counter >= 7}
            <div class="down" on:mousemove|once={one}>
              <p>mas</p>
            </div>
          {/if}

          {#if counter >= 8}
            <div class="down" on:mousemove|once={one}>
              <p>ya casi lleguas</p>
            </div>
          {:else}
            <div class="down"><h1>hiciste trampa regresate por donde viniste</h1></div>
          {/if}

        {/if}

        {#if counter >= 9}
          <div>
            <button on:click={two} on:dblclick|once={one}>
              <p>por ultimo haz 100 clicks</p>
              <progress min="0" max="100" value={count} />
            </button>
          </div>
        {/if}
        {#if count >= 100}
          <div><h2>este es el fin total de tiempo perdido: {time}s</h2></div>
        {/if}
      </div>
    {/if}
  </section>
</div>

<style>
  :global(body) {
    background-color: #676778;
    color: white;
  }

  p {
    font-size: 1.5rem;
    display: block;
  }

  .grid {
    display: grid;
    grid-gap: 5rem;
  }

  .down {
    background-color: #676778;
    color: white;
    font-size: 3rem;
    display: block;

    border: 10px solid  rgb(124, 124, 249);
    border-radius: 4px;
    padding-top: 200vh;
    padding-bottom: 200vh;
  }

</style>
