# Encounter card unrolling

See [Card Quantity](../cardquantity/CardQuantity.md) for full details on how Zoop calculates card quantities.

If you want Zoop to create multiple copies of a card when exporting you can take advantage of the encounter set number field in SE. Here’s an example

![image](https://github.com/mickeytheq/ZoopDocs/assets/42071167/7b971db5-836a-471a-8264-a8b310cb4309)

In this example the encounter set number on the card will look like this

![image](https://github.com/mickeytheq/ZoopDocs/assets/42071167/25b173e8-c8fe-4fc0-b2bb-1b2c69416c22)

Zoop will create two copies of the card. This will only work if you use the format ```<number><hyphen><number>```. Any other content will result in a single copy of the card. You do not have to specify the second number (which indicates the total number of cards in in the encounter set) for this to work.
