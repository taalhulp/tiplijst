# Tiplijst
Gegevensbron voor de taaltips op taalhulp123.nl. Deze bewaarplaats heeft twee zgn. "branches".

- `test`: Hierin worden wijzigingen gemaakt. Bron van de verborgen testsite: https://www.taalhulp123.nl/tiptest#/
- `master`: Na review worden de wijzigen vanuit test naar master gefuseerd. Bron van de live website: https://www.taalhulp123.nl/taaltip#/

# Instructies
Voor wijzigingen of toevoegingen aan de taaltips, volg deze stappen (zie onder voor details):

1. Kopieer een taaltip (voor iedere nieuwe taaltip)
2. Wijzig de gegevens in de [test dataset](https://github.com/taalhulp/tiplijst/edit/test/tiplijst.yaml)
3. Toon het resultaat in de [test omgeving](https://www.taalhulp123.nl/tiptest#/) en corrigeer waar nodig
4. Voer de wijzigingen door in de [master dataset](https://github.com/taalhulp/tiplijst/compare/test?expand=1)

## 1. Kopieer een taaltip
Indien je een taaltip wilt toevoegen, is het handig om onderstaand voorbeeld als sjabloon te gebruiken. De teksten achter een # zijn slechts instructies en hebben geen invloed op het resultaat. Selecteer alles en kopieer met `Ctrl` + `C`.

```yaml
unieke-id-voor-de-browser-zonder-spaties:
  cat: stijl          # Kies: stijl/spelling/werkwoord
  ref: kolom 13       # Verschijnt als: "Stijlhulp123 kolom 13"
  datum: 2018-11-19   # YYYY-MM-DD
  title: >
    Titel in browser tabblad en bij de opsomming
  intro: >
    Dit is de tekst die in de opsomming verschijnt. 
    Er is hier geen html opmaak toegestaan, teneinde het overzichtelijk te houden.
  voorbeeld:
    - "Neutrale tekst en "
    - fout: "foute tekst"
      goed: "goede tekst"
    - " (vergeet de spaties niet). Meer "
    - fout: "verkeerde"
      goed: "correcte"
    - " tekst."
  hints:
    - >
      Hint 1, <strong>html</strong> is hier <em>toegestaan</em>
    - >
      Hint 2, en zoveel hints als je wilt
  uitleg: >
    <p>
      Hier de <strong>HTML uitleg</strong> die op de kaart zal verschijnen.
      Knippen en plakken van <a href="https://html5-editor.net/">html5-editor.net</a>.
    </p>

```

## 2. Wijzig de gegevens
Open de [test dataset](https://github.com/taalhulp/tiplijst/edit/test/tiplijst.yaml).

Indien je een taaltip toevoegt, plak met `Ctrl` + `V` het sjaboon bovenin het bestand.

We gebruiken een gestructureerd "YAML" bestand, dat een hoop flexibiliteit biedt om gegevens toe te voegen. Telkens voor de dubbele punt staat een sleutelwoord. Pas alleen het eerste sleutelwoord aan (`unieke-id-voor-de-browser-zonder-spaties`), en laat de overige ongewijzigd. Na de dubbele punt of streepje bevindt zich de inhoud om aan te passen. In enkele gevallen staat de inhoud op de volgende regel (na een >): zorg
