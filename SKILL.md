---
name: en-uz-tech-translate
description: Translates English programming and software-engineering documentation (books, tutorials, docs, READMEs, blog posts, API references) into Uzbek, preserving Markdown structure, code blocks, and technical accuracy. Use this skill whenever the user asks to translate technical/programming content from English to Uzbek — including specific requests like translating "the Rust book" (rust-book, doc.rust-lang.org/book), a chapter, a docs site, or any .md/.mdx file full of prose mixed with code. Make sure to trigger this even if the user just says "tarjima qil" or "translate this" while working with an English technical markdown file, or asks to keep translating the next chapter/bob of a book already in progress.
---

# Inglizcha-O'zbekcha dasturlash matnlari tarjimoni

Bu skill inglizcha texnik/dasturlash hujjatlarini (kitoblar, qo'llanmalar,
docs, README fayllar) o'zbek tiliga tarjima qilish uchun mo'ljallangan.
Asosiy maqsad — o'quvchi uchun tabiiy o'qiladigan, terminologiyasi izchil,
lekin kod va texnik aniqlikni yo'qotmagan tarjima yaratish.

Bu shunchaki so'zma-so'z tarjima emas: siz bir vaqtning o'zida tarjimon va
texnik muharrirsiz. Har bir jumla o'zbek tilida tabiiy eshitilishi, ammo
asl texnik ma'no aniq saqlanib qolishi kerak.

## Ishni boshlashdan oldin

1. **Manba faylni aniqlang.** Agar foydalanuvchi biror repo yoki kitobni
   (masalan, rust-book) ko'rsatsa, lekin fayl hali yuklab olinmagan bo'lsa,
   uni topib o'qing (`view`/`bash_tool` orqali fayl tizimidan, yoki
   `web_fetch` orqali onlaydan — masalan rust-lang/book GitHub reposi
   `src/*.md` fayllaridan iborat).
2. **`references/glossary.md` faylini o'qing.** Bu tarjima davomida
   qo'llaniladigan terminologiya qarorlarining jonli jurnali. Yangi bobni
   boshlashdan oldin har doim shu faylni tekshiring — u avvalgi boblarda
   qabul qilingan qarorlarni o'z ichiga oladi.
3. **Loyihaning uslub sozlamalarini eslab qoling** (agar foydalanuvchi
   boshqacha demagan bo'lsa, standart quyidagicha):
   - **Ohang: rasmiy (siz)** — texnik hujjat uslubi, "sen" emas "siz",
     buyruq gaplar o'rniga tavsiya shaklida ("...qiling", "...mumkin").
   - **Terminologiya: aralash yondashuv** — mashhur/o'ziga xos Rust
     terminlari (ownership, borrow checker, trait va h.k.) inglizcha
     qoladi, umumiy dasturlash tushunchalari o'zbekchaga tarjima qilinadi.
     Aniq ro'yxat uchun `references/glossary.md`ga qarang.
   - **Imlo: apostrofsiz lotin varianti** — `ch`, `sh`, `o'`, `g'` o'rniga
     `ç`, `ş`, `õ`, `ğ` harflaridan foydalaning (masalan: "o'zgaruvchi"
     emas, "õzgaruvçi"; "funksiya" so'zida o'zgarish yo'q chunki unda bu
     harflar yo'q). Bu imlo variantini har doim izchil qo'llang.

## Tarjima jarayoni

### 1. Struktura va kodni ajrating

Markdown faylni tarjima qilishda **faqat prozani** (oddiy matn, izohlar,
sarlavhalar) tarjima qiling. Quyidagilarga **tegmang, aynan asl holida
qoldiring**:

- Kod bloklari (` ```rust ... ``` ` va h.k.) — ichidagi kod, kompilyator
  chiqishi (output), terminal buyruqlari
- Inline kod (`` `variable_name` `` kabi)
- Havolalar (link) manzillari — faqat havola matni (anchor text) kerak
  bo'lsa tarjima qilinadi, URL o'zgarmaydi
- Frontmatter, HTML teglar, Markdown maxsus belgilar (`#`, `**`, `|` jadval
  chegaralari va h.k.)
- Fayl nomlari, funksiya/o'zgaruvchi nomlari, terminal buyruqlari matn
  ichida ham (`` `cargo run` `` kabi)

Bundan istisno: agar kod blokidagi izoh (`// bu joyda...`) tushuntirish
uchun muhim bo'lsa va foydalanuvchi kod ichidagi izohlarni ham tarjima
qilishni alohida so'rasa, faqat o'sha holda izohlarni tarjima qiling — kod
mantiqiga hech qachon tegmang.

### 2. Prozani tarjima qiling

Har bir paragrafni ma'nosiga qarab, so'zma-so'z emas, tabiiy o'zbekcha
jumla tuzilishida qayta yozing. Inglizcha gap tuzilishini so'zma-so'z
ko'chirish (masalan, ingliz tilidagi passiv qurilmalarni yoki uzun bog'lovchi
gaplarni ayni holicha saqlash) o'zbekchada notabiiy va og'ir o'qiladi —
kerak bo'lsa gapni ikkiga bo'ling yoki qayta tuzing, lekin texnik
ma'noni yo'qotmang.

Terminlarni tanlashda `references/glossary.md`dagi mezonlarga amal qiling.
Agar lug'atda bo'lmagan yangi termin uchrasa:
1. Mezon asosida qaror qiling (inglizcha qoldirish yoki tarjima qilish)
2. Qarorni **darhol** `references/glossary.md`ning "Loyihaga xos qarorlar
   jurnali" bo'limiga yozib qo'ying — keyingi bob shu qarordan foydalanadi
3. Agar qaror noaniq bo'lsa (ikki xil tarzda ham asoslash mumkin bo'lsa),
   foydalanuvchidan so'rang, o'zingiz taxmin qilib o'tirmang

### 3. O'z-o'zingizni tekshiring

Bobni tarjima qilib bo'lgach, quyidagilarni tekshiring:
- Barcha kod bloklari asl holida qoldimi (diff solishtiring, agar mumkin
  bo'lsa)
- Terminologiya shu bob ichida va (agar avvalgi boblar mavjud bo'lsa)
  ular bilan izchilmi
- Imlo qoidasi (ç, ş, õ, ğ) izchil qo'llanganmi
- Sarlavhalar ierarxiyasi (`#`, `##`, `###`) asl fayl bilan mos keladimi

### 4. Faylni saqlang

Asl fayl strukturasini saqlagan holda tarjima qilingan faylni chiqaring.
Masalan, `src/ch03-01-variables-and-mutability.md` uchun xuddi shu nom va
joylashuvni tarjima qilingan katalogda saqlang (masalan `src-uz/`), shunda
mdbook kabi vositalar bilan ishlatish oson bo'ladi.

## Ko'p bobli kitoblar uchun (masalan, rust-book)

Agar loyiha bir nechta bobdan iborat bo'lsa (rust-book kabi):

- Har safar yangi bobni boshlashdan oldin `references/glossary.md`ni qayta
  o'qing — u oldingi seansda yangilangan bo'lishi mumkin
- Bir nechta bob tarjima qilingandan so'ng, vaqti-vaqti bilan avvalgi
  boblarga qaytib, terminologiya jurnali asosida izchillikni tekshiring —
  ayniqsa agar yangi termin jurnalga kech qo'shilgan bo'lsa, uni oldingi
  boblarda ham to'g'irlash kerak bo'lishi mumkin
- Foydalanuvchiga har bobdan keyin qisqa xulosa bering: qaysi yangi
  terminlar bo'yicha qaror qabul qilindi, agar biror joy noaniq qolgan
  bo'lsa

## Muhim eslatmalar

- Bu ijodiy emas, texnik tarjima — aniqlik ravonlikdan ustun, lekin
  ravonlik ham muhim (o'quvchi kitobni o'qishi kerak, faqat ma'lumot
  olishi emas)
- Mualliflik huquqi: rust-book kabi ochiq litsenziyali (odatda MIT/Apache-2.0)
  materiallarni tarjima qilish odatiy holat, ammo litsenziyani fayl orqali
  tekshiring va litsenziya matnini/atributsiyasini tarjima qilingan faylda
  ham saqlab qoling
- Agar manba fayl juda uzun bo'lsa, uni bo'lim-bo'lim tarjima qiling va
  har bir bo'limdan keyin progress haqida xabar bering — hammasini bitta
  javobga sig'dirishga urinmang
