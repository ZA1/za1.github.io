---
title: Blockchain 
image: blockchain.jpg
subTitle: In this post I look at what a blockchain actually is and dig much deeper into the tech.
---
So first of all, what is a blockchain? A block chain is a list of records called "blocks" that are linked together sequentially. Each block is contains the hash of the previous blocks records. This makes the "chain" [immutable](terms#immutable) and can only be added to.

{.img-thumbnail .text-center}
:::
<svg viewBox="0 0 620 140">
  <defs>
    <marker id="arrow" viewBox="0 0 10 10" refX="5" refY="5"
        markerWidth="6" markerHeight="6"
        orient="auto-start-reverse">
      <path d="M 0 0 L 10 5 L 0 10 z" />
    </marker>
  </defs>

  <g id="block" transform="translate(50 10)">
    <rect x="0" y="0" width="100" height="100" style="fill: none; stroke: blue; stroke-width: 1" />
    <rect x="0" y="0" width="100" height="20" style="fill: none; stroke: blue; stroke-width: 1" />
    <text x="10" y="15">Hash()</text>
    <path d="M 0 50 h -10 v -40 h -35" marker-end="url(#arrow)" style="fill: none; stroke: #000; stroke-width: 1" />
  </g>
  
  <use xlink:href="#block" transform="translate(150 0)"></use>
  <use xlink:href="#block" transform="translate(300 0)"></use>
  <use xlink:href="#block" transform="translate(450 0)"></use>
</svg>
:::

After this explanation it leaves some topics we need to explore:
1. Hashing