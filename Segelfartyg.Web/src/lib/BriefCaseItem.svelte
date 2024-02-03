<script lang="ts">
  export let briefItemPositionOffsetX: number;
  export let briefItemPositionOffsetY: number;
  export let color: string;
  let animationDistance = 0;
  let hoverDistance = -50;
  let continueAnimating = true;

  function onHover(e: any) {
    if (animationDistance >= -50 && continueAnimating) {
        console.log(continueAnimating);
        console.log(animationDistance)
      window.requestAnimationFrame(step);
    }

    function step() {
      animationDistance -= 2.5;
      if (animationDistance >= -50 && continueAnimating) {
        window.requestAnimationFrame(step);
      }
    }
  }

  function onDeHover(e: any) {
 
    continueAnimating = false;
    console.log(continueAnimating)
    if (animationDistance <= 0) {
      window.requestAnimationFrame(animateDown);
    }

    function animateDown() {
      animationDistance += 1;
      if (animationDistance <= 0) {
        window.requestAnimationFrame(animateDown);
        
      }
      continueAnimating = true;
    }
  }
</script>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<!-- svelte-ignore a11y-mouse-events-have-key-events -->
<div
  on:mouseover={onHover}
  on:mouseleave={onDeHover}
  class="briefCaseItem"
  style="--xOffset:{briefItemPositionOffsetX +
    'px'};--yOffset:{briefItemPositionOffsetY +
    'px'};--briefColor:{color};--hoverDistance:{briefItemPositionOffsetY +
    hoverDistance +
    'px'};transform:translateY({animationDistance}px)"
></div>

<style>
  .briefCaseItem {
    margin-left: var(--xOffset);
    /* margin-top:var(--yOffset); */
    transform: translateY(var(--yOffset));
    height: 200px;
    width: 300px;
    border: solid black 5px;
    filter: drop-shadow(1px 1px 1px black);
    background: var(--briefColor);
    /* background: white; */
    position: absolute;
    border-radius: 10px;
  }

</style>
