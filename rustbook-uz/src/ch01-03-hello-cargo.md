## Hello, Cargo!

Cargo - bu Rustning build tizimi va paketlar menejeri. Aksariyat Rustaceanlar õzlarining Rust loyihalarini boşqariş uçun uşbu vositadan foydalanadilar, çunki Cargo siz uçun kodni yaratiş, kodingizga boğliq kutubxonalarni yuklab oliş va uşbu kutubxonalarni yaratiş kabi kõplab vazifalarni bajaradi.(Biz sizning kodingizga kerak bõlgan kutubxonalarni çaqiramiz
*dependencies*.)

Eng oddiy Rust dasturlari, biz hozirgaça yozganimiz kabi, heç qanday dependencylarga ega emas. Agar biz  “Hello, world!” Cargo bilan loyiha bõlsa, u faqat sizning kodingizni yaratiş bilan şuğullanadigan Cargo qismidan foydalanadi. Murakkab Rust dasturlarini yozganingizda, siz dependencylarni qõşasiz va agar siz Cargo yordamida loyihani boşlasangiz, dependencylarni qõşiş osonroq bõladi.

Rust loyihalarining aksariyati Cargolardan foydalanganligi sababli, uşbu kitobning qolgan qismida siz ham Cargodan foydalanasiz deb taxmin qilinadi. [Õrnatiş][installation]<!-- ignore -->  bõlimida muhokama qilingan rasmiy õrnatuvçilardan foydalansangiz, Cargo Rust bilan birga keladi. Agar siz Rust-ni boşqa vositalar orqali õrnatgan bõlsangiz, terminalingizga quyidagilarni kiritiş orqali Cargo õrnatilganligini tekşiring:

```console
$ cargo --version
```

Agar siz versiya raqamini kõrsangiz, sizda bor! Agar siz `command not found` kabi xatolikni kõrsangiz, Cargoni qanday qilib alohida õrnatiş bõyiça texnik hujjatlarni kõrib çiqing.

### Cargo bilan loyiha yaratiş

Keling, Cargo-dan foydalanib yangi loyiha yarataylik va u bizning asl “Hello, world!” loyihadan qanday farq qilişini kõrib çiqaylik. `projects` jildiga (yoki kodingizni saqlaşga qaror qilgan joyingizga) qayting. Keyin istalgan operatsion tizimda quyidagilarni bajaring:

```console
$ cargo new hello_cargo
$ cd hello_cargo
```

Birinçi buyruq *hello_cargo* nomli yangi jild va loyihani yaratadi.
Biz loyihamizga *hello_cargo* deb nom berdik va Cargo õz fayllarini xuddi şu nomdagi jildda yaratadi.

*hello_cargo* jildiga õting va fayllar rõyxatini kõring.Cargo biz uçun ikkita fayl va bitta jild yaratganini kõrasiz: *Cargo.toml* fayli va içida *main.rs* fayli bõlgan *src* jildi.

Şuningdek, u *.gitignore* fayli bilan birga yangi Git repositoryni işga tuşirdi. Mavjud Git repositoryda `cargo new` ni işga tuşirsangiz, Git fayllari yaratilmaydi; `cargo new - vcs=git` yordamida bu xatti-harakatni bekor qilişingiz mumkin.

> Eslatma: Git — keng tarqalgan versiyalarni boşqariş tizimidir. Siz `--vcs` parametri
> yordamida `cargo new`'ni boşqa *versiyalarni boşqariş tizimi*dan foydalanadigan qilib
> yoki umuman versiyalarni boşqariş tizimisiz işlaydigan qilib õzgartirişingiz mumkin.
> Mavjud parametrlarni kõriş uçun `cargo new --help` buyruğini işga tuşiring.

Siz tanlagan matn muharririda `Cargo.toml`'ni oçing. U 1-2 rõyxatdagi kodga õxşaş bõlişi kerak.

<span class="filename">Fayl nomi: Cargo.toml</span>

```toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

<span class="caption">Rõyxat 1-2: `cargo new` tomonidan yaratilgan *Cargo.toml* tarkibi</span>

Bu fayl [*TOML*][toml]<!-- ignore --> da (*Tom’s Obvious, Minimal
Language*) formati, bu Cargo konfiguratsiya formati.

Birinçi qator, `[package]`, bõlim sarlavhasi bõlib, undan keyingi iboralar paketni sozlayotganligini bildiradi. Uşbu faylga qõşimça malumot qõşsak, biz boşqa bõlimlarni qõşamiz.

Keyingi uçta qator Cargõga dasturingizni kompilyaçiya qilişi uçun kerak bõlgan sozlaş malumotlarini belgilaydi: nomi, versiyasi va işlatiladigan Rust naşri (edition). Edition
kaliti haqida [E ilovasi][appendix-e]<!-- ignore -->da gaplaşamiz.

Oxirgi qator, `[dependencies]`, loyihangizning har qanday dependencylarini rõyxatlaş uçun bõlimning boşlanişi. Rustda kod paketlari *crates* deb ataladi. Uşbu loyiha uçun bizga boşqa cratelar kerak bõlmaydi, lekin biz 2-bobdagi birinçi loyihada bõlamiz, şuning uçun biz uşbu dependencies bõlimidan foydalanamiz.

Endi *src/main.rs* oçing va qarang:

<span class="filename">Fayl nomi: src/main.rs</span>

```rust
fn main() {
    println!("Hello, world!");
}
```

Cargo siz uçun "Hello, world!" dasturini yaratdi — xuddi biz 1-1-rõyxatda yozgan dasturga õxşaş! Hozirça bizning loyihamiz bilan Cargo yaratgan loyiha orasidagi farq şundan iborat: Cargo kodni `src` katalogiga joylaştirdi, va bizda yuqori
katalogda `Cargo.toml` konfiguratsiya fayli bor.

Cargo manba fayllaringiz `src` katalogi içida bõlişini kutadi. Eng yuqori darajadagi loyiha katalogi esa faqat README fayllari, lisenziya malumoti, konfiguratsiya fayllari va kodingizga aloqador bõlmagan boşqa narsalar uçundir. Cargõdan foydalaniş loyihalaringizni tartibga solişga yordam beradi. Har bir
narsa uçun õz õrni bor, va har bir narsa õz õrnida turadi.

Agar Cargo'dan foydalanmaydigan loyiha boşlagan bõlsangiz — biz "Hello, world!" loyihasida qilganimizdek — uni Cargo'dan foydalanadigan loyihaga õzgartirişingiz mumkin. Loyiha kodini `src` katalogiga kõçiring va mos `Cargo.toml` faylini
yarating. `Cargo.toml` fayli yaratişning oson yõli — `cargo init` buyruğini işga tuşiriş, u buni siz uçun avtomatik yaratadi.

### Cargo loyihasini quriş va işga tuşiriş

Keling, “Hello, world!” ni quriş va işga tuşirişda nima farq qilişini kõrib çiqaylik. Cargo bilan dasturni *hello_cargo* jildidan quyidagi buyruqni kiritiş orqali loyihangizni build qiling:

```console
$ cargo build
   Compiling hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 2.85 secs
```

Uşbu buyruq bajariladigan faylni joriy jildingizda emas, balki *target/debug/hello_cargo* da (yoki Windowsda *target\debug\hello_cargo.exe*)da  yaratadi. Odatiy tuziliş debug tuzilişi bõlgani uçun Cargo binary faylni *debug* nomli jildga joylaştiradi. Uşbu buyruq bilan bajariladigan faylni işga tuşirişingiz mumkin:

```console
$ ./target/debug/hello_cargo # yoki .\target\debug\hello_cargo.exe Windowsda
Hello, world!
```

Agar hammasi yaxşi bõlsa, `Hello, world!` terminalga çop etilişi kerak.`cargo build` ni birinçi marta işga tuşiriş ham Cargoning yuqori darajadagi yangi faylni yaratişiga olib keladi: *Cargo.lock*. Uşbu fayl loyihangizdagi dependencylarning aniq versiyalarini kuzatib boradi. Uşbu loyihada dependencylar yõq, şuning uçun faylda kod biroz kam. Siz heç qaçon uşbu faylni qõlda õzgartirişingiz şart emas; Cargo uning tarkibini siz uçun boşqaradi.

Biz hozirgina `cargo build` orqali loyihasini build qildik va uni `./target/debug/hello_cargo` bilan işga tuşirdik, lekin kodni kompilyatsiya qiliş uçun `cargo run` dan ham foydalanişimiz va natijada bajariladigan faylni bitta buyruqda işga tuşirişimiz mumkin:

```console
$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.0 secs
     Running `target/debug/hello_cargo`
Hello, world!
```

`cargo run` dan foydalaniş `cargo build` ni işga tuşirişdan kõra qulayroqdir va keyin binary yõlni tõliq işlatadi, şuning uçun kõpçilik işlab çiquvçilar `cargo run` dan foydalanadilar.

E'tibor bering, bu safar biz `Hello_cargo` ni kompilyatsiya qilayotganini kõrsatadigan natijani kõrmadik. Cargo fayllar õzgarmaganligini aniqladi, şuning uçun u qayta tiklanmadi, balki binary faylni işga tuşirdi. Agar siz manba kodingizni õzgartirgan bõlsangiz, Cargo loyihani işga tuşirişdan oldin uni qayta build qilgan bõlar edi va siz uşbu natijani kõrgan bõlar edingiz:

```console
$ cargo run
   Compiling hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.33 secs
     Running `target/debug/hello_cargo`
Hello, world!
```

Cargo şuningdek, `cargo check` deb nomlangan buyruqni taqdim etadi. Bu buyruq kompilyatsiya qiliş uçun kodingizni tezda tekşiradi, lekin bajariladigan fayl yaratmaydi:

```console
$ cargo check
   Checking hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.32 secs
```

Nima uçun bajariladigan faylni xohlamaysiz? Kõpinça `cargo check` `cargo build`dan kõra tezroq bõladi,, çunki u bajariladigan faylni yaratiş bosqiçini õtkazib yuboradi. Agar siz kod yoziş paytida işingizni doimiy ravişda tekşirayotgan bõlsangiz, `cargo check` dan foydalaniş loyihangiz hali ham kompilyatsiya qilinayotganligini bildiriş jarayonini tezlaştiradi! Şunday qilib, kõplab Rustaceanlar vaqti-vaqti bilan `cargo check` ni amalga oşiradilar, çunki ular õz dasturlarini kompilyatsiya qilişiga işonç hosil qiliş uçun yozadilar. Keyin ular bajariladigan fayldan foydalanişga tayyor bõlgaç, `cargo build` ni işga tuşiradilar.

Cargo haqida şu paytgaça õrganganlarimizni takrorlaymiz:

* Biz `cargo new` yordamida loyiha yaratamiz.
* `cargo build` yordamida loyihani build qilişimiz mumkin.
* Biz `cargo run` yordamida bir bosqiçda loyiha build qilişimiz va işga tuşirişimiz mumkin.
* `cargo check` yordamida xatolarni tekşiriş uçun binary  işlab çiqarmasdan loyihani build qilişimiz mumkin.
* Build natijasini bizning kodimiz bilan bir xil jildda saqlaş õrniga, Cargo uni *target/debug* jildida saqlaydi.

Cargo-dan foydalanişning qõşimça afzalligi şundaki, qaysi operatsion tizimda işlayotganingizdan qat'i nazar, buyruqlar bir xil bõladi. Şunday qilib, biz endi Linux va MacOS uçun Windows-ga nisbatan maxsus kõrsatmalar bermaymiz.

### Loyihani Reliz qiliş

Loyihangiz nihoyat relizga tayyor bõlgaç, uni optimallaştiriş bilan kompilyatsiya qiliş uçun `cargo build --release` dan foydalanişingiz mumkin. Uşbu buyruq *target/debug* õrniga *target/release* da bajariladigan fayl yaratadi. Optimizatsiya Rust kodingizni tezroq işga tuşiradi, lekin bu kompilyatsiya vaqtini uzaytiradi. Şuning uçun ikkita turli profil mavjud: biri tez va tez-tez qayta tiklamoqçi bõlganingizda işlab çiqiş uçun, ikkinçisi esa oxirgi dasturni yaratiş uçun siz foydalanuvçiga qayta tiklanmaydigan va mkon qadar tez işlaydigan oxirgi dastur. Agar siz kodingizning işlaş vaqtini soliştirmoqçi bõlsangiz, `cargo build --release` dasturini işga tuşiring va *target/release* da bajariladigan fayl bilan taqqoslang.

### Konventsiya sifatida Cargo

Oddiy loyihalar bilan Cargo `rustc` dan foydalanişdan kõra unçalik katta foyda keltirmaydi, ammo dasturlaringiz yanada murakkablaşgani sayin u õz qiymatini isbotlaydi.
Dasturlar bir neçta fayllarga kõpayib rivojlanganda yoki ularga dependency kerak bõlsa, Cargo-ga buildni muvofiqlaştirişga ruxsat beriş ança oson bõladi.

`hello_cargo` loyihasi oddiy bõlsa ham, u endi Rust karyerangizning qolgan qismida foydalanadigan haqiqiy asboblarning kõp qismini işlatadi. Haqiqatan ham, mavjud loyihalar ustida işlaş uçun siz Git yordamida kodni tekşiriş, uşbu loyiha jildiga õzgartiriş va build qiliş uçun quyidagi buyruqlardan foydalanişingiz mumkin:

```console
$ git clone github.com/birorta-loyiha
$ cd birorta-loyiha
$ cargo build
```

Cargo haqida kõproq ma'lumot oliş uçun uning [texnik hujjatlarini][cargo] tekşiring.

## Xulosa

Siz allaqaçon Rust sayohatingizni ajoyib boşladingiz! Uşbu bobda siz quyidagilarni õrgandingiz:

* Rust-ning sõnggi barqaror versiyasini `rustup` yordamida õrnatiş
* Rustning yangi versiyasiga yangilaş
* Mahalliy õrnatilgan texnik hujjatlarni oçiş
* “Hello, world!” deb yozing va işga tuşiring. tõğridan-tõğri `rustc` dan foydalangan holda dastur
* Cargo konventsiyalaridan foydalangan holda yangi loyiha yaratiş va işga tuşiriş

Bu Rust kodini õqiş va yozişga odatlaniş uçun yanada muhimroq dastur yaratiş uçun ajoyib vaqt. Şunday qilib, 2-bobda biz taxminiy õyin dasturini tuzamiz.
Agar siz Rust-da umumiy dasturlaş tuşunçalari qanday işlaşini õrganişni afzal kõrsangiz, 3-bobga qarang va keyin 2-bobga qayting.

[installation]: ch01-01-installation.html#installation
[toml]: https://toml.io
[appendix-e]: appendix-05-editions.html
[cargo]: https://doc.rust-lang.org/cargo/
