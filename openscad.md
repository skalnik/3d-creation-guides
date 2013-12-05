# OpenSCAD

I'm not going to lie. OpenSCAD can be a big pain. It is extremely nice for programatic things however.

You'll need to grab OpenSCAD first from their website: [http://www.openscad.org/downloads.html](http://www.openscad.org/downloads.html). Once downloaded and installed, you'll launch it and see something like this:

![empty preview](https://dl.dropboxusercontent.com/s/12hskiaph85gysv/2013-12-04%20at%203.18%20PM%202x.png)

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

Assuming you have a directory called "glyphs" with STL files for each of these letters (like these: https://github.com/make-me/glyphs), this will take letter, import the STL, and translate each one 12mm further to the right to spell whatever you'd like.

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
