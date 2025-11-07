Vandringsleder Stockholm
Projektbeskrivning
En responsiv webbplats som presenterar vandringsleder i Stockholmsområdet, kategoriserade efter svårighetsgrad och tillgänglighet. Projektet syftar till att göra det enkelt för både nybörjare och erfarna vandrare att hitta passande leder i närområdet.
Webbplatsen innehåller:
●	Startsida med fyra huvudkategorier av vandringsleder
●	Enkla leder för nybörjare
●	Utmanande leder för erfarna vandrare
●	Familjeleder med barnvänlig information
●	Kollektivtrafikleder för lättillgängliga alternativ
Länk till live-version: https://johanmisundstrom.github.io/vandringsleder-stockholm/
Skärmdumpar
●	Startsida mobilvy: https://github.com/johanmisundstrom/vandringsleder-stockholm/blob/main/screenshots/mobileindex.jpeg
●	Startsida desktop: https://github.com/johanmisundstrom/vandringsleder-stockholm/blob/main/screenshots/desktopindex.jpeg
●	Led-vy: https://github.com/johanmisundstrom/vandringsleder-stockholm/blob/main/screenshots/enklaleder.jpeg
●	Hovereffekt kategorikort: https://github.com/johanmisundstrom/vandringsleder-stockholm/blob/main/screenshots/hovereffektenklaleder.jpeg
Designbeslut
Färgpalett
Projektet använder en naturinspirerad färgpalett som speglar vandringens koppling till skog, vatten och natur:
●	Primärfärg (Grön): Symboliserar skog och natur, skapar en lugn och inbjudande känsla
●	Accentfärger: Jordfärger och naturliga toner för att skapa harmoni
●	Kontrastfärger: Används sparsamt för active-sidan och med hover-effekter
Motivering: Färgvalet förstärker webbplatsens tema och skapar en omedelbar association till utomhusaktiviteter. Den gröna färgen är dessutom bekant från vandringskartor och vägskyltning i naturen.
Typografi
●	Rubriker: Sans-serif-typsnitt för tydlighet och modern känsla
●	Brödtext: Lättläst typsnitt med god radavstånd för optimal läsbarhet
●	Hierarki: Tydlig typografisk hierarki med varierande textstorlekar för h1, h2 och brödtext
Motivering: Valet av sans-serif ger en ren och modern look som fungerar bra på alla enheter. God läsbarhet är prioriterat eftersom användare ofta läser informationen på mobila enheter utomhus.
Layout
●	Grid-baserad layout: Kategorikorten på startsidan presenteras i ett responsivt rutnät
●	Card-design: Varje vandringskategori presenteras som ett visuellt kort med bild, beskrivning och länk
●	Mobile-first approach: Layouten anpassar sig från en kolumn på mobil till flera kolumner på desktop. Nav-menyn är en hamburger-meny på mobil och blir knappar på desktop.
●	Whitespace: Generöst med luft mellan element för att skapa en luftig och inbjudande design
Motivering: En kortbaserad design gör det enkelt att skanna innehållet snabbt. Grid-layouten är flexibel och ger en strukturerad presentation som fungerar väl för kategorisering av innehåll.
CSS-mönster för interaktivitet
1. Hover-effekt på kategorikort
.category-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 16px rgba(0,0,0,0.15);
}
Kort lyfts upp och får starkare skugga vid hover, vilket ger användaren tydlig feedback om att elementet är klickbart.
2. Bild-zoom vid hover
.category-card:hover .category-image img,
.trail-card:hover .trail-image img {
    transform: scale(1.05);
}
Bilder zoomas in lätt när användaren hovrar över ett kort, vilket skapar en dynamisk och engagerande effekt.
3. Knapp-interaktivitet med flera states
.btn:hover {
    background-color: #3a6b32;
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}
.btn:active {
    background-color: #1e4519;
    transform: translateY(0);
    box-shadow: 0 2px 4px rgba(0,0,0,0.3);
    transition: all 0.1s;
}
Knappar har tre states - normal, hover (lyfts upp) och active (trycks ner), vilket ger en realistisk känsla av interaktion.

4. Navigationslänkar med färgövergångar
nav a:hover {
    color: #a8d5a3;
}

nav a:active {
    color: #8bc34a;
    transform: scale(0.95);
}
Länkar i navigationen ändrar färg vid hover och krymper lätt vid klick för att ge omedelbar feedback.
5. Tillgänglighetsanpassad fokusmarkering
a:focus, a:hover, button:focus, button:hover {
color: #0055aa; 
outline: 3px solid #2d5a27;
outline-offset: 3px; 
box-shadow: 0 0 8px #2d5a27cc;
text-decoration: underline;
}
a:focus-visible, button:focus-visible {
    outline: 3px solid #2d5a27;
    outline-offset: 3px;
    box-shadow: 0 0 12px #2d5a27dd;
}
Både fokus och hover ger tydlig feedback med mörkblå färg (#0055aa), grön ram och understrukning. Tangentbordsnavigation får extra stark fokusmarkering med intensivare skugga, vilket uppfyller tillgänglighetskrav enligt WCAG.

6. Interaktiv accordion/FAQ
.faq-item summary:hover {
    background: #e9f0e8;
}

.faq-item summary::after {
    content: "+";
    transition: transform 0.3s ease;
}

.faq-item[open] summary::after {
    content: "−";
}
FAQ-sektioner använder HTML <details> med visuell feedback - plus-ikon roterar till minus när sektionen öppnas.
7. Skip-to-content länk för tillgänglighet
.skip-link:focus,
.skip-link:active {
    clip-path: none;
    width: auto;
    height: auto;
    top: 0;
}
En dold länk som endast visas när användaren tabbar med tangentbordet, vilket låter dem hoppa direkt till huvudinnehållet.
8. Aktiv navigationsindikator 
nav a.active {
 	color: #0055aa;
 	text-decoration: underline;
 } 
Den aktiva sidan i navigationen markeras med mörkblå färg och understrukning, vilket ger användaren tydlig orientering om var de befinner sig på webbplatsen. Detta förbättrar användarupplevelsen genom att visa det aktuella sidläget i navigationsmenyn.
9. Responsiv hamburgermeny
@media (max-width: 600px) {
    nav input[type="checkbox"]:checked ~ ul {
        display: flex;
    }
}
På mobil används en checkbox-hack för att visa/dölja menyn utan JavaScript, vilket är en ren CSS-lösning.
________________________________________
Kända begränsningar
Begränsad filteringsfunktion: Användare kan inte kombinera flera filter (t.ex. "enkla leder nära kollektivtrafik").
Ingen karttjänst: Saknar integration med Google Maps eller liknande för att enkelt guida användarna till startplatsen av en vandringsled till exempel.


Begränsad bildoptimering: Bilder kanske inte är fullständigt optimerade för alla skärmstorlekar och anslutningshastigheter.


Ingen bokmärkningsfunktion: Användare kan inte spara sina favoritleder för senare. I nuvarande skick så är sidan dock så pass liten så det behövs inte. Hade man gjort om sidan för vandringsleder för hela Sverige så hade det varit användbart med konto-funktioner med databaser, där användaren kan spara favoritleder, markera vilka de gått, jämföra med sina vänner eller jämföra tider med sina vänner.

Språk: Endast svenska, ingen flerspråksstöd.

________________________________________
Förbättringsidéer
Kortsiktiga förbättringar
●	Sökfunktion: Möjlighet att söka efter specifika leder eller områden(om sidan omfattar ett större område)
●	Bildgalleri: Fler bilder från varje led
Långsiktiga förbättringar
●	Interaktiv karta: Integration med kartjänst för att visa ledernas exakta läge och rutt
●	Användarrecensioner: Möjlighet för besökare att betygsätta och recensera leder
●	Vädertjänst: Integration som visar aktuellt väder för olika vandringsområden
●	Svårighetsgrad-kalkylator: Verktyg som hjälper användare välja led baserat på kondition och erfarenhet
●	Olika teman skulle kunna vara tillgängliga, så att beroende på årstid så ändras temat för hemsidan och det ser annorlunda. Eller att användaren kan välja fritt själv bland dessa teman som finns tillgängliga.
●	Flerspråksstöd: Engelska för internationella besökare

