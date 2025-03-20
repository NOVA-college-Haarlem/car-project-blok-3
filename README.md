# Project Car

## Opdrachten

### Opdracht 1 - Database ontwerp

- Maak op basis van onderstaande userstories en het SQL-bestand een database ontwerp. 

### Opdracht 2 - Repository

- Maak gebruik van de repository: https://github.com/NOVA-college-Haarlem/car-project-blok-3
- Fork de repository
- Clone de repository

### Opdracht 3 - Website

- Maak een website voor een car dealer.

### Opdracht 4 - Controleren

- Controleer je website door gebruik te maken van de rubric.

## Userstories

### Overzichtspagina

# User Stories Car Showroom

## Overzichtspagina

**Als een** bezoeker  
**Wil ik** een overzicht zien van alle beschikbare auto's  
**Zodat ik** snel kan bladeren door verschillende modellen

**Als een** bezoeker  
**Wil ik** basisinformatie zien van elke auto (merk, model, thumbnail afbeelding)  
**Zodat ik** een eerste indruk krijg zonder naar de detailpagina te hoeven gaan

**Als een** bezoeker  
**Wil ik** op een auto kunnen klikken  
**Zodat ik** naar de detailpagina kan gaan voor meer informatie

## Filtering (beperkt tot 2)

**Als een** bezoeker  
**Wil ik** kunnen filteren op merk (BMW, Toyota, Volkswagen, etc.)  
**Zodat ik** alleen auto's zie van merken waarin ik geïnteresseerd ben

**Als een** bezoeker  
**Wil ik** kunnen filteren op prijsklasse  
**Zodat ik** auto's kan vinden binnen mijn budget

## Overige Functionaliteiten

**Als een** bezoeker  
**Wil ik** kunnen sorteren op bouwjaar (van nieuw naar oud of oud naar nieuw)  
**Zodat ik** de nieuwste modellen of juist klassiekers kan vinden

**Als een** bezoeker  
**Wil ik** zien hoeveel resultaten er beschikbaar zijn binnen mijn gekozen filters  
**Zodat ik** weet hoeveel opties ik heb

```sql
-- Database schema voor Car Showroom met één tabel

-- Auto's tabel
CREATE TABLE autos (
    id INT PRIMARY KEY AUTO_INCREMENT,
    merk VARCHAR(50) NOT NULL,
    model VARCHAR(100) NOT NULL,
    prijsklasse VARCHAR(20) NOT NULL, -- Budget, Midden, Premium, Luxe
    bouwjaar INT NOT NULL,
    kilometerstand INT,
    brandstof VARCHAR(20),
    vermogen INT, -- in pk
    transmissie VARCHAR(20),
    kleur VARCHAR(30),
    beschrijving TEXT,
    prijs DECIMAL(10, 2),
    thumbnail_url VARCHAR(255)
);

-- Voorbeelddata invoegen
INSERT INTO autos (merk, model, prijsklasse, bouwjaar, kilometerstand, brandstof, vermogen, transmissie, kleur, beschrijving, prijs, thumbnail_url) VALUES 
('Toyota', 'Corolla', 'Budget', 2020, 45000, 'Benzine', 116, 'Handgeschakeld', 'Wit', 'Betrouwbare gezinsauto met laag verbruik en goede uitrusting.', 19500.00, 'corolla.jpg'),
('BMW', '3-Serie', 'Premium', 2021, 30000, 'Diesel', 190, 'Automaat', 'Zwart', 'Sportieve sedan met luxe interieur en krachtige motor.', 42500.00, 'bmw3.jpg'),
('Volkswagen', 'Golf', 'Midden', 2019, 65000, 'Benzine', 130, 'Handgeschakeld', 'Blauw', 'Compacte hatchback met goede rijeigenschappen en ruim interieur.', 18900.00, 'golf.jpg'),
('Mercedes-Benz', 'S-Klasse', 'Luxe', 2022, 10000, 'Hybride', 435, 'Automaat', 'Zilver', 'Luxe limousine met de nieuwste technologie en uitmuntend comfort.', 125000.00, 'sklasse.jpg'),
('Ford', 'Focus', 'Budget', 2018, 85000, 'Benzine', 125, 'Handgeschakeld', 'Rood', 'Praktische gezinsauto met goede wegligging en modern infotainment.', 14500.00, 'focus.jpg'),
('Audi', 'A4', 'Premium', 2020, 55000, 'Diesel', 163, 'Automaat', 'Grijs', 'Stijlvolle zakenauto met Quattro vierwielaandrijving en verfijnd interieur.', 37900.00, 'a4.jpg'),
('Fiat', '500', 'Budget', 2020, 25000, 'Benzine', 69, 'Handgeschakeld', 'Geel', 'Compacte stadsauto met retro design en laag verbruik.', 12900.00, '500.jpg'),
('Tesla', 'Model 3', 'Premium', 2021, 20000, 'Elektrisch', 325, 'Automaat', 'Wit', 'Populaire elektrische sedan met indrukwekkende prestaties en moderne technologie.', 45900.00, 'model3.jpg'),
('Volvo', 'XC60', 'Premium', 2019, 70000, 'Diesel', 190, 'Automaat', 'Zwart', 'Veilige en ruime SUV met Scandinavisch design en veel comfort.', 39500.00, 'xc60.jpg'),
('Peugeot', '208', 'Midden', 2022, 5000, 'Benzine', 100, 'Handgeschakeld', 'Blauw', 'Stijlvolle stadsauto met innovatief i-Cockpit dashboard en efficient verbruik.', 18700.00, '208.jpg'),
('Porsche', '911', 'Luxe', 2020, 15000, 'Benzine', 450, 'Automaat', 'Rood', 'Iconische sportwagen met ongeëvenaarde rijeigenschappen en prestaties.', 139000.00, '911.jpg'),
('Kia', 'Picanto', 'Budget', 2021, 10000, 'Benzine', 67, 'Handgeschakeld', 'Groen', 'Compacte en betaalbare stadsauto met lange garantie.', 11900.00, 'picanto.jpg'),
('Jaguar', 'F-Pace', 'Luxe', 2019, 60000, 'Diesel', 240, 'Automaat', 'Donkerblauw', 'Sportieve SUV met indrukwekkend design en krachtige motor.', 48500.00, 'fpace.jpg'),
('Renault', 'Clio', 'Midden', 2020, 35000, 'Benzine', 90, 'Handgeschakeld', 'Oranje', 'Populaire hatchback met stijlvol ontwerp en zuinige motor.', 15800.00, 'clio.jpg'),
('Lamborghini', 'Huracán', 'Luxe', 2018, 12000, 'Benzine', 640, 'Automaat', 'Geel', 'Exotische supersportwagen met V10 motor en spectaculaire prestaties.', 235000.00, 'huracan.jpg');
```

## Beoordelingsrubric

### Overzichtspagina

| Criterium | Onvoldoende | Voldoende | Goed |
|-----------|-------------|------------|------|
| Basisweergave van auto's | Auto's worden niet of nauwelijks getoond | Auto's worden correct weergegeven | Auto's worden aantrekkelijk weergegeven met duidelijke visuele hiërarchie |
| Filter op merk | Filter werkt niet of met ernstige fouten | Filter werkt, maar heeft kleine gebreken | Filter werkt perfect en is gebruiksvriendelijk |
| Filter op prijsklasse | Filter werkt niet of met ernstige fouten | Filter werkt, maar heeft kleine gebreken | Filter werkt perfect en is gebruiksvriendelijk |
| Sortering op bouwjaar | Sortering werkt niet of met ernstige fouten | Sortering werkt, maar heeft kleine gebreken | Sortering werkt perfect en is gebruiksvriendelijk |
| Doorklikken naar detailpagina | Links werken niet of met ernstige fouten | Links werken, maar zijn niet optimaal geplaatst | Links werken perfect en zijn intuïtief |
Detailpagina
| Criterium | Onvoldoende | Voldoende | Goed |
|-----------|-------------|------------|------|
| Weergave van auto details | Details worden niet of nauwelijks getoond | Details worden correct weergegeven | Details worden uitgebreid en aantrekkelijk weergegeven |
| Teruglink naar overzichtspagina | Link werkt niet of is niet aanwezig | Link is aanwezig en werkt | Link is duidelijk zichtbaar en gebruiksvriendelijk |
Algemene aspecten
| Criterium | Onvoldoende | Voldoende | Goed |
|-----------|-------------|------------|------|
| Database connectie | Query's werken niet of met ernstige fouten | Query's werken, maar zijn niet geoptimaliseerd | Query's werken goed en zijn geoptimaliseerd |
| Code kwaliteit | Rommelige code met veel fouten | Redelijk nette code met enkele fouten | Nette, goed gestructureerde code zonder fouten |
