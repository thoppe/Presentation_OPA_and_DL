# md2reveal
python tool to convert extended markdown to [reveal.js](https://github.com/hakimel/reveal.js). `make demo` builds a reveal.js version of this text.

## slide control
	====  horizontal slide
	====* vertical slide
	====+ slide pause
	==== [name] named slide, useful for linking
    ====* <<transistion:none>> custom slide transistions

## text formatting
    #      h1     (headers) 
    ##     h2     (headers) etc for h6
	*text* strong (bold)
	_text_ emph   (italics)
	$LaTeX$ LaTeX rendered to SVG
	       four spaces or \t is a code block

## images
	!(image src)[optional image link] <<options>>
    
Image options can be combined with a semicolon, all options listed below

	!(foo.svg) <<width:400; height:200; transparent>>


## links
	[link text](link src)

## Reference footnotes
	&& Footnote text
	
