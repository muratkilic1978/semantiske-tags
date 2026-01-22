# Semantiske HTML-tags

## Hvad er semantiske tags?
Semantiske tags beskriver indholdets funktion og struktur, ikke bare dets udseende. De gør koden lettere at læse og forstå for både udviklere, søgemaskiner og hjælpeteknologier som skærmlæsere.

## De vigtigste semantiske tags

### Grundlæggende dokumentstruktur
- `<head>` - Metadata om siden (ikke synligt for brugeren) **[par tag]**
- `<body>` - Alt det synlige indhold på siden **[par tag]**
- `<header>` - Topsektion med logo, navigation eller introducerende indhold **[par tag]**
- `<nav>` - Navigationsområde med links **[par tag]**
- `<main>` - Hovedindholdet på siden (kun én per side) **[par tag]**
- `<footer>` - Bundsektion med copyright, links eller kontaktinfo **[par tag]**

### Indholdsorganisering
- `<section>` - Tematisk gruppering af indhold **[par tag]**
- `<article>` - Selvstændigt indhold (blogindlæg, nyhedsartikel) **[par tag]**
- `<aside>` - Sideindhold relateret til hovedindholdet **[par tag]**
- `<ul>` - Usorteret liste (perfekt til navigation) **[par tag]**
- `<ol>` - Sorteret/nummereret liste **[par tag]**
- `<li>` - Listeelement (bruges i både ul og ol) **[par tag]**

### Medier og indhold
- `<figure>` og `<figcaption>` - Billeder, diagrammer med billedtekst **[par tags]**
- `<picture>` - Responsive billeder med flere kilder **[par tag]**
- `<img>` - Billeder **[enkelt tag]**
- `<time>` - Tidsangivelser og datoer **[par tag]**
- `<address>` - Kontaktoplysninger **[par tag]**
- `<mark>` - Fremhævet eller markeret tekst **[par tag]**
- `<details>` og `<summary>` - Sammenklappelig indhold **[par tags]**

### Neutrale containere (kun når semantiske tags ikke passer)
- `<div>` - Neutral blok-container **[par tag]**
- `<span>` - Neutral inline-container **[par tag]**

## Nesting-regler (parent og child struktur)
Semantiske tags kan indeholde andre tags i en hierarkisk struktur:

```html
<!-- Parent tag indeholder child tags -->
<main> <!-- Parent -->
    <section> <!-- Child af main, parent for h2 og p -->
        <h2>Overskrift</h2> <!-- Child af section -->
        <p>Tekst indhold</p> <!-- Child af section -->
    </section>
</main>

<!-- Navigation med nested lister -->
<nav> <!-- Parent -->
    <ul> <!-- Child af nav, parent for li -->
        <li><a href="#">Link</a></li> <!-- li er child af ul, a er child af li -->
    </ul>
</nav>
```

**Vigtige nesting-principper:**
- Brug logisk hierarki (header → nav → ul → li → a)
- Block elementer kan indeholde både block og inline elementer
- Inline elementer må kun indeholde andre inline elementer
- Brug altid semantiske tags når det er muligt - kun `<div>` og `<span>` som sidste udvej

## Forskel mellem `<head>` og `<body>`
- **`<head>`**: Indeholder metadata om siden som ikke vises direkte på siden
- **`<body>`**: Indeholder alt det synlige indhold som brugeren ser og interagerer med på selve siden

⚠️ **Vigtigt**: Kun `<title>` og `<link rel="icon">` (favicon) fra `<head>` tagget er synlige for brugeren - de vises i browserens faneblad/tab. Alt andet i `<head>` er usynligt metadata.

### Standard HTML-dokumentstruktur
```html
<!DOCTYPE html>
<html lang="da">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <!-- Alt synligt indhold kommer her -->
    
    <script src="js/script.js"></script>
</body>
</html>
```

**Forklaring af grundelementer:**
- `<!DOCTYPE html>` - Fortæller browseren at det er HTML5
- `<html lang="da">` - Hovedcontainer, `lang` angiver sproget
- `<meta charset="UTF-8">` - Tegnsæt (understøtter danske karakterer)
- `<meta name="viewport"...>` - Vigtig for responsive design
- `<title>` - Vises i browserens faneblad og søgeresultater
- `<link rel="stylesheet" href="css/style.css">` - Forbinder til CSS-stylesheet i css-mappen
- `<script src="js/script.js">` - Indlæser JavaScript fra js-mappen (placeret før `</body>` for bedre performance)

## Grundlæggende HTML-koncepter

### Enkelt tags vs. par tags
**Enkelt tags (self-closing)** - lukker sig selv:
- `<img src="billede.jpg" alt="Beskrivelse">`
- `<br>` (linjeskift)
- `<hr>` (vandret linje)
- `<meta charset="UTF-8">`
- `<link rel="stylesheet" href="style.css">`

**Par tags** - har åbnings- og lukketag:
- `<p>Tekst her</p>`
- `<div>Indhold her</div>`
- `<section>Sektion indhold</section>`

### Block vs. inline elementer
**Block elementer** - fylder hele bredden, starter på ny linje:
- `<div>`, `<p>`, `<h1>-<h6>`
- `<section>`, `<article>`, `<header>`, `<footer>`
- `<main>`, `<nav>`, `<aside>`
- `<ul>`, `<ol>` (lister er block elementer)

**Inline elementer** - kun den plads de bruger, kan stå på samme linje:
- `<span>`, `<a>`, `<strong>`, `<em>`
- `<mark>`, `<time>`, `<img>`

```html
<!-- Block elementer starter på ny linje -->
<p>Dette er et afsnit</p>
<p>Dette starter på en ny linje</p>

<!-- Inline elementer kan stå på samme linje -->
<p>Her er <strong>fed tekst</strong> og <a href="#">et link</a> på samme linje</p>

<!-- Lister til navigation -->
<nav>
    <ul>
        <li><a href="#home">Hjem</a></li>
        <li><a href="#about">Om</a></li>
    </ul>
</nav>
```

## Vigtige regler for semantiske tags

### Overskrifter (h1-h6)
- **Kun ét `<h1>` tag per side** - dette er sidens hovedoverskrift
- Hver `<section>` og `<article>` skal have en overskrift (typisk h2-h6)
- Brug overskrifter i logisk rækkefølge (h1 → h2 → h3...)

### Alt-attributter
- **Alle billeder SKAL have alt-attributter** for tilgængelighed
- Beskriv billedets indhold og funktion
- Hvis billedet er dekorativt, brug `alt=""` (tom streng)

## Eksempel 1: Komplet dokumentstruktur
```html
<!DOCTYPE html>
<html lang="da">
<head>
    <!-- Alt i head er IKKE synligt for brugeren -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Min Portfolio - Jane Doe</title>
    <meta name="description" content="Portfolio for multimediedesigner Jane Doe">
    <link rel="stylesheet" href="style.css">
</head>

<body>
    <!-- Alt i body ER synligt for brugeren -->
    <header>
        <h1>Jane Doe - Multimediedesigner</h1>
        <nav>
            <ul>
                <li><a href="#om">Om mig</a></li>
                <li><a href="#projekter">Projekter</a></li>
                <li><a href="#kontakt">Kontakt</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="om">
            <h2>Om mig</h2>
            <p>Jeg er en kreativ multimediedesigner...</p>
            
            <!-- Responsive billede med picture tag -->
            <picture>
                <source media="(max-width: 768px)" srcset="profil-mobil.jpg">
                <source media="(min-width: 769px)" srcset="profil-desktop.jpg">
                <img src="profil-desktop.jpg" alt="Profilbillede af Jane Doe">
            </picture>
        </section>

        <section id="projekter">
            <h2>Mine projekter</h2>
            <article>
                <h3>Website redesign</h3>
                <p>Et responsive redesign af en lokal virksomheds hjemmeside.</p>
                <time datetime="2024-03-15">15. marts 2024</time>
            </article>
        </section>
    </main>

    <footer>
        <address>
            Email: jane@example.com<br>
            Telefon: +45 12 34 56 78
        </address>
        <p>&copy; 2024 Jane Doe</p>
    </footer>
</body>
</html>
```

## Eksempel 2: Blog med responsive billeder
```html
<main>
    <article>
        <header>
            <h1>Responsive Design Principper</h1>
            <p>Publiceret <time datetime="2024-06-20">20. juni 2024</time></p>
        </header>

        <section>
            <h2>Mobile-first tilgang</h2>
            <p>Når vi designer responsive websites...</p>
            
            <figure>
                <!-- Picture tag for forskellige skærmstørrelser -->
                <picture>
                    <source media="(max-width: 480px)" srcset="mobile-wireframe-small.webp">
                    <source media="(max-width: 768px)" srcset="mobile-wireframe-medium.webp">
                    <source media="(min-width: 769px)" srcset="mobile-wireframe-large.webp">
                    <img src="mobile-wireframe-large.webp" alt="Mobile wireframe eksempel">
                </picture>
                <figcaption>Eksempel på mobile-first wireframe i forskellige størrelser</figcaption>
            </figure>
        </section>

        <section>
            <h2>Breakpoints</h2>
            <p><mark>Breakpoints</mark> er de skærmstørrelser hvor designet ændrer sig...</p>
        </section>
    </article>

    <aside>
        <h3>Relaterede artikler</h3>
        <ul>
            <li><a href="/css-grid">CSS Grid Tutorial</a></li>
            <li><a href="/flexbox">Flexbox Guide</a></li>
        </ul>
    </aside>
</main>
```

## Eksempel 3: Produktside med interaktivt indhold
```html
<main>
    <article>
        <header>
            <h1>Adobe Creative Suite Kursus</h1>
            <p>Lær de grundlæggende værktøjer til grafisk design</p>
        </header>

        <section>
            <h2>Kursusbeskrivelse</h2>
            <p>Dette intensive kursus dækker Photoshop, Illustrator og InDesign...</p>

            <details>
                <summary>Se fuldt kursusindhold</summary>
                <ul>
                    <li>Photoshop: Billedredigering og retouchering</li>
                    <li>Illustrator: Vektordesign og logoer</li>
                    <li>InDesign: Layout og typografi</li>
                </ul>
            </details>
        </section>

        <section>
            <h2>Praktiske oplysninger</h2>
            <p>Kurset afholdes hver <time datetime="2024-09-01">1. september</time></p>
            <p>Pris: <mark>3.500 kr.</mark> (inkl. materialer)</p>
        </section>
    </article>

    <aside>
        <h3>Kursusinformation</h3>
        <address>
            <strong>Kursussted:</strong><br>
            Designskolen<br>
            Vestergade 12<br>
            8000 Aarhus C
        </address>
    </aside>
</main>
```

## Eksempel 4: Navigationsmenu med lister
```html
<!DOCTYPE html>
<html lang="da">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Designstudio - Kreative Løsninger</title>
    <style>
        /* Grundlæggende styling til navigation */
        nav ul {
            list-style: none; /* Fjerner prikker */
            padding: 0;
            margin: 0;
            display: flex; /* Vandret menu */
        }
        
        nav li {
            margin-right: 2rem;
        }
        
        nav a {
            text-decoration: none;
            color: #333;
            font-weight: bold;
        }
        
        nav a:hover {
            color: #007acc;
        }
    </style>
</head>

<body>
    <header>
        <h1>Designstudio</h1>
        
        <!-- Navigation med ul og li -->
        <nav>
            <ul>
                <li><a href="#forside">Forside</a></li>
                <li><a href="#services">Services</a></li>
                <li><a href="#portfolio">Portfolio</a></li>
                <li><a href="#om">Om os</a></li>
                <li><a href="#kontakt">Kontakt</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="services">
            <h2>Vores services</h2>
            
            <!-- Sorteret liste med ol -->
            <h3>Designproces i 5 trin:</h3>
            <ol>
                <li>Møde og briefing</li>
                <li>Konceptudvikling</li>
                <li>Design og prototype</li>
                <li>Test og feedback</li>
                <li>Finalisering og levering</li>
            </ol>
            
            <!-- Usorteret liste med ul -->
            <h3>Hvad vi tilbyder:</h3>
            <ul>
                <li>Webdesign og udvikling</li>
                <li>Grafisk design og branding</li>
                <li>UI/UX design</li>
                <li>Logodesign</li>
                <li>Print og digital markedsføring</li>
            </ul>
        </section>
    </main>
</body>
</html>
```

## Eksempel 5: Footer med navigation og adresse
```html
<footer>
    <!-- Footer navigation -->
    <nav>
        <h3>Hurtige links</h3>
        <ul>
            <li><a href="#privatlivspolitik">Privatlivspolitik</a></li>
            <li><a href="#vilkaar">Vilkår og betingelser</a></li>
            <li><a href="#sitemap">Sitemap</a></li>
            <li><a href="#support">Support</a></li>
        </ul>
    </nav>
    
    <!-- Kontaktoplysninger med address tag -->
    <address>
        <h3>Kontakt os</h3>
        <strong>Designstudio ApS</strong><br>
        Kreativ Gade 42, 2. sal<br>
        8000 Aarhus C<br>
        <br>
        Email: <a href="mailto:info@designstudio.dk">info@designstudio.dk</a><br>
        Telefon: <a href="tel:+4587654321">+45 87 65 43 21</a><br>
        CVR: 12345678
    </address>
    
    <!-- Sociale medier navigation -->
    <nav>
        <h3>Følg os</h3>
        <ul>
            <li><a href="https://facebook.com/designstudio" target="_blank">Facebook</a></li>
            <li><a href="https://instagram.com/designstudio" target="_blank">Instagram</a></li>
            <li><a href="https://linkedin.com/company/designstudio" target="_blank">LinkedIn</a></li>
        </ul>
    </nav>
    
    <!-- Copyright -->
    <p>&copy; 2024 Designstudio ApS. Alle rettigheder forbeholdes.</p>
</footer>
```

## Fordele ved semantiske tags
- **SEO**: Søgemaskiner forstår bedre din sides struktur
- **Tilgængelighed**: Skærmlæsere kan navigere lettere
- **Kodekvalitet**: Mere læsbar og vedligeholdelig kode
- **Fremtidssikring**: Følger webstandarder og best practices

## Husk - vigtige regler
- Brug kun én `<main>` per side
- **Kun ét `<h1>` tag per side** - dette er hovedoverskriften
- Hver `<section>` og `<article>` skal have en overskrift (h2-h6)
- **Alle billeder skal have alt-attributter** - beskriv indholdet for tilgængelighed
- **Brug `<ul>` og `<li>` til navigation** - dette er semantisk korrekt for menuer
- `<ol>` til nummererede lister, `<ul>` til punktlister
- `<article>` skal kunne stå alene (fx blogindlæg)
- `<section>` bruges til at gruppere relateret indhold
- Kombiner altid semantiske tags med passende overskrifter i logisk rækkefølge