# Taxmin qiliş õyinini dasturlaş

Keling, birga amaliy loyiha ustida işlab, Rust bilan tanişaylik! Bu bob sizga bir neçta keng tarqalgan Rust tuşunçalarini haqiqiy dastur misolida
kõrsatiş orqali taniştiradi. Siz `let`, `match`, metodlar, boğlangan
funksiyalar, taşqi crate'lar va boşqa kõp narsalar haqida bilib olasiz!
Keyingi boblarda bu ğoyalarni batafsilroq kõrib çiqamiz. Bu bobda esa
faqat asosiy tuşunçalarni amalda maşq qilasiz.

Biz klassik boşlanğiçlar uçun dasturlaş masalasini — Taxmin qiliş õyinini —
amalga oşiramiz. Mana u qanday işlaydi: dastur 1 dan 100 gaça bõlgan
tasodifiy butun sonni generatsiya qiladi. Sõngra õyinçidan bir sonni
kiritişni sõraydi. Taxmin kiritilgandan keyin, dastur taxmin juda
kiçik yoki juda katta ekanligini kõrsatadi. Agar taxmin tõğri bõlsa,
õyin tabriklovçi xabar çiqarib, tugaydi.

## Yangi loyiha yaratiş

Yangi loyiha yaratiş uçun, 1-bobda yaratgan _projects_ katalogiga õting va
Cargo yordamida yangi loyiha yarating:

```console
$ cargo new guessing_game
$ cd guessing_game
```

Birinçi buyruq, `cargo new`, birinçi argument sifatida loyiha nomini
(`guessing_game`) oladi. Ikkinçi buyruq esa yangi loyiha katalogiga õtadi.

Generatsiya qilingan _Cargo.toml_ fayliga qarang:

<!-- manual-regeneration
cd listings/ch02-guessing-game-tutorial
rm -rf no-listing-01-cargo-new
cargo new no-listing-01-cargo-new --name guessing_game
cd no-listing-01-cargo-new
cargo run > output.txt 2>&1
cd ../../..
-->

<span class="filename">Fayl nomi: Cargo.toml</span>

```toml
{{#include ../listings/ch02-guessing-game-tutorial/no-listing-01-cargo-new/Cargo.toml}}
```

1-bobda kõrganingizdek, `cargo new` siz uçun "Hello, world!" dasturini
generatsiya qiladi. _src/main.rs_ fayliga qarang:

<span class="filename">Fayl nomi: src/main.rs</span>

```rust
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/no-listing-01-cargo-new/src/main.rs}}
```

Endi bu "Hello, world!" dasturini `cargo run` buyruği yordamida bir
qadamda kompilyatsiya qilib işga tuşiraylik:

```console
{{#include ../listings/ch02-guessing-game-tutorial/no-listing-01-cargo-new/output.txt}}
```

`run` buyruği loyiha ustida tez iteratsiya qilmoqçi bõlganingizda qõl
keladi — bu õyinda ham har bir iteratsiyani keyingisiga õtişdan oldin
tezda sinab kõramiz.

_src/main.rs_ faylini qayta oçing. Bu bobdagi barça kodni şu faylga
yozasiz.

## Taxminni qayta işlaş

Taxmin õyini dasturining birinçi qismi foydalanuvçidan kirişni sõraydi,
uni qayta işlaydi va kirişning kutilgan şaklda ekanligini tekşiradi.
Boşlaş uçun, õyinçiga taxminni kiritişga ruxsat beramiz. 2-1-listingdagi
kodni _src/main.rs_ ga kiriting.

<Listing number="2-1" file-name="src/main.rs" caption="Foydalanuvçidan bashoratni oluvçi va uni çop etuvçi kod">

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-01/src/main.rs:all}}
```

</Listing>

Bu kodda kõp maʼlumot bor, şuning uçun uni qator-qator qilib kõrib çiqaylik.
Foydalanuvçi kirişini olib, natijani çiqiş sifatida çop etiş uçun, `io`
kiriş/çiqiş kutubxonasini iş doirasiga (scope) kiritişimiz kerak. `io`
kutubxonasi standart kutubxonadan, yaʼni `std`dan keladi:

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-01/src/main.rs:io}}
```

Standart bõyiça Rust har bir dasturning iş doirasiga standart
kutubxonada aniqlangan bir tõplam elementlarni kiritadi. Bu tõplam
_prelude_ deb ataladi va siz undagi hamma narsani [standart kutubxona
hujjatlarida][prelude] kõrişingiz mumkin.

Agar işlatmoqçi bõlgan tur prelude'da bõlmasa, uni `use` bayonoti
yordamida iş doirasiga aniq kiritişingiz kerak. `std::io`
kutubxonasidan foydalaniş sizga foydalanuvçi kirişini qabul qiliş
qobiliyati kabi bir qança foydali imkoniyatlarni beradi.

1-bobda kõrganingizdek, `main` funksiyasi dasturga kiriş nuqtasidir:

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-01/src/main.rs:main}}
```

`fn` sintaksisi yangi funksiya eʼlon qiladi; qavslar, `()`, hiç qanday
parametr yõqligini bildiradi; jingalak qavs, `{`, esa funksiya tanasini
boşlaydi.

1-bobda şuningdek õrgangandek, `println!` ekranga satr çop etuvçi
makrodir:

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-01/src/main.rs:print}}
```

Bu kod õyin nima ekanligini bildiruvçi va foydalanuvçidan kiriş talab
qiluvçi xabarni çop etadi.

### Qiymatlarni õzgaruvçilarda saqlaş

Keyingi qadamda foydalanuvçi kirişini saqlaş uçun _õzgaruvçi_ yaratamiz:

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-01/src/main.rs:string}}
```

Endi dastur qiziqarli bõlib bormoqda! Bu kiçkina qatorda kõp narsa sodir
bõlmoqda. Biz õzgaruvçini yaratiş uçun `let` bayonotidan foydalanamiz.
Mana yana bir misol:

```rust,ignore
let apples = 5;
```

Bu qator `apples` nomli yangi õzgaruvçini yaratadi va uni `5` qiymatiga
boğlaydi. Rustda õzgaruvçilar standart bõyiça õzgarmasdir — yaʼni bir
marta õzgaruvçiga qiymat berilgandan sõng, u qiymat õzgarmaydi. Biz bu
tuşunçani [3-bobdagi "Õzgaruvçilar va Õzgaruvçanlik"][variables-and-mutability]<!-- ignore -->
bõlimida batafsil muhokama qilamiz. Õzgaruvçini õzgaruvçan qiliş uçun,
õzgaruvçi nomidan oldin `mut` qõşamiz:

```rust,ignore
let apples = 5; // õzgarmas
let mut bananas = 5; // õzgaruvçan
```

> Eslatma: `//` sintaksisi qator oxirigaça davom etuvçi izohni
> boşlaydi. Rust izohlardagi hamma narsani eʼtiborsiz qoldiradi. Izohlar
> haqida batafsil [3-bobda][comments]<!-- ignore --> muhokama qilamiz.

Taxmin õyini dasturimizga qaytsak, endi siz `let mut guess`
õzgaruvçan `guess` nomli õzgaruvçini kiritişini bilasiz. Tenglik belgisi
(`=`) Rustga hozir õzgaruvçiga biror narsani boğlamoqçi ekanligimizni
bildiradi. Tenglik belgisining õng tomonida `guess` boğlangan qiymat
turadi, bu esa yangi `String` nusxasini qaytaruvçi funksiya bõlgan
`String::new` çaqiruvining natijasidir. [`String`][string]<!-- ignore -->
— standart kutubxona taʼminlaydigan, kengayuvçan, UTF-8 kodlangan matn
bõlagi bõlgan satr turi.

`::new` qatoridagi `::` sintaksisi `new` `String` turining boğlangan
funksiyasi ekanligini bildiradi. _Boğlangan funksiya_ deb, biror turda
amalga oşirilgan funksiyaga aytiladi — bu holda `String` turida. Bu `new`
funksiyasi yangi, bõş satr yaratadi. Kõplab turlarda `new` funksiyasini
uçratasiz, çunki bu qandaydir turning yangi qiymatini yaratuvçi funksiya
uçun keng tarqalgan nom.

Xulosa qilib aytganda, `let mut guess = String::new();` qatori hozirda
yangi, bõş `String` nusxasiga boğlangan õzgaruvçan õzgaruvçini yaratdi.
Uf!

### Foydalanuvçi kirişini qabul qiliş

Eslatib õtamiz, biz dasturning birinçi qatorida `use std::io;` orqali
standart kutubxonadan kiriş/çiqiş funksionalligini kiritgan edik. Endi
`io` modulidan `stdin` funksiyasini çaqiramiz, bu bizga foydalanuvçi
kirişini qayta işlaş imkonini beradi:

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-01/src/main.rs:read}}
```

Agar biz dastur boşida `use std::io;` orqali `io` modulini import
qilmagan bõlsak ham, bu funksiyani `std::io::stdin` deb yozib çaqira
olardik. `stdin` funksiyasi [`std::io::Stdin`][iostdin]<!-- ignore -->
nusxasini qaytaradi, bu terminalingizning standart kirişiga hendl
(handle) bõlgan turdir.

Keyin, `.read_line(&mut guess)` qatori standart kiriş hendlida
[`read_line`][read_line]<!-- ignore --> metodini çaqirib, foydalanuvçidan
kiriş oladi. Biz şuningdek `read_line`ga foydalanuvçi kirişini qaysi
satrda saqlaş kerakligini bildiriş uçun `&mut guess`ni argument sifatida
uzatamiz. `read_line`ning asosiy vazifasi — foydalanuvçi standart kirişga
nima kiritsa, uni satrga (mavjud mazmunini qayta yozmasdan) qõşişdir,
şuning uçun biz õşa satrni argument sifatida uzatamiz. Argument sifatida
uzatilgan satr õzgaruvçan bõlişi kerak, çunki metod satr mazmunini
õzgartira olişi lozim.

`&` belgisi bu argument _referens_ ekanligini bildiradi — bu esa kodning
turli qismlariga bir maʼlumot bõlagini xotirada bir neçta marta
kõçirmasdan kiriş imkonini beradi. Referenslar murakkab xususiyat, va
Rustning asosiy afzalliklaridan biri referenslardan qançalik xavfsiz va
oson foydalaniş mumkinligidir. Bu dasturni tugatiş uçun bu detallarni
kõp bilişingiz şart emas. Hozirça faqat şuni bilişingiz kerak: xuddi
õzgaruvçilar kabi, referenslar ham standart bõyiça õzgarmasdir. Şu sababli
`&guess` õrniga `&mut guess` yozib, uni õzgaruvçan qiliş kerak (4-bob
referenslarni batafsilroq tuşuntiradi).

<!-- Old headings. Do not remove or links may break. -->

<a id="handling-potential-failure-with-the-result-type"></a>

### `Result` bilan mumkin bõlgan muvaffaqiyatsizlikni qayta işlaş

Biz hali şu bir qator kod ustida işlamoqdamiz. Endi matnning uçinçi
qatorini muhokama qilyapmiz, ammo eʼtibor bering — bu hali ham bitta
mantiqiy kod qatorining bir qismi. Keyingi qism şu metod:

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-01/src/main.rs:expect}}
```

Biz bu kodni şunday ham yozişimiz mumkin edi:

```rust,ignore
io::stdin().read_line(&mut guess).expect("Failed to read line");
```

Ammo, uzun bitta qator õqiş qiyin, şuning uçun uni bõliş maʼqul. Kõpinça
`.method_name()` sintaksisi bilan metod çaqirilganda, uzun qatorlarni
bõlişga yordam beriş uçun yangi qator va boşqa boş joy kiritiş oqilona
hisoblanadi. Endi bu qator nima qilişini muhokama qilaylik.

Yuqorida aytilganidek, `read_line` foydalanuvçi nima kiritsa, uni biz
uzatgan satrga joylaştiradi, ammo u şuningdek `Result` qiymatini ham
qaytaradi. [`Result`][result]<!-- ignore --> — _enumeratsiya_ (kõpinça
_enum_ deb ataladi), bu bir neça mumkin bõlgan holatlardan birida bõla
oladigan turdir. Har bir mumkin bõlgan holatni _variant_ deb ataymiz.

[6-bob][enums]<!-- ignore --> enum'larni batafsilroq yoritadi. Bu
`Result` turlarining maqsadi — xatolarni qayta işlaş maʼlumotlarini
kodlaştirişdir.

`Result`ning variantlari `Ok` va `Err`. `Ok` varianti amaliyot
muvaffaqiyatli bõlganini bildiradi va muvaffaqiyatli generatsiya qilingan
qiymatni õz içiga oladi. `Err` varianti esa amaliyot muvaffaqiyatsiz
bõlganini bildiradi va amaliyot nima uçun yoki qanday muvaffaqiyatsiz
bõlgani haqida maʼlumot saqlaydi.

`Result` turining qiymatlari, har qanday turning qiymatlari kabi, õzida
aniqlangan metodlarga ega. `Result`ning nusxasida çaqirişingiz mumkin
bõlgan [`expect` metodi][expect]<!-- ignore --> mavjud. Agar `Result`ning
bu nusxasi `Err` qiymati bõlsa, `expect` dasturni çõktiradi va argument
sifatida uzatgan xabaringizni kõrsatadi. Agar `read_line` metodi `Err`
qaytarsa, bu ehtimol operatsion tizimdan kelgan xato natijasi bõladi.
Agar `Result`ning bu nusxasi `Ok` qiymati bõlsa, `expect` `Ok` içida
saqlangan qaytiş qiymatini olib, uni sizga foydalaniş uçun qaytaradi. Bu
holatda, bu qiymat foydalanuvçi kirişidagi baytlar sonidir.

Agar `expect`ni çaqirmasangiz, dastur kompilyatsiya bõladi, ammo
ogohlantiriş olasiz:

```console
{{#include ../listings/ch02-guessing-game-tutorial/no-listing-02-without-expect/output.txt}}
```

Rust `read_line`dan qaytarilgan `Result` qiymatidan foydalanmaganingizni
ogohlantiradi, bu esa dastur mumkin bõlgan xatoni qayta işlamaganini
bildiradi.

Ogohlantiriş ovozini õçirişning tõğri yõli — haqiqatan ham xatolarni
qayta işlaş kodini yozişdir, ammo bizning holimizda muammo yuzaga kelganda
dasturni oddiygina çõktirişni xohlaymiz, şuning uçun `expect`dan
foydalanamiz. Xatolardan tiklaniş haqida [9-bobda][recover]<!-- ignore
--> õrganasiz.

### `println!` bilan qiymatlarni õrin bosuvçilar orqali çop etiş

Yopuvçi jingalak qavsdan taşqari, hozirgaça kõrib çiqilgan kodda faqat
bitta qator qoldi:

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-01/src/main.rs:print_guess}}
```

Bu qator hozir foydalanuvçi kirişini saqlovçi satrni çop etadi. `{}`
jingalak qavslar tõplami õrin bosuvçidir: `{}`ni qiymatni õz joyida
tutib turuvçi kiçik qisqiç deb tasavvur qiling. Õzgaruvçining qiymatini
çop etganda, õzgaruvçi nomini jingalak qavslar içiga qõyişingiz mumkin.
Ifodani baholaş natijasini çop etganda esa, format satrida bõş jingalak
qavslarni qoldiring, sõngra format satridan keyin vergul bilan ajratilgan
ifodalar rõyxatini yozing — ular har bir bõş jingalak qavs õrin
bosuvçisiga navbat bilan mos keladi. Bitta `println!` çaqiruvida
õzgaruvçini ham, ifoda natijasini ham çop etiş şunday kõrinadi:

```rust
let x = 5;
let y = 10;

println!("x = {x} and y + 2 = {}", y + 2);
```

Bu kod `x = 5 and y + 2 = 12` deb çop etadi.

### Birinçi qismni sinab kõriş

Taxmin õyinining birinçi qismini sinab kõraylik. Uni `cargo run` orqali
işga tuşiring:

<!-- manual-regeneration
cd listings/ch02-guessing-game-tutorial/listing-02-01/
cargo clean
cargo run
input 6 -->

```console
$ cargo run
   Compiling guessing_game v0.1.0 (file:///projects/guessing_game)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 6.44s
     Running `target/debug/guessing_game`
Guess the number!
Please input your guess.
6
You guessed: 6
```

Bu bosqiçda õyinning birinçi qismi tayyor: biz klaviaturadan kiriş
olyapmiz va sõngra uni çop etyapmiz.

## Maxfiy sonni generatsiya qiliş

Keyingi qadamda foydalanuvçi Taxmin qiladigan maxfiy sonni generatsiya
qiliş kerak. Maxfiy son har safar boşqaça bõlişi kerak, şunda õyin bir
neça marta õynaş uçun ham qiziqarli bõladi. Biz 1 dan 100 gaça bõlgan
tasodifiy sondan foydalanamiz, şunda õyin juda ham qiyin bõlmaydi. Rust
hali õzining standart kutubxonasida tasodifiy son funksionalligini õz
içiga olmaydi. Ammo Rust jamoasi buning uçun [`rand`
crate'i][randcrate]ni taqdim etadi.

<!-- Old headings. Do not remove or links may break. -->
<a id="using-a-crate-to-get-more-functionality"></a>

### Crate yordamida funksionallikni oşiriş

Esingizda bõlsin, crate — Rust manba kod fayllari tõplamidir. Biz
qurayotgan loyiha bajariladigan fayl bõlgan binary crate hisoblanadi.
`rand` crate'i esa boşqa dasturlarda foydalaniş uçun mõljallangan va õz
holiça işga tuşirilmaydigan kutubxona crate'idir.

Cargoning taşqi crate'larni muvofiqlaştiriş qobiliyati aynan şu yerda
õzini kõrsatadi. `rand`dan foydalanuvçi kod yozişdan oldin, `rand`
crate'ini boğliqlik sifatida qõşiş uçun _Cargo.toml_ faylini õzgartiriş
kerak. Endi şu faylni oçing va Cargo siz uçun yaratgan
`[dependencies]` bõlim sarlavhasi ostiga quyidagi qatorni qõşing.
`rand`ni aynan şu yerda kõrsatilganidek, aynan şu versiya raqami bilan
kõrsatişga eʼtibor bering — aks holda bu qõllanmadagi kod misollari
işlamasligi mumkin:

<!-- When updating the version of `rand` used, also update the version of
`rand` used in these files so they all match:

* ch01-01-installation.md
* ch07-04-bringing-paths-into-scope-with-the-use-keyword.md
* ch14-03-cargo-workspaces.md
-->

<span class="filename">Fayl nomi: Cargo.toml</span>

```toml
{{#include ../listings/ch02-guessing-game-tutorial/listing-02-02/Cargo.toml:8:}}
```

_Cargo.toml_ faylida, har bir sarlavhadan keyin keladigan hamma narsa
boşqa bõlim boşlanguniça õşa bõlimga tegişli bõladi. `[dependencies]`
içida siz Cargoga loyihangiz qaysi taşqi crate'larga boğliq ekanligini
va õşa crate'larning qaysi versiyalari kerak ekanligini aytasiz. Bu
holatda, biz `rand` crate'ini `0.10.1` semantik versiya belgisi bilan
kõrsatyapmiz. Cargo [Semantik Versiyalaş][semver]<!-- ignore -->ni
(baʼzan _SemVer_ deb ham ataladi) tuşunadi — bu versiya raqamlarini
yozişning standarti. `0.10.1` belgisi aslida `^0.10.1`ning qisqartma
şaklidir, bu esa kamida 0.10.1, ammo 0.11.0 dan past bõlgan istalgan
versiyani anglatadi.

Cargo bu versiyalarni 0.10.1 versiyasi bilan mos oçiq API'ga ega deb
hisoblaydi, va bu spetsifikatsiya sizga bu bobdagi kod bilan hamon
kompilyatsiya bõladigan eng sõnggi patç relizini olişingizni taʼminlaydi.
0.11.0 yoki undan yuqori istalgan versiya quyidagi misollar
foydalanadigan API bilan bir xil bõlişi kafolatlanmaydi.

Endi, kodni õzgartirmasdan, loyihani 2-2-listingda kõrsatilganidek quraylik.

<!-- manual-regeneration
cd listings/ch02-guessing-game-tutorial/listing-02-02/
rm Cargo.lock
cargo clean
cargo build -->

<Listing number="2-2" caption="`rand` crate'ini bog'liqlik sifatida qõşgandan keyin `cargo build`ni işga tuşiriş natijasi">

```console
$ cargo build
    Updating crates.io index
     Locking 8 packages to latest Rust 1.96.0 compatible versions
  Downloaded rand_core v0.10.1
  Downloaded chacha20 v0.10.1
  Downloaded rand v0.10.1
  Downloaded 3 crates (162.9KiB) in 0.59s
   Compiling libc v0.2.186
   Compiling rand_core v0.10.1
   Compiling getrandom v0.4.3
   Compiling cfg-if v1.0.4
   Compiling chacha20 v0.10.1
   Compiling rand v0.10.1
   Compiling guessing_game v0.1.0 (file:///projects/guessing_game)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 2.03s
```

</Listing>

Sizda boşqaça versiya raqamlari kõrinişi mumkin (ammo ular SemVer
tufayli barçasi kod bilan mos bõladi) va qatorlar boşqaça bõlişi mumkin
(operatsion tizimga qarab), qatorlarning tartibi ham boşqaça bõlişi
mumkin.

Taşqi boğliqlikni qõşganimizda, Cargo õşa boğliqlikka kerak bõlgan
hamma narsaning eng sõnggi versiyalarini _registr_dan oladi — bu esa
[Crates.io][cratesio]dagi maʼlumotlarning nusxasidir. Crates.io — Rust
ekotizimidagi odamlar õzlarining oçiq manbali Rust loyihalarini boşqalar
foydalanişi uçun joylaştiradigan joy.

Registrni yangilagandan keyin, Cargo `[dependencies]` bõlimini tekşiradi
va hali yuklab olinmagan crate'larni yuklab oladi. Bu holatda, garçi biz
faqat `rand`ni boğliqlik sifatida kõrsatgan bõlsak-da, Cargo `rand`
işlaşi uçun kerak bõlgan boşqa crate'larni ham oldi. Crate'larni yuklab
olgandan keyin, Rust ularni kompilyatsiya qiladi, sõngra loyihani mavjud
boğliqliklar bilan kompilyatsiya qiladi.

Agar hiç qanday õzgarişsiz darhol yana `cargo build`ni işga tuşirsangiz,
`Finished` qatoridan boşqa hiç qanday çiqişni olmaysiz. Cargo boğliqlik-
larni allaqaçon yuklab olganini va kompilyatsiya qilganini biladi, va siz
_Cargo.toml_ faylida ular haqida hiç narsani õzgartirmagansiz. Cargo
şuningdek kodingizda ham hiç narsa õzgartirmaganingizni biladi, şuning
uçun uni ham qayta kompilyatsiya qilmaydi. Qilinadigan hiç narsa
bõlmagani uçun, u oddiygina çiqib ketadi.

Agar _src/main.rs_ faylini oçib, arzimas õzgarişni kiritib, saqlab,
qayta qursangiz, faqat ikkita qator çiqişni kõrasiz:

<!-- manual-regeneration
cd listings/ch02-guessing-game-tutorial/listing-02-02/
touch src/main.rs
cargo build -->

```console
$ cargo build
   Compiling guessing_game v0.1.0 (file:///projects/guessing_game)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.13s
```

Bu qatorlar Cargo faqat _src/main.rs_ fayliga kiritgan kiçkina
õzgarişingiz bilan build'ni yangilaganini kõrsatadi. Boğliqliklaringiz
õzgarmagan, şuning uçun Cargo ular uçun allaqaçon yuklab olingan va
kompilyatsiya qilingan narsalardan qayta foydalanişi mumkinligini
biladi.

<!-- Old headings. Do not remove or links may break. -->
<a id="ensuring-reproducible-builds-with-the-cargo-lock-file"></a>

#### Takrorlanuvçi build'larni taʼminlaş

Cargoda siz yoki boşqa birov kodingizni qurgan sayin bir xil artifaktni
qayta qura olişingizni taʼminlovçi mexanizm bor: Cargo siz boşqaçasini
kõrsatmaguniça faqat siz kõrsatgan boğliqlik versiyalaridan foydalanadi.
Masalan, aytaylik keyingi hafta `rand` crate'ining 0.10.2 versiyasi
çiqadi, va bu versiya muhim xatolik tuzatişini õz içiga oladi, ammo
şuningdek kodingizni buzadigan regressiyani ham õz içiga oladi. Buni hal
qiliş uçun, Rust siz birinçi marta `cargo build`ni işga tuşirganingizda
_Cargo.lock_ faylini yaratadi, şuning uçun endi bu fayl _guessing_game_
katalogida mavjud.

Loyihani birinçi marta qurganingizda, Cargo mezonlarga mos keluvçi
boğliqliklarning barça versiyalarini aniqlab, ularni _Cargo.lock_
fayliga yozadi. Loyihangizni kelajakda qurganingizda, Cargo
_Cargo.lock_ faylining mavjudligini kõrib, versiyalarni qayta aniqlaş
işini bajariş õrniga õşa faylda kõrsatilgan versiyalardan foydalanadi.
Bu sizga avtomatik ravişda takrorlanuvçi build imkonini beradi. Boşqaça
aytganda, loyihangiz _Cargo.lock_ fayli tufayli, aniq yangilamaguningiz-
ça, 0.10.1 versiyasida qoladi. _Cargo.lock_ fayli takrorlanuvçi
build'lar uçun muhim bõlgani sababli, u kõpinça loyihangizning qolgan
kodi bilan birga versiyalar boşqaruv tizimiga (source control)
qõşiladi.

#### Crate'ni yangi versiyaga yangilaş

Crate'ni yangilamoqçi bõlganingizda, Cargo `update` buyruğini taqdim
etadi, bu esa _Cargo.lock_ faylini eʼtiborsiz qoldirib, _Cargo.toml_
dagi spetsifikatsiyalaringizga mos keluvçi barça eng sõnggi versiyalarni
aniqlaydi. Sõngra Cargo õşa versiyalarni _Cargo.lock_ fayliga yozadi.
Aks holda, standart bõyiça, Cargo faqat 0.10.1 dan katta va 0.11.0 dan
kiçik versiyalarni qidiradi. Agar `rand` crate'i ikkita yangi versiya —
0.10.2 va 0.999.0 — çiqargan bõlsa, `cargo update`ni işga tuşirganingizda
quyidagini kõrasiz:

<!-- manual-regeneration
cd listings/ch02-guessing-game-tutorial/listing-02-02/
cargo update
assuming there is a new version of rand; otherwise use another update
as a guide to creating the hypothetical output shown here -->

```console
$ cargo update
    Updating crates.io index
     Locking 1 package to latest Rust 1.96.0 compatible version
    Updating rand v0.10.1 -> v0.10.2 (available: v0.999.0)
```

Cargo 0.999.0 relizini eʼtiborsiz qoldiradi. Bu bosqiçda, _Cargo.lock_
faylingizda ham õzgariş kõrasiz — endi foydalanayotgan `rand`
crate'ining versiyasi 0.10.2 ekanligi qayd etilgan. `rand`ning 0.999.0
versiyasidan yoki 0.999._x_ seriyasidagi istalgan versiyadan
foydalaniş uçun, _Cargo.toml_ faylini quyidagiça õzgartirişingiz kerak
bõlardi (bu õzgarişni haqiqatda amalga oşirmang, çunki keyingi misollar
siz `rand` 0.10 dan foydalanayotganingizni faraz qiladi):

```toml
[dependencies]
rand = "0.999.0"
```

Keyingi safar `cargo build`ni işga tuşirganingizda, Cargo mavjud
crate'lar registrini yangilaydi va `rand` talablaringizni siz kõrsatgan
yangi versiyaga muvofiq qayta baholaydi.

[Cargo][doccargo]<!-- ignore --> va [uning ekotizimi][doccratesio]<!--
ignore --> haqida aytadigan yana kõp narsa bor, buni 14-bobda muhokama
qilamiz, ammo hozirça sizga bilişingiz kerak bõlgan hamma narsa şu. Cargo
kutubxonalardan qayta foydalanişni juda oson qiladi, şuning uçun
Rustaseanlar bir neça paketlardan yiğilgan kiçikroq loyihalarni yoza
oladilar.

### Tasodifiy son generatsiya qiliş

Taxmin qiliş uçun sonni generatsiya qiliş uçun `rand`dan foydalanişni
boşlaylik. Keyingi qadam — 2-3-listingda kõrsatilganidek _src/main.rs_ ni
yangilaş.

<Listing number="2-3" file-name="src/main.rs" caption="Tasodifiy son generatsiya qiliş uçun kod qõşiş">

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-03/src/main.rs:all}}
```

</Listing>

Birinçidan, `use rand::prelude::*;` qatorini qõşamiz. `prelude` moduli
`rand` crate'ining eng kõp işlatiladigan qismlarini õz içiga oladi, va
`use` bu elementlarni dasturimizning iş doirasida mavjud qiladi.

Keyin, õrtaga ikkita qator qõşamiz. Birinçi qatorda, biz foydalanadigan
maxsus tasodifiy son generatorini beruvçi `rand::rng` funksiyasini
çaqiramiz: bu joriy ijro oqimiga (thread) xos va operatsion tizim
tomonidan uruğlantirilgan (seeded) generator. Sõngra, tasodifiy son
generatorida `random_range` metodini çaqiramiz. Bu metod `use
rand::prelude::*;` bayonoti bilan iş doirasiga kiritgan
`rand::prelude` modulining bir qismi bõlgan `RngExt` trait'i tomonidan
aniqlangan. `random_range` metodi argument sifatida diapazon ifodasini
oladi va õşa diapazonda tasodifiy sonni generatsiya qiladi. Biz bu
yerda foydalanayotgan diapazon ifodasi turi `start..=end` şaklida bõlib,
quyi va yuqori çegaralarni ham õz içiga oladi, şuning uçun 1 dan 100
gaça bõlgan sonni sõraş uçun `1..=100` deb kõrsatişimiz kerak.

> Eslatma: siz şunçaki nimani iş doirasiga kiritişni va crate'dan qaysi
> metod va funksiyalarni çaqirişni bilmaysiz, şuning uçun har bir
> crate'da undan foydalaniş bõyiça kõrsatmalar bilan hujjatlar mavjud.
> Cargoning yana bir ajoyib xususiyati — `cargo doc --open` buyruğini
> işga tuşiriş barça boğliqliklaringiz taqdim etgan hujjatlarni mahalliy
> ravişda quradi va uni brauzeringizda oçadi. Agar `rand` crate'idagi
> boşqa funksionallik bilan qiziqsangiz, `cargo doc --open`ni işga
> tuşiring va çap tomondagi yon panelda `rand`ni bosing.

Ikkinçi yangi qator maxfiy sonni çop etadi. Bu dasturni işlab çiqişda
uni sinaş imkonini beriş uçun foydali, ammo biz uni yakuniy versiyadan
õçiramiz. Agar dastur işga tuşişi bilanoq javobni çop etsa, bu unçalik
õyin bõlmaydi-da!

Dasturni bir neça marta işga tuşirib kõring:

<!-- manual-regeneration
cd listings/ch02-guessing-game-tutorial/listing-02-03/
cargo run
4
cargo run
5
-->

```console
$ cargo run
   Compiling guessing_game v0.1.0 (file:///projects/guessing_game)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.02s
     Running `target/debug/guessing_game`
Guess the number!
The secret number is: 7
Please input your guess.
4
You guessed: 4

$ cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.02s
     Running `target/debug/guessing_game`
Guess the number!
The secret number is: 83
Please input your guess.
5
You guessed: 5
```

Siz turli tasodifiy sonlarni olişingiz kerak, va ularning barçasi 1 dan
100 gaça bõlgan sonlar bõlişi kerak. Agar ogohlantiriş olsangiz, ularni
eʼtiborsiz qoldiraverişingiz mumkin. Agar xatoliklar olsangiz, iltimos
*Cargo.toml* faylingizda `rand = "0.10.1"` borligini tekşiring, çunki
`rand`ning kelajakdagi versiyalari boşqaça API'ga ega bõlişi mumkin,
ammo `0.10` seriyasidagi istalgan versiya bu bobdagi kod bilan işlaşi
kerak.

## Taxminni maxfiy son bilan soliştiriş

Endi bizda foydalanuvçi kirişi va tasodifiy son bor ekan, ularni
soliştirişimiz mumkin. Bu qadam 2-4-listingda kõrsatilgan. Eʼtibor
bering, bu kod hali kompilyatsiya bõlmaydi — buni tuşuntiramiz.

<Listing number="2-4" file-name="src/main.rs" caption="Ikki sonni soliştirişning mumkin bõlgan qaytiş qiymatlarini qayta işlaş">

```rust,ignore,does_not_compile
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-04/src/main.rs:here}}
```

</Listing>

Birinçidan, standart kutubxonadan `std::cmp::Ordering` nomli turni iş
doirasiga kiritib, yana bitta `use` bayonotini qõşamiz. `Ordering` turi
yana bir enum bõlib, `Less`, `Greater` va `Equal` variantlariga ega. Bu
uçtasi ikki qiymatni soliştirganingizda mumkin bõlgan natijalardir.

Keyin, oxiriga `Ordering` turidan foydalanuvçi beşta yangi qator
qõşamiz. `cmp` metodi ikkita qiymatni soliştiradi va soliştirilişi
mumkin bõlgan istalgan narsada çaqirilişi mumkin. U soliştirmoqçi
bõlgan narsangizga referensni oladi: bu yerda, `guess`ni
`secret_number` bilan soliştiryapti. Sõngra u iş doirasiga `use`
bayonoti bilan kiritilgan `Ordering` enumining bir variantini qaytaradi.
Biz `cmp`ni `guess` va `secret_number` dagi qiymatlar bilan çaqiriş
natijasida qaytarilgan `Ordering`ning qaysi varianti asosida keyin nima
qilişni hal qiliş uçun [`match`][match]<!-- ignore --> ifodasidan
foydalanamiz.

`match` ifodasi _tarmoqlar_dan tuziladi. Tarmoq — soliştiriş uçun
_şablon_ va agar `match`ga berilgan qiymat õşa tarmoqning şabloniga
mos kelsa işga tuşişi kerak bõlgan koddan iborat. Rust `match`ga berilgan
qiymatni oladi va har bir tarmoqning şablonini navbat bilan kõrib
çiqadi. Şablonlar va `match` konstruksiyasi Rustning kuçli
xususiyatlaridir: ular kodingiz duç kelişi mumkin bõlgan turli xil
holatlarni ifodalaş imkonini beradi va ularning barçasini qayta işlaşni
taʼminlaydi. Bu xususiyatlar mos ravişda 6-bob va 19-bobda batafsil
yoritiladi.

`match` ifodasi bilan boğliq misolni kõrib çiqaylik — bu yerda
foydalanuvçi 50ni Taxmin qilgan va şu safar tasodifiy generatsiya
qilingan maxfiy son 38 bõlsin.

Kod 50ni 38 bilan soliştirganda, `cmp` metodi `Ordering::Greater`ni
qaytaradi, çunki 50, 38dan katta. `match` ifodasi `Ordering::Greater`
qiymatini oladi va har bir tarmoqning şablonini tekşira boşlaydi. U
birinçi tarmoqning şabloni bõlgan `Ordering::Less`ga qaraydi va
`Ordering::Greater` qiymati `Ordering::Less`ga mos kelmasligini kõrib,
õşa tarmoqdagi kodni eʼtiborsiz qoldirib, keyingi tarmoqqa õtadi.
Keyingi tarmoqning şabloni `Ordering::Greater` — bu esa aynan
`Ordering::Greater`ga mos keladi! Şu tarmoqdagi boğliq kod işga tuşadi
va ekranga `Too big!` deb çop etadi. `match` ifodasi birinçi
muvaffaqiyatli mos kelişdan sõng tugaydi, şuning uçun bu ssenariyda oxirgi
tarmoqqa qaramaydi.

Ammo, 2-4-listingdagi kod hali kompilyatsiya bõlmaydi. Keling, sinab
kõraylik:

<!--
The error numbers in this output should be that of the code **WITHOUT** the
anchor or snip comments
-->

```console
{{#include ../listings/ch02-guessing-game-tutorial/listing-02-04/output.txt}}
```

Xatoning mağzi — _mos kelmagan turlar_ borligida. Rustda kuçli, statik
tur tizimi bor. Şu bilan birga, unda tur çiqarişi (inference) ham
mavjud. Biz `let mut guess = String::new()` deb yozganimizda, Rust
`guess` `String` bõlişi kerakligini çiqarib olişga qodir edi va bizga
turni yozişni majbur qilmadi. `secret_number` esa, boşqa tomondan, son
turidir. Rustning bir neça son turlari 1 dan 100 gaça qiymatga ega
bõlişi mumkin: `i32` — 32-bitli son; `u32` — işorasiz 32-bitli son;
`i64` — 64-bitli son; şuningdek boşqalari. Boşqaça kõrsatilmagan bõlsa,
Rust standart bõyiça `i32`ga õtadi, bu esa Rust boşqa joyda boşqa son
turini çiqarib olişga sabab bõladigan tur maʼlumotini qõşmasangiz,
`secret_number`ning turi bõladi. Xatoning sababi — Rust satr va son
turini soliştira olmasligidadir.

Oxir-oqibat, biz dastur foydalanuvçi kirişi sifatida õqigan `String`ni
maxfiy son bilan sonli tarzda soliştira olişimiz uçun son turiga
aylantirmoqçimiz. Buni `main` funksiya tanasiga quyidagi qatorni qõşib
amalga oşiramiz:

<span class="filename">Fayl nomi: src/main.rs</span>

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/no-listing-03-convert-string-to-number/src/main.rs:here}}
```

Bu qator:

```rust,ignore
let guess: u32 = guess.trim().parse().expect("Please type a number!");
```

Biz `guess` nomli õzgaruvçi yaratamiz. Ammo bir daqiqa, dasturda
allaqaçon `guess` nomli õzgaruvçi yõq edimi? Bor edi, ammo Rust bizga
`guess`ning avvalgi qiymatini yangisi bilan _soyalaş_ (şadowing)
imkonini beradi. _Şadowing_ bizga `guess_str` va `guess` kabi ikkita
alohida õzgaruvçi yaratişga majburlaş õrniga `guess` õzgaruvçi nomidan
qayta foydalaniş imkonini beradi. Buni [3-bobda][shadowing]<!-- ignore
--> batafsilroq yoritamiz, ammo hozirça, bu xususiyat kõpinça bir
qiymatni bir turdan boşqa turga aylantirmoqçi bõlganingizda
işlatilişini biling.

Biz bu yangi õzgaruvçini `guess.trim().parse()` ifodasiga boğlaymiz.
Ifodadagi `guess` — kiriş satr sifatida saqlangan asl `guess`
õzgaruvçisiga işora qiladi. `String` nusxasida `trim` metodi boşida va
oxiridagi istalgan bõş joyni yõq qiladi, buni satrni faqat sonli
maʼlumotni saqlaşi mumkin bõlgan `u32`ga aylantirişdan oldin bajarişimiz
şart. Foydalanuvçi Taxminini kiritiş uçun `read_line`ni qanoatlantiriş
uçun <kbd>enter</kbd> tugmasini bosişi kerak, bu esa satrga yangi qator
belgisini qõşadi. Masalan, agar foydalanuvçi <kbd>5</kbd>ni kiritib
<kbd>enter</kbd>ni bossa, `guess` şunday kõrinadi: `5\n`. `\n` "yangi
qator"ni bildiradi. (Windows'da <kbd>enter</kbd>ni bosiş karetani
qaytariş va yangi qatorni, `\r\n`, keltirib çiqaradi.) `trim` metodi
`\n` yoki `\r\n`ni yõq qilib, faqat `5`ni qoldiradi.

Satrlardagi [`parse` metodi][parse]<!-- ignore --> satrni boşqa turga
aylantiradi. Bu yerda biz undan satrni songa aylantiriş uçun
foydalanamiz. Rustga `let guess: u32` yordamida aynan qaysi son turini
xohlaşimizni aytişimiz kerak. `guess`dan keyingi ikki nuqta (`:`) Rustga
õzgaruvçining turini belgilamoqçi ekanligimizni bildiradi. Rustda bir
qança õrnatilgan son turlari bor; bu yerda kõrgan `u32` — işorasiz,
32-bitli butun son. Bu kiçik musbat son uçun yaxşi standart tanlovdir.
Boşqa son turlari haqida [3-bobda][integers]<!-- ignore --> õrganasiz.

Bundan taşqari, bu misol dasturidagi `u32` belgisi va `secret_number`
bilan soliştiriş, Rustga `secret_number` ham `u32` bõlişi kerakligini
çiqarib olişga imkon beradi. Şunday qilib, endi soliştiriş bir xil
turdagi ikki qiymat orasida bõladi!

`parse` metodi faqat mantiqan songa aylantirilişi mumkin bõlgan
belgilar bilan işlaydi, şuning uçun u osonlikça xatolarga sabab bõlişi
mumkin. Masalan, agar satr `A👍%`ni õz içiga olsa, uni songa aylantirişning
iloji bõlmaydi. Bu muvaffaqiyatsiz bõlişi mumkinligi sababli, `parse`
metodi, xuddi `read_line` metodi kabi (bu haqida yuqorida ["`Result`
bilan mumkin bõlgan muvaffaqiyatsizlikni qayta
işlaş"](#handling-potential-failure-with-result)<!-- ignore --> bõlimida
muhokama qilingan), `Result` turini qaytaradi. Biz bu `Result`ni ham
yana `expect` metodidan foydalanib xuddi şunday qayta işlaymiz. Agar
`parse` satrdan son yarata olmagani uçun `Err` `Result` variantini
qaytarsa, `expect` çaqiruvi õyinni çõktiradi va biz bergan xabarni çop
etadi. Agar `parse` satrni songa muvaffaqiyatli aylantira olsa, u
`Result`ning `Ok` variantini qaytaradi, va `expect` bizga kerak bõlgan
sonni `Ok` qiymatidan qaytaradi.

Endi dasturni işga tuşiraylik:

<!-- manual-regeneration
cd listings/ch02-guessing-game-tutorial/no-listing-03-convert-string-to-number/
touch src/main.rs
cargo run
  76
-->

```console
$ cargo run
   Compiling guessing_game v0.1.0 (file:///projects/guessing_game)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.26s
     Running `target/debug/guessing_game`
Guess the number!
The secret number is: 58
Please input your guess.
  76
You guessed: 76
Too big!
```

Ajoyib! Taxmindan oldin bõş joylar qõşilgan bõlsa-da, dastur baribir
foydalanuvçi 76ni Taxmin qilganini aniqladi. Dasturni bir neça marta
işga tuşirib, turli kiriş turlari bilan turli xatti-harakatlarni
tekşiring: sonni tõğri Taxmin qiling, juda katta sonni Taxmin
qiling va juda kiçik sonni Taxmin qiling.

Endi õyinimizning kõp qismi işlamoqda, ammo foydalanuvçi faqat bitta
Taxmin qila oladi. Keling, buni sikl qõşib õzgartiraylik!

## Sikl bilan bir neça Taxminga ruxsat beriş

`loop` kalit sõzi çeksiz siklni yaratadi. Foydalanuvçilarga sonni
Taxmin qiliş uçun kõprroq imkoniyat beriş uçun sikl qõşamiz:

<span class="filename">Fayl nomi: src/main.rs</span>

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/no-listing-04-looping/src/main.rs:here}}
```

Kõrib turganingizdek, biz Taxmin kirişi sõroviçidan boşlab hamma
narsani sikl içiga kõçirdik. Sikl içidagi qatorlarni yana tõrtta bõşliq
bilan çekiniş (indent) qilişni unutmang va dasturni qayta işga tuşiring.
Endi dastur foydalanuvçidan çeksiz ravişda yana bir Taxminni sõraydi,
bu esa aslida yangi muammoni keltirib çiqaradi. Foydalanuvçi çiqib
ketolmaydigandek tuyuladi!

Foydalanuvçi doim <kbd>ctrl</kbd>-<kbd>C</kbd> klaviatura tugma
birikmasidan foydalanib dasturni tõxtatişi mumkin. Ammo bu tõyimsiz
maxluqdan qutulişning yana bir yõli bor — bu haqida ["Taxminni maxfiy
son bilan soliştiriş"](#comparing-the-guess-to-the-secret-number)<!--
ignore --> bõlimidagi `parse` muhokamasida aytib õtilgan edi: agar
foydalanuvçi son bõlmagan javob kiritsa, dastur çõkib tuşadi. Buni
foydalanuvçiga çiqib ketiş imkonini beriş uçun quyidagiça foydalanişimiz
mumkin:

<!-- manual-regeneration
cd listings/ch02-guessing-game-tutorial/no-listing-04-looping/
touch src/main.rs
cargo run
(too small guess)
(too big guess)
(correct guess)
quit
-->

```console
$ cargo run
   Compiling guessing_game v0.1.0 (file:///projects/guessing_game)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.23s
     Running `target/debug/guessing_game`
Guess the number!
The secret number is: 59
Please input your guess.
45
You guessed: 45
Too small!
Please input your guess.
60
You guessed: 60
Too big!
Please input your guess.
59
You guessed: 59
You win!
Please input your guess.
quit

thread 'main' (6694925) panicked at src/main.rs:28:47:
Please type a number!: ParseIntError { kind: InvalidDigit }
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
```

`quit` deb yozib kiritiş õyinni tugatadi, ammo diqqat qilsangiz, bunga
istalgan boşqa sonsiz kiriş ham sabab bõladi. Bu, yumşoq qilib
aytganda, unçalik yaxşi emas; biz õyinning tõğri son Taxmin
qilinganda ham tõxtaşini xohlaymiz.

### Tõğri Taxmindan keyin çiqib ketiş

Keling, õyinni `break` bayonotini qõşib, foydalanuvçi yutganda tõxtaşga
dasturlaymiz:

<span class="filename">Fayl nomi: src/main.rs</span>

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/no-listing-05-quitting/src/main.rs:here}}
```

`You win!`dan keyin `break` qatorini qõşiş dasturni foydalanuvçi maxfiy
sonni tõğri Taxmin qilganda sikldan çiqişga majbur qiladi. Sikldan
çiqiş dasturdan çiqiş degani ham, çunki sikl `main`ning oxirgi qismidir.

### Notõğri kirişni qayta işlaş

Õyinning xatti-harakatini yanada takomillaştiriş uçun, foydalanuvçi
sonsiz maʼlumot kiritganda dasturni çõktiriş õrniga, keling õyinni
sonsiz kirişni eʼtiborsiz qoldirib, foydalanuvçining Taxmin qiliş-ni
davom ettirişiga imkon beraylik. Buni `guess`ning `String`dan `u32`ga
aylantirilgan qatorini õzgartirib amalga oşira olamiz, 2-5-listingda
kõrsatilganidek.

<Listing number="2-5" file-name="src/main.rs" caption="Sonsiz bashoratni eʼtiborsiz qoldirib, dasturni çõktiriş õrniga yana bir bashoratni sõraş">

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-05/src/main.rs:here}}
```

</Listing>

Biz xatoda çõkiş õrniga xatoni qayta işlaş uçun `expect` çaqiruvidan
`match` ifodasiga õtamiz. Esingizda bõlsin, `parse` `Result` turini
qaytaradi va `Result` — `Ok` va `Err` variantlariga ega enum. Biz bu
yerda ham, `cmp` metodining `Ordering` natijasi bilan qilganimizdek,
`match` ifodasidan foydalanamiz.

Agar `parse` satrni songa muvaffaqiyatli aylantira olsa, u natijaviy
sonni õz içiga olgan `Ok` qiymatini qaytaradi. Õşa `Ok` qiymati
birinçi tarmoqning şabloniga mos keladi, va `match` ifodasi oddiygina
`parse` yaratgan va `Ok` qiymati içiga qõygan `num` qiymatini qaytaradi.
Õşa son biz yaratayotgan yangi `guess` õzgaruvçisida xohlagan joyimizda
qoladi.

Agar `parse` satrni songa aylantira olmasa, u xato haqida kõprroq
maʼlumotni õz içiga olgan `Err` qiymatini qaytaradi. `Err` qiymati
birinçi `match` tarmoğidagi `Ok(num)` şabloniga mos kelmaydi, ammo u
ikkinçi tarmoqdagi `Err(_)` şabloniga mos keladi. Pastki çiziq, `_`,
hamma narsani uşlovçi qiymatdir; bu misolda, biz içida qanday
maʼlumot bõlişidan qatʼiy nazar barça `Err` qiymatlarini mos kelişini
xohlayotganimizni bildiryapmiz. Şunday qilib, dastur ikkinçi tarmoqning
kodini, `continue`ni işga tuşiradi, bu esa dasturga `loop`ning keyingi
iteratsiyasiga õtib, yana bir Taxminni sõraşni bildiradi. Şunday qilib,
aslida dastur `parse` duç kelişi mumkin bõlgan barça xatolarni
eʼtiborsiz qoldiradi!

Endi dasturdagi hamma narsa kutilganidek işlaşi kerak. Keling, sinab
kõraylik:

<!-- manual-regeneration
cd listings/ch02-guessing-game-tutorial/listing-02-05/
cargo run
(too small guess)
(too big guess)
foo
(correct guess)
-->

```console
$ cargo run
   Compiling guessing_game v0.1.0 (file:///projects/guessing_game)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.13s
     Running `target/debug/guessing_game`
Guess the number!
The secret number is: 61
Please input your guess.
10
You guessed: 10
Too small!
Please input your guess.
99
You guessed: 99
Too big!
Please input your guess.
foo
Please input your guess.
61
You guessed: 61
You win!
```

Ajoyib! Bitta kiçkina õzgariş bilan, Taxmin õyinini tugatamiz.
Eslatib õtaylik, dastur hali ham maxfiy sonni çop etib turibdi. Bu
sinaş uçun yaxşi işlagan edi, ammo bu õyinni buzadi. Keling, maxfiy
sonni çiqaruvçi `println!`ni õçiraylik. 2-6-listing yakuniy kodni
kõrsatadi.

<Listing number="2-6" file-name="src/main.rs" caption="Tõliq bashorat õyini kodi">

```rust,ignore
{{#rustdoc_include ../listings/ch02-guessing-game-tutorial/listing-02-06/src/main.rs}}
```

</Listing>

Bu bosqiçda, siz Taxmin õyinini muvaffaqiyatli qurdingiz.
Tabriklaymiz!

## Xulosa

Bu loyiha sizni kõplab yangi Rust tuşunçalari bilan amaliy tarzda
tanıştirdi: `let`, `match`, funksiyalar, taşqi crate'lardan foydalaniş
va boşqa kõp narsalar. Keyingi bir neça bobda bu tuşunçalar haqida
batafsilroq õrganasiz. 3-bob kõpçilik dasturlaş tillarida mavjud bõlgan
tuşunçalarni, masalan õzgaruvçilar, maʼlumot turlari va funksiyalarni
qamrab oladi va ulardan Rustda qanday foydalanişni kõrsatadi. 4-bob
Rustni boşqa tillardan farqlantiruvçi xususiyat bõlgan ownerşip'ni
õrganadi. 5-bob struct'lar va metod sintaksisini muhokama qiladi, 6-bob
esa enum'lar qanday işlaşini tuşuntiradi.

[prelude]: ../std/prelude/index.html
[variables-and-mutability]: ch03-01-variables-and-mutability.html#variables-and-mutability
[comments]: ch03-04-comments.html
[string]: ../std/string/struct.String.html
[iostdin]: ../std/io/struct.Stdin.html
[read_line]: ../std/io/struct.Stdin.html#method.read_line
[result]: ../std/result/enum.Result.html
[enums]: ch06-00-enums.html
[expect]: ../std/result/enum.Result.html#method.expect
[recover]: ch09-02-recoverable-errors-with-result.html
[randcrate]: https://crates.io/crates/rand
[semver]: http://semver.org
[cratesio]: https://crates.io/
[doccargo]: https://doc.rust-lang.org/cargo/
[doccratesio]: https://doc.rust-lang.org/cargo/reference/publishing.html
[match]: ch06-02-match.html
[shadowing]: ch03-01-variables-and-mutability.html#shadowing
[parse]: ../std/primitive.str.html#method.parse
[integers]: ch03-02-data-types.html#integer-types
