# Color spaces (focusing on RGB and CMYK)

Though this text is about "**Color spaces**", but as is evident from the title i will focus on 2 color spaces, RGB (**R**ed, **G**reen, **B**lue) and CMYK (**C**yan, **M**agenta, **Y**ellow, **K**ey (black)) for reasons relating to their usage in common domains of art and design.

So firstly, to define a color space in layman understand it as large set of vector spaces where the vectors along the unit vectors denote the individual components of that vector space (color model). This is a somewhat accurate description of a color space to get to working. Being completely accurate would be that a color space is just an abstract system created to denote colors in a certain constrained environment like a device for example.

Color model and color spaces are pretty much interchangeable words in most cases but in strict sense color models are a subset of color spaces.

Now focusing on **RGB** and **CMYK** ~

Firstly **RGB color model** follows an additive color mixing model. This based basically around the idea that RGB is used digitally and we know blending in simple sense is -

> C_mix = α*C_1 + β*C_2   
> 
> (add ? additive ? makes sense...)

which pretty much explains the additive color mixing model, as color mixing in computer graphics is mainly based on color blending.  

As of **CMYK color model**, a subtractive color mixing model is utilised. To understand this, first realize that color in real world is best illustrated by CMYK model

For some more insight understand that unlike real world, **in digital displays the light actually comes to us** instead of the reflecting phenomena in real world. So, when you bring togther red, yellow and blue color in digital devices (bring together here is analogous to mixing colors) you get white.

BUT, guess what you get when you mix these using crayons/water-colors/acrylic-colors (you choose). You get **brown**. Get it now the subtractive and additive models.

### Now why is this important, specially for artists ?

Well, consider you create some graphic design on a computer and export it in the sRGB model. Then you print it to maybe showcase it or something.

Then it hits you when you see the printed copy. The colors look kind of inconsistent to in your digital copy. Reason being that your printer is setup colors using the mechanical way of mixing colors. So for a RGB color config, in a world that accepts CMYK we get the inconsistent color.

This is why you always export to CMYK for graphics that need to be printed out. They would be consistent to how colors work in the real world.

You can actually see this systems existence in real world. Next time you read a newspaper, check at the page bottom you will see the `CMYK` text and 4 colored circles denoting -
"Cyan", "Magenta", "Yellow" and "Key" (black).

