# Případy užití
## Účastníci
### Návštěvník
Osoba, která přišla do webového rozhraní aplikace a není v současné chvíli
přihlášena. Tato osoba může přistupovat pouze k veřejnému obsahu. Pro přístup
k uzavřené části aplikace se musí přihlásit nebo zaregistrovat (pokud ještě
svůj účet nemá).

### Uživatel
Osoba, která se do systému registrovala pomocí emailové adresy a hesla. Na
základě registrace může zakládat nové kampaně sledování konkurence, upřesnit
detaily sledování a manipulovat s výsledky.

### Administrátor
Osoba představující správce systému, zodpovědného za správnost údajů u
sledované konkurence. Sleduje upozornění systému na nesrovnalosti v nasbíraných
datech a ručně je řeší. Na žádost uživatele může administrovat jeho účet a
spravovat jeho kampaně. Chováli-li se uživatel v rozporu s podmínkami použití
systému, může jeho účet administrátor zablokovat.

## Případy užití

### Správa uživatelů
#### UC1 - Registrace uživatele
Umožňuje každému návštěvníkovi vytvořit si svůj uživatelský účet. Po registraci
se z návštěvníka stává uživatel a může využívat uzavřenou část systému.

* Případ užití začíná přichodem neregistrovaného Uživatele (Navštěvník) na web
aplikace. Na odpovídající stránce si vybere možnost registrace.
* Systém zobrazí návštěvníkovi formulář, vyžadující vyplnění jména, příjmení,
emailu a hesla. Volitelně může zadat i bydliště a fakturační údaje.
* Návštěvník vypní požadované údaje.
* Systém zkontroluje validitu vložených údajů, v případě neplatnosti některého
z údajů se registrační formulář znovu zobrazí.
* Systém odešle Návštěvníkovi kontrolní email.
* Návštěvník v obdrženém emailu rozklikne uvedený odkaz na ověření emailové
adresy.
* Systém spáruje navštívený odkaz s registrovaným účtem a účet aktivuje.
* Z Návštěvníka se stává Uživatel a registrace je dokončena.

* Alternativně: Účet zakládá administrator

#### UC2 - Změna údajů uživatele
Uživatel má možnost upravit informace ve svém profilu, které zadal během
registrace.

* Případ užití začíná, na hlavní stránce administrace, když Uživatel chce změnit
informace o svém účtu.
* Uživatel v aplikaci vybere záložku "Můj účet".
* Systém zobrazí formulář s detailními informaceni o účtu Uživatele.
* Uživatel aktualizuje informace a jejich uložení potvrdí tlačítkem "Uložit".
* Systém ověří správnost zadaných údajů a data uloží.
* Změna údajů proběhla a případ užití tím končí.

#### UC3 - Zablokování uživatele
Dovoluje Administrátorovi znemožnit přístup Uživateli k jeho účtu, nevyužívá-li
systém v souladu s podmínkami používání nebo je-li to bezpodmínečně nutné.

* Tento případ začíná na hlavní stránce administrace v momentě,
kdy Administrátor chce zablokovat účet uživatele.
* Administrátor zvolí záložku "Správa uživatelů".
* Systém zobrazí seznam Uživatelů se stručnými informacemi o nich.
* Administrátor vyhledá Uživatele, kterého chce zablokovat a vybere ho.
* Systém požádá Administrátora o potvrzení zvolené akce.
* Systém deaktivuje Uživatelský účet a všechny kampaně s ním spojené.
* Uživatel je automaticky odhlášen a nemůže se znovu přihlásit.
* Užitel je nyní zablokovaný a případ užití tím končí.

#### UC4 - Přihlášení uživatele
Dává návštěvníkovi možnost ověření identity pro vstup do aplikace. Pokud
existuje profil uživatele, kterým se chce návštěvník přihlásit a současně
autentizace proběhne úspěšně, může návštěvní (nyní už v roli uživatele) do
uzavřené části systému.

* Tento případ užití začíná na hlavní stránce veřejné části aplikace, kde se
chce Návštěvník přihlásit do uzavřené části. Návštěvník klikne na odkaz
"Vstoupit do administrace".
* Systém zobrazí formulář pro přihlášení, tedy textový vstup na
email a heslo.
* Návštěvník zadá své přihlašovací údaje, které si zvolil při registraci do
systému, případně které si aktualizoval pomocí administrace.
* Systém ověří správnost vložených údajů, v případě validního vstupu vpustí
uživatele do administrace.
* Návštěvník je nyní na hlavní stránce administrace v roli Uživatele. Tím je
přihlašování u konce.

### Správa kampaní
#### UC5 - Vytvoření kampaně
Umožňuje uživateli seskupit produkty, u kterých vyžaduje monitorování se
stejným nastavením do jednoho celku. Nastavení se týká především intervalu
aktualizace a formy výstupu.

* Vytváření nové kampaně začíná na hlavní stránce administrace. Uživatel vybere
položku "Kampaně".
* Systém vypíše uživateli seznam aktivních kampaní, které dříve vytvořil.
* Uživatel klikne na tlačítko "Vytvořit kampaň".
* Systém zobrazí formulář s povinnými informacemi o kampani. Uživatel musí
vyplnit, jak často se má kampaň spouštět (jednou denně, jednou za tři dny,
jednou týdně nebo pouze souhrnný měsíční report).
* Uživatel nahraje XML soubor podle uvedené specifikace se seznamem produktů
ke sledování.
* Systém po kompletním nahrání souboru zkontroluje validitu vstupního souboru.
* Uživatel klikne na "Vytvořit kampaň".
* Systém zkontroluje validitu všech zadaných vstupů, v případně pozitivní
validace založí kampaň v systému. Uživateli se zobrazí zpráva o úspěšném přidání
kampaně.
* Uživatel je nyní zpět na seznamu aktivních kampaní. Tím je vytváření kampaně
u konce.

* Alternativně: pordukty vkládá ručně
* Alternativně: seznam konkurentů vkládá ručně

#### UC6 - Přidání sledovaných produktů do kampaně
Umožňuje uživateli přidat do kampaně sledovaný produkt. Produkt je zboží, které
si uživatel přeje sledovat jednoznačně určené EAN kódem. Vložit lze i produkt,
který kampaň už obsahuje, v takovém případě bude existující produkt
aktualizován.

* Tento případ užití začíná na hlavní stránce administrace. Uživatel chce do
existující kampaně přidat nové produkty. Klikne na odkaz "Kampaně".
* Systém zobrazí seznam aktivních kampaní, které Uživatel již dříve vytvořil.
* Uživatel vyhledá kampaň, do které chce nové produkty přidat. A klikne na
odkaz "Přidat produkty ke sledování".
* Systém zobrazí formulář pro nahrání souboru XML (podle uvedené specifikace)
se seznamem produktů.
* Systém ověří validitu nahraného souboru. Je-li soubor validní podle
specifikace, nové produkty budou v dalším cyklu také sledovány. Nacházejí-li
se v souboru produkty již dříve přidané do kampaně, systém aktualizuje jejich
vlastnosti tak, aby odpovídaly vložným datům, ale jejich historie zůstane
nezměněna.
* Uživatel je přesměrován na detail upravované kampaně a je informován o
úspěšném přidání. Přidávání produktů je u konce.

* Alternativně: Uživatel je na stránce kampaně
* Alternativně: Uživatel zadá produkty ručně

#### UC7 - Úprava kampaně
Systém dovoluje uživateli vlastnosti kampaně měnit během její existence. Pokud
to povaha změny dovoluje, její efekt se projeví ihned. V opačném případě se
efekt projeví až s odpovídajícím zpožděním.

* Tento případ užití začíná na hlavní stránce administrace. Uživatel kline na
odkaz "Kampaně".
* Systém zobrazí seznam aktivních kampaní, které uživatel již dříve přidal.
* Uživatel vyhledá kampaň, kterou chce editovat a klikne na odkaz "Nastavit
kampaň".
* Systém zobrazí formulář s informacemi o kampani a seznam produktů, které
kampaň obsahuje.
* Uživatel může změnit veškeré nastavení kampaně včetně seznamu produktů. Po
provedení změn Uživatel uložení dat potvrdí tlačítkem "Uložit".
* Systém provede validaci dat a přesměruje uživatele na detail editované
kampaně.
* Uživateli se zobrazí zpráva o úspěšném uložení změn. Kampaň je upravena.

* Alternativně: Začíná na detailu kampaně

### Evidence konkurence
#### UC8  - Přidání konkurenčního obchodu
#### UC9  - Úprava údajů o produktu
#### UC10 - Úprava údajů o obchodu
#### UC11 - Správa sledovaných produktů
#### UC12 - Správa sledovaných obchodů

### Prioritizace konkurence
#### UC13 - Nastavení priority
#### UC14 - Vyhledání prioritní konkurence

### Výstup sledování
#### UC15 - Zobrazení výstupu
#### UC16 - Exportování výstupu
