I'd like to replace Android phones' Li-ion batteries with DC DC step down converters (from 5V to 3.7V) using USB type-C chargers/ports as input (and use the phones as headless servers on WiFi).

I'm comfortable with removing the actual Li-ion cells from the built-in battery packages and solder my 3.7V output onto the batteries' charging panels - making use of the connectors to the phones' main PCBs.

I'd like to manufacture these via JLCPCB, optimizing for cost, using basic components wherever I can get away with them.

I uploaded the converter's datasheet [[here][1]]. I followed the typical application layout on page 1 and added my own edits in red on pages 10-11. I picked the capacitors (22uF are `25V X5R ±10%` while the 100nF is `50V X7R ±10%`) based on the table. The inductor is `22mΩ 4.7uH 6.5A 6A ±20% SMD,7.3x6.8mm Inductors (SMD) ROHS`.


# My schematics

Arranged similarly as seen on page 1.

[![schematics][2]][2]

Will this be able to power most Android phones even during sudden peaks - e.g. CPU or WiFi?

# PCB

The outer size of the board was measured as 11.1 x 22.5mm and the 5 pieces of 100x100mm panels (at JLCPCB) should yield 5x9x4 pieces (leaving 2x5mm strips on the sides for manufacturing holes). 

[![F. Cu layer][3]][3]
[![B. Cu layer][4]][4]
[![3D top view][5]][5]


  [1]: https://mega.nz/file/cMBjjTBZ#Cbj150NFu8j_5WNAerRJANiM3nzMNcL_I3tFo9oOCWY
  [2]: https://i.sstatic.net/YF2qK0lx.png
  [3]: https://i.sstatic.net/zOVD7IV5.png
  [4]: https://i.sstatic.net/MLt93PpB.png
  [5]: https://i.sstatic.net/tCvsdMmy.png
