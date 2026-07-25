## Hello, World!

Endi siz Rustni õrnatdingiz, hozir sizning birinçi Rust dasturingizni yozişning ayni vaqti.
Yangi dasturlaş tilini õrganişda `Hello, World!` matnini ekranga çop etuvçi kiçik va sodda
dastur tuziş an'anaga aylangan, şunday ekan biz ham sinab kõramiz!

> Eslatma: Bu kitob terminal bilan işlay olişning boşlanğiç kõnikmalarini
> talab qiladi. Rust sizning kod muxarriringiz foydalanadigan asboblaringiz va
> kodingizni qayerda joylaşişi bõyiça talablar qõymaydi, şuning uçun agar siz
> terminal õrniga integratsiyalaşgan işlab çiqiş muhitidan (IDE) foydalanişni afzal kõrsangiz,
> õzingizning sevimli IDE-dan foydalaning. Kõpgina IDElar endi ma'lum darajada
> Rust-ni qõllab-quvvatlaydi; tafsilotlar uçun IDE hujjatlarini tekşiring.
> Rust jamoasi `rust-analyzer` orqali ajoyib IDE yordamini ta'minlaşga e'tibor qaratdi.
> Batafsil ma’lumot uçun [D ilovasi][devtools]<!-- ignore -->ni kõzdan keçiring.

### Loyiha jildini yaratiş

Siz işni Rust kodingizni joylaytiriş uçun jild yaratişdan boşlaysiz.
Rust uçun sizning kodingiz qayerda joylaşining ahamiyati yõq, lekin biz
bu kitobdagi maşq va loyihalarni joylaş uçun *projects* nomli jild yaratişingizni
maslahat beramiz.

Terminalni oçing va *projects* jildini yaratiş va uning içidan “Hello, world!” loyihasi
jildini yaratiş uçun quyidagi buyruqlarni kiriting.

Linux, macOS va Windows Powerşell uçun:

```console
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

Windows CMD uçun:

```cmd
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

### Rust dasturi yoziş va işga tuşiriş.

Endi, *main.rs* nomli yangi fayl yarating. Rust kodlar har doim *.rs* kengaytmasi
bilan tugaydi. Agar fayl nomida bir neçta sõzlardan foydalansangiz, ularni ajratiş uçun pastki çiziqdan foydalaniş şart. Masalan, *helloworld.rs* õrniga *hello_world.rs* dan foydalaning.

Endi hozirgina yaratgan *main.rs* faylingizni kod muharririda oçing.

<span class="filename">Fayl nomi: main.rs</span>

```rust
fn main() {
    println!("Hello, world!");
}
```

<span class="caption">Rõyxat 1-1: `Hello, world!` ni çop etuvçi dastur</span>

Faylni saqlang va Terminalda *~/projects/hello_world* jildiga qayting.
Linux yoki macOS da faylni kompilyatsiya qiliş va işga tuşiriş uçun quyidagi buyruqlarni kiriting:

```console
$ rustc main.rs
$ ./main
Hello, world!
```

Windowsda `./main` ning õrniga `.\main.exe` buyruğini kiriting:

```powershell
> rustc main.rs
> .\main.exe
Hello, world!
```
Operatsion tizimingizdan qat'i nazar, terminalda `Hello, world!` qatori çop etilişi kerak.Agar siz uşbu çiqişni kõrmasangiz, yordam oliş usullari uçun Õrnatiş bõlimining [”Muammolarni bartaraf etiş”][troubleshooting]<!-- ignore --> bõlimiga qayting.

Agar `Hello, world!` çop etilgan bõlsa, tabriklaymiz! Siz rasmiy ravişda Rust dasturini yozdingiz. Bu sizni Rust dasturçisiga aylantiradi - xuş kelibsiz!

### Rust dasturining tuzilişi.

Keling "Hello, world!" dasturiga çuqurroq nazar solamiz. Boşqotirmaning 1-qismi:

```rust
fn main() {

}
```

Bu qatorlar `main` nomli funksiyani e'lon qiladi. `main` funksiyasi alohida: u har doim bajariladigan Rust dasturida işlaydigan birinçi koddir. Bu yerda birinçi satr heç qanday parametrga ega bõlmagan va heç narsani qaytarmaydigan `main` funksiyasini eʼlon qiladi.
Agar parametrlar mavjud bõlsa, ular `()` qavslar içiga kiradi.

Funksiyasing tanasi `{}` bilan õralgan. Rust har bir funksiyalarda e'lon qilişda
`{}` dan foydalanişni talab qiladi.

> Eslatma: Agar siz Rust loyihalarda standart usulda kod yozmoqçi bõlsangiz
> kodingizni maʼlum bir uslubda formatlaş uçun `rustfmt` nomli avtomatik formatlaş vositasidan
> foydalanişingiz mumkin (batafsilroq `rustfmt` [D ilovasi][devtools]<!-- ignore --> -da)
> Rust jamoasi uşbu vositani standart Rust distributiviga kiritdi,
> çunki `rustc` kabi, u allaqaçon kompyuteringizga õrnatilgan bõlişi kerak!

`main` funksiyaning tanasi quyidagi kodni õz içiga oladi:

```rust
    println!("Hello, world!");
```

Şu bir qator kod şu kiçik dasturdagi barça işni amalga oşiardi: u
matnni ekranga çop etadi.Bu yerda ahamiyat qaratiş zarur bõlgan
tõrtta muhim narsalar bor.

<!-- Birinchidan, Rust stili 4ta bo'sh joydan iborat 1ta tabdan emas. -->
Birinçidan, Rust style tõrtta bõşliqdan iborat tab emas

Ikkinçidan, `println!` Rust makrosini çaqiradi. Agar u funktsiyani õrniga çaqirgan bõlsa, u `println` (`!` belgisiz) sifatida kiritiladi. Biz Rust makrolari haqida 19-bobda batafsilroq muhokama qilamiz.Hozirça siz şuni bilişingiz kerakki, `!` belgisidan foydalaniş oddiy funksiya õrniga makrosni çaqirayotganingizni anglatadi va makrolar har doim ham funksiyalar bilan bir xil qoidalarga amal qilmaydi.

Uçinçidan, siz `"Hello, world!"` qatorini kõrasiz. Bu satrni argument sifatida `println!` ga uzatamiz va satr ekranga çop etiladi.

Tõrtinçidan, satrni nuqtali vergul (`;`) bilan tugatamiz, bu esa bu ifoda tugaganligini va keyingisi boşlaşga tayyorligini bildiradi. Rust kodining aksariyat satrlari nuqtali vergul bilan tugaydi.


### Kompilyatsiya va işga tuşiriş alohida bosqiçlardir

Siz yangi yaratilgan dasturni işga tuşirdingiz, şuning uçun jarayonning har bir bosqiçini kõrib çiqamiz.

Rust dasturini işga tuşirişdan oldin uni Rust kompilyatoridan foydalanib, `rustc` buyruğini kiritib, unga manba faylingiz nomini quyidagi tarzda kiritişingiz kerak:

```console
$ rustc main.rs
```

Agar siz C yoki C++ bilan işlagan bõlsangiz, bu `gcc` yoki `clang` ga õxşaşligini sezasiz. Muvaffaqiyatli kompilyatsiyadan sõng Rust binary bajariladigan faylni çiqaradi.

Linux, macOS va Windows-dagi PowerŞell-da siz şelldagi `ls` buyruğini kiritiş orqali bajariladigan faylni kõrişingiz mumkin:


```console
$ ls
main  main.rs
```

Linux va macOS-da siz ikkita faylni kõrasiz. Windows-dagi PowerŞell bilan siz CMD-dan foydalangan holda kõrgan uçta faylni kõrasiz. Windows-da CMD bilan siz quyidagilarni kiritasiz:


```cmd
> dir /B %= the /B faqat fayl nomlarini ko'rsatishni aytadi =%
main.exe
main.pdb
main.rs
```

Bu sizga *.rs* kengaytmali kod faylini, bajariluvçi faylni(Windowsda `main.exe`
boşqa barça tizimlarda `main`), va Windowsdan foydalanayotganingizda, debugging 
ma'lumotlarini õz içida saqlovçi *.pdb* kengaytmali faylni kõrsatadi.

Bu yerdan siz *main* yoki *main.exe* faylini işga tuşirasiz, masalan:

```console
$ ./main # or .\Windows-da main.exe
```

Agar sizning *main.rs* faylingiz “Hello, world!” dasturi bõlsa, bu dastur
ekranga `Hello, world!` matnini çop etadi.

Agar siz Ruby, Python yoki JavaScript kabi dinamik tilni yaxşi bilsangiz, dasturni alohida bosqiçlar sifatida kompilyatsiya qiliş va işga tuşirişga odatlanmagan bõlişingiz mumkin. Rust - bu oldindan tuzilgan kompilyatsiya tili, ya'ni siz dasturni kompilyatsiya qilişingiz va bajariladigan faylni boşqa birovga berişingiz mumkin va ular Rustni õrnatmasdan ham uni işga tuşirişlari mumkin.Agar siz kimgadir *.rb*, *.py* yoki *.js* faylini bersangiz, ularda Ruby, Python yoki JavaScript ilovasi õrnatilgan bõlişi kerak (mos ravişda). Ammo bu tillarda dasturni kompilyatsiya qiliş va işga tuşiriş uçun faqat bitta buyruq kerak bõladi. Til dizaynida hamma narsa õzaro kelişuvdir.

Oddiy dasturlar uçun `rustc` bilan kompilyatsiya qiliş juda mos keladi, lekin loyihangiz õsib borişi bilan siz barça variantlarni boşqarişni va kodingizni almaşişni osonlaştirişni xohlaysiz.
Endi, biz siz bilan haqiqiy Rust dasturlarini tuzişda qulaylik yaratuvçi
Cargo yordamçisi bilan tanişamiz.

[troubleshooting]: ch01-01-installation.html#troubleshooting
[devtools]: appendix-04-useful-development-tools.md
