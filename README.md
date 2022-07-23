# Anglicko-Český slovník pro MacOS zdarma

Slovník pro oficiální aplikaci "Slovník" (Dictionary) od Applu. Stačí nakopírovat a v nastavení zaktivovat.

Vygenerováno ze slovníků https://www.svobodneslovniky.cz které jsou a vždy budou zdarma. Přesněji řečeno, slovníky vytváří komunita a svoji práci dává k dispozici pod svobodnou licencí GNU FDL ve formátu textu. Ten ovšem MacOS Slovník neumí číst, proto jsem vytvořil verzi ušitou na míru pro tuto aplikaci od Applu. Dále zde najdeš i návod, jak takový slovník převést sám.

## Instalace

* Stáhni si [balíček](https://github.com/lzap/cesky-slovnik-macos/archive/refs/heads/main.zip) a rozbal ho poklepáním.

![](/images/step_extract.png)

* Ve složce `cesky-slovnik-macos-main` najdi podsložku `Czech/objects/Czech.dictionary` a zkopíruj ji (Command-C).

![](/images/step_copy.png)

* Jdi do své Knihovny (Command-Shift-L nebo menu Otevřít - Knihovna) a najdi složku `Dictionaries`.
* Vlož do Dictionaries složku Czech.dictionary (Command-V).

![](/images/step_library.png)

* Spusť slovník a dej nastavení (Command-,).
* Najdi slovník pojmenovaný en-cs.txt a zaktivuj ho.

![](/images/step_settings.png)

* Hotovo! Stažený balíček ZIP i rozbalený adresář `cesky-slovnik-macos-main` můžeš v klidu smazat.

![](/images/step_done.png)

## Podpora

Funguje? Bezva. Piju kafe a to stojí peníze, Sponsor tlačítko je vpravo nahoře. Tak na co ještě čekáš? :-)

## Vytvoření vlastní verze

* Stáhnout `Additional_Tools_for_XCode.dmg` z Apple developer portálu (balíček je malý, neboj se :-).
* Připojit (mount) a zkopírovat obsah adresáře `Utilities/Dictionary Development Kit` do tohoto projektu do adresáře `./ddk`.
* V adresáři `ddk` musejí být jednotlivé podsložky jako `bin` a nikoliv kořenový `Dictionary Develpment Kit`!
* Instalace pythonu3, závislostí a provedení git checkoutu slovníku a nástroje pyglossary:

```
git submodule update
brew install python3
pip3 install prompt_toolkit lxml beautifulsoup4 html5lib
```

* Konverze do AppleDict:

```
./pyglossary/main.py --read-format=Tabfile --write-format=AppleDict svobodneslovniky/en-cs/en-cs.txt Czech
```

* Konverze do binární podoby AppleDictu:

```
make -C Czech DICT_BUILD_TOOL_DIR=../ddk
```

* Výsledný slovník je vygenerován v `./Czech/objects/Czech.dictionary` a tento lze distribuovat za dodržení podmínek licence GNU FDL, nebo kopírovat do `/Library/Dictionaries`.
* Instalaci lze provést automaticky příkazem:

```
make -C Czech install DICT_BUILD_TOOL_DIR=../ddk
```

Pokud vygeneruješ novou verzi a ověříš, že funguje dobře, pošli mi pull request!

## Místo na dotazy

Často se mě ptáte...

### Uděláš i němčinu

Umím jen anglicky a potřebuju jen tenhle slovník, takže ne, ale pull requestům se nebudu bránit!

### Chci jazyk XYZ

Mohu tě odkázat na program od Vaška Slavíka https://dictionaries.io/ který za lidových 599,- korun českých nabízí přes 80 jazyků.

## LICENCE

GNU FDL

Já nejsem autorem slovníků ani do nich nijak nepřispívám, tento repozitář obsahuje kopii a je jen návod, jak zkonvertovat svobodný slovník na Apple MacOS Dictionary formát.

Pro další info běž na https://www.svobodneslovniky.cz

Pokud umíš anglicky, zapoj se!
