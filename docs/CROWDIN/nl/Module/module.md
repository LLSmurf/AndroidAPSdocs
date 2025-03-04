

<div id="front-matter"><ul><li><div class="yaml-key" translate="no" has_child_nodes="yes">substitutions: </div><ul><li><div class="yaml-key" translate="no" has_child_nodes="no">DiaLink: </div><div class="yaml-value">`{image} ../images/omnipod/DiaLink.png`</div></li>
- <div class="yaml-key" translate="no" has_child_nodes="no">EmaLink: </div><div class="yaml-value">
    <code>{image} ../images/omnipod/EmaLink.png</code>
  </div>
- <div class="yaml-key" translate="no" has_child_nodes="no">LoopLink: </div><div class="yaml-value">
    <code>{image} ../images/omnipod/LoopLink.png</code>
  </div>
- <div class="yaml-key" translate="no" has_child_nodes="no">OrangeLink: </div><div class="yaml-value">
    <code>{image} ../images/omnipod/OrangeLink.png</code>
  </div>
- <div class="yaml-key" translate="no" has_child_nodes="no">RileyLink: </div><div class="yaml-value">
    ```{image} ../images/omnipod/RileyLink.png</p> 
    
    <pre><code class="&lt;/div&gt;&lt;/li&gt;&lt;/ul&gt;&lt;/li&gt;&lt;/ul&gt;&lt;/div&gt;">

# Component Overview

AndroidAPS is not just a (self-built) application, it is just one of several modules of your closed loop system. Before deciding for components, it would be a good idea to have a look at the [component setup](../index.md#component-setup), too.

```{image} ../images/modules.png
:alt: Components overview
</code></pre>
    
    <p spaces-before="0">
      :::{note}<br x-id="2" /> <strong x-id="1">IMPORTANT SAFETY NOTICE</strong>
    </p>
    
    <p spaces-before="0">
      De veiligheidsfuncties die in AndroidAPS zitten, maken gebruik van ingebouwde veiligheidsmaatregelen van de hardware componenten waaruit jouw systeem bestaat. Het is daarom van cruciaal belang dat je alleen een volledig functionerende FDA of CE goedgekeurde insulinepomp en CGM gebruikt voor het bouwen van jouw eigen closed loop. Gebruik alleen insulinepompen en CGMs die in deze handleiding beschreven staan, waarvoor de AndroidAPS software is geschreven en getest. Hardware of software wijzigingen aan deze componenten kunnen voor onverwachte uitkomsten zorgen (denk aan het ongewenst afgeven van insuline), waardoor de gebruiker een aanzienlijk risico loopt. If you find or get offered broken, modified or self-made insulin pumps or CGM receivers, <em x-id="3">do not use</em> these for creating an AndroidAPS system.
    </p>
    
    <p spaces-before="0">
      Daarnaast is het belangrijk om alleen originele verbruiksartikelen te gebruiken, zoals infuussets, inschiethulpen en reservoirs die door de fabrikant zijn goedgekeurd voor gebruik met jouw pomp of CGM. Door het gebruik van niet-originele, niet-geteste verbruiksmaterialen kunnen CGM metingen onnauwkeurig worden en/of fouten optreden in de insulinedosering. Insuline is zeer gevaarlijk wanneer het verkeerd wordt gedoseerd - speel alstublieft niet met je leven door jouw hulpmiddelen aan te passen.
    </p>
    
    <p spaces-before="0">
      Tensotte een belangrijke opmerking: je mag géén SGLT-2 inhibitors (glifozines) gebruiken wanneer je loopt. Omdat deze medicatie ook de bloedsuiker verlaagt.  Deze medicatie in combinatie met een systeem dat de basale insuline verlaagt om BG te verhogen is bijzonder gevaarlijk, omdat deze stijging in BG mogelijk niet zal gebeuren en daardoor een gevaarlijk gebrek aan insuline kan ontstaan.
:::
    </p>

<h2 spaces-before="0">
  Benodigde onderdelen
</h2>

<h3 spaces-before="0">
  Correcte insulineprofiel instellingen voor jouw diabetesbehandeling
</h3>

<p spaces-before="0">
  Dit is misschien niet het eerste waar je aan denkt bij een 'onderdeel'. Toch is het waarschijnlijk het meest belangrijke onderdeel van jouw closed loop. Wanneer je de behandeling van jouw diabetes overlaat aan een algoritme, dan is het cruciaal dat je dit algoritme de juiste instellingen geeft. Anders kunnen er grote fouten optreden in de beslissingen die het algoritme neemt. Wanneer je de andere onderdelen van jouw closed loop nog niet bij elkaar hebt, dan kun je de tussenliggende tijd benutten om, samen met jouw behandelaars, jouw instellingen te perfectioneren. De meeste loopers maken gebruik van basaalstanden, ISF en KH ratios die zijn aangepast aan een variërende insulinegevoeligheid gedurende de dag (zgn. circadiaans ritme).
</p>

<p spaces-before="0">
  Het profiel bevat
</p>

<ul>
  <li>
    BR (Basal rates)
  </li>
  <li>
    ISF (insulin sensitivity factor) is your blood glucose unit per one unit insulin
  </li>
  <li>
    CR (carb ratio) is grams carbohydrate per one unit insulin
  </li>
  <li>
    DIA (duration of insulin acting).
  </li>
</ul>

<p spaces-before="0">
  (no-use-of-sglt-2-inhibitors)=
</p>
<h3 spaces-before="0">
  Geen gebruik van SGLT-2-remmers
</h3>

<p spaces-before="0">
  SGLT-2 remmers, ook wel glifozines genoemd, remmen de herabsorptie van glucose in de nieren. Omdat ze de bloedsuikerspiegel verlagen met een voor het algoritme niet-berekenbare hoeveelheid, mag je ze ABSOLUUT NIET gebruiken wanneer je een closed loop systeem zoals AndroidAPS gebruikt! Dit vanwege het zeer grote risico op ketoacidose en/of ernstige hypo's. Deze medicatie in combinatie met een systeem dat de basale insuline verlaagt om BG te verhogen is bijzonder gevaarlijk, omdat er een gevaarlijk gebrek aan insuline kan ontstaan.
</p>

<p spaces-before="0">
  (phone)=
</p>
<h3 spaces-before="0">
  Telefoon
</h3>

<p spaces-before="0">
  Voor de huidige versie van AndroidAPS is een Android smartphone nodig met Google Android 8.0 of hoger. Dus als je denkt over een nieuwe telefoon, dan raden we aan om op zijn minst voor Android 8.1 te gaan maar liever Android 9 of 10. Users are strongly encouraged to keep their build of AndroidAPS up to date for safety reason, however for users unable to use a device with a minimum version of Android 8.0, AndroidAPS version 2.6.1.4, suitable for older Android versions, remains available from the <a href="https://github.com/miloskozak/androidaps">old repository.</a>
</p>

<p spaces-before="0">
  Users are creating a <a href="https://docs.google.com/spreadsheets/d/1gZAsN6f0gv6tkgy9EBsYl0BQNhna0RDqA9QGycAqCQc/edit?usp=sharing">list of tested phones and watches</a>
</p>

<p spaces-before="0">
  To record a phone or watch that isn't already listed in the spreadsheet then please fill in the <a href="https://docs.google.com/forms/d/e/1FAIpQLScvmuqLTZ7MizuFBoTyVCZXuDb__jnQawEvMYtnnT9RGY6QUw/viewform">form</a>.
</p>

<p spaces-before="0">
  Any problems with the spreadsheet please send an email to <a href="mailto:hardware@androidaps.org">hardware@androidaps.org</a>, any donations of phone/watch models that still need testing please send an email to <a href="mailto:hardware@androidaps.org">donations@androidaps.org</a>.
</p>

<h3 spaces-before="0">
  Insulinepomp
</h3>

<p spaces-before="0">
  AndroidAPS <strong x-id="1">currently</strong> works with
</p>

<ul>
  <li>
    <a href="../Configuration/Accu-Chek-Combo-Pump.md">Accu-Chek Combo</a> (additionally needed: Ruffy app, LineageOS or Android 8.1 on your phone)
  </li>
  <li>
    <a href="../Configuration/Accu-Chek-Insight-Pump.md">Accu-Chek Insight</a>
  </li>
  <li>
    <a href="../Configuration/DanaR-Insulin-Pump.md">DanaR</a>
  </li>
  <li>
    <a href="../Configuration/DanaRS-Insulin-Pump.md">Dana-i/RS</a>
  </li>
  <li>
    <a href="../Configuration/MedtronicPump.md">some old Medtronic pumps</a> from upcoming version 2.4 (<a href="../Module/module.md#additional-communication-device">additional communication device</a> needed)
  </li>
  <li>
    <a href="../Configuration/OmnipodEros.md">Omnipod Eros</a> (<a href="../Module/module.md#additional-communication-device">additional communication device</a> needed)
  </li>
  <li>
    <a href="../Configuration/OmnipodDASH.md">Omnipod DASH</a>
  </li>
</ul>

<p spaces-before="0">
  If no additional communication device  is mentioned the communication betweeen insulin pump and AndroidAPS is based on the integrated bluetooth stack of Android without the need of an additional communication device to translate the communnication protocol.
</p>

<p spaces-before="0">
  <strong x-id="1">Other pumps</strong> that may have the potential to work with AndroidAPS are listed on the <a href="../Getting-Started/Future-possible-Pump-Drivers.md">Future (possible) Pumps</a> page.
</p>

<p spaces-before="0">
  If you need to <strong x-id="1">privately buy</strong> a pump then you can find various distributors is in <a href="https://drive.google.com/open?id=1CRfmmjA-0h_9nkRViP3J9FyflT9eu-a8HeMrhrKzKz0">this spreadsheet</a>, please share the details of yours if not already listed.
</p>

<p spaces-before="0">
  (additional-communication-device)=
</p>
<h4 spaces-before="0">
  Extra communicatie apparaatje (Link)
</h4>

<p spaces-before="0">
  For old medtronic pumps an additional communication device (besides your phone) is needed to "translate" the radio signal from pump to bluetooth. Zorg ervoor dat je de juiste versie kiest, afhankelijk van jouw pomp.
</p>

<ul>
  <li>
    {{ OrangeLink }}  <a href="https://getrileylink.org/product/orangelink">OrangeLink Website</a>
  </li>
  <li>
    {{ RileyLink }} <a href="https://getrileylink.org/product/rileylink433">433MHz RileyLink</a>
  </li>
  <li>
    {{ EmaLink }}  <a href="https://github.com/sks01/EmaLink">Emalink Website</a> - <a href="mailto:getemalink@gmail.com">Contact Info</a>
  </li>
  <li>
    {{ DiaLink }}  DiaLink - <a href="mailto:Boshetyn@ukr.net">Contact Info</a>
  </li>
  <li>
    {{ LoopLink }}  <a href="https://www.getlooplink.org/">LoopLink Website</a> - <a href="https://jameswedding.substack.com/">Contact Info</a> - Untested
  </li>
</ul>

<p spaces-before="0">
  <strong x-id="1">So what's the best pump for looping with AndroidAPS?</strong>
</p>

<p spaces-before="0">
  De Combo, de Insight en de oudere Medtronics zijn goede pompen en loopbaar. De Combo heeft ook als voordeel dat er veel meer keuze is in infuussets, aangezien hij een standaard luer-lock aansluiting heeft. Er gaat een normale batterij in, die je bij een tankstation of supermarkt kunt kopen en mocht het echt nodig zijn, kunt je hem altijd nog stelen/lenen van de afstandsbediening in een hotelkamer ;-).
</p>

<p spaces-before="0">
  The advantages of the DanaR/RS and Dana-i vs. the Combo as the pump of choice however are:
</p>

<ul>
  <li>
    The Dana pumps connect to almost any phone with Android >= 5.1 without the need to flash lineage. If your phone breaks you usually can find easily any phone that works with the Dana pumps as quick replacement... not so easy with the Combo. (Dit kan veranderen in de toekomst, als Android 8.1 populairder wordt)
  </li>
  <li>
    Initial pairing is simpler with the Dana-i/RS. Maar dit doe je meestal eenmalig.
  </li>
  <li>
    So far the Combo works with screen parsing. In het algemeen werkt dit prima, maar het is traag. Bij het loopen merk je dit vaak niet eens omdat alles op de achtergrond werkt. Still there is much more time you need to be connected so more time where the BT connection might break, which isn't so easy if you walk away from your phone whilst bolusing & cooking.
  </li>
  <li>
    The Combo vibrates on the end of TBRs, the DanaR vibrates (or beeps) on SMB. Waarschijnlijk gebruikt de loop 's nachts vaker een TBR dan SMB.  The Dana-i/RS is configurable that it does neither beep or vibrate.
  </li>
  <li>
    Reading the history on the Dana-i/RS in a few seconds with carbs makes it possible to switch phones easily while offline and continue looping as soon a soon as some CGM values are in.
  </li>
  <li>
    All pumps AndroidAPS can talk with are waterproof on delivery. Alleen de Dana pompen zijn ook gegarandeerd waterdicht tijdens gebruik, doordat de ruimtes voor batterij en reservoir volledig afgesealed zijn.
  </li>
</ul>

<h3 spaces-before="0">
  BG bron
</h3>

<p spaces-before="0">
  Dit is slechts een kort overzicht van alle compatibele CGMs/FGM met AndroidAPS. For further details, look <a href="../Configuration/BG-Source.md">here</a>. Even kort samengevat: als je jouw glucosewaardes kunt laten weergeven in de xDrip+ app of op jouw Nightscout site, dan kun je in AAPS als "BG bron" kiezen voor xDrip+ (of voor Nightscout, maar dan heb je wel continu een internetverbinding nodig).
</p>

<ul>
  <li>
    <a href="../Hardware/DexcomG6.md">Dexcom G6</a>: BOYDA is recommended as of version 3.0 (see <a href="../Installing-AndroidAPS/Releasenotes.md#important-hints-3-0-0">release notes</a> for details). xDrip+ must be at least version 2022.01.14 or newer
  </li>
  <li>
    <a href="../Hardware/DexcomG5.md">Dexcom G5</a>: It works with xDrip+ app or patched Dexcom app
  </li>
  <li>
    <a href="../Hardware/DexcomG4.md">Dexcom G4</a>: These sensors are quite old, but you can find instructions on how to use them with xDrip+ app
  </li>
  <li>
    <a href="../Hardware/Libre2.md">Libre 2</a>: It works with xDrip+ (no transmitter needed), but you have to build your own patched app.
  </li>
  <li>
    <a href="../Hardware/Libre1.md">Libre 1</a>: You need a transmitter like Bluecon or MiaoMiao for it (build or buy) and xDrip+ app
  </li>
  <li>
    <a href="../Hardware/Eversense.md">Eversense</a>: It works so far only in combination with ESEL app and a patched Eversense-App (works not with Dana RS and LineageOS, but DanaRS and Android or Combo and Lineage OS work fine)
  </li>
  <li>
    <a href="../Hardware/MM640g.md">Enlite (MM640G/MM630G)</a>: quite complicated with a lot of extra stuff
  </li>
</ul>

<h3 spaces-before="0">
  Nightscout
</h3>

<p spaces-before="0">
  Nightscout is een open source web-applicatie die jouw CGM-gegevens en AndroidAPS gegevens kan opslaan, weergeven en rapporten kan maken. You can find more information on the <a href="http://nightscout.github.io/">website of the Nightscout project</a>. You can create your own <a href="https://nightscout.github.io/nightscout/new_user/">Nightscout website</a>, use the semi-automated Nightscout setup on <a href="https://ns.10be.de/en/index.html">zehn.be</a> or host it on your own server (this is for IT experts).
</p>

<p spaces-before="0">
  Nightscout werkt onafhankelijk van de andere onderdelen. Je hebt het nodig om voorbij Doel 1 te komen.
</p>

<p spaces-before="0">
  Additional information on how to configure Nightscout for use with AndroidAPS can be found <a href="../Installing-AndroidAPS/Nightscout.md">here</a>.
</p>

<h3 spaces-before="0">
  AAPS-.apk-bestand
</h3>

<p spaces-before="0">
  De basiscomponent van het systeem. Voordat je de app installeert, moet je eerst het apk-bestand (dat is de bestandsnaam extensie voor een Android app) maken. Instructions are  <a href="../Installing-AndroidAPS/Building-APK.md">here</a>.
</p>

<h2 spaces-before="0">
  Optionele onderdelen
</h2>

<h3 spaces-before="0">
  Smartwatch
</h3>

<p spaces-before="0">
  Elke smartwatch met Android Wear 1.x en hoger is geschikt. Sommige loopers dragen een Sony Smartwatch 3 (SWR50) omdat het het enige horloge is dat elke 5 minuten een Dexcom G5/G6 ontvangt zonder de telefoon in de buurt te hebben. Dit wordt "stand alone" ontvanger genoemd. Some other watches can be patched to work as a standalone receiver as well (see <a href="https://github.com/NightscoutFoundation/xDrip/wiki/Patching-Android-Wear-devices-for-use-with-the-G5">this documentation</a> for more details).
</p>

<p spaces-before="0">
  Users are creating a <a href="https://docs.google.com/spreadsheets/d/1gZAsN6f0gv6tkgy9EBsYl0BQNhna0RDqA9QGycAqCQc/edit?usp=sharing">list of tested phones and watches</a>. There are different watchfaces for use with AndroidAPS, which you can find <a href="../Configuration/Watchfaces.md">here</a>.
</p>

<p spaces-before="0">
  To record a phone or watch that isn't already listed in the spreadsheet then please fill in the <a href="https://docs.google.com/forms/d/e/1FAIpQLScvmuqLTZ7MizuFBoTyVCZXuDb__jnQawEvMYtnnT9RGY6QUw/viewform">form</a>.
</p>

<p spaces-before="0">
  Any problems with the spreadsheet please send an email to <a href="mailto:hardware@androidaps.org">hardware@androidaps.org</a>, any donations of phone/watch models that still need testing please send an email to <a href="mailto:hardware@androidaps.org">donations@androidaps.org</a>.
</p>

<h3 spaces-before="0">
  xDrip+
</h3>

<p spaces-before="0">
  Even if you don't need to have the xDrip+ App as BG Source, you can still use it for i.e. alarms or a good blood glucose display. Je kunt in xDrip+ zoveel alarmen aanmaken als je wilt, en zelf tijdvakken specificeren wanneer een alarm actief moet zijn, of het alarm toch moet afgaan wanneer de telefoon in 'stille modus' staat, etc. Some xDrip+ information can be found <a href="../Configuration/xdrip.md">here</a>. Houd er rekening mee dat de documentatie van deze app niet altijd up-to-date is, aangezien hij zeer regelmatig wordt geupdatet.
</p>

<h2 spaces-before="0">
  Wat te doen tijdens het wachten op onderdelen
</h2>

<p spaces-before="0">
  Het duurt soms een tijdje voordat je alle onderdelen voor het maken van een closed loop bij elkaar hebt. Maar geen zorgen, er zijn een heleboel dingen die je kunt doen tijdens het wachten. It is NECESSARY to check and (where appropriate) adapt basal rates (BR), insulin-carbratio (IC), insulin-sensitivity-factors (ISF) etc. AndroidAPS gebruiken in open loop modus kan een goede manier zijn om jouw profielinstellingen te testen en vertrouwd te raken met het syteem. In de open loop modus geeft AndroidAPS behandelingsadviezen die je handmatig moet doorvoeren.
</p>

<p spaces-before="0">
  You can keep on reading through the docs here, get in touch with other loopers online or offline, <a href="../Where-To-Go-For-Help/Background-reading.md">read</a> documentations or what other loopers write (even if you have to be careful, not everything is correct or good for you to reproduce).
</p>

<p spaces-before="0">
  <strong x-id="1">Done?</strong> If you have your AAPS components all together (congrats!) or at least enough to start in open loop mode, you should first read through the <a href="../Usage/Objectives.md">Objective description</a> before each new Objective and setup up your <a href="../index.md#component-setup">hardware</a>.
</p>

<p spaces-before="0">
  % Image aliases resource for referencing images by name with more positioning flexibility
</p>

<p spaces-before="0">
  % Hardware and Software Requirements
</p>
