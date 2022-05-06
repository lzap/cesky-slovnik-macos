== Anglicko-Český slovník pro MacOS zdarma

Slovník pro oficiální aplikaci "Slovník" (Dictionary) od Applu. Stačí nakopírovat a v nastavení zaktivovat.

Vygenerováno ze slovníků https://www.svobodneslovniky.cz (svobodná licence GNU FDL)

== Vytvoření vlastní verze

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

* Výsledný slovník je vygenerován v `./Czech/objects/Czech.dictionary` a tento lze distribuovat, nebo kopírovat do `/Library/Dictionaries`.
* Instalaci lze provést automaticky příkazem:

```
make -C Czech install DICT_BUILD_TOOL_DIR=../ddk
```

== LICENCE

GNU FDL

Já nejsem autorem slovníků ani do nich nijak nepřispívám, tento repozitář je jen návod, jak zkonvertovat svobodný slovník na Apple MacOS Dictionary formát.

Pro další info běž na https://www.svobodneslovniky.cz
