## Õrnatiş

Birinçi qadam Rustni õrnatişdir. Rustni Rust versiyalari va tegişli vositalarni boşqariş uçun buyruq qatori vositasi bõlgan `rustup` orqali yuklab olamiz. Yuklab oliş uçun sizga internet ulanişi kerak bõladi.

> Eslatma: Agar biron sababga kõra `rustup` dan foydalanmaslikni xohlasangiz, boşqa variantlar uçun
> [Rustni õrnatişning boşqa usullari][otherinstall] sahifasiga qarang.

Quyidagi qadamlar Rust kompilyatorining sõnggi barqaror versiyasini õrnatadi.
Rustning barqarorligi kafolati kitobdagi kompilyatsiya qilingan barça misollar Rustning yangi versiyalari bilan kompilyatsiya qilişda davom etişini ta'minlaydi. Çiqiş versiyalar orasida biroz farq qilişi mumkin, çunki Rust kõpinça xato xabarlari va ogohlantirişlarni yaxşilaydi. Boşqaça qilib aytadigan bõlsak, uşbu qadamlar yordamida õrnatgan har qanday yangi, barqaror Rust versiyasi uşbu kitob mazmuni bilan kutilganidek işlaşi kerak.

> ### Buyruqlar qatori yozuvi
>
> Uşbu bobda va butun kitobda biz terminalda işlatiladigan ba'zi buyruqlarni kõrsatamiz.
> Terminalga kiritişingiz kerak bõlgan barça qatorlar `$` bilan boşlanadi.
> `$` belgisini kiritişingiz şart emas; bu har bir buyruqning boşlanişini kõrsatiş
> uçun kõrsatilgan buyruq qatori. `$` bilan boşlanmagan qatorlar odatda oldingi buyruqning
> natijasini kõrsatadi. Bundan taşqari, PowerŞell-ga xos misollarda `$` emas, `>` işlatiladi.

### Linux yoki macOS-ga  `rustup` õrnatiş

Agar siz Linux yoki macOS dan foydalansangiz, terminalni oçing va quyidagi buyruqni kiriting:

```console
$ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```

Buyruq skriptni yuklab oladi va Rustning eng sõnggi barqaror versiyasini õrnatadigan `rustup` vositasini õrnatişni boşlaydi. Sizdan parol sõralişi mumkin. Õrnatiş muvaffaqiyatli bõlsa, quyidagi qator paydo bõladi:

```text
Rust is installed now. Great!
```

Şuningdek, sizga  *linker*, kerak bõladi, ya'ni Rust õzining kompilyatsiya qilingan natijalarini bitta faylga birlaştiriş uçun foydalanadigan dastur. Ehtimol,bu sizda allaqaçon mavjud. Agar linker xatolarga duç kelsangiz, odatda linkerni õz içiga olgan C kompilyatorini õrnatişingiz kerak. C kompilyatori ham foydalidir, çunki ba'zi umumiy Rust paketlari C kodiga boğliq va C kompilyatoriga muhtoj bõladi.

MacOS-da siz C kompilyatorini işga tuşiriş orqali olişingiz mumkin:

```console
$ xcode-select --install
```

Linux foydalanuvçilari odatda distributiv texnik hujjatlariga muvofiq GCC yoki Clang õrnatişlari kerak. Misol uçun, agar siz Ubuntu'dan foydalansangiz, `build-essential` paketini õrnatişingiz mumkin.

### Windows-ga `rustup` õrnatiş

Windows tizimida [https://www.rust-lang.org/tools/install][install] saytiga õting va Rustni õrnatiş bõyiça kõrsatmalarga amal qiling. Õrnatişning bir nuqtasida sizga Visual Studio 2013 yoki undan keyingi versiyalari uçun MSVC yaratiş vositalari kerakligi haqida xabar keladi.

Build toolsini oliş uçun [Visual Studio 2022][visualstudio] ni õrnatişingiz kerak bõladi. Qaysi iş dasturlarini õrnatiş kerakligi sõralganda, quyidagilarni  kiriting:

* “Desktop Development with C++”
* TWindows 10 yoki 11 SDK
* Ingliz tili tõplami komponenti va siz tanlagan boşqa tillar tõplami

Uşbu kitobning qolgan qismi *cmd.exe* va PowerŞell da işlaydigan buyruqlardan foydalanadi.
Agar aniq farqlar bõlsa, qaysi birini işlatişni tuşuntiramiz.

### Muammolarni bartaraf etiş

Rust tõğri õrnatilganligini tekşiriş uçun şellni oçing va quyidagi qatorni kiriting:

```console
$ rustc --version
```

Quyidagi formatda çiqarilgan sõnggi barqaror versiya uçun versiya raqami, xeş va tasdiqlangan sanani kõrişingiz kerak:

```text
rustc x.y.z (abcabcabc yyyy-mm-dd)
```

Agar siz uşbu ma'lumotni kõrsangiz, Rustni muvaffaqiyatli õrnatdingiz! Agar siz uşbu ma'lumotni kõrmasangiz, Rust `%PATH%` tizim õzgaruvçingizda quyidagi tarzda ekanligini tekşiring.

Windows CMD-da quyidagilardan foydalaning:

```console
> echo %PATH%
```

PowerŞell-da foydalaning:

```powershell
> echo $env:Path
```

Linux va macOS-da quyidagilardan foydalaning:

```console
$ echo $PATH
```

Agar hammasi tõğri bõlsa va Rust hali ham işlamasa, yordam olişingiz mumkin bõlgan bir qança joylar mavjud. Boşqa Rustaceanlar (biz õzimizni çaqiradigan ahmoqona taxallus) bilan qanday boğlanişni [hamjamiyat sahifasida][community] bilib oling.

### Yangilaş va õçiriş

Rust `rustup` orqali õrnatilgandan sõng, yangi çiqarilgan versiyaga yangilaş oson. Şelldan quyidagi yangilaş skriptini işga tuşiring:

```console
$ rustup update
```

Rust va  `rustup`-ni õçiriş uçun şelldan quyidagi õçiriş skriptini işga tuşiring:

```console
$ rustup self uninstall
```

### Mahalliy texnik hujjatlar

Rust-ning õrnatilişi texnik hujjatlarning mahalliy nusxasini ham õz içiga oladi, şunda siz uni oflayn rejimda õqişingiz mumkin. Brauzeringizda mahalliy texnik hujjatlarni oçiş uçun `rustup doc` dasturini işga tuşiring.

Istalgan vaqtda standart kutubxona tomonidan tur yoki funksiya taqdim etilsa va siz u nima qilişini yoki undan qanday foydalanişni bilmasangiz, biliş uçun amaliy dasturlaş interfeysi (API) texnik hujjatlaridan foydalaning!

[otherinstall]: https://forge.rust-lang.org/infra/other-installation-methods.html
[install]: https://www.rust-lang.org/tools/install
[visualstudio]: https://visualstudio.microsoft.com/downloads/
[community]: https://www.rust-lang.org/community
