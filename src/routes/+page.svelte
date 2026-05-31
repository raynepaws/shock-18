<script lang="ts">
  import shock from "$lib/assets/unc.png";
  import shockSpin from "$lib/assets/unc.gif";
  import shockSquish from "$lib/assets/squish.gif";
</script>

<style>
  :root {
    --shock: #f45ab9;

    --raynebow: linear-gradient(90deg, #f00, #ff0, #0f0, #0ff, #00f, #f0f, #f00)
  }
</style>

<div style="display: flex;">
  <img src={shockSpin} alt="shock unc">
  <h1 style="transform-style: preserve-3d; flex-grow: 1; font-size: 5rem; transform: perspective(100px) rotate3d(1, 0, 0, 15deg); text-align: center; background-image: var(--raynebow); background-clip: text; color: transparent;">happy birthday<br>Shock 59!</h1>
  <img src={shockSpin} alt="shock unc">
</div>
<p>hi shock it's me rayne! i made this website for you for your 18th birthday!</p>
<div style="display: flex; align-items: center;">
  <img src={shockSquish} alt="shock unc">
  <blockquote>
    "Woah no way what a cool website!!!" - you
  </blockquote>
</div>
