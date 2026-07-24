# Dasturlash terminlari lug'ati (Inglizcha → O'zbekcha)

Bu ro'yxat boshlang'ich tayanch nuqta, yakuniy qonun emas. Tarjima davomida yangi
termin uchraganda: (1) shu jadvaldan qidiring, (2) yo'q bo'lsa, quyidagi
"Qaror qabul qilish mezoni"ga asosan qaror qiling, (3) qarorni shu faylga
**qo'shib qo'ying**, shunda keyingi boblarda bir xillik saqlanadi. Bu fayl
loyihaning umri davomida o'sib boradi — uni har safar yangilang.

## Qaror qabul qilish mezoni

Inglizcha holicha qoldiring, agar:
- Termin Rust tilining o'ziga xos kalit tushunchasi bo'lsa va tarjimasi
  ma'noni yo'qotsa yoki chalkash bo'lsa (masalan, "ownership")
- Termin kod/kompilyator xabarlarida aynan shu shaklda ko'rinsa (o'quvchi
  terminalda ingliz tilida ko'radigan narsa bilan mos kelishi kerak)
- Termin allaqachon o'zbek/rus tilidagi dasturchilar orasida keng
  ingliz(cha)/inglizcha-transliteratsiya shaklida qabul qilingan bo'lsa
  (masalan, "compiler", "runtime")
- Bu biror kutubxona, vosita yoki funksiya nomi (masalan, `Cargo`, `rustc`,
  `println!`)

O'zbekchaga tarjima qiling, agar:
- Termin umumiy dasturlash tushunchasi bo'lib, tabiiy o'zbekcha muqobili
  mavjud va tushunarli bo'lsa (masalan, "function" → "funksiya" — bu aslida
  baynalmilal so'z, lekin o'zbek tilida standart)
- Tarjima qilinmasa jumla notabiiy yoki og'ir o'qiladigan bo'lib qolsa

## Inglizcha holicha qoldiriladigan asosiy terminlar

| Termin | Izoh |
|---|---|
| ownership | Rust'ning o'ziga xos konsepti, tarjimasi ma'noni yo'qotadi |
| borrow / borrowing | "qarz olish" so'zma-so'z tarjimasi tushunarsiz, inglizcha qoldiriladi |
| borrow checker | shu tarzda keng tanilgan |
| trait | o'zbekchada aniq muqobili yo'q |
| struct | kalit so'z, kod bilan mos kelishi kerak |
| enum | kalit so'z |
| lifetime | Rust'ga xos konsept, tarjima chalkashtiradi |
| closure | umumiy dasturlash termini, keng tanilgan holicha |
| generic / generics | keng qo'llaniladi |
| trait bound | trait bilan bog'liq, birga inglizcha qoladi |
| crate | Rust paket tizimining o'ziga xos atamasi |
| macro | keng tanilgan |
| panic | Rust'dagi maxsus xatti-harakat nomi (`panic!`) |
| unwrap | metod nomi, kod bilan mos kelishi kerak |
| shadowing | Rust'ga xos konsept |
| move (semantics) | "ko'chirish" chalkash bo'lishi mumkin, kontekstga qarab hal qilinadi |
| compiler | keng qabul qilingan |
| runtime | keng qabul qilingan |
| thread | keng qabul qilingan |
| async / await | kalit so'zlar |

## O'zbekchaga tarjima qilinadigan asosiy terminlar

| Termin (EN) | O'zbekcha |
|---|---|
| variable | o'zgaruvchi |
| function | funksiya |
| type | tur |
| value | qiymat |
| error | xato / xatolik |
| method | metod |
| argument / parameter | argument / parametr |
| return (qaytarmoq) | qaytarish |
| loop | sikl |
| condition | shart |
| array | massiv |
| memory | xotira |
| scope | ko'lam |
| block | blok |
| expression | ifoda |
| statement | bayonot |
| immutable | o'zgarmas |
| mutable | o'zgaruvchan |
| reference | ishora / murojaat (kontekstga qarab) |
| pointer | ko'rsatkich |
| string | satr |
| vector | vektor |
| iterator | iterator |
| module | modul |
| package | paket |
| library | kutubxona |
| documentation | hujjat / hujjatlashtirish |
| example | misol |
| chapter | bob |
| section | bo'lim |

## Loyihaga xos qarorlar jurnali

Tarjima jarayonida qabul qilingan yangi qarorlarni shu yerga qo'shib boring:

<!-- Misol: | HashMap | HashMap (inglizcha, chunki std kutubxona nomi) | -->
| constant | konstanta (tarjima qilinadi, keng qabul qilingan baynalmilal shakl) |
| shadowing | Inglizcha qoldiriladi, lekin fe'l sifatida "shadow qilmoq" tarzida moslashtiriladi (masalan: "x'ni shadow qiladi") |
| Rustacean(s) | Inglizcha qoldiriladi — Rust hamjamiyati a'zolarining norasmiy nomi, tarjimasi yo'q |
| bug | "xatolik" deb tarjima qilinadi (error bilan bir xil so'z, kontekst ajratadi) |
