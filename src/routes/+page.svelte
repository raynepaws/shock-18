<script lang="ts">
  import shockSpin from "$lib/assets/unc.gif";
  import { onMount } from "svelte";

  let tick = $state(0);
  let canvas = $state() as HTMLCanvasElement;

  interface Confetti {
    x: number;
    y: number;
    yv: number;
    color: number;
    weird: number;
  };

  onMount(() => {
    const context = canvas.getContext("2d");
    let confetti: Confetti[] = [];

    setInterval(() => tick += 1, 1);
    setInterval(() => confetti.push({
      x: (Math.random() * (innerWidth + 100)) - 50,
      y: -10,
      yv: Math.random() * 2.5 + 1,
      color: Math.floor(Math.random() * 255),
      weird: Math.random() * 2 * Math.PI
    }), 1);
    setInterval(() => {
      if (context) {
        context.clearRect(0, 0, canvas.width, canvas.height);
        let i = 0;
        while (confetti[i]) {
          context.fillStyle = `hsl(${confetti[i].color}, 100%, 50%)`;
          context.fillRect(confetti[i].x + Math.sin((tick / 70) + confetti[i].weird) * 30, confetti[i].y, 2, 8);
          confetti[i].y += confetti[i].yv;
          i++;
        }
      }
    }, 1);
  });
</script>

<svelte:head>
  <title>shock's 18th birthday</title>
</svelte:head>

<style>
  :root {
    --shock: #f45ab9;
    --raynebow: linear-gradient(90deg, #f00, #ff0, #0f0, #0ff, #00f, #f0f, #f00);
  }

  :global(body) {
    display: flex;
    align-items: center;
    width: 100vw;
    height: 100vh;
  }

  div {
    display: flex;
    flex-grow: 1;
    transform-style: preserve-3d;
  }

  h1 {
    transform-style: preserve-3d;
    flex-grow: 1;
    font-size: 5rem;
    transform: perspective(100px) rotate3d(1, 0, 0, 15deg);
    text-align: center;
    animation: rainbow 3s forwards linear infinite;
  }

  @keyframes rainbow {
    0% {
      color: #f00;
    }
    16% {
      color: #ff0;
    }
    33% {
      color: #0f0;
    }
    50% {
      color: #0ff;
    }
    67% {
      color: #00f;
    }
    84% {
      color: #f0f;
    }
    100% {
      color: #f00;
    }
  }

  canvas {
    position: absolute;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    pointer-events: none;
    z-index: -1;
  }
</style>

<div style:transform="perspective(100vw) rotate3d(0, 1, 0, {tick / 5}deg) rotate3d(0, 0, 1, {Math.sin((tick + 2) / 40) * 5}deg) rotate3d(1, 1, 1, {Math.cos(tick / 100) * 100}deg) rotate3d(1, 0, 1, {tick / -40}deg) rotate3d(0, 1, 0, {Math.sin((tick + 1) / 20)}deg)">
  <img src={shockSpin} alt="shock unc">
  <h1>happy birthday<br>Shock 59!!!</h1>
  <img src={shockSpin} alt="shock unc">
</div>
<canvas width="1000" height="1000" bind:this={canvas}></canvas>
