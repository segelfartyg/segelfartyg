<script lang="ts">

  import BriefCaseItem from "./BriefCaseItem.svelte";
  import { writable } from "svelte/store";

export let briefItemPositionOffsetX: number = 10;
export let briefItemPositionOffsetY: number = 10;

interface BriefItem {
    offsetX: string,
    offsetY: string
}

export let TotalBriefItems: {offsetX: number, offsetY: number, color: string}[] = [{
    offsetX: 0,
    offsetY: 0,
    color: "#316fce"
}];

let briefOffsetX = 0;
let briefOffsetY = 0;

let colors: string[] = [
    "#d02f3c",
    "#411be4",
    "#40bf5c",
    "#316fce",
    "#dc23b7",
    "#5b6ca4",
    "#e3e2e2"
]

for(let i = 0; i < 25; i++){
    briefOffsetX -= 10;
    briefOffsetY += 0;
    TotalBriefItems.push({ offsetX: briefOffsetX, offsetY: briefOffsetY, color: colors[Math.floor(Math.random() * 7)] })
}


</script>
<div class="briefCase">
   {#each TotalBriefItems as BriefItem} 
   <BriefCaseItem briefItemPositionOffsetX={BriefItem.offsetX} briefItemPositionOffsetY={BriefItem.offsetY} color={BriefItem.color}></BriefCaseItem>
   {/each}
</div>

<style>

</style>