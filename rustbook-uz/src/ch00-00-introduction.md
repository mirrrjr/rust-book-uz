# Kiriş

> Eslatma: Kitobning bu naşri [No Starch Press][nsp] tomonidan bosma va
> elektron kitob formatida çiqarilgan [The Rust Programming
> Language][nsprust] bilan bir xil.

[nsprust]: https://nostarch.com/rust-programming-language-3rd-edition
[nsp]: https://nostarch.com/

_The Rust Programming Language_ — Rust haqidagi kiriş kitobiga xuş kelibsiz.
Rust dasturlaş tili sizga tezroq va işonçliroq dasturiy taminot yozişga
yordam beradi. Dasturlaş tillarini loyihalaştirişda yuqori darajali
ergonomika va past darajali nazorat köpinça bir-biriga zid keladi; Rust bu
ziddiyatga qarşi çiqadi. Kuçli texnik imkoniyatlarni ajoyib dasturçi
tajribasi bilan muvozanatlaş orqali, Rust sizga past darajali tafsilotlarni
(masalan, xotiradan foydalanişni) ananaviy ravişda bunday nazorat bilan
boğliq bõlgan qiyinçiliklarsiz boşqariş imkonini beradi.

## Rust Kim Uçun

Rust kõp sabablarga kõra kõpçilik uçun ideal tanlovdir. Keling, eng muhim
guruhlardan bir neçtasini kõrib çiqamiz.

### Dasturçilar Jamoalari

Rust turli darajadagi tizim dasturlaş bilimiga ega bõlgan katta dasturçilar
jamoalari õrtasidagi hamkorlik uçun samarali vosita ekanligini
isbotlamoqda. Past darajali kod turli nozik xatoliklarga moyil bõlib,
kõpçilik boşqa tillarda ular faqat keng kõlamli testlaş va tajribali
dasturçilar tomonidan ehtiyotkorlik bilan kod kõrib çiqiliş orqaligina
aniqlanişi mumkin. Rustda kompilyator ushbu qiyin aniqlanadigan
xatoliklarga, jumladan concurrency xatoliklariga ega kodni kompilyatsiya
qiliş(dan) tortib, darvozabon rolini õynaydi. Kompilyator bilan birga
işlaş orqali jamoa õz vaqtini xatoliklarni izlaş õriga dasturning
mantiğiga qaratişga sarflaşi mumkin.

Rust şuningdek tizim dasturlaş dunyosiga zamonaviy dasturçi vositalarini
olib keladi:

- Cargo — õrnatilgan boğliqliklar boşqaruvçisi va qurilma vositasi —
  boğliqliklarni qõşiş, kompilyatsiya qiliş va boşqarişni butun Rust
  ekotizimida oson va izçil qiladi.
- `rustfmt` formatlaş vositasi dasturçilar õrtasida izçil kodlaş uslubini
  taminlaydi.
- Rust Language Server kod va qator içi xato xabarlari uçun
  integratsiyalaşgan işlab çiqiş muhiti (IDE) integratsiyasini taminlaydi.

Ushbu va boşqa Rust ekotizimidagi vositalardan foydalanib, dasturçilar
tizim darajasidagi kod yozişda samarali işlaşi mumkin.

### Talabalar

Rust talabalar va tizim kontseptsiyalarini örganişga qiziquvçilar uçundir.
Köpçilik odamlar Rust'dan foydalanib operatsion tizimlarni işlab çiqiş
kabi mavzularni õrgangan. Hamjamiyat juda mehmondõst bõlib, talabalarning
savollariga javob berişdan xursand. Uşbu kitob kabi harakatlar orqali,
Rust jamoalari tizim kontseptsiyalarini kõproq odamlarga, ayniqsa
dasturlaşda yangi bõlganlarga kõproq oçiq qiliş(ni) istaydi.

### Kompaniyalar

Yuzlab kompaniyalar, katta va kiçik, Rust'ni işlab çiqarişda turli
vazifalar uçun işlatadi, jumladan buyruq qatori vositalari, veb-xizmatlar,
DevOps vositalari, embedded qurilmalar, audio va video
tahlili va transkodlaş, kriptovalyutalar, bioinformatika, qidiruv
tizimlari, Narsalar Interneti (IoT) ilovalari, maşinali õrganiş, hatto
Firefox veb-brauzerining asosiy qismlari.

### Oçiq Manba Dasturçilari

Rust Rust dasturlaş tilini, hamjamiyatini, dasturçi vositalarini va
kutubxonalarini qurmoqçi bõlgan odamlar uçundir. Sizning Rust tiliga
hissa qõşişingizdan mamnun bõlamiz.

### Tezlik va Barqarorlikni Qadrlovçilar

Rust tili tezlik va barqarorlikka intiluvçi odamlar uçundir. Tezlik
deganda biz ham Rust kodining qançalik tez işlaşi mumkinligini, ham
Rust'ning dasturlar yozişga imkon berişi tezligini nazarda tutamiz. Rust
kompilyatorining tekşiruvlari xususiyatlar qõşiş va refaktoring orqali
barqarorlikni taminlaydi. Bu esa şunday tekşiruvlarga ega bõlmagan
tillardagi mõrt meros (legacy) koddan farqli õloroq, dasturçilar kõpinça
uni õzgartirişdan qõrqişadi. Nolinchi xarajatli abstraksiyalarga — qõlda
yozilgan kod kabi tez past darajali kodga kompilyatsiya qilinadigan
yuqori darajali xususiyatlarga — intiliş orqali, Rust xavfsiz kodni ham
tez kod qiliş(ga) harakat qiladi.

Rust tili boşqa kõplab foydalanuvçilarni ham qõllab-quvvatlaşni umid
qiladi; bu yerda tilga olinganlar shunçaki eng katta manfaatdor
tomonlarning bir qismidir. Umuman olganda, Rust'ning eng katta maqsadi
dasturçilar öçlab yillar davomida qabul qilib kelgan kelişuvlarni —
xavfsizlik *va* samaradorlik, tezlik *va* ergonomika taqdim etiş orqali —
bartaraf etişdir. Rust'ni sinab körüng va uning tanlovlari sizga mos
kelişini körüng.

## Bu Kitob Kim Uçun

Bu kitob sizning boşqa dasturlaş tilida kod yozgan bölişingizni faraz
qiladi, lekin qaysi til ekanligi haqida hiç qanday taxmin qilmaydi. Biz
materialni turli xil dasturlaş kelib çiqişiga ega odamlar uçun keng
qamrovda oçiq qiliş(ga) harakat qildik. Biz dasturlaş nima ekanligi yoki u
haqida qanday öylaş kerakligi haqida köp vaqt sarflamaymiz. Agar siz
dasturlaşda mutlaqo yangi bölsangiz, dasturlaşga maxsus kiriş beruvçi
kitobni öqiş sizga köproq foyda keltiradi.

## Bu Kitobdan Qanday Foydalaniş Kerak

Umuman olganda, bu kitob sizning uni boşidan oxirigaça ketma-ket
öqişingizni faraz qiladi. Keyingi boblar oldingi boblardagi tuşunçalar
asosida quriladi, oldingi boblar esa ma'lum bir mavzu tafsilotlariga
çuqur kirmasligi mumkin, ammo mavzuga keyingi bobda qaytadi.

Bu kitobda ikki xil bob törini topasiz: kontseptual boblar va loyiha
boblari. Kontseptual boblarda siz Rust'ning bir jihati haqida örganasiz.
Loyiha boblarida biz hozirgaça örganganlaringizni qõllagan holda kiçik
dasturlarni birgalikda quramiz. 2-bob, 12-bob va 21-bob loyiha boblari;
qolganlari esa kontseptual boblardir.

**1-bob** Rust'ni qanday ö'rnatiş, "Hello, world!" dasturini qanday yozish
va Cargo'dan — Rust'ning paket boşqaruvçisi va qurilma vositasidan —
qanday foydalanişni tuşuntiradi. **2-bob** Rustda dastur yozişga amaliy
kiriş bölib, sizga son toppiş öyinini quriş(ni) tayinlaydi. Bu yerda biz
kontseptlarni yuqori darajada yoritamiz, keyingi boblar esa qõşimça
tafsilotlarni beradi. Agar darhol amaliyotga kirişmoqçi bölsangiz, 2-bob
aynan shu uçundir. Agar siz keyingisiga ötişdan oldin har bir tafsilotni
örganişni afzal köradigan, ayniqsa puxta örganuvçi bölsangiz, 2-bobni
ötkazib yuborib, toğridan-toğri boşqa dasturlaş tillariga öxşaş Rust
xususiyatlarini yorituvçi **3-bob**ga ötişni istaşingiz mumkin; keyin,
örgangan tafsilotlaringizni qõllaydigan loyiha üstida işlamoqçi
bölganingizda, 2-bobga qaytişingiz mumkin.

**4-bob**da siz Rust'ning ownership tizimi haqida örganasiz. **5-bob**
struct'lar va metodlarni muhokama qiladi. **6-bob** enum'larni, `match`
ifodalarini, hamda `if let` va `let...else` boşqaruv oqimi qurilmalarini
qamrab oladi. Siz maxsus turlarni yaratiş uçun struct'lar va enum'lardan
foydalanasiz.

**7-bob**da siz Rust'ning modul tizimi hamda kodingizni va uning oçiq
dasturlaş interfeysi (API)ni tashkillaştiriş uçun maxfiylik qoidalari
haqida örganasiz. **8-bob** standart kutubxona taqdim etadigan bir qançа
keng tarqalgan tõplam ma'lumotlar tuzilmalarini muhokama qiladi:
vektorlar, satrlar va hash map'lar. **9-bob** Rust'ning xatoliklarni
boşqariş falsafasi va usullarini örganadi.

**10-bob** generic'lar, trait'lar va lifetime'larga çuqur kiradi, bular
sizga köplab turlarga tegişli kodni aniqlaş qudratini beradi. **11-bob**
toliq testlaş haqida bölib, bu hatto Rust'ning xavfsizlik kafolatlari
bilan ham dasturingiz mantig'ining toğriligini ta'minlaş uçun zarurdir.
**12-bob**da biz fayllar içidagi matnni qidiradigan `grep` buyruq qatori
vositasining funksionalligi qismidan öz implementatsiyamizni quramiz.
Buning uçun biz oldingi boblarda muhokama qilgan köplab kontseptlardan
foydalanamiz.

**13-bob** closure'lar va iteratorlarni örganadi: bular funksional
dasturlaş tillaridan kelib çiqqan Rust xususiyatlaridir. **14-bob**da biz
Cargo'ni çuqurroq körib çiqamiz va kutubxonalaringizni boşqalar bilan
bölişişning eng yaxşi amaliyotlari haqida gaplaşamiz. **15-bob** standart
kutubxona taqdim etadigan smart pointer'lar va ularning funksionalligini
ta'minlovçi trait'larni muhokama qiladi.

**16-bob**da biz concurrent dasturlaşning turli modellari boşidan ötamiz
va Rust'ning sizga köp thread'larda qörqmasdan dasturlaş(ga) qanday
yordam berişi haqida gaplaşamiz. **17-bob**da biz buning üstiga
Rust'ning async va await sintaksisini, şuningdek task'lar, future'lar va
stream'larni hamda ular ta'minlaydigan yengil concurrency modelini
örganib, davom ettiramiz.

**18-bob** Rust idiomalari sizga tanış bölgan ob'ektga yönaltirilgan
dasturlaş tamoyillari bilan qanday taqqoslanişini körib çiqadi. **19-bob**
pattern'lar va pattern matching böyiça manba bölib, bular Rust
dasturlarida g'oyalarni ifodalaşning kuçli usullaridir. **20-bob** unsafe
Rust, macro'lar, şuningdek lifetime'lar, trait'lar, turlar, funksiyalar va
closure'lar haqida qõşimça ma'lumotlarni öz içiga olgan qiziqarli
murakkab mavzular tõplamini içeradi.

**21-bob**da biz past darajali köp-thread'li veb-server implementatsiya
qiladigan loyihani yakunlaymiz!

Nihoyat, ba'zi ilovalar til haqida köproq manba körinişidagi foydali
ma'lumotlarni öz içiga oladi. **A-ilova** Rust'ning kalit sözlarini,
**B-ilova** Rust'ning operatorlari va belgilarini, **C-ilova** standart
kutubxona taqdim etadigan derivable trait'larni, **D-ilova** ba'zi
foydali işlab çiqiş vositalarini qamrab oladi, **E-ilova** esa Rust
nashrlarini (editions) tuşuntiradi. **F-ilova**da kitobning tarjimalarini
topişingiz mumkin, **G-ilova**da esa Rust qanday yaratilganini va
nightly Rust nima ekanligini qamrab olamiz.

Bu kitobni öqişning notöğri usuli yöq: agar oldinga ötmoqçi bölsangiz,
marhamat! Agar biror çalkaşlikka duç kelsangiz, oldingi boblarga
qaytişingiz kerak bölişi mumkin. Ammo özingizga mos keladigan narsani
qiling.

<span id="ferris"></span>

Rustni örganiş jarayonining muhim qismi kompilyator körsatadigan xato
xabarlarini qanday öqişni örganişdir: ular sizni işlaydigan kodga
yönaltiradi. Şu sababli, biz kompilyatsiya qilinmaydigan köplab
misollarni, har bir holatda kompilyator körsatadigan xato xabari bilan
birga taqdim etamiz. Bilib qõying: agar tasodifiy misolni kiritib işga
tuşirsangiz, u kompilyatsiya qilinmasligi mumkin! Işga tuşirmoqçi
bölgan misolingiz xato beriş uçun möljallanganmi-yöqmi(ni) körish uçun
atrofdagi matnni öqiganingizga işonç hosil qiling. Köpçilik holatlarda
biz sizni kompilyatsiya qilinmaydigan har qanday kodning toğri
versiyasiga yönaltiramiz. Ferris şuningdek işlaşi möljallanmagan kodni
ajratib olişda sizga yordam beradi:

| Ferris                                                                                                           | Ma'no                                           |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| <img src="img/ferris/does_not_compile.svg" class="ferris-explain" alt="Ferris with a question mark"/>            | Bu kod kompilyatsiya qilinmaydi!                 |
| <img src="img/ferris/panics.svg" class="ferris-explain" alt="Ferris throwing up their hands"/>                   | Bu kod panic qiladi!                             |
| <img src="img/ferris/not_desired_behavior.svg" class="ferris-explain" alt="Ferris with one claw up, shrugging"/> | Bu kod kutilgan xatti-harakatni bermaydi.         |

Köpçilik holatlarda biz sizni kompilyatsiya qilinmaydigan har qanday
kodning toğri versiyasiga yönaltiramiz.

## Manba Kodi

Bu kitob yaratilgan manba fayllarni [GitHub][book]da topişingiz mumkin.

[book]: https://github.com/rust-lang/book/tree/main/src
