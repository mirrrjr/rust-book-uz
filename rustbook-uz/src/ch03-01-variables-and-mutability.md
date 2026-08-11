## Õzgaruvçilar va Õzgaruvçanlik

<a id="variables-and-mutability"></a>

["Qiymatlarni Õzgaruvçilarda Saqlaş"][storing-values-with-variables]<!-- ignore --> bõlimida aytib õtilganidek, õzgaruvçilar standart bõyiça õzgarmasdir. Bu — Rust sizni uning taqdim etadigan xavfsizlik va oson [ondoşlik](https://tilsevarlar-gurungu.github.io/izohli-atamalar-lugati/terms/concurrency.html) afzalliklaridan foydalanadigan kod yozişga undaydigan kõplab imkoniyatlaridan biridir. Biroq, õzgaruvçilarni õzgaruvçan qiliş imkoniyati hali ham mavjud. Keling, Rust nima uçun va qanday qilib sizni õzgarmaslikni afzal kõrişga undaşini hamda bazan nima uçun bu imkoniyatdan voz keçişni xohlaşişingiz mumkinligini kõrib çiqaylik.

Õzgaruvçi õzgarmas bõlgaç, qiymat nomga boğlangandan sõng, siz u qiymatni õzgartira olmaysiz. Buni misolda kõriş uçun, `cargo new variables` buyruğidan foydalanib, _projects_ katalogingizda _variables_ nomli yangi loyiha yarating.

Sõngra, yangi _variables_ katalogida _src/main.rs_ faylini oçing va undagi kodni quyidagi kod bilan almaştiring — bu kod hozirça kompilyatsiya bõlmaydi:

<span class="filename">Fayl nomi: src/main.rs</span>

```rust,ignore,does_not_compile
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-01-variables-are-immutable/src/main.rs}}
```

Dasturni saqlang va `cargo run` yordamida işga tuşiring. Quyidagi çiqişda kõrsatilganidek, õzgarmaslik hatosi haqida hato xabari olasiz:

```console
{{#include ../listings/ch03-common-programming-concepts/no-listing-01-variables-are-immutable/output.txt}}
```

Uşbu misol kompilyatorning dasturlaringizdagi hatolarni topişga qanday yordam berişini kõrsatadi. Kompilyator hatolari asabga tegişi mumkin, lekin aslida ular şunçaki dasturingiz hali havfsiz ravişda siz hohlagan narsani bajarmayotganini bildiradi; ular sizning yahşi dasturçi emasligingizni _anglatmaydi_! Tajribali Rustacean'lar ham kompilyator hatolariga duç keladi.

Siz `` cannot assign twice to immutable variable `x` `` hato xabarini oldingiz, çunki õzgarmas `x` õzgaruvçisiga ikkinçi qiymatni berişga urindingiz.

Õzgarmas deb belgilangan qiymatni õzgartirmoqçi bõlganimizda kompilyatsiya vaqtida hato olişimiz juda muhim, çunki aynan şunday holat hatoliklarga olib kelişi mumkin. Agar kodingizning bir qismi qiymat heç qaçon õzgarmaydi degan tahmin bilan işlasa, kodingizning boşqa bir qismi esa u qiymatni õzgartirsa, birinçi qism õz vazifasini bajarmasligi mumkin. Bunday hatoning sababini keyinroq aniqlab topiş qiyin bõlişi mumkin, ayniqsa ikkinçi kod qismi qiymatni faqat _bazan_ õzgartirsa. Rust kompilyatori qiymat õzgarmaydi deb aytsangiz, u haqiqatan ham õzgarmasligini kafolatlaydi, şuning uçun buni õzingiz kuzatib bõrişingiz şart emas. Natijada kodingizni tahlil qiliş osonroq bõladi.

Ammo õzgaruvçanlik juda foydali bõlişi va kod yozişni qulayroq qilişi mumkin. Õzgaruvçilar standart bõyiça õzgarmas bõlsa-da, [2-bobda][storing-values-with-variables] qilganingizdek, õzgaruvçi nomidan oldin `mut` qõşib ularni õzgaruvçan qilişingiz mumkin. `mut` qõşiş, kodning boşqa qismlari uşbu õzgaruvçining qiymatini õzgartirişini bildiriş orqali kodni kelajakda õqiydiganlarga ham niyatni yetkazadi.

Masalan, _src/main.rs_ faylini quyidagiça õzgartiraylik:

<span class="filename">Fayl nomi: src/main.rs</span>

```rust
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-02-adding-mut/src/main.rs}}
```

Endi dasturni işga tuşirsak, quyidagini olamiz:

```console
{{#include ../listings/ch03-common-programming-concepts/no-listing-02-adding-mut/output.txt}}
```

`mut` işlatilganda, `x`ga boğlangan qiymatni `5`dan `6`ga õzgartirişimizga ruhsat beriladi. Ohir-oqibat, õzgaruvçanlikni işlatiş yoki işlatmaslik sizga boğliq bõlib, muayyan vaziyatda qaysi yõl eng tuşunarli ekaniga qarab qaror qabul qilasiz.

<!-- Old headings. Do not remove or links may break. -->
<a id="constants"></a>

### Konstanta elon qiliş

Õzgarmas õzgaruvçilar kabi, _konstantalar_ ham nomga boğlangan va õzgartirişi mumkin bõlmagan qiymatlardir, lekin konstantalar bilan õzgaruvçilar õrtasida bir neçta farq bor.

Birinçidan, konstantalarda `mut` işlatişga ruhsat berilmaydi. Konstantalar şunçaki standart bõyiça õzgarmas emas — ular doim õzgarmasdir. Konstantalar `let` kalit sõzi õrniga `const` kalit sõzi yordamida elon qilinadi va qiymatning turi _albatta_ annotatsiya qilinişi kerak. Turlar va tur annotatsiyalari haqida keyingi bõlim, ["Malumot Turlari"][data-types]<!-- ignore -->da batafsil tõhtalamiz, şuning uçun hozirça tafsilotlar haqida qayğurmang. Faqat şuni biling: tur har doim annotatsiya qilinişi kerak.

Konstantalar istalgan iş doirasida, jumladan global iş doirasida eʼlon qilinişi mumkin, bu esa ularni kodning kõp qismlari bilişi kerak bõlgan qiymatlar uçun foydali qiladi.

Sõnggi farq şundaki, konstantalar faqat konstanta ifodasiga tenglaştirilişi mumkin, iş vaqtidagina hisoblanadigan qiymatning natijasiga emas.

Mana konstanta eʼlonining misoli:

```rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

Konstantaning nomi `THREE_HOURS_IN_SECONDS` bõlib, uning qiymati 60 (bir daqiqadagi soniyalar soni) ni 60 (bir soatdagi daqiqalar soni) ga va 3 (uşbu dasturda hisoblamoqçi bõlgan soatlar soni) ga kõpaytiriş natijasiga teng. Rustning konstanta nomlaş qoidasiga kõra, nomlar katta harflar bilan yoziladi va sõzlar õrtasiga pastki çiziq qõyiladi. Kompilyator kompilyatsiya vaqtida çeklangan miqdordagi amallarni hisoblay oladi, bu esa bizga uşbu konstanta qiymatini 10,800 deb yozgandan kõra, uni tuşuniş va tekşiriş osonroq bõlgan şaklda yozişni tanlaş imkonini beradi. Konstantalarni eʼlon qilişda qanday amallardan foydalaniş mumkinligi haqida kõproq maʼlumot uçun [Rust Referensining konstanta hisoblaş bõlimiga][const-eval] qarang.

Konstantalar eʼlon qilingan iş doirasida dastur işlaşining butun davomiyligi davomida amal qiladi. Bu xususiyat konstantalarni dasturning bir neçta qismi bilişi kerak bõlgan ilova sohangizdagi qiymatlar uçun foydali qiladi — masalan, õyinning biror õyinçisi tõplaşi mumkin bõlgan maksimal ballar soni yoki yoruğlik tezligi.

Dasturingiz davomida işlatiladigan qattiq kodlangan qiymatlarga konstanta nomi beriş, u qiymatning manosini kelajakda kodni saqlovçilarga yetkazişda foydalidir. Şuningdek, kelajakda qattiq kodlangan qiymatni yangilaş kerak bõlsa, kodingizda faqat bitta joyni õzgartiriş kerakligi ham yordam beradi.

### Soyalaş (Shadowing)

<a id="shadowing"></a>

[2-bobdagi][comparing-the-guess-to-the-secret-number]<!-- ignore --> taxmin qiliş õyini boşlaşmasida kõrganingizdek, avvalgi õzgaruvçi bilan bir xil nomga ega yangi õzgaruvçini eʼlon qilişingiz mumkin. Rustaceanlarning aytişiça, birinçi õzgaruvçi ikkinçisi tomonidan _soyalaşadi_, yaʼni õzgaruvçi nomini işlatganingizda kompilyator aynan ikkinçi õzgaruvçini kõradi. Aslida, ikkinçi õzgaruvçi birinçisini soya qiladi va õzgaruvçi nomidan barcha foydalanişlarni õziga tortadi — toki uning õzi soyalaşmagunça yoki iş doirasi tugagunça. Õzgaruvçini quyidagiça, õşa nomni işlatib va `let` kalit sõzini takrorlaş orqali soyalaşimiz mumkin:

<span class="filename">Fayl nomi: src/main.rs</span>

```rust
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-03-shadowing/src/main.rs}}
```

Bu dastur avval `x`ni `5` qiymatiga boğlaydi. Sõngra `let x =`ni takrorlab, dastlabki qiymatni olib, unga `1` qõşib yangi `x` õzgaruvçisini yaratadi, natijada `x`ning qiymati `6` bõladi. Sõng, jingalak qavslar bilan yaratilgan içki iş doirasida uçinçi `let` bayonoti ham `x`ni soyalaşadi va avvalgi qiymatni `2`ga kõpaytirib, `x`ga `12` qiymatini beruvçi yangi õzgaruvçi yaratadi. U iş doirasi tugaganda, içki soyalaş ham tugaydi va `x` yana `6` bõladi. Dasturni işga tuşirsak, u quyidagini çop etadi:

```console
{{#include ../listings/ch03-common-programming-concepts/no-listing-03-shadowing/output.txt}}
```

Soyalaş õzgaruvçini `mut` deb belgilaşdan farq qiladi, çunki `let` kalit sõzini işlatmasdan uşbu õzgaruvçiga qayta qiymat berişga tasodifan urinsak, kompilyatsiya vaqtida hato olamiz. `let` yordamida biz qiymat ustida bir neçta õzgartiriş amalga oşirişimiz mumkin, ammo bu õzgartirişlar tugagaç, õzgaruvçi õzgarmas bõlib qoladi.

`mut` va soyalaş õrtasidagi yana bir farq şundaki, `let` kalit sõzini qayta işlatganimizda amalda yangi õzgaruvçi yaratamiz, şuning uçun qiymat turini õzgartira olamiz, ammo õşa nomdan qayta foydalana olamiz. Masalan, dasturimiz foydalanuvçidan boşliq belgilari kiritib, matn õrtasida neçta boşliq qoldirişni xohlaşini kõrsatişini sõrasin, biz esa u kirişni son sifatida saqlamoqçi bõlaylik:

```rust
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-04-shadowing-can-change-types/src/main.rs:here}}
```

Birinçi `spaces` õzgaruvçisi satr turiga, ikkinçi `spaces` õzgaruvçisi esa son turiga ega. Şunday qilib, soyalaş bizni `spaces_str` va `spaces_num` kabi turli nomlar õylab topişdan xalos qiladi; buning õrniga oddiyroq `spaces` nomidan qayta foydalana olamiz. Biroq, bu yerda kõrsatilganidek, buning uçun `mut` işlatişga harakat qilsak, kompilyatsiya vaqtida hato olamiz:

```rust,ignore,does_not_compile
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-05-mut-cant-change-types/src/main.rs:here}}
```

hato õzgaruvçining turini õzgartirişga ruhsat berilmasligini bildiradi:

```console
{{#include ../listings/ch03-common-programming-concepts/no-listing-05-mut-cant-change-types/output.txt}}
```

Endi õzgaruvçilar qanday işlaşini kõrib çiqdik, keling, ular ega bõla oladigan boşqa maʼlumot turlarini kõrib çiqaylik.

[comparing-the-guess-to-the-secret-number]: ch02-00-guessing-game-tutorial.html#comparing-the-guess-to-the-secret-number
[data-types]: ch03-02-data-types.html#data-types
[storing-values-with-variables]: ch02-00-guessing-game-tutorial.html#qiymatlarni-õzgaruvçilarda-saqlaş
[const-eval]: ../reference/const_eval.html
