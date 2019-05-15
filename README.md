# Tiplijst
Gegevensbron voor de taaltips op taalhulp123.nl. Deze bewaarplaats heeft twee zgn. "branches".

- `test`: Hierin worden wijzigingen gemaakt. Bron van de verborgen testsite: https://www.taalhulp123.nl/tiptest#/
- `master`: Na review worden de wijzigen vanuit test naar master gefuseerd. Bron van de live website: https://www.taalhulp123.nl/taaltip#/

# Instructies
Voor wijzigingen of toevoegingen aan de taaltips, volg deze stappen (zie onder voor details):

1. Kopieer een taaltip (voor iedere nieuwe taaltip)
2. Wijzig de gegevens in de [test gegevensbron](https://github.com/taalhulp/tiplijst/edit/test/tiplijst.yaml)
3. Toon het resultaat in de [test omgeving](https://www.taalhulp123.nl/tiptest#/) en corrigeer waar nodig
4. Voer de wijzigingen door in de [master gegevensbron](https://github.com/taalhulp/tiplijst/compare/test?expand=1)

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
  voorbeeld:  # Onderstaande segmenten vormen samen de voorbeeldzin. Neutraal + fout/goed herhalen zoveel als nodig
    - "Neutrale tekst en "
    - fout: "foute tekst"
      goed: "goede tekst"
    - " (vergeet de spaties niet). Meer "
    - fout: "verkeerde"
      goed: "correcte"
    - " tekst."
  hints:    # Dit zijn de hints die onder de voorbeeldzin verschijnen. Zoveel als nodig.
    - >
      Eerste hint <strong>html</strong> is hier <em>toegestaan</em>
    - >
      Tweede hint en zoveel hints als je wilt
  uitleg: >
    <p>
      Hier de <strong>HTML uitleg</strong> die op de kaart zal verschijnen.
      Knippen en plakken van <a href="https://html5-editor.net/">html5-editor.net</a>.
    </p>

# De witregel hierboven (zonder spaties) is nodig tussen twee taaltips
```

## 2. Wijzig de gegevens
Open de [test dataset](https://github.com/taalhulp/tiplijst/edit/test/tiplijst.yaml).

Indien je een taaltip toevoegt, plak eerst met `Ctrl` + `V` het sjaboon bovenin het bestand.

We gebruiken een gestructureerd "YAML" bestand, dat een hoop flexibiliteit biedt om gegevens toe te voegen. Telkens voor de dubbele punt staat een sleutelwoord. Pas alleen het eerste sleutelwoord aan (`unieke-id-voor-de-browser-zonder-spaties`), en laat de overige ongewijzigd. Na de dubbele punt of streepje bevindt zich de inhoud om aan te passen. In enkele gevallen staat de inhoud op de volgende regel (na een >): zorg ervoor dat er dan een inspringing van tenminst 2 spaties is (zoals het voorbeeld).

- `unieke-id-etc`: Dit produceert het unieke adres in de browser. Pas dit eenmalig aan.
- `cat`: Kies hierna uit *spelling*, *stijl* of *werkwoord*. Hierop kan de lijst worden gefilterd.
- `ref`: Een referentie naar een plaats op de werkwoorden- / spelling- / stijlkaart. De kaart wordt er automatisch bijgezet.
- `datum`: Plaatsingsdatum uitgeschreven zoals `2019-01-13`. Hierop kun je de lijst sorteren.
- `title`: De titel die verschijnt in de lijst en in het browser tabblad. Ook hierop kun je de lijst sorteren.
- `intro`: De tekst die verschijnt in de lijst. Opmaak niet mogelijk. Let op dat iedere regel inspringt.
- `voorbeeld`: De voorbeeldzin als samenstelling van de segmenten (tussen aanhalingstekens). Ieder segment wordt vooraf gegaan door een - streepje. Er zijn neutrale segmenten en `goed:`/`fout:` segmenten. Gebruik zoveel segmenten als nodig.
- `hints`: Opeenvolging van tips onder de voorbeeldzin, zoveel als nodig. Iedere hint wordt voorafgegaan door: - > en start met inspringing op een nieuwe regel. Het is toegestaan HTML code te gebruiken voor de opmaak, maar bij voorkeur beperkt tot &lt;strong&gt;vette&lt;/strong&gt; en &lt;em&gt;schuine&lt;/em&gt; tekst.
- `uitleg`: De uitleg die onderaan verschijnt. Ook hier is HTML code toegestaan. Gebruik de editor op [html5-editor.net](https://html5-editor.net/) en plak de code hier. Code tussen &lt;h4&gt;header 4&lt;/h4&gt; verschijnt als oranje kopje.

Github gebruikt een versie-controle systeem. Beschrijf de wijzigingen onder **Commit changes** en klik op de **[Commit changes]** knop. Je kunt de wijzigingen altijd later terugvinden en eventueel terughalen.

## 3. Toon het resultaat

De taaltip app maakt direct gebruik van de gegevens op Github. Je kunt het resultaat van de wijzigingen na ongeveer een minuut zien op [taalhulp123.nl/tiptest#/](https://www.taalhulp123.nl/tiptest#/). Als je geen lijst met resultaten ziet, is het waarchijnlijk dat de opmaak van het bestand in de vorige stap niet goed gegaan is. Deze link is niet vindbaar voor normale gebruikers, dus geen probleem als er hier iets niet goed gaat.

Je kunt achtereenvolgens meerdere wijzigingen doorvoeren, opslaan via **Commit** (zie boven) en tonen in de testomgeving.

## 4. Voer de wijzigingen door

De live website [taalhulp123.nl/taaltip#/](https://www.taalhulp123.nl/taaltip#/) is verbonden met de `master` branch van deze bewaarplaats. We kunnen een `merge` doen van de `test` branch naar de `master`.

- Ga naar [deze link](https://github.com/taalhulp/tiplijst/compare/test?expand=1) en zie de verschillen tussen `test` en `master` onderaan de pagina. Kies **[Create pull request]**
- Je komt op een pagina met *Merge van test*. Als het goed is zijn er geen conflicten en kies je **[Merge pull request]** en dan **[Confirm merge]**.

De gegevens zijn nu live, en zullen een minuutje later op de website te zien zijn.

# Overige info

Deze gegevens zijn open source gepubliceerd en derhalve openbaar toegankelijk. Plaats hier nooit vertrouwelijke informatie.

Dit README bestand zelf kan op dezelfde wijze aangepast worden als hierboven beschreven voor de taaltips. Begin stap 2 dan door [dit bestand](https://github.com/taalhulp/tiplijst/edit/test/README.md) aan te passen en volg verder de stappen.

