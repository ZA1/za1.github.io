---
title: Blockchain 
image: blockchain.jpg
subTitle: In this post I look at what a blockchain actually is and dig much deeper into the tech.
---

By itself a block chain is a very simple concept. So first of all, what is a blockchain? A block chain is a list of records called "blocks" that are linked together sequentially. A block consists of a header and some data. The important part is that to add a valid block you add the hash of the previous block to the data of the current block and add the hash to the header. This is why it is called a chain, because each block references the previous block.

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
{: .img-thumbnail .text-center}

We will dig into hashes in a later post, but for now think of hash as a calculation that takes any set of data and produces a unique number that represents that data. If you give it the same data it produces the same number, but if you change even a single bit of the input you get a different answer. To check if a block has been changes is as simple as calculating the has for that block and checking that it matches the header.

The important part is that it is only ever possible to add a new block to the end of the chain and never update any of the blocks. This [immutable]({% post_url 2010-07-21-name-of-post %}#immutable) nature of the block chain is what ensures that anyone can verify that the data contained in the chain has not been tampered with.

This is a nice concept, but by it's self a blockchain is not very useful. As we will see, this is just one powerful piece of the puzzle in creating a _decentralized_ system.

### Show me the code

``` cs
public class Block
{
  public static Block GenisisBlock { get; } = new Block(DateTime.Now, new byte[] { });

  public DateTime Date { get; }
  public Block PreviousBlock { get; }
  public byte[] Hash { get; }

  public byte[] Data { get; }

  public Block(DateTime date, Block previousBlock, byte[] data)
  {
    Date = date;
    PreviousBlock = previousBlock;
    Data = data;

    Hash = ComputeHash();
  }

  private Block(DateTime date, byte[] data)
  {
    Date = date;
    // Start with a number of our chosing
    Hash = new byte[]{ 10, 9, 8, 7, 6, 5, 4, 3, 2, 1 };
    Data = data;
  }

  public byte[] ComputeHash()  
  {  
    SHA256 sha256 = SHA256.Create();
    var input = PreviousBlock.Hash.Concat(Data).ToArray();
    return sha256.ComputeHash(input);
  }

  public bool IsValid()
  {
    return GenisisBlock == this || PreviousBlock.IsValid() && Hash.SequenceEqual(ComputeHash());
  }
}
```
