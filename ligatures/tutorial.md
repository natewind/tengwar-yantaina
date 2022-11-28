1. Open font in FontForge.
2. Save as project (SFD).
3. Encoding > Add Encoding Slots > OK (1)
4. Right Click on the glyph > Glyph Info > Glyph Name = [exclam_equal] > OK
5. Element > Font Info > Lookups
	1. Add Lookup
		1. Type = Ligature Substitution
		2. New Feature > Type = Standard Ligatures
		3. Lookup Name = ['liga' Coding Ligatures]
	2. Add Subtable > Set Name > OK
		1. Ligature Glyph Name = [exclam_equal]
		2. Source Glyph Name = [exclam(!) equal(=)]
		3. OK
	3. OK > Save
6. Build the glyph
	1. Edit > Copy From > TrueType Instructions [✓]
	2. Copy-paste the base glyph to the new one
	3. Double Click on the glyph > Edit
	4. Move the Ligature Caret if necessary
	5. Hints > Edit Instructions
		1. Learn hinting!
		2. Edit / Add / Remove > OK
	6. Save > Close
7. Save
8. Test: Window > New Metrics Window
9. File > Generate Fonts
