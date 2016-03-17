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
* Systém zobrazí návštěvníkovi formulář vyžadující vyplnění jména, příjmení,
emailu a hesla. Volitelně může zadat i bydliště a fakturační údaje.
* Návštěvník vypní požadované údaje.
* Systém zkontroluje validitu vložených údajů, v případě neplatnosti některého
z údajů se registrační formulář znovu zobrazí.
* Systém odešle Návštěvníkovi kontrolní email.
* Návštěvník v obdrženém emailu rozklikne uvedený odkaz na ověření emailové
adresy.
* Systém spáruje navštívený odkaz s registrovaným účtem a účet aktivuje.
* Z Návštěvníka se stává Uživatel a registrace je dokončena.

* **Alternativně**: Účet zakládá administrator (1-4)
* Případ užití začíná na hlavní stránce administrace. Administrátor klikne na
odkaz "Uživatelé".
* Systém zobrazí seznam aktivních Uživatelů.
* Administrátor klikne na odkaz "Přidat uživatele".
* Systém zobrazí formulář vyžadující vyplnění jména, příjmení, emailu a hesla.
* Administrátor vypní údaje specifikující nového uživatele.

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
kdy Administrátor chce zablokovat účet Uživatele.
* Administrátor zvolí záložku "Správa uživatelů".
* Systém zobrazí seznam Uživatelů se stručnými informacemi o nich.
* Administrátor vyhledá Uživatele, kterého chce zablokovat a vybere ho.
* Systém požádá Administrátora o potvrzení zvolené akce.
* Administrátor potvrdí blokaci účtu.
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
* Uživatel zaškrtne "Vyhledat konkurenci automaticky".
* Uživatel klikne na "Vytvořit kampaň".
* Systém zkontroluje validitu všech zadaných vstupů, v případně pozitivní
validace založí kampaň v systému. Uživateli se zobrazí zpráva o úspěšném přidání
kampaně.
* Uživatel je nyní zpět na seznamu aktivních kampaní. Tím je vytváření kampaně
u konce.

* **Alternativně**: Produkty vkládá ručně (5-7)
* Uživatel nemá k dispozici XML seznam produktů a vkládá je tedy ručně. U
každého produktu vyplní povinné údaje.

* **Alternativně**: Seznam konkurentů vkládá ručně (7-8)
* Uživatel zaškrtne "Sledovat vybranou konkurenci".
* Systém zobrazí pole pro textový vstup pro vložení URL adres.
* Uživatel vloží seznam URL adres konkurentů, které chce sledovat.

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
se seznamem produktů a formulář pro přidání produktů ručně.
* Uživatel vybere možnost nahrát soubor XML a nahraje ho do aplikace.
* Systém načte data z nahraného XML.
* Systém ověří validitu načtených dat. Jsou-li data validní podle
specifikace, nové produkty budou v dalším cyklu také sledovány. Nacházejí-li
se v datech produkty již dříve přidané do kampaně, systém aktualizuje jejich
vlastnosti tak, aby odpovídaly vložným datům, ale jejich historie zůstane
nezměněna.
* Uživatel je přesměrován na detail upravované kampaně a je informován o
úspěšném přidání. Přidávání produktů je u konce.

* **Alternativně**: Uživatel je na stránce kampaně (1-3)
* Uživatel je na stránce detailu kampaně. Klikne na odkaz "Přidat produkty
ke sledování".

* **Alternativně**: Uživatel zadá produkty ručně
* Uživatel vybere možnost přidat produkty ručně.
* Systém zobrazí povinná pole pro přidání nových polí.
* Uživatel vyplní zobrazená pole.
* Systém načte data z vyplněného formuláře.


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

* **Alternativně**: Začíná na detailu kampaně
* Uživatel je na stránce detailu kampaně. Klikne na odkaz "Upravit nastavení
kampaně".

### Evidence konkurence
#### UC8  - Přidání konkurenčního obchodu
Je možné, že systém požadovanou konkurenci nenajde, případně ji zná uživatel
dopředu. Tento případ užití tedy umožnuje u produktu explicitně specifikovat
množinu eshopu, na kterých se produkt nachází.

* Případ užití začíná na hlavní stránce eshopu, kde uživatel klikne na odkaz
"Kampaně".
* Systém zobrazí seznam kampaní, které uživatel již dříve založil.
* Uživatel v seznamu vyhledá kampaň, ke které chce přidat nové URL adresy
konkurence. Po nalezení na Uživatel klikne na název kampaně v seznamu.
* Systém zobrazí Uživateli podrobné informace o kampani.
* Uživatel klikne na odkaz "Přidat konkurenční web".
* Systém uživateli zobrazí fomulář s textovým vstupem.
* Uživatel vyplní URL adresy konkurenčních eshopů, které chce sledovat. Uložení
změn provede tlačítkem "Uložit".
* Systém projde seznam konkurentů, pokud některé zadané URL nezná a nedokáže
je sám zpracovat, notifikuje Administrátora a připraví tyto URL k ručnímu
naparsování.
* <<include UC17>>
* Systém zpracuje nově sledovanou konkurenci a v příštím cyklu skenování. Případ
užití je u konce

#### UC9  - Úprava údajů o produktu
Systém může při skenování konkurenčních eshopů narazit na chybu, kdy se mu údaje
 z webu nepodaří správně namapovat na atributy produktu. V takovém případě může
 Administrátor mapování ručně upravit.

#### UC10 - Úprava údajů o obchodu
Systém interně eviduje informace o jednotlivých eshopech. Jelikož muže dojít ke
špatnému vyhodnocení údajů nebo jejich změně, Administrátorovi je poskytnuto
rozhraní pro jejich editaci.

#### UC11 - Správa sledovaných produktů
Aby Uživatel mohl za běhu kampaně upravit údaje o produktech které sleduje,
nabízí systém prostředí pro úpravu vložených produktů. Efekt změn se projeví při
následujícím cyklu sledování.

#### UC12 - Správa sledovaných obchodů
Uživatel může v systému nastavit preferenci konkurenčních webů. V nastavení
kampaně může vybrat, jaké konkurenční weby jsou pro něj důležité a tím ušetřit
množství provedených skenování systému.

#### UC17 - Parsování webů Administrátorem
Systém nabízí prostředí pro Administrátora, ve kterém mu zobrazí náhled stránky,
kterou bude skenovat. Administrátor ručně zvolí, kde na stránce se vyskytují
sledované atributy produktu.

### Prioritizace konkurence
#### UC13 - Nastavení priority
#### UC14 - Vyhledání prioritní konkurence

### Výstup sledování
#### UC15 - Zobrazení výstupu
#### UC16 - Exportování výstupu
