# Pilvipalvelut ja automaatio – Portfolio

Tämä repositorio toimii julkisena sivustona ja portfoliona pilvipalvelut-kurssin harjoituksille. Sivusto on toteutettu hyödyntämällä **GitHub Pages** -palvelua ja puhtaasti **Markdown**-syntaksia ilman erillistä HTML-koodia.

---

##  Toteutetut projektit

Kurssin aikana olen toteuttanut monipuolisesti erilaisia pilvi- ja automaatioratkaisuja. Alla on yhteenveto tehdyistä tehtävistä:

| Tehtävä | Aihe / Teknologia | Kuvaus | Status |
| :--- | :--- | :--- | :--- |
| **Tehtävä 1** | Render & CI/CD | Node.js-verkkosovelluksen pystytys ja automaattinen julkaisu | Valmis ✅ |
| **Tehtävä 2** | Terraform (IaC) | Linux VPS -palvelimen automatisoitu pystytys Hetzneriin | Valmis ✅ |
| **Tehtävä 3** | Cloudflare Pages | Staattisen verkkosivuston julkaisu ja jakelu[cite: 1] | Valmis ✅ |
| **Tehtävä 4** | Google Firebase | Pilvitietokannan (Firestore) hyödyntäminen dynaamisessa sovelluksessa[cite: 1] | Valmis ✅ |
| **Tehtävä 5** | Playwright / RPA | Lounaslistojen automaattinen skrapaus verkkosivulta[cite: 1] | Valmis ✅ |

---

##  Esimerkki koodista (Playwright bot)

Tässä on lyhyt pätkä koodia, jolla automatisoin lounaslistojen haun sivustolta:

```javascript
const { chromium } = require('playwright');

async function runBot() {
    const browser = await chromium.launch({ headless: true });
    const page = await browser.newPage();
    
    await page.goto('[[https://www.esimerkki-ravintola.fi/lounas](https://www.esimerkki-ravintola.fi/lounas](https://www.sodexo.fi/ravintolat/ravintolat-hilla-ja-mustikka))');
    await page.click('#ui-id-2'); 
    
    const meals = await page.locator('.meal-wrapper').allInnerTexts();
    console.log(`Löytyi ${meals.length} ateriaa.`);
    
    await browser.close();
}

runBot();
