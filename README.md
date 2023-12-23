# Tengwar Yantaina

This is a modification of Tengwar Sindarin by Daniel Smith that includes an automatic transcriber for [Classical Mode](https://at.boktypografen.se/teng_quenya.htm), built on OpenType substitutions. Just apply the font to any Quenya text and observe the magic!

Bug reports are welcome.

**[Download](https://github.com/natewind/tengwar-yantaina/raw/master/yantaina.otf)**

## Tips

* S is always denoted by *silme*, since there’s no way for a font to understand etymology. If you want *súle* instead, you have to spell out TH.
* *Noldo* is not used anywhere by default, for the reason above and because no Classical Mode samples of it are known. Type Ñ if you want it anyway.
* To denote duodecimal 10 and 11, J and Z are used, since they’re the only Latin letters that never appear in transcriptions of Noldorin Quenya.

## TODO

* [ ] Test & fix stuff
* [ ] Consider using appropriate OpenType features instead of just `liga`
* [ ] Combine glyphs for long vowels & diphtongs to simplify GSUB (without breaking hinting)
* [ ] Import issues
	* [ ] `Ignoring 'PCLT' PCL 5 data table`
	* [ ] `Windows will reject fonts with an OS/2 version number of 0`
* [ ] Export issues
	* [ ] Em size should be 1000, not 2048 for OpenType (not an error though)
	* [ ] Self-intersecting `eleven`
	* [ ] Missing BlueValues entry
* [ ] Double-stroked capital letters

### Capital Letters

I plan to add double-stroked capital letters, but there are two problems:

* It’s not trivial to copy glyphs to another font with hinting (and other similar data?) preserved
* None of the original four typefaces have *tehtar* for capital letters (they need to be slightly bigger and higher)

To solve the first issue, I could just use a separate fallback font, but if anyone knows how to do it properly, please let me know. Or if you’re willing to create the *tehtar* variations (I’m not an actual type designer).
