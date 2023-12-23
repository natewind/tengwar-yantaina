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
…: qdash     (Â)

space: self
 nbsp: self
```

## Unmapped

```
   alda: (m)
   ampa: (r)
   anca: (f)
   ando: (2)
   anga: (s)
   anna: (h)
   anto: (4)
   arda: (u)
   esse: (k)
  halla: (½)
 hwesta: (c)
hyarmen: (9)
 nwalme: (b)
  romen: (7)
   sule: (3)
  umbar: (w)
  ungwe: (x)
  unque: (v)
    ure: (.)
  yanta: (l)

 esse_nuquerna: (,)
silme_nuquerna: (i)

telco: (`)
  ara: (~)

 right_s: (+)
bottom_s: (|)

narrow_tilde: (;)
  wide_tilde: (:)
middle_tilde: (°)

 narrow_y: (Í)
   wide_y: (Ì)
 middle_y: (´)
shifted_y: (Î)

 narrow_[aeiou]: ([ERTYU])
   wide_[aeiou]: ([#$%^&])
shifted_[aeiou]: ([DFGHJ])
carried_[aeiou]: ([CVBNM])
```

## Groups

```js
short_vowel = { a, e, i, o, u }
 long_vowel = { á, é, í, ó, ú }

vowel = short_vowel + long_vowel

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

digit = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, j, z }
```

## Substitutions

*Outdated (see `transcriber.fea`)*

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

### Consonant clusters

```
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
```

### Alternative forms

```
h([lr]) => halla
\bh     => hyarmen

   r([ry]?\vowel)  => romen
   s(\short_vowel) => silme_nuquerna
esse(\short_vowel) => esse_nuquerna

([tp])s =>  right_s
   (c)s => bottom_s
```

### Double consonants

```
([cfprt])\1 => narrow_tilde
   (romen)r => narrow_tilde
   ([mn])\1 =>   wide_tilde
      (l)\1 => middle_tilde
```

### Palatization

```
([ht]|hyarmen)y => narrow_y
        ([mn])y => wide_y
           (l)y => middle_y
             ry => romen + shifted_y
              y =>  anna + narrow_y
```

### Diphtongs

```
[aou]i => yanta + narrow_[aou]
[aei]u =>   ure + narrow_[aei]
```

### Vowels

```
                    [áéíóú] =>   ara + carried_[aeiou]
((hyarmen)narrow_y?)[aeiou] =>         shifted_[aeiou]
           (\narrow)[aeiou] =>          narrow_[aeiou]
             right_s[aeiou] =>          narrow_[aeiou] + right_s
             (\wide)[aeiou] =>            wide_[aeiou]
                    [aeiou] => telco + carried_[aeiou]
```

### Punctuation

```
apostrophe (’)          => empty ()
[space|nbsp](mdash (—)) => empty ()
...                     => …
```
