---
layout: post
title:  "Tankar om jekyll"

---

<h3>Vad tycker du om pre-compiling din CSS?</h3>
<div class = "answere">
<ul>
    <li><h4>Jämför med vanlig CSS</h4>
        <blockquote> När man väl har sats sig in i strukturen för jekyll så där det väldigt smidigt att göra ändringar för css.</blockquote>
    </li>
    <li><h4>Vilken teknik använde du?</h4>
      <blockquote> Jag använde mig av grundstrukturen ifrån jekyll för css, sen skrev skapde jag en fil (main.scss) där jag skrev över bara det jag ville ändra</blockquote>
    </li>    
      <li><h4>Fördelar och nackdelar?</h4>
      <blockquote>
        <div class = "pros">Det stora arbetet är redan gjort, nu är det förhållandevis enkelt att göra förändringar av CSSen</div>
        <div class = "pros">Med små förändringar kan du uppnå bra resultat då layouten är redan gjord. Min erfarenhet av CSS är att layouten tog fruktansvärt lång tid att göra</div>
        <hr>
        <div class = "cons">Svårt att veta var koden kommer ifrån</div>
        <div class = "cons">Svårt att felsöka</div>
     </blockquote>
   
    </li>    
</ul>
</div>
<h3>Vad tycker du om static site generators?</h3>
  <blockquote> 
         Jag tyckte till en början att det var svårt att veta vad jag skulle göra för att uppnå det jag ville, 
         men bara efter 2-3 dagar med jekyll så känner jag att det är ganska lätt att skapa en sida.
         Nästa gång jag använder jekyll så kommer det gå väldigt fort att slänga upp en webbplats av god kvalité.
  </blockquote>
<h3>Vad är robots.txt och hur har du konfigurerat det för din sida?</h3>
  <blockquote> 
         robots.txt ligger i rotmappen och talar om för sökrobotor (crawlers) om de får indexera sidan.
         Jag valde att blockera allt då min mail ligger i footer på alla mina sidor.
  </blockquote> 
<h3> Vad är humans.txt och hur har du konfigurerat det för din sida?</h3>
  <blockquote>
         humans.txt ligger likt robots.txt i root, humans.txt ansvänds till att beskriva lite om webbplatsen. 
         Man kan t.ex ange vem som gjort/äger platsen, vilka mjukvaror man använt och vem vill tacka osv.
         Jag väljer att tacka jekyll samt github i detta projekt.
  </blockquote>
<h3> Hur har du implementerat kommentarer till blog posts?</h3>
  <blockquote>
         Jag har använt mig av disqus för kommentarer för mina blogginlägg, jag kan om jag vill stänga av kommentarer för en blog med.
         comments: false
         Jag skapde en "override" disqus_comments.html där jag angav mina inställningar för disqus.
  </blockquote>
<h3>Vad är Open Graph och hur har du använt dig utav det?</h3>
<blockquote>
     Open graph är en teknik framtaget av facebook, som används för att presentera länkar till webbplatser på ett mer delikat sätt.
     Man du kan välja själv hur det ska presenteras, genom att välja vilken bild som ska visas, vilken titel och även en beskrivning av webplatsen kan anges.
     Jekyll hjälper mig att genera upp de flesta opengraph tagsen.
     Jag har valt att göra en kopia på head.html och där jag har lagt information om Opengraph image.     
</blockquote>
