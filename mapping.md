# Mapping

## Characters

```
# Tengwar

c: calma  (a)
f: formen (e)
h: aha    (d)
l: lambe  (j)
m: malta  (t)
n: númen  (5)
ñ: noldo  (g)
p: parma  (q)
q: quesse (z)
r: óre    (6)
s: silme  (8)
t: tinco  (1)
v: vala   (y)
w: vilya  (n)

# Digits

0: q0  (ð)
1: q1  (ñ)
2: q2  (ò)
3: q3  (ó)
4: q4  (ô)
5: q5  (õ)
6: q6  (ö)
7: q7  (÷)
8: q8  (ø)
9: q9  (ù)
j: q10 (ú)
z: q11 (û)

# Punctuation

.: qcolon    (-)
,: qdot      (=)
;: qdot      (=)
:: qtridot   (ˆ)
!: qexclam   (Á)
?: qquestion (À)
-: qhyphen   (\)
(: qparen    (›)
): qparen    (›)
“: qlquote   («)
”: qrquote   (»)

space: self
 nbsp: self
```

## Groups

```js
narrow =
{
	c, f, h, l, p, q, t, v, w,
	alda, rómen, arda, hwesta, súle,
	silme_nuquerna, esse_nuquerna,
	narrow_tilde, middle_tilde,
	narrow_y, middle_y, shifted_y,
	bottom_s
}

wide =
{
	m, n, ñ,
	ampa, anca, ando, anga, anto,
	nwalme, umbar, ungwe, unque,
	wide_tilde, wide_y
}

digits = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, j, z }
```

## Substitutions

**TODO: Recheck & reorder**

```
[A-Z]   => [a-z]
[ÁÉÍÓÚ] => [áéíóú]
[Ëë]    => e
Ñ       => ñ

k  => c
x  => cs
cw => q
qu => q

aa => á
ee => é
ii => í
oo => ó
uu => ú

\bh   => hyarmen (9)
  hw  => hwesta  (c)
  ld  => alda    (m)
  mb  => umbar   (w)
  mp  => ampa    (r)
  nc  => anca    (f)
  nd  => ando    (2)
  ngw => ungwe   (x)
  ng  => anga    (s)
  nq  => unque   (v)
  nt  => anto    (4)
\bnw  => nwalme  (b)
  rd  => arda    (u)
  ss  => esse    (k)
  th  => súle    (3)

h([lr]) =>  halla   (½)
([tp])s =>  right_s (+)
   (c)s => bottom_s (|)

r(r?y?[aeiou]) => rómen          (7)
s(y?[aeiou])   => silme_nuquerna (i)
ss([aeiou])    => esse_nuquerna  (,)

# Double consonants

([cfprt])\1 => narrow_tilde (;)
   ([mn])\1 =>   wide_tilde (:)
      (l)\1 => middle_tilde (°)

# Palatization

([ht]|hyarmen)y => narrow_y (Í)
        ([mn])y => wide_y (Ì)
           (l)y => middle_y (´)
             ry => rómen (7) + shifted_y (Î)
              y =>  anna (h) + narrow_y (Í)

# Diphtongs

[aou]i => yanta (l) + narrow_[aou] ([EYU])
[aei]u =>   úre (.) + narrow_[aei] ([ERT])

# Vowels

                    [áéíóú] =>   ára (~) + carried_[aeiou] ([CVBNM])
((hyarmen)narrow_y?)[aeiou] =>             shifted_[aeiou] ([DFGHJ])
           (\narrow)[aeiou] =>              narrow_[aeiou] ([ERTYU])
             right_s[aeiou] =>              narrow_[aeiou] ([ERTYU]) + right_s
             (\wide)[aeiou] =>                wide_[aeiou] ([#$%^&])
                    [aeiou] => telco (`) + carried_[aeiou] ([CVBNM])

# Punctuation

apostrophe (’)            => empty ()
[space|nbsp]? + mdash (—) => colon (:)
...                       => ddash (Â)

# Digits

\b(\digits) => rtl_override  (U+202E)
(\digits)\b => pop_direction (U+202C)
```
