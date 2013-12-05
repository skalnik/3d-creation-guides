# OpenSCAD

I'm not going to lie. OpenSCAD can be a big pain. It is extremely nice for programatic things however.


## Installation

You'll need to grab OpenSCAD first from their website: [http://www.openscad.org/downloads.html](http://www.openscad.org/downloads.html). Once downloaded and installed, you'll launch it and see something like this:

![empty preview](https://dl.dropboxusercontent.com/s/12hskiaph85gysv/2013-12-04%20at%203.18%20PM%202x.png)

Once you've written some code (Check [Syntax](#syntax) below), hit `F5` to go ahead and compile it. Errors may show up:

![errors](https://dl.dropboxusercontent.com/s/ch6ca0n7e6ls4vc/Screen%20Shot%202013-12-05%20at%2010.23.24%20AM%202x.png)

They're not always the most clear, but they're worth a read to give you an idea of whats going wrong. However if all goes well, you'll get a nice preview:

![preview](https://dl.dropboxusercontent.com/s/35d60esb0irxibo/Screen%20Shot%202013-12-05%20at%2010.24.37%20AM%202x.png)

You can manipulate it with left click to rotate, right click to translate. If all looks well you'll want to export an STL for printing:

![export](https://dl.dropboxusercontent.com/s/3xdj6gahqhwjjlp/Screen%20Shot%202013-12-05%20at%2010.26.02%20AM%202x.png)

## Syntax

I find the best way to write OpenSCAD is to just play with it and follow the documentation like crazy. The documentation [on the OpenSCAD wiki](http://en.wikibooks.org/wiki/OpenSCAD_User_Manual/The_OpenSCAD_Language) is kept up to date and worth looking at. Here are a few examples to show syntax and point out some useful features.

First, spelling your name with some premade glyphs:


```
word = "SKALNIK";

for ( i = [ 0 : len(word) - 1] )
{
        translate([12*i, 0, 0])
                import(str("glyphs/", word[i], ".stl"));
}
```

Assuming you have a directory called `glyphs` with STL files for each of these letters (like these: https://github.com/make-me/glyphs), this will take letter, import the STL, and translate each one 12mm further to the right to spell whatever you'd like.

STL importing is very useful and I've used it multiple times. Often I generate something more complex in another program (a logo, glyphs, etc), and then use OpenSCAD to add/subtract them from existing models.

Another useful feature is modules. You can define small bits of things and name them as a module to use them later. For example:


```
module logo() {
        scale([.7, .7, 1]) {
                import("play-logo.stl");
        }
}
```

This imports the `play-logo.stl` file and scales it. Later in the OpenSCAD code I can just call `logo();` and it will execute this snippet of code, allowing me to manipulate it further with other objects, but treating it as one.
