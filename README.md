# Tengwar Yantaina

This is a modification of Tengwar Sindarin by Daniel Smith that utilizes OpenType substitutions to automate transcription in the [Classical Mode](http://www.at.mansbjorkman.net/teng_quenya.htm). Just apply the font to any Quenya text and see the magic!

## Tips

* S is always denoted by *silme*, since there’s no way for a font to understand etymology. If you want *súle* instead, you have to spell out TH.
* *Noldo* is not used anywhere by default, for the reason above and because no Classical Mode samples of it are known. Type Ñ if you want it anyway.
* To denote duodecimal 10 and 11, J and Z are used, since they’re the only letters that never appear in Latin transcriptions of Noldorin Quenya.
* You don’t need to change text direction for numbers: it’s done automatically via directional marks.

## TODO

* [ ] [?] Reorder glyphs
* [ ] Create groups
* [ ] Implement substitutions
* [ ] Recheck the issues when opening the original font
	* [ ] `Ignoring 'PCLT' PCL 5 data table`
	* [ ] `Windows will reject fonts with an OS/2 version number of 0`
* [ ] Edit metadata
* [ ] Export font

___

I plan to add double-stroked capital letters, but there are two problems:

* It’s not trivial to copy glyphs to another font with TrueType instructions preserved (hinting and stuff)
* None of the original four font variations have *tehtar* for capital letters (they need to be slightly bigger and higher)

To solve the first issue, I could just use a separate fallback font, but if anyone knows how to do it properly, please let me know. Or if you’re willing to create the *tehtar* variations (I’m not a real type designer).
