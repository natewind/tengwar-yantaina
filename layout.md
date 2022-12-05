# Layout

## Mapped

### Tengwar

```
c: calma  (a)
f: formen (e)
h: aha    (d)
l: lambe  (j)
m: malta  (t)
n: numen  (5)
ñ: noldo  (g)
p: parma  (q)
q: quesse (z)
r: ore    (6)
s: silme  (8)
t: tinco  (1)
v: vala   (y)
w: vilya  (n)
```

### Digits

```
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
```

### Punctuation

```
.: qcolon    (-)
,: qdot      (=)
;: qdot      (=)
:: qtridot   (ˆ)
!: qexclam   (Á)
?: qquestion (À)
-: qhyphen   (\)
—: qtridot   (ˆ)
(: qparen    (›)
): qparen    (›)
“: qlquote   («)
”: qrquote   (»)

space: self
 nbsp: self
```

## Unmapped

```
hyarmen: (9)
 hwesta: (c)
   alda: (m)
  umbar: (w)
   ampa: (r)
   anca: (f)
   ando: (2)
  ungwe: (x)
   anga: (s)
  unque: (v)
   anto: (4)
 nwalme: (b)
   arda: (u)
   esse: (k)
   sule: (3)
```

## Groups

```js
narrow =
{
	c, f, h, l, p, q, t, v, w,
	alda, romen, arda, hwesta, sule,
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

### Normalization

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
```

**TODO: Recheck & reorder**

```
\bh   => hyarmen
  hw  => hwesta
  ld  => alda
  mb  => umbar
  mp  => ampa
  nc  => anca
  nd  => ando
  ngw => ungwe
  ng  => anga
  nq  => unque
  nt  => anto
\bnw  => nwalme
  rd  => arda
  ss  => esse
  th  => sule

h([lr]) =>  halla   (½)
([tp])s =>  right_s (+)
   (c)s => bottom_s (|)

r(r?y?[aeiou]) => romen          (7)
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
             ry => romen (7) + shifted_y (Î)
              y =>  anna (h) + narrow_y (Í)

# Diphtongs

[aou]i => yanta (l) + narrow_[aou] ([EYU])
[aei]u =>   ure (.) + narrow_[aei] ([ERT])

# Vowels

                    [áéíóú] =>   ara (~) + carried_[aeiou] ([CVBNM])
((hyarmen)narrow_y?)[aeiou] =>             shifted_[aeiou] ([DFGHJ])
           (\narrow)[aeiou] =>              narrow_[aeiou] ([ERTYU])
             right_s[aeiou] =>              narrow_[aeiou] ([ERTYU]) + right_s
             (\wide)[aeiou] =>                wide_[aeiou] ([#$%^&])
                    [aeiou] => telco (`) + carried_[aeiou] ([CVBNM])
```

### Digits

```
\b(\digits) => rtl_override  (U+202E)
(\digits)\b => pop_direction (U+202C)
```

### Punctuation

```
apostrophe (’)          => empty ()
[space|nbsp](mdash (—)) => empty ()
...                     => qdash (Â)
```
