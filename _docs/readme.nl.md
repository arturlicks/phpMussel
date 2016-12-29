## Documentatie voor phpMussel (Nederlandse).

### Inhoud
- 1. [PREAMBULE](#SECTION1)
- 2A. [HOE TE INSTALLEREN (VOOR WEBSERVERS)](#SECTION2A)
- 2B. [HOE TE INSTALLEREN (VOOR CLI)](#SECTION2B)
- 3A. [HOE TE GEBRUIKEN (VOOR WEBSERVERS)](#SECTION3A)
- 3B. [HOE TE GEBRUIKEN (VOOR CLI)](#SECTION3B)
- 4. [FRONTEND MANAGEMENT](#SECTION4)
- 5. [CLI (COMMANDLIJN INTERFACE)](#SECTION5)
- 6. [BESTANDEN IN DIT PAKKET](#SECTION6)
- 7. [CONFIGURATIEOPTIES](#SECTION7)
- 8. [HANDTEKENINGFORMAAT](#SECTION8)
- 9. [BEKENDE COMPATIBILITEITSPROBLEMEN](#SECTION9)
- 10. [VEELGESTELDE VRAGEN (FAQ)](#SECTION10)

*Opmerking over vertalingen: In geval van fouten (bv, verschillen tussen vertalingen, typefouten, ezv), de Engels versie van de README wordt beschouwd als het origineel en gezaghebbende versie. Als u vinden elke fouten, uw hulp bij het corrigeren van hen zou worden toegejuicht.*

---


###1. <a name="SECTION1"></a>PREAMBULE

Dank u voor het gebruiken van phpMussel, een PHP-script ontwikkeld om trojans, virussen, malware en andere bedreigingen te ontworpen, binnen bestanden geüpload naar uw systeem waar het script is haakte, gebaseerd op de handtekeningen van ClamAV en anderen.

PHPMUSSEL COPYRIGHT 2013 en verder GNU/GPLv2 van Caleb M (Maikuolan).

Dit script is gratis software; u kunt, onder de voorwaarden van de GNU General Public License zoals gepubliceerd door de Free Software Foundation, herdistribueren en/of wijzigen dit; ofwel versie 2 van de Licentie, of (naar uw keuze) enige latere versie. Dit script wordt gedistribueerd in de hoop dat het nuttig zal zijn, maar ZONDER ENIGE GARANTIE; zonder zelfs de impliciete garantie van VERKOOPBAARHEID of GESCHIKTHEID VOOR EEN BEPAALD DOEL. Zie de GNU General Public License voor meer informatie, gelegen in het `LICENSE.txt` bestand en ook beschikbaar uit:
- <http://www.gnu.org/licenses/>.
- <http://opensource.org/licenses/>.

Speciale dank aan [ClamAV](http://www.clamav.net/) voor zowel project inspiratie en voor de handtekeningen dat dit script maakt gebruik daarvan, zonder welke, het script zou waarschijnlijk niet bestaan, of op zijn best, zou heeft zeer beperkte waarde.

Speciale dank aan Sourceforge en GitHub voor het hosten van de project-bestanden, ann [Spambot Security](http://www.spambotsecurity.com/forum/viewforum.php?f=55) voor het hosten van de phpMussel discussies forums, en de extra bronnen van een aantal handtekeningen gebruikt door phpMussel: [SecuriteInfo.com](http://www.securiteinfo.com/), [PhishTank](http://www.phishtank.com/), [NLNetLabs](http://nlnetlabs.nl/) en anderen, en speciale dank aan allen die het project steunen, aan iemand anders die ik anders misschien vergeten te vermelden, en voor u, voor het gebruik van het script.

Dit document en de bijbehorende pakket kunt gedownload gratis zijn van:
- [Sourceforge](http://phpmussel.sourceforge.net/).
- [GitHub](https://github.com/Maikuolan/phpMussel/).

---


###2A. <a name="SECTION2A"></a>HOE TE INSTALLEREN (VOOR WEBSERVERS)

Ik hoop te stroomlijnen dit proces door maken een installateur op een bepaald punt in de niet al te verre toekomst, maar tot die tijd, volg deze instructies te werken phpMussel om meeste systemen en CMS:

1) Omdat u zijn lezen dit, ik ben ervan uit u al gedownload een gearchiveerde kopie van het script, uitgepakt zijn inhoud en heeft het ergens op uw lokale computer. Vanaf hier, u nodig te bepalen waar op uw host of CMS die inhoud te plaatsen. Een bestandsmap zoals `/public_html/phpmussel/` of soortgelijk (hoewel, het is niet belangrijk welke u kiest, zolang het is iets veilig en iets waar u blij mee bent) zal volstaan. *Voordat u het uploaden begint, lees verder..*

2) Hernoemen `config.ini.RenameMe` naar `config.ini` (gelegen binnen `vault`), en facultatief (sterk aanbevolen voor ervaren gebruikers, maar niet aan te raden voor beginners of voor de onervaren), open het (dit bestand bevat alle beschikbare phpMussel configuratie opties; boven elke optie moet een korte opmerking te beschrijven wat het doet en wat het voor). Pas deze opties als het u past, volgens welke geschikt is voor uw configuratie. Sla het bestand, sluiten.

3) Upload de inhoud (phpMussel en zijn bestanden) naar het bestandsmap die u zou op eerder besloten (u nodig niet de `*.txt`/`*.md` bestanden opgenomen, maar meestal, u moeten uploaden alles).

4) CHMOD het bestandsmap `vault` naar "755" (als er problemen, u kan proberen "777"; dit is minder veilig, hoewel). De belangrijkste bestandsmap opslaan van de inhoud (degene die u eerder koos), gewoonlijk, kunt worden genegeerd, maar CHMOD-status moet worden gecontroleerd als u machtigingen problemen heeft in het verleden met uw systeem (standaard, moet iets zijn als "755").

5) Volgende, u nodig om "haak" phpMussel om uw systeem of CMS. Er zijn verschillende manieren waarop u kunt "haak" scripts zoals phpMussel om uw systeem of CMS, maar het makkelijkste is om gewoon omvatten voor het script aan het begin van een kern bestand van uw systeem of CMS (een die het algemeen altijd zal worden geladen wanneer iemand heeft toegang tot een pagina in uw website) met behulp van een `require` of `include` opdracht. Meestal is dit wel iets worden opgeslagen in een bestandsmap zoals `/includes`, `/assets` of `/functions`, en zal vaak zijn vernoemd iets als `init.php`, `common_functions.php`, `functions.php` of soortgelijk. U nodig om te bepalen welk bestand dit is voor uw situatie; Als u problemen ondervindt bij het bepalen van dit voor uzelf, ga naar de phpMussel kwesties/issues pagina op Github of de phpMussel support forums voor assistentie; Het is mogelijk dat ofwel mijzelf of een andere gebruiker kunt ervaring met de CMS die u gebruikt heeft (u nodig om ons te laten weten welk CMS u gebruikt), en dus, in staat zijn om wat hulp te bieden in dit gebied. Om dit te doen [te gebruiken `require` of `include`], plaatst u de volgende regel code aan het begin op die kern bestand, vervangen van de string die binnen de aanhalingstekens met het exacte adres van het `loader.php` bestand (lokaal adres, niet het HTTP-adres; zal vergelijkbaar zijn met de eerder genoemde vault adres).

`<?php require '/user_name/public_html/phpmussel/loader.php'; ?>`

Opslaan bestand, sluiten, heruploaden.

-- OF ALTERNATIEF --

Als u gebruik een Apache webserver en als u heeft toegang om `php.ini`, u kunt gebruiken de `auto_prepend_file` richtlijn naar prepend phpMussel wanneer een PHP verzoek wordt gemaakt. Zoiets als:

`auto_prepend_file = "/user_name/public_html/phpmussel/loader.php"`

Of dit in het `.htaccess` bestand:

`php_value auto_prepend_file "/user_name/public_html/phpmussel/loader.php"`

6) Op dit punt, u bent klaar! Echter, u moet waarschijnlijk test het uit om ervoor te zorgen dat het werken correct. Voor het testen van het bestand upload protecties, proberen om de testen bestanden te uploaden opgenomen in het pakket als `_testfiles` naar uw website via uw gebruikelijke browser-gebaseerde uploaden methoden. Wanneer alles werkt, verschijnt er een bericht uit phpMussel bevestigen dat de upload met succes werd geblokkeerd. Wanneer er niets, is er iets niet correct werkt. Als u met behulp van een geavanceerde functies of als u met behulp van de andere types van het scannen mogelijk met het gereedschap, ik stel het uit te proberen met die ervoor zorgen dat het werkt zoals verwacht, ook.

---


###2B. <a name="SECTION2B"></a>HOE TE INSTALLEREN (VOOR CLI)

Ik hoop te stroomlijnen dit proces door maken een installateur op een bepaald punt in de niet al te verre toekomst, maar tot die tijd, volg deze instructies te werken phpMussel met CLI (beseffen dat op dit moment, CLI is alleen bekend om te werken met Windows-gebaseerde systemen; Linux en andere systemen zal binnenkort komen tot een latere versie van phpMussel):

1) Omdat u zijn lezen dit, ik ben ervan uit u al gedownload een gearchiveerde kopie van het script, uitgepakt zijn inhoud en heeft het ergens op uw lokale computer. Wanneer u heeft beslist dat u bent tevreden met de gekozen phpMussel locatie, voortzetten.

2) phpMussel vereist van PHP moet worden geïnstalleerd op de host machine om uit te werken correct. Als u niet heeft PHP geïnstalleerd op uw machine, installeer PHP op uw machine, volgende instructies door de PHP installateur geleverd.

3) Facultatief (sterk aanbevolen voor ervaren gebruikers, maar niet aan te raden voor beginners of voor de onervaren), open `config.ini` (gelegen binnen `vault`) - Dit bestand bevat alle beschikbare phpMussel configuratie opties. Boven elke optie moet een korte opmerking te beschrijven wat het doet en wat het voor. Wijzigen deze opties volgens welke geschikt is voor uw configuratie. Sla het bestand, sluiten.

4) Facultatief, u kunt om phpMussel in CLI-modus te maken makkelijker voor uzelf door het creëren van een batch-bestand te automatisch laden PHP en phpMussel. Om dit te doen, open een platte tekst editor zoals Notepad of Notepad++, typt u het volledige pad naar de `php.exe` bestand in het bestandsmap van uw PHP-installatie, gevolgd door een spatie, gevolgd door het volledige pad naar de `loader.php` bestand in het bestandsmap van uw phpMussel installatie, Sla het bestand op met een ".bat" extensie ergens dat u het gemakkelijk vinden, en dubbelklik op het bestand om phpMussel te opereren in de toekomst.

5) Op dit punt, u bent klaar! Echter, u moet waarschijnlijk test het uit om ervoor te zorgen dat het werken correct. Om phpMussel testen, draaien phpMussel en probeer het scannen van de `_testfiles` bestandsmap die bij het pakket.

---


###3A. <a name="SECTION3A"></a>HOE TE GEBRUIKEN (VOOR WEBSERVERS)

phpMussel moet in staat zijn om correct te werken met minimale eisen van uw kant: Na de installatie, het moeten onmiddellijk aan het werk en zijn onmiddellijk bruikbare.

Het scannen van het bestanden uploaden is geautomatiseerd en ingeschakeld door standaard, zo niets is vereist op namens u voor deze specifieke functie.

Echter, u bent ook in staat om te instrueren phpMussel om te scannen specifiek bestanden, bestandsmappen en/of archieven. Om dit te doen, ten eerste, moet u ervoor zorgen dat de juiste configuratie is ingesteld in het `config.ini` configuratiebestand (`cleanup` moet worden uitgeschakeld), en als u klaar bent, in een PHP-bestand dat wordt gehaakt op phpMussel, gebruik de volgende functie in uw code:

`$phpMussel['Scan']($what_to_scan, $output_type, $output_flatness);`

- `$what_to_scan` kunt worden een tekenreeks, een array, of een array van arrays, en vermelding welk bestand, bestanden, bestandsmap en/of bestandsmappen om scannen.
- `$output_type` is een boolean, met vermelding van het formaat voor de scanresultaten te worden geretourneerd als. False instrueert de functie om de resultaten als een integer retourneer (een geretourneerd resultaat van -3 betekent problemen werden aangetroffen met de phpMussel handtekeningen bestanden of handtekening kaart bestanden en dat zij mogelijk worden beschadigd of ontbreekt, -2 betekent dat beschadigd gegevens tijdens de scan werd ontdekt en dus de scan niet voltooid, -1 betekent dat uitbreidingen of addons vereist door PHP om de scan te voeren werd ontbraken zijn en dus de scan niet voltooid, 0 betekent dat het scandoel bestaat niet en dus was er niets te scannen, 1 betekent dat het doel met succes werden gescand en geen problemen gedetecteerd, en 2 betekent dat het doel met succes werd gescand en problemen werden gedetecteerd). True instrueert de functie om de resultaten als leesbare tekst retourneer. Bovendien, in elk geval, de resultaten kunnen worden geraadpleegd via globale variabelen na het scannen is voltooid. Deze variabele is optioneel, voorgedefinieerd als false.
- `$output_flatness` is een boolean, vermelding van de functie of de resultaten van de scan retourneren (wanneer er meerdere scandoelen) als een array of een tekenreeks. False zullen de resultaten als een array retourneer. True zullen de resultaten als een tekenreeks retourneer. Deze variabele is optioneel, voorgedefinieerd als false.

Voorbeeld:

```
 $results = $phpMussel['Scan']('/user_name/public_html/my_file.html', true, true);
 echo $results;
```

Retourneren iets als dit (als een tekenreeks):

```
 Wed, 16 Sep 2013 02:49:46 +0000 Gestart.
 > Verifiëren '/user_name/public_html/my_file.html':
 -> Geen problemen gevonden.
 Wed, 16 Sep 2013 02:49:47 +0000 Afgewerkt.
```

Voor een volledige beschrijving van de soorten van de handtekeningen gebruikt door phpMussel tijdens de scans en hoe het omgaat met deze handtekeningen, raadpleeg de Handtekeningformaat sectie van dit README bestand.

Als u tegenkomen valse positieven, als u iets nieuws tegenkomen waarvan u denkt dat zou moeten geblokkeerd worden, of voor iets anders met betrekking tot handtekeningen, neem dan contact met mij over het zo dat ik de noodzakelijke veranderingen kunnen maken, die, als u niet contact met mij over, ik zou niet per se bewust van.

Voor uitschakelen om de handtekeningen die bij phpMussel (zoals als u het ervaren van een vals positief specifiek voor uw doeleinden dat mag niet normaal van stroomlijn worden verwijderd), raadpleeg de greylisting aantekeningen binnen de FRONTEND MANAGEMENT sectie van dit README bestand.

---


###3B. <a name="SECTION3B"></a>HOE TE GEBRUIKEN (VOOR CLI)

Raadpleeg de "HOE TE INSTALLEREN (VOOR CLI)" sectie van dit README bestand.

Gelieve bewust te zijn, hoewel toekomstige versies van phpMussel andere systemen moet ondersteunen, momenteel, phpMussel CLI-modus ondersteuning is alleen geoptimaliseerd voor gebruik op Windows gebaseerde systemen (u kunt, natuurlijk, probeer het op andere systemen, maar ik kan niet garanderen dat het zal werken zoals bedoeld).

Eveneens, noteren dat phpMussel is een *on-demand* scanner; Het is *GEEN* *on-access* scanner (anders dan voor het uploaden van bestanden, bij de tijd van de upload), en in tegenstelling tot conventionele anti-virus suites, het maakt niet actief geheugen controleren! Het zal alleen virussen te detecteren, in de bestand uploaden en in specifieke bestanden dat u expliciet zeggen dat het te scannen.

---


###4. <a name="SECTION4"></a>FRONTEND MANAGEMENT

@TODO@

---


###5. <a name="SECTION5"></a>CLI (COMMANDLIJN INTERFACE)

phpMussel kan worden uitgevoerd als een interactief bestand scanner in de CLI-modus onder Windows-gebaseerde systemen. Raadpleeg de sectie "HOE TE INSTALLEREN (VOOR CLI)" van deze README bestand voor meer informatie.

Voor een lijst van beschikbare CLI commando's, bij de CLI-prompt, typ 'c', en druk op Enter.

Daarnaast, voor diegenen die geïnteresseerd, een video-tutorial voor hoe te gebruiken phpMussel in de CLI-modus is hier beschikbaar:
- <https://www.youtube.com/watch?v=H-Pa740-utc>

---


###6. <a name="SECTION6"></a>BESTANDEN IN DIT PAKKET

Het volgende is een lijst van alle bestanden die moeten worden opgenomen in de gearchiveerde kopie van dit script als u gedownload het, alle bestanden die kunt mogelijk worden gemaakt als resultaat van uw gebruik van dit script, samen met een korte beschrijving van wat al deze bestanden zijn voor.

Bestand | Beschrijving
----|----
/_docs/ | Documentatie bestandsmap (bevat verschillende bestanden).
/_docs/readme.ar.md | Arabisch documentatie.
/_docs/readme.de.md | Duitse documentatie.
/_docs/readme.en.md | Engels documentatie.
/_docs/readme.es.md | Spaanse documentatie.
/_docs/readme.fr.md | Franse documentatie.
/_docs/readme.id.md | Indonesisch documentatie.
/_docs/readme.it.md | Italiaanse documentatie.
/_docs/readme.ja.md | Japanse documentatie.
/_docs/readme.nl.md | Nederlandse documentatie.
/_docs/readme.pt.md | Portugees documentatie.
/_docs/readme.ru.md | Russische documentatie.
/_docs/readme.vi.md | Vietnamees documentatie.
/_docs/readme.zh-TW.md | Chinees (traditioneel) documentatie.
/_docs/readme.zh.md | Chinees (vereenvoudigd) documentatie.
/_testfiles/ | Testbestanden bestandsmap (bevat verschillende bestanden). Alle opgenomen bestanden zijn testbestanden voor het testen als phpMussel correct op uw systeem is geïnstalleerd, en u hoeft niet om deze map of een van het bestanden, behalve bij het doen van dergelijke testen te uploaden.
/_testfiles/ascii_standard_testfile.txt | Testbestand voor het testen phpMussel genormaliseerde ASCII handtekeningen.
/_testfiles/coex_testfile.rtf | Testbestand voor het testen phpMussel complexe uitgebreide handtekeningen.
/_testfiles/exe_standard_testfile.exe | Testbestand voor het testen phpMussel PE handtekeningen.
/_testfiles/general_standard_testfile.txt | Testbestand voor het testen phpMussel algemene handtekeningen.
/_testfiles/graphics_standard_testfile.gif | Testbestand voor het testen phpMussel grafische handtekeningen.
/_testfiles/html_standard_testfile.html | Testbestand voor het testen phpMussel genormaliseerde HTML handtekeningen.
/_testfiles/md5_testfile.txt | Testbestand voor het testen phpMussel MD5 handtekeningen.
/_testfiles/ole_testfile.ole | Testbestand voor het testen phpMussel OLE handtekeningen.
/_testfiles/pdf_standard_testfile.pdf | Testbestand voor het testen phpMussel PDF handtekeningen.
/_testfiles/pe_sectional_testfile.exe | Testbestand voor het testen phpMussel PE Sectionele handtekeningen.
/_testfiles/swf_standard_testfile.swf | Testbestand voor het testen phpMussel SWF handtekeningen.
/vault/ | Vault bestandsmap (bevat verschillende bestanden).
/vault/cache/ | Cache bestandsmap (tijdelijke data).
/vault/cache/.htaccess | Een hypertext toegang bestand (in dit geval, om gevoelige bestanden die behoren tot het script te beschermen tegen toegang door niet-geautoriseerde bronnen).
/vault/fe_assets/ | Frontend data/gegevens.
/vault/fe_assets/.htaccess | Een hypertext toegang bestand (in dit geval, om gevoelige bestanden die behoren tot het script te beschermen tegen toegang door niet-geautoriseerde bronnen).
/vault/fe_assets/_accounts.html | Een HTML sjabloon voor de frontend accounts pagina.
/vault/fe_assets/_accounts_row.html | Een HTML sjabloon voor de frontend accounts pagina.
/vault/fe_assets/_config.html | Een HTML sjabloon voor de frontend configuratie pagina.
/vault/fe_assets/_files.html | Een HTML sjabloon voor de bestandsbeheer.
/vault/fe_assets/_files_edit.html | Een HTML sjabloon voor de bestandsbeheer.
/vault/fe_assets/_files_rename.html | Een HTML sjabloon voor de bestandsbeheer.
/vault/fe_assets/_files_row.html | Een HTML sjabloon voor de bestandsbeheer.
/vault/fe_assets/_home.html | Een HTML sjabloon voor de frontend startpagina.
/vault/fe_assets/_login.html | Een HTML sjabloon voor de frontend inlogpagina.
/vault/fe_assets/_logs.html | Een HTML sjabloon voor de frontend logbestanden pagina.
/vault/fe_assets/_nav_complete_access.html | Een HTML sjabloon voor de frontend navigatie-links, voor degenen met volledige toegang.
/vault/fe_assets/_nav_logs_access_only.html | Een HTML sjabloon voor de frontend navigatie-links, voor degenen met logbestanden toegang alleen.
/vault/fe_assets/_updates.html | Een HTML sjabloon voor de frontend updates pagina.
/vault/fe_assets/_updates_row.html | Een HTML sjabloon voor de frontend updates pagina.
/vault/fe_assets/_upload_test.html | Een HTML sjabloon voor de upload test pagina.
/vault/fe_assets/frontend.css | CSS-stijlblad voor de frontend.
/vault/fe_assets/frontend.dat | Database voor de frontend (bevat accounts en sessies informatie; alleen gegenereerd als de frontend geactiveerd en gebruikt).
/vault/fe_assets/frontend.html | De belangrijkste HTML-template-bestand voor de frontend.
/vault/lang/ | Bevat phpMussel taaldata/taalgegevens.
/vault/lang/.htaccess | Een hypertext toegang bestand (in dit geval, om gevoelige bestanden die behoren tot het script te beschermen tegen toegang door niet-geautoriseerde bronnen).
/vault/lang/lang.ar.fe.php | Arabisch taaldata/taalgegevens voor het frontend.
/vault/lang/lang.ar.php | Arabisch taaldata/taalgegevens.
/vault/lang/lang.de.fe.php | Duitse taaldata/taalgegevens voor het frontend.
/vault/lang/lang.de.php | Duitse taaldata/taalgegevens.
/vault/lang/lang.en.fe.php | Engels taaldata/taalgegevens voor het frontend.
/vault/lang/lang.en.php | Engels taaldata/taalgegevens.
/vault/lang/lang.es.fe.php | Spaanse taaldata/taalgegevens voor het frontend.
/vault/lang/lang.es.php | Spaanse taaldata/taalgegevens.
/vault/lang/lang.fr.fe.php | Franse taaldata/taalgegevens voor het frontend.
/vault/lang/lang.fr.php | Franse taaldata/taalgegevens.
/vault/lang/lang.id.fe.php | Indonesisch taaldata/taalgegevens voor het frontend.
/vault/lang/lang.id.php | Indonesisch taaldata/taalgegevens.
/vault/lang/lang.it.fe.php | Italiaanse taaldata/taalgegevens voor het frontend.
/vault/lang/lang.it.php | Italiaanse taaldata/taalgegevens.
/vault/lang/lang.ja.fe.php | Japanse taaldata/taalgegevens voor het frontend.
/vault/lang/lang.ja.php | Japanse taaldata/taalgegevens.
/vault/lang/lang.nl.fe.php | Nederlandse taaldata/taalgegevens voor het frontend.
/vault/lang/lang.nl.php | Nederlandse taaldata/taalgegevens.
/vault/lang/lang.pt.fe.php | Portugees taaldata/taalgegevens voor het frontend.
/vault/lang/lang.pt.php | Portugees taaldata/taalgegevens.
/vault/lang/lang.ru.fe.php | Russische taaldata/taalgegevens voor het frontend.
/vault/lang/lang.ru.php | Russische taaldata/taalgegevens.
/vault/lang/lang.vi.fe.php | Vietnamees taaldata/taalgegevens voor het frontend.
/vault/lang/lang.vi.php | Vietnamees taaldata/taalgegevens.
/vault/lang/lang.zh-tw.fe.php | Chinees (traditioneel) taaldata/taalgegevens voor het frontend.
/vault/lang/lang.zh-tw.php | Chinees (traditioneel) taaldata/taalgegevens.
/vault/lang/lang.zh.fe.php | Chinees (vereenvoudigd) taaldata/taalgegevens voor het frontend.
/vault/lang/lang.zh.php | Chinees (vereenvoudigd) taaldata/taalgegevens.
/vault/quarantine/ | Quarantaine bestandsmap (bestanden in quarantaine bevat).
/vault/quarantine/.htaccess | Een hypertext toegang bestand (in dit geval, om gevoelige bestanden die behoren tot het script te beschermen tegen toegang door niet-geautoriseerde bronnen).
/vault/signatures/ | Handtekeningen bestandsmap (handtekening bestanden bevat).
/vault/signatures/.htaccess | Een hypertext toegang bestand (in dit geval, om gevoelige bestanden die behoren tot het script te beschermen tegen toegang door niet-geautoriseerde bronnen).
/vault/signatures/ascii_clamav_regex.cvd | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/signatures/ascii_clamav_regex.map | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/signatures/ascii_clamav_standard.cvd | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/signatures/ascii_clamav_standard.map | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/signatures/ascii_mussel_regex.cvd | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/signatures/ascii_mussel_standard.cvd | Bestand voor genormaliseerde ASCII handtekeningen.
/vault/signatures/coex_clamav.cvd | Bestand voor complexe uitgebreide handtekeningen.
/vault/signatures/coex_mussel.cvd | Bestand voor complexe uitgebreide handtekeningen.
/vault/signatures/elf_clamav_regex.cvd | Bestand voor ELF handtekeningen.
/vault/signatures/elf_clamav_regex.map | Bestand voor ELF handtekeningen.
/vault/signatures/elf_clamav_standard.cvd | Bestand voor ELF handtekeningen.
/vault/signatures/elf_clamav_standard.map | Bestand voor ELF handtekeningen.
/vault/signatures/elf_mussel_regex.cvd | Bestand voor ELF handtekeningen.
/vault/signatures/elf_mussel_standard.cvd | Bestand voor ELF handtekeningen.
/vault/signatures/exe_clamav_regex.cvd | Bestand voor PE (Portable Executable) handtekeningen.
/vault/signatures/exe_clamav_regex.map | Bestand voor PE (Portable Executable) handtekeningen.
/vault/signatures/exe_clamav_standard.cvd | Bestand voor PE (Portable Executable) handtekeningen.
/vault/signatures/exe_clamav_standard.map | Bestand voor PE (Portable Executable) handtekeningen.
/vault/signatures/exe_mussel_regex.cvd | Bestand voor PE (Portable Executable) handtekeningen.
/vault/signatures/exe_mussel_standard.cvd | Bestand voor PE (Portable Executable) handtekeningen.
/vault/signatures/filenames_clamav.cvd | Bestand voor bestandsnaam handtekeningen.
/vault/signatures/filenames_mussel.cvd | Bestand voor bestandsnaam handtekeningen.
/vault/signatures/general_clamav_regex.cvd | Bestand voor algemene handtekeningen.
/vault/signatures/general_clamav_regex.map | Bestand voor algemene handtekeningen.
/vault/signatures/general_clamav_standard.cvd | Bestand voor algemene handtekeningen.
/vault/signatures/general_clamav_standard.map | Bestand voor algemene handtekeningen.
/vault/signatures/general_mussel_regex.cvd | Bestand voor algemene handtekeningen.
/vault/signatures/general_mussel_standard.cvd | Bestand voor algemene handtekeningen.
/vault/signatures/graphics_clamav_regex.cvd | Bestand voor grafische handtekeningen.
/vault/signatures/graphics_clamav_regex.map | Bestand voor grafische handtekeningen.
/vault/signatures/graphics_clamav_standard.cvd | Bestand voor grafische handtekeningen.
/vault/signatures/graphics_clamav_standard.map | Bestand voor grafische handtekeningen.
/vault/signatures/graphics_mussel_regex.cvd | Bestand voor grafische handtekeningen.
/vault/signatures/graphics_mussel_standard.cvd | Bestand voor grafische handtekeningen.
/vault/signatures/hex_general_commands.csv | Hex-gecodeerde CSV van algemene commando detecties optioneel gebruikt door phpMussel.
/vault/signatures/html_clamav_regex.cvd | Bestand voor genormaliseerde HTML handtekeningen.
/vault/signatures/html_clamav_regex.map | Bestand voor genormaliseerde HTML handtekeningen.
/vault/signatures/html_clamav_standard.cvd | Bestand voor genormaliseerde HTML handtekeningen.
/vault/signatures/html_clamav_standard.map | Bestand voor genormaliseerde HTML handtekeningen.
/vault/signatures/html_mussel_regex.cvd | Bestand voor genormaliseerde HTML handtekeningen.
/vault/signatures/html_mussel_standard.cvd | Bestand voor genormaliseerde HTML handtekeningen.
/vault/signatures/macho_clamav_regex.cvd | Bestand voor Mach-O handtekeningen.
/vault/signatures/macho_clamav_regex.map | Bestand voor Mach-O handtekeningen.
/vault/signatures/macho_clamav_standard.cvd | Bestand voor Mach-O handtekeningen.
/vault/signatures/macho_clamav_standard.map | Bestand voor Mach-O handtekeningen.
/vault/signatures/macho_mussel_regex.cvd | Bestand voor Mach-O handtekeningen.
/vault/signatures/macho_mussel_standard.cvd | Bestand voor Mach-O handtekeningen.
/vault/signatures/mail_clamav_regex.cvd | Bestand voor mail handtekeningen.
/vault/signatures/mail_clamav_regex.map | Bestand voor mail handtekeningen.
/vault/signatures/mail_clamav_standard.cvd | Bestand voor mail handtekeningen.
/vault/signatures/mail_clamav_standard.map | Bestand voor mail handtekeningen.
/vault/signatures/mail_mussel_regex.cvd | Bestand voor mail handtekeningen.
/vault/signatures/mail_mussel_standard.cvd | Bestand voor mail handtekeningen.
/vault/signatures/clamav.hdb | Bestand voor MD5 gebaseerde handtekeningen.
/vault/signatures/phpmussel.hdb | Bestand voor MD5 gebaseerde handtekeningen.
/vault/signatures/ole_clamav_regex.cvd | Bestand voor OLE handtekeningen.
/vault/signatures/ole_clamav_regex.map | Bestand voor OLE handtekeningen.
/vault/signatures/ole_clamav_standard.cvd | Bestand voor OLE handtekeningen.
/vault/signatures/ole_clamav_standard.map | Bestand voor OLE handtekeningen.
/vault/signatures/ole_mussel_regex.cvd | Bestand voor OLE handtekeningen.
/vault/signatures/ole_mussel_standard.cvd | Bestand voor OLE handtekeningen.
/vault/signatures/pdf_clamav_regex.cvd | Bestand voor PDF handtekeningen.
/vault/signatures/pdf_clamav_regex.map | Bestand voor PDF handtekeningen.
/vault/signatures/pdf_clamav_standard.cvd | Bestand voor PDF handtekeningen.
/vault/signatures/pdf_clamav_standard.map | Bestand voor PDF handtekeningen.
/vault/signatures/pdf_mussel_regex.cvd | Bestand voor PDF handtekeningen.
/vault/signatures/pdf_mussel_standard.cvd | Bestand voor PDF handtekeningen.
/vault/signatures/phpmussel.pex | Bestand voor PE uitgebreide handtekeningen.
/vault/signatures/clamav.mdb | Bestand voor PE Sectionele handtekeningen.
/vault/signatures/phpmussel.mdb | Bestand voor PE Sectionele handtekeningen.
/vault/signatures/swf_clamav_regex.cvd | Bestand voor the Shockwave handtekeningen.
/vault/signatures/swf_clamav_regex.map | Bestand voor the Shockwave handtekeningen.
/vault/signatures/swf_clamav_standard.cvd | Bestand voor the Shockwave handtekeningen.
/vault/signatures/swf_clamav_standard.map | Bestand voor the Shockwave handtekeningen.
/vault/signatures/swf_mussel_regex.cvd | Bestand voor the Shockwave handtekeningen.
/vault/signatures/swf_mussel_standard.cvd | Bestand voor the Shockwave handtekeningen.
/vault/signatures/switch.dat | Controles en sets bepaalde variabelen.
/vault/signatures/urlscanner.cvd | Bestand voor URL scanner handtekeningen.
/vault/signatures/whitelist_clamav.cvd | Bestand-specifieke whitelist.
/vault/signatures/whitelist_mussel.cvd | Bestand-specifieke whitelist.
/vault/.htaccess | Een hypertext toegang bestand (in dit geval, om gevoelige bestanden die behoren tot het script te beschermen tegen toegang door niet-geautoriseerde bronnen).
/vault/cli.php | CLI handler.
/vault/config.ini.RenameMe | Configuratiebestand; Bevat alle configuratieopties van phpMussel, het vertellen wat te doen en hoe om te werken correct (hernoemen om te activeren).
/vault/config.php | Configuratie handler.
/vault/core.dat | Bevat informatie over de belangrijkste bestanddelen van phpMussel; Gebruikt door de updates functie verzorgd door de frontend.
/vault/frontend.php | Frontend-handler.
/vault/functions.php | Functies bestand (essentieel).
/vault/greylist.csv | CSV van greylisted handtekeningen aangeeft om phpMussel waarop handtekeningen moet worden negeren (bestand automatisch aangemaakt opnieuw als verwijderd).
/vault/l10n.dat | Bevat informatie over de L10N bestanddelen van phpMussel; Gebruikt door de updates functie verzorgd door de frontend.
/vault/lang.php | Taal-handler.
/vault/php5.4.x.php | Polyfills voor PHP 5.4.X (nodig voor PHP 5.4.X achterwaartse compatibiliteit; veilig te verwijderen voor nieuwere PHP-versies).
※ /vault/scan_kills.txt | Een record van elk bestand uploaden geblokkeerde/gedood door phpMussel.
※ /vault/scan_log.txt | Een record van alles gescand door phpMussel.
※ /vault/scan_log_serialized.txt | Een record van alles gescand door phpMussel.
/vault/template.html | Sjabloonbestand; Sjabloon voor HTML-uitvoer geproduceerd door phpMussel voor zijn geblokkeerd bestand te uploaden bericht (het bericht gezien te de uploader).
/vault/template_custom.html | Sjabloonbestand; Sjabloon voor HTML-uitvoer geproduceerd door phpMussel voor zijn geblokkeerd bestand te uploaden bericht (het bericht gezien te de uploader).
/vault/upload.php | Upload handler.
/.gitattributes | Een GitHub project bestand (niet vereist voor een goede werking van het script).
/Changelog-v1.txt | Een overzicht van wijzigingen in het script tussen verschillende versies (niet vereist voor een goede werking van het script).
/composer.json | Composer/Packagist informatie (niet vereist voor een goede werking van het script).
/CONTRIBUTING.md | Informatie over hoe bij te dragen aan het project.
/LICENSE.txt | Een kopie van de GNU/GPLv2 licentie (niet vereist voor een goede werking van het script).
/loader.php | De lader/loader. Dit is wat u zou moeten worden inhaken in (essentieel)!
/PEOPLE.md | Informatie over de bij het project betrokken personen.
/README.md | Project beknopte informatie.
/web.config | Een ASP.NET-configuratiebestand (in dit geval, naar het bestandsmap "vault" te beschermen tegen toegang door niet-geautoriseerde bronnen indien het script is geïnstalleerd op een server op basis van ASP.NET technologieën).

※ Bestandsnaam kan verschillen, afhankelijk van de configuratie bedingen (van `config.ini`).

####*MET BETREKKING TOT HANDTEKENING BESTANDEN*
CVD is een acroniem voor "ClamAV Virus Definitions", in verwijzing zowel om hoe ClamAV verwijst aan zijn eigen handtekeningen en het gebruik van de handtekeningen voor phpMussel; Bestanden eindigend met "CVD" bevatten handtekeningen.

Bestanden eindigend met "MAP" kaart die handtekeningen phpMussel moeten en niet moeten gebruik voor individuele scans; Niet alle handtekeningen zijn noodzakelijkerwijs nodig voor elke scan, en zo, phpMussel maakt gebruik van kaarten van het handtekening bestanden te versnellen het scanproces (een proces dat zou worden anders zeer traag en vervelend).

Handtekening bestanden gemarkeerd met "_regex" bevatten handtekeningen dat maakt gebruiken van reguliere expressie patroon controleren (regex).

Handtekening bestanden gemarkeerd met "_standard" bevatten handtekeningen dat niet maakt gebruik van ieder specifiek vorm van patroon controleren.

Handtekening bestanden gemarkeerd niet met "_regex" noch "_standard" zal zijn als ene of de andere, maar niet beide (raadpleeg de Handtekeningformaat sectie van dit README bestand voor documentatie en specifieke details).

Handtekening bestanden gemarkeerd met "_clamav" bevatten handtekeningen dat zijn geheel afkomstig van de ClamAV databank (GNU/GPL).

Handtekening bestanden gemarkeerd met "_mussel" bevatten handtekeningen dat specifiek zijn niet afkomstig van ClamAV, handtekeningen dat, in algemeen, ik heeft persoonlijk geschreven en/of gebaseerd op diverse verschillende bronnen.

---


###7. <a name="SECTION7"></a>CONFIGURATIEOPTIES
Het volgende is een lijst van variabelen die in de `config.ini` configuratiebestand van phpMussel, samen met een beschrijving van hun doel en functie.

####"general" (Categorie)
Algemene configuratie voor phpMussel.

"cleanup"
- Vrijmaken script variabelen en de cache na de uitvoering? False = Nee; True = Ja [Standaard]. Als u niet gebruik het script na de eerste scan van upload, moet zetten op `true` (ja), om minimaliseren de geheugengebruik. Als u gebruik het script voor de doeleinden na de eerste scan van upload, moet zetten op `false` (nee), om te voorkomen dat onnodig herladen dubbele gegevens in het geheugen. In de huisartspraktijk, moet waarschijnlijk worden zetten op `true` (ja), maar, als u dit doet, het zal niet mogelijk zijn om het script te gebruiken voor iets anders dan het scannen van bestand uploaden.
- Heeft geen invloed in CLI-modus.

"scan_log"
- Bestandsnaam van het bestand te opnemen alle scanresultaten. Geef een bestandsnaam of laat leeg om te uitschakelen.

"scan_log_serialized"
- Bestandsnaam van het bestand te opnemen alle scanresultaten (formaat is geserialiseerd). Geef een bestandsnaam of laat leeg om te uitschakelen.

"scan_kills"
- Bestandsnaam van het bestand te opnemen alle geblokkeerde of gedood upload. Geef een bestandsnaam of laat leeg om te uitschakelen.

*Handige tip: Als u wil, U kunt datum/tijd informatie toevoegen om de namen van uw logbestanden door deze op in naam inclusief: `{yyyy}` voor volledige jaar, `{yy}` voor verkorte jaar, `{mm}` voor maand, `{dd}` voor dag, `{hh}` voor het uur.*

*Voorbeelden:*
- *`logfile='logfile.{yyyy}-{mm}-{dd}-{hh}.txt'`*
- *`logfileApache='access.{yyyy}-{mm}-{dd}-{hh}.txt'`*
- *`logfileSerialized='serial.{yyyy}-{mm}-{dd}-{hh}.txt'`*

"timeOffset"
- Als uw server tijd niet overeenkomt met uw lokale tijd, u kunt opgeven hier een offset om de datum/tijd informatie gegenereerd door phpMussel aan te passen volgens uw behoeften. Het is in het algemeen in plaats aanbevolen de tijdzone richtlijn in uw bestand `php.ini` aan te passen, maar somtijds (zoals bij het werken met beperkte shared hosting providers) dit is niet altijd mogelijk om te voldoen, en dus, Dit optie is hier voorzien. Offset is in een minuten.
- Voorbeeld (een uur toe te voegen): `timeOffset=60`

"ipaddr"
- Waar het IP-adres van het aansluiten verzoek te vinden? (Handig voor diensten zoals Cloudflare en dergelijke) Standaard = REMOTE_ADDR. WAARSCHUWING: Verander dit niet tenzij u weet wat u doet!

"enable_plugins"
- Activeer ondersteuning voor phpMussel plugins? False = Nee; True = Ja [Standaard].

"forbid_on_block"
- Moet phpMussel reageren met 403 headers met het bestanden upload geblokkeerd bericht, of blijven met de gebruikelijke 200 OK? False = Nee (200); True = Ja (403) [Standaard].

"delete_on_sight"
- Het inschakelen van dit richtlijn zal instrueren het script om elke gescande geprobeerd bestand upload dat gecontroleerd tegen elke detectie criteria te proberen onmiddellijk verwijderen, via handtekeningen of anderszins. Bestanden vastbesloten te zijn schoon zal niet worden aangeraakt. In het geval van archieven, het hele archief wordt verwijderd, ongeacht of niet het overtredende bestand is slechts één van meerdere bestanden vervat in het archief. Voor het geval van bestand upload scannen, doorgaans, het is niet nodig om dit richtlijn te inschakelen, omdat doorgaans, PHP zal automatisch zuiveren de inhoud van zijn cache wanneer de uitvoering is voltooid, wat betekent dat het doorgans zal verwijdert ieder bestanden geüpload doorheen aan de server tenzij ze zijn verhuisd, gekopieerd of verwijderd alreeds. Dit richtlijn is toegevoegd hier als een extra maatregel van veiligheid voor degenen wier kopies van PHP misschien niet altijd gedragen op de manier verwacht. False = Na het scannen, met rust laten het bestand [Standaard]; True = Na het scannen, als niet schoon, onmiddellijk verwijderen.

"lang"
- Geef de standaardtaal voor phpMussel.

"quarantine_key"
- phpMussel is in staat om gevlagd geprobeerd bestandsuploads te quarantaine in isolatie binnen de phpMussel vault, als dit is iets wat u wilt doen. Regelmatige gebruikers van phpMussel dat gewoon willen om hun websites of hosting-omgeving te beschermen zonder enige interesse in diep analyseren van gevlagd geprobeerd bestandsuploads moet dit functionaliteit hebben uitgeschakeld, maar elke gebruikers geïnteresseerd in de verdere analyse van gevlagd geprobeerd bestandsuploads voor malware onderzoek of voor soortgelijke zaken moeten inschakelen dit functionaliteit. Quarantaine van gevlagd geprobeerd bestandsuploads kunt ook somtijds helpen bij het opsporen van vals-positieven, als dit is iets dat vaak voorkomt voor u. Voor de uitschakelen van quarantaine functionaliteit, gewoon laat de `quarantine_key` richtlijn leeg, of wissen de inhoud van de richtlijn als het niet leeg alreeds. Voor de inschakelen van quarantaine functionaliteit, invoeren soms waarde in de richtlijn. De `quarantine_key` is een belangrijke beveiliging kenmerk van de quarantaine functionaliteit vereist als middel om de functionaliteit quarantaine te verhinderen exploitatie door potentiële aanvallers en als middel om verhinderen van elke mogelijke gegevens uitvoering van gegevens opgeslagen in de quarantaine. De `quarantine_key` moeten op dezelfde manier als uw wachtwoorden worden behandeld: De langer de beter, en bewaken het goed. Voor het beste gevolg, gebruik in combinatie met `delete_on_sight`.

"quarantine_max_filesize"
- De maximaal toegestane bestandsgrootte van bestanden te worden in quarantaine plaatsen. Bestanden groter dan de opgegeven waarde zal NIET in quarantaine plaatsen. Dit richtlijn is belangrijk als een middel van maak het moeilijker voor potentiële aanvallers te overspoelen uw quarantaine met ongewenste gegevens potentieel veroorzaakt weggelopen gebruiksgegevens op uw hosting service. Waarde is in KB. Standaard =2048 =2048KB =2MB.

"quarantine_max_usage"
- De maximale geheugengebruik toegestaan voor de quarantaine. Als de totale geheugengebruik van de quarantaine bereikt dit waarde, de oudste bestanden in quarantaine zullen worden verwijderd totdat het totale geheugengebruik niet meer bereikt dit waarde. Dit richtlijn is belangrijk als een middel van maak het moeilijker voor potentiële aanvallers te overspoelen uw quarantaine met ongewenste gegevens potentieel veroorzaakt weggelopen gebruiksgegevens op uw hosting service. Waarde is in KB. Standaard =65536 =65536KB =64MB.

"honeypot_mode"
- Wanneer honeypot-modus is ingeschakeld, phpMussel zal proberen om ieder bestandsupload dat het tegenkomt in quarantaine plaatsen, ongeacht of niet het bestand wordt geüpload is gecontroleerd tegen een meegeleverde handtekeningen, en geen daadwerkelijke scannen of analyse van deze gevlagd geprobeerd bestandsuploads zal daadwerkelijk optreedt. Dit functionaliteit moet nuttig zijn voor degenen dat willen gebruik phpMussel voor de toepassing van virus/malware onderzoek, maar het is niet aanbevolen om dit functionaliteit te inschakelen wanneer het beoogde gebruik van phpMussel door de gebruiker is voor werkelijke bestandsupload scannen, noch aanbevolen te gebruik de honeypot functionaliteit voor andere doeleinden andere dan honeypotting. Als standaard, dit optie is uitgeschakeld. False = Uitgeschakeld [Standaard]; True = Ingeschakeld.

"scan_cache_expiry"
- Hoe lang moeten phpMussel cache de resultaten van de scan? Waarde is het aantal seconden dat de resultaten van het scannen moet wordt gecached voor. Standaard is 21600 seconden (6 uur); Een waarde van 0 zal uitschakelen caching de resultaten van de scan.

"disable_cli"
- Uitschakelen CLI-modus? CLI-modus is standaard ingeschakeld, maar kunt somtijds interfereren met bepaalde testtools (zoals PHPUnit bijvoorbeeld) en andere CLI-gebaseerde applicaties. Als u niet hoeft te uitschakelen CLI-modus, u moeten om dit richtlijn te negeren. False = Inschakelen CLI-modus [Standaard]; True = Uitschakelen CLI-modus.

"disable_frontend"
- Uitschakelen frontend toegang? frontend toegang kan phpMussel beter beheersbaar te maken, maar kan ook een potentieel gevaar voor de veiligheid zijn. Het is aan te raden om phpMussel te beheren via het backend wanneer mogelijk, maar frontend toegang is hier voorzien voor wanneer het niet mogelijk is. Hebben het uitgeschakeld tenzij u het nodig hebt. False = Inschakelen frontend toegang; True = Uitschakelen frontend toegang [Standaard].

"max_login_attempts"
- Maximum aantal inlogpogingen (frontend). Standaard = 5.

"FrontEndLog"
- Bestand om de front-end login pogingen te loggen. Geef een bestandsnaam, of laat leeg om uit te schakelen.

####"signatures" (Categorie)
Configuratie voor handtekeningen.

"MD5"
- Gebruik MD5 handtekeningen bij het scannen? Als dat zo is, geef de namen van de handtekening bestanden te gebruiken, gescheiden door komma's.

"PE_Sectional"
- Gebruik PE Sectionele handtekeningen voor de PE-bestanden (EXE, DLL, e.z.v.) bij het scannen? Als dat zo is, geef de namen van de handtekening bestanden te gebruiken, gescheiden door komma's.

"PE_Extended"
- Gebruik PE uitgebreide handtekeningen voor de PE-bestanden (EXE, DLL, e.z.v.) bij het scannen? Als dat zo is, geef de namen van de handtekening bestanden te gebruiken, gescheiden door komma's.

Controleer tegen algemeen handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "general_clamav"
- "general_mussel"

Controleer tegen genormaliseerde ASCII handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "ascii_clamav"
- "ascii_mussel"

Controleer tegen genormaliseerde HTML handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "html_clamav"
- "html_mussel"

Controleer PE (Portable Executable) bestanden (EXE, DLL, ezv) tegen PE handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "exe_clamav"
- "exe_mussel"

Controleer ELF bestanden tegen ELF handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "elf_clamav"
- "elf_mussel"

Controleer Mach-O bestanden (OSX, ezv) tegen Mach-O handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "macho_clamav"
- "macho_mussel"

Controleer grafische bestanden tegen grafische-gebaseerde handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "graphics_clamav"
- "graphics_mussel"

Controleer OLE-objecten tegen OLE handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "ole_clamav"
- "ole_mussel"

Controleer bestandsnamen tegen bestandsnaam gebaseerd handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "filenames_clamav"
- "filenames_mussel"

Controleer tegen email handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "mail_clamav"
- "mail_mussel"

Inschakelen bestand-specifieke whitelist? False = Nee; True = Ja [Standaard].
- "whitelist_clamav"
- "whitelist_mussel"

Controleer tegen complexe uitgebreide handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "coex_clamav"
- "coex_mussel"

Controleer tegen PDF handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "pdf_clamav"
- "pdf_mussel"

Controleer tegen Shockwave handtekeningen wanneer scannen? False = Nee; True = Ja [Standaard].
- "swf_clamav"
- "swf_mussel"

"fail_silently"
- Moet phpMussel rapporteren wanneer handtekeningen bestanden zijn ontbrekend of beschadigd? Als `fail_silently` is uitgeschakeld, ontbrekende en beschadigde bestanden zal worden gerapporteerd op het scannen, en als `fail_silently` is ingeschakeld, ontbrekende en beschadigde bestanden zal zijn genegeerd, met het scannen rapporten voor het bestanden die er geen problemen. Dit moet in het algemeen met rust gelaten worden tenzij u ervaart mislukt of soortgelijke problemen. False = Uitgeschakeld; True = Ingeschakeld [Standaard].

"fail_extensions_silently"
- Moet phpMussel rapporteren wanneer extensies zijn ontbreken? Als `fail_extensions_silently` is uitgeschakeld, ontbrekende extensies zal worden gerapporteerd op het scannen, en als `fail_extensions_silently` is ingeschakeld, ontbrekende extensies zal zijn genegeerd, met het scannen rapporten voor het bestanden die er geen problemen. Het uitschakelen van dit richtlijn kunt mogelijk verhogen van uw veiligheid, maar kunt ook leiden tot een toename van valse positieven. False = Uitgeschakeld; True = Ingeschakeld [Standaard].

"detect_adware"
- Moet phpMussel verwerken handtekeningen voor het detecteren van adware? False = Nee; True = Ja [Standaard].

"detect_joke_hoax"
- Moet phpMussel verwerken handtekeningen voor het detecteren van grap/beetnemerij malware/virussen? False = Nee; True = Ja [Standaard].

"detect_pua_pup"
- Moet phpMussel verwerken handtekeningen voor het detecteren van PUAs/PUPs? False = Nee; True = Ja [Standaard].

"detect_packer_packed"
- Moet phpMussel verwerken handtekeningen voor het detecteren van verpakkers en verpakt gegevens? False = Nee; True = Ja [Standaard].

"detect_shell"
- Moet phpMussel verwerken handtekeningen voor het detecteren van shell scripts? False = Nee; True = Ja [Standaard].

"detect_deface"
- Moet phpMussel verwerken handtekeningen voor het detecteren van schendingen/defacements en schenders/defacers? False = Nee; True = Ja [Standaard].

####"files" (Categorie)
Bestand hanteren configuratie.

"max_uploads"
- Maximaal toegestane aantal bestanden te scannen tijdens bestandsupload scan voordat aborteren de scan en informeren de gebruiker ze zijn uploaden van te veel in een keer! Biedt bescherming tegen een theoretische aanval waardoor een aanvaller probeert te DDoS uw systeem of CMS door overbelasting phpMussel te vertragen het PHP proces tot stilstand. Aanbevolen: 10. U zou kunnen wil te verhogen of verlagen dit nummer afhankelijk van de snelheid van uw hardware. Noteren dat dit aantal niet verklaren voor of opnemen de inhoud van de archieven.

"filesize_limit"
- Bestandsgrootte limiet in KB. 65536 = 64MB [Standaard]; 0 = Geen limiet (altijd op de greylist), ieder (positief) numerieke waarde aanvaard. Dit kunt handig zijn als uw PHP configuratie beperkt de hoeveelheid van geheugen een proces kunt houden of als u PHP configuratie beperkt het bestandsgrootte van uploads.

"filesize_response"
- Wat te doen met bestanden dat overschrijden het bestandsgrootte limiet (als aanwezig). False = Whitelist; True = Blacklist [Standaard].

"filetype_whitelist", "filetype_blacklist", "filetype_greylist"
- Als uw systeem vergunningen alleen specifieke bestandstypen te uploaden, of als uw systeem expliciet ontkent bepaalde bestandstypen, specificeren deze bestandstypen in whitelists, blacklists en greylists kunt toenemen de snelheid waarin scannen is uitgevoerd via vergunningen het script te negeren bepaalde bestandstypen. Formaat is CSV (komma's gescheiden waarden). Als u wilt te scannen alles, eerder dan whitelist, blacklist of greylist, laat de variabele(/n) leeg; doen zo zal uitschakelen whitelist/blacklist/greylist.
- Logische volgorde van de verwerking is:
  - Als het bestandstype is op de whitelist, niet scannen en niet blokkeren het bestand, en niet controleer het bestand tegen de blacklist of de greylist.
  - Als het bestandstype is op de blacklist, niet scannen het bestand maar blokkeren het niettemin, en niet controleer het bestand tegen de greylist.
  - Als de greylist is leeg of als de greylist is niet leeg en het bestandstype is op de greylist, scannen het bestand als per normaal en bepalen als om het gebaseerd op de resultaten van de scan te blokkeren, maar als de greylist is niet leeg en het bestandstype is niet op de greylist, behandel het bestand alsof op de blacklist, dus om het niet te scannen, maar toch blokkeren het niettemin.

"check_archives"
- Om de inhoud van archieven proberen te controleer? False = Nee (niet doen controleer); True = Ja (doen controleer) [Standaard].
- Momenteel, het enige archief en compressie-formaten ondersteund zijn BZ/BZIP2, GZ/GZIP, LZF, PHAR, TAR en ZIP (archief en compressie-formaten RAR, CAB, 7z en etcetera momenteel niet ondersteund).
- Dit is niet onfeilbaar! Hoewel ik beveel het houden van dit ingeschakeld, ik kan niet garanderen dat het zal altijd vind alles.
- Ook noteren dat archief controleren momenteel is niet recursief voor PHAR of ZIP formaten.

"filesize_archives"
- Erven het bestandsgrootte blacklist/whitelist staat om de inhoud van archieven? False = Nee (gewoon greylist alles); True = Ja [Standaard].

"filetype_archives"
- Erven het bestandstype blacklist/whitelist staat om de inhoud van archieven? False = Nee (gewoon greylist alles); True = Ja [Standaard].

"max_recursion"
- Maximale recursiediepte limiet voor archieven. Standaard = 10.

"block_encrypted_archives"
- Detecteren en blokkeren gecodeerde archieven? Omdat phpMussel is niet in staat te scannen de inhoud van gecodeerde archieven, het is mogelijk dat archief encryptie kan worden toegepast door een aanvaller als middel van probeert te omzeilen phpMussel, anti-virus scanners en andere dergelijke beveiligingen. Instrueren phpMussel te blokkeren elke archieven dat het ontdekt worden gecodeerde zou kunnen helpen het risico in verband met deze dergelijke mogelijkheden te verminderen. False = Nee; True = Ja [Standaard].

####"attack_specific" (Categorie)
Aanval-specifieke richtlijnen.

Chameleon aanval detectie: False = Uitgeschakeld; True = Ingeschakeld.

"chameleon_from_php"
- Zoeken naar PHP header in bestanden die niet zijn PHP-bestanden noch herkende archieven.

"chameleon_from_exe"
- Zoeken naar PHP header in bestanden die niet zijn executables noch herkende archieven en naar executables waarvan de headers zijn onjuist.

"chameleon_to_archive"
- Zoeken naar archieven waarvan headers zijn onjuist (Ondersteunde: BZ, GZ, RAR, ZIP, RAR, GZ).

"chameleon_to_doc"
- Zoeken naar office documenten waarvan headers zijn onjuist (Ondersteunde: DOC, DOT, PPS, PPT, XLA, XLS, WIZ).

"chameleon_to_img"
- Zoeken naar beelden waarvan headers zijn onjuist (Ondersteunde: BMP, DIB, PNG, GIF, JPEG, JPG, XCF, PSD, PDD, WEBP).

"chameleon_to_pdf"
- Zoeken naar PDF-bestanden waarvan headers zijn onjuist.

"archive_file_extensions"
- Herkende archief bestandsextensies (formaat is CSV; moet alleen toevoegen of verwijderen wanneer problemen voorkomen; onnodig verwijderen kan leiden tot vals-positieven te verschijnen voor archiefbestanden, terwijl onnodig toevoeging zal effectief whitelist wat u toevoegt van aanval-specifieke detectie; wijzigen met voorzichtigheid; ook noteren dat Dit heeft geen effect op welke archieven kan en niet kan wordt geanalyseerd op inhoudsniveau). De lijst, als is bij standaard, geeft die formaten gebruikt meest vaak door de meeste systemen en CMS, maar opzettelijk is niet noodzakelijk alomvattend.

"general_commands"
- Zoeken de inhoud van bestanden voor algemene commando's zoals `eval()`, `exec()` en `include`? False = Nee (niet doen controleer) [Standaard]; True = Ja (doen controleer). Uitschakelen dit optie als u plannen te uploaden om één van de volgende om uw systeem of CMS via uw browser: PHP, JavaScript, HTML, python, perl bestanden en zo voort. Inschakelen dit optie als u heeft geen extra bescherming op uw systeem en niet plannen te uploaden dergelijke bestanden. Als u gebruik extra beveiliging in combinatie met phpMussel zoals ZB Block, er is geen noodzaak om dit optie te inschakelen, omdat de meeste van wat phpMussel zal zoek naar (in het kader van dit optie) zijn duplicaties van beveiligingen die zijn voorzien alreeds.

"block_control_characters"
- Blokkeren alle bestanden bevatten controle karakters (andere dan nieuwe regels)? (`[\x00-\x08\x0b\x0c\x0e\x1f\x7f]`) Als u _**ALLEEN**_  uploaden platte tekst, dan u kan inschakelen dit optie te bieden extra bescherming aan uw systeem. Hoewel, als u uploaden iets anders dan platte tekst, inschakelen dit kan leiden tot valse positieven. False = Niet blokkeren [Standaard]; True = Doen blokkeren.

"corrupted_exe"
- Corrupte bestanden en verwerking fouten. False = Negeren; True = Blokkeren [Standaard]. Detecteren en blokkeren mogelijk beschadigd PE (Portable Executable) bestanden? Vaak (maar niet altijd), wanneer bepaalde aspecten van een PE-bestand zijn beschadigd of kan niet correct worden verwerkt, het kan wijzen op een virale infectie. De processen gebruikt door de meeste anti-virus programma's om virussen in PE-bestanden te detecteren vereisen de verwerking van die bestanden op bepaalde manieren, dat, als de programmeur van een virus kent, specifiek zal proberen te verhinderen, zodat haar virus onopgemerkt blijven.

"decode_threshold"
- Optionele limiet of drempelwaarde de lengte van onverwerkte gegevens waarbinnen decoderen commando's moeten worden gedetecteerd (in het geval er enige merkbare prestatieproblemen terwijl scannen). Waarde is een integer vertegenwoordigen bestandsgrootte in KB. Standaard = 512 (512KB). Zero of nulwaarde zal uitschakelen het drempelwaarde (het verwijderen van een dergelijke limiet gebaseerd op bestandsgrootte).

"scannable_threshold"
- Optionele limiet of drempelwaarde de lengte van onverwerkte gegevens dat phpMussel is toegestaan te lezen en scan (in het geval er enige merkbare prestatieproblemen terwijl scannen). Waarde is een integer vertegenwoordigen bestandsgrootte in KB. Standaard = 32768 (32MB). Zero of nulwaarde zal uitschakelen het drempelwaarde. Algemeen, dit waarde moeten niet zijn lagere dan de gemiddelde bestandsgrootte van het bestandsuploads dat u wilt en verwacht te ontvangen aan uw server of website, moeten niet zijn meer dan de filesize_limit richtlijn, en moeten niet zijn meet dan ongeveer een vijfde van de totale toegestane geheugentoewijzing toegekend aan PHP via de `php.ini` configuratiebestand. Dit richtlijn bestaat te proberen om phpMussel te verhinderen van het gebruik van teveel geheugen (dat zou verhinderen het van de mogelijkheid te scannen bestanden met succes boven een bepaalde bestandsgrootte).

####"compatibility" (Categorie)
Compatibiliteit richtlijnen voor phpMussel.

"ignore_upload_errors"
- Dit richtlijn moet in het algemeen worden uitgeschakeld tenzij het is vereist voor de juiste functionaliteit van phpMussel op uw specifieke systeem. Normaal, wanneer uitgeschakeld, wanneer phpMussel detecteert de aanwezigheid van elementen van de `$_FILES` array(), het zal proberen initiëren een scan van het bestanden deze elementen vertegenwoordigen, en, als deze elementen zijn leeg, phpMussel zal terugkeren een foutmelding. Dit is het juiste gedrag voor phpMussel. Dat gezegd hebbende, voor sommige CMS, lege elementen in `$_FILES` kan optreden als gevolg van het natuurlijke gedrag van deze CMS, of fouten zouden zijn gerapporteerd wanneer er geen, in welk geval, het normale gedrag voor phpMussel zullen bemoeien met het normale gedrag van deze CMS. Als dergelijke een situatie optreedt voor u, inschakelen dit optie zal instrueren phpMussel niet te proberen te initiëren scannen voor dergelijke lege elementen, negeer hem wanneer gevonden en niet terugkeren gerelateerde foutmeldingen, dus toelaten de voortzetting van de pagina-aanvraag. False = UITGESCHAKELD; True = INGESCHAKELD.

"only_allow_images"
- Als u alleen verwachten of alleen bedoelen toestaan beelden worden geüpload om uw systeem of CMS, en als u absoluut nodig geen bestanden behalve afbeeldingen te wordt geüpload om uw systeem of CMS, dit richtlijn moet worden ingeschakeld, maar moet anderszins worden uitgeschakeld. Als dit richtlijn is ingeschakeld, het zal instrueren phpMussel zonder onderscheid te blokkeren elke upload geïdentificeerd als niet-beeldbestanden, zonder te scannen. Dit kan verminderen verwerkingstijd en geheugengebruik voor het geprobeerd uploaden van niet-beeldbestanden. False = UITGESCHAKELD; True = INGESCHAKELD.

####"heuristic" (Categorie)
Heuristische richtlijnen.

"threshold"
- Er zijn bepaalde handtekeningen van phpMussel dat zijn bedoeld om verdachte en potentieel kwaadaardige kwaliteiten te identificeren van bestanden wordt geüpload zonder zichzelf om bestanden wordt geüpload te identificeren specifiek als kwaadaardige. Dit "threshold" waarde vertelt phpMussel het maximaal totaalgewicht van verdachte en potentieel kwaadaardige kwaliteiten van bestanden wordt geüpload dat is toelaatbaar voordat deze bestanden worden gemarkeerd als kwaadaardig. De definitie van gewicht in dit verband is het aantal van verdachte en potentieel kwaadaardige kwaliteiten dat zijn geïdentificeerd. Standaard, dit waarde wordt ingesteld op 3. Algemeen, een lagere waarde zal resulteren in meer valse positieven maar meer kwaadaardige bestanden wordt gemarkeerd, terwijl een hogere waarde zal resulteren in minder valse positieven maar minder kwaadaardige bestanden wordt gemarkeerd. Algemeen, het is beste om dit waarde te laten op zijn standaard, tenzij u problemen ondervindt met betrekking tot het.

####"virustotal" (Categorie)
VirusTotal.com richtlijnen.

"vt_public_api_key"
- Optioneel, met phpMussel, het is mogelijk om bestanden te scannen met behulp van de Virus Total API als een manier om een sterk verbeterde mate van bescherming te bieden tegen virussen, trojans, malware en andere bedreigingen. Standaard, scannen van bestanden met behulp van de Virus Total API is uitgeschakeld. Om het te inschakelen, een Virus Total API-sleutel is nodig. Vanwege de aanzienlijke voordeel dat dit zou kunnen om u te voorzien, het is iets dat ik sterk aanbevelen te inschakelen. Wees u ervan bewust, echter, dat voor gebruik op de Virus Total API, u _**MOET**_ akkoord gaan hun Algemene Voorwaarden en u _**MOET**_ voldoen aan alle richtlijnen per beschreven door de Virus Total documentatie! U bent NIET toegestaan om dit integratie functie te gebruiken TENZIJ:
  - U heeft gelezen en u akkoord met de Algemene Voorwaarden van de Virus Total en zijn API. De Algemene Voorwaarden van de Virus Total en zijn API kan [Hier](https://www.virustotal.com/en/about/terms-of-service/) worden gevonden.
  - U heeft gelezen en u begrijpt, ten minste, de preambule van de Virus Total Public API-documentatie (alles na "VirusTotal Public API v2.0" maar vóór "Contents"). De Virus Total Public API-documentatie kan [Hier](https://www.virustotal.com/en/documentation/public-api/) worden gevonden.

Noteren: Als het scannen van bestanden met behulp van de Virus Total API is uitgeschakeld, u hoeft niet herziening van de richtlijnen in dit categorie (`virustotal`), omdat geen van hen iets te doen als dit is uitgeschakeld. Om een Virus Total API-sleutel te verwerven, van ergens op hun website, klik op de "Registreren" link gelegen in de richting van de rechterbovenhoek van de pagina, invoeren in de gevraagde informatie, en klik "Registreren" wanneer u klaar. Volg alle instructies geleverd, en wanneer u uw publieke API-sleutel heeft, kopieren/plakken dat publieke API om de `vt_public_api_key` richtlijn van de `config.ini` configuratiebestand.

"vt_suspicion_level"
- Normaal, phpMussel zal beperken welke bestanden scant met behulp van de Virus Total API om het bestanden die zijn beschouwd "achterdochtig". Optioneel, u kan dit beperking aan te passen door de waarde van het `vt_suspicion_level` richtlijn.
- `0`: Bestanden worden beschouwd achterdochtig alleen als, na te zijn gescand door phpMussel met eigen handtekeningen, zij geacht worden een heuristische gewicht te dragen. Dit zou effectief betekenen dat het gebruik van de Virus Total API zou zijn voor een tweede mening wanneer phpMussel vermoedt dat een bestand potentieel kwaadaardig kan zijn, maar kan niet helemaal uitsluiten dat het kan ook potentieel goedaardig zijn (niet-kwaadaardig) en daarom anders zou normaal niet blokkeren of vlag als kwaadaardig.
- `1`: Bestanden worden beschouwd achterdochtig alleen als, na te zijn gescand door phpMussel met eigen handtekeningen, zij geacht worden een heuristische gewicht te dragen, als ze bekend is executable te zijn (PE bestanden, Mach-O bestanden, ELF/Linux bestanden, etc), of als ze bekend zijn van een formaat dat potentieel executable gegevens kan bevatten (zoals executable macros, DOC/DOCX bestanden, archiefbestanden zoals RARs, ZIPS en etc). Dit is de standaard en aanbevolen achterdocht niveau toe te passen, effectief betekent dat het gebruik van de Virus Total API zou zijn voor een tweede mening wanneer in eerste instantie niets kwaadaardige of slecht wordt gevonden door phpMussel met een bestand beschouwd achterdochtig te zijn en daarom anders zou normaal niet blokkeren of vlag als kwaadaardig.
- `2`: Alle bestanden beschouwd achterdochtig worden en moeten worden gescand met behulp van de Virus Total API. Ik meestal niet raden het toepassen van dit achterdocht niveau, vanwege het risico bereiken API-quotum veel sneller dan anders het geval zou zijn, maar er zijn bepaalde omstandigheden (zoals wanneer de webmaster of hostmaster heeft weinig geloof of vertrouwen in de geringste in een van de geüploade inhoud van hun gebruikers) waarin dit achterdocht niveau kon passend zijn. Met dit achterdocht niveau, Alle bestanden normaal niet geblokkeerd of gemarkeerd als kwaadaardig zou worden gescand met behulp van de Virus Total API. Noteren, echter, dat phpMussel zal ophouden met behulp van de Virus Total API wanneer uw API-quotum is bereikt (ongeacht van achterdocht niveau), en dat uw API-quotum zal waarschijnlijk veel sneller bereikt met het gebruik van dit achterdocht niveau.

Noteren: Ongeacht van achterdocht niveau, elke bestanden die ofwel worden de zwarte lijst of witte lijst door phpMussel zal niet worden gescand met behulp van de Virus Total API, omdat die dergelijke bestanden reeds zou hebben verklaard als ofwel kwaadaardig of goedaardig door phpMussel tegen de tijd dat ze anders zouden hebben gescand door de Virus Total API, en daarom, extra scannen zou niet nodig. Het vermogen van phpMussel om bestanden te scannen met de Virus Total API is bedoeld om het vertrouwen bouwen verder voor of een bestand is kwaadaardig of goedaardig in die omstandigheden waarin phpMussel zelf is niet helemaal zeker de vraag van of een bestand is kwaadaardig of goedaardig.

"vt_weighting"
- Moeten phpMussel de resultaten van het scannen met behulp van de Virus Total API toe te passen als detecties of detectie weging? Dit richtlijn bestaat, omdat, hoewel het scannen van een bestand met behulp van meerdere motoren (als Virus Total doet) moet leiden tot een verhoogde aantal van detecties (en dus in een hoger aantal van kwaadaardige bestanden worden gedetecteerd), het kan ook resulteren in een hoger aantal van valse positieven, en daarom, in sommige gevallen, de resultaten van de scan kan beter worden benut als betrouwbaarheidsscore eerder dan als een definitieve conclusie. Als een waarde van 0 wordt gebruikt, de resultaten van het scannen met behulp van de Virus Total API zal worden toegepast als detecties, en zo, als een motor gebruikt door Virus Total vlaggen het bestand wordt gescand als kwaadaardige, phpMussel zal het bestand overwegen kwaadaardig te zijn. Als een andere waarde wordt gebruikt, de resultaten van het scannen met behulp van de Virus Total API zal worden toegepast als detectie weging, en zo, het aantal van motoren gebruikt door Virus Total dat vlag het bestand wordt gescand als kwaadaardige zal dienen als een betrouwbaarheidsscore (of detectie weging) voor of het bestand dat wordt gescand moet worden beschouwd als kwaadaardige door phpMussel (de waarde die wordt gebruikt zal vertegenwoordigen de minimale betrouwbaarheidsscore of weging vereist om kwaadaardige te worden beschouwd). Een waarde van 0 wordt standaard gebruikt.

"vt_quota_rate" en "vt_quota_time"
- Volgens de Virus Total API-documentatie, het is beperkt tot maximaal 4 verzoeken van welke aard in elk 1 minuut tijdsbestek. Als u een honeyclient, honeypot of andere automatisering te voorzien, dat gaat om middelen te verschaffen om VirusTotal en niet alleen rapporten opvragen heeft u recht op een hogere API-quotum. Normaal, phpMussel zal strikt houden aan deze beperkingen, maar vanwege de mogelijkheid van deze API-quotum verhoogd te worden, deze twee richtlijnen worden verstrekt als middel voor u om instrueren phpMussel wat limiet moeten houden worden. Tenzij u heeft geïnstrueerd om dit te doen, het is niet aan te raden voor u om deze waarden te verhogen, maar, als u heeft ondervonden problemen met betrekking tot uw tarief quota bereiken, afnemende deze waarden kunnen u soms helpen in het omgaan met deze problemen. Uw maximaal tarief bepaald als `vt_quota_rate` verzoeken van welke aard in elk `vt_quota_time` minuut tijdsbestek.

####"urlscanner" (Categorie)
URL scanner configuratie.

"urlscanner"
- Ingebouwd in phpMussel is een URL scanner, het opsporen van kwaadaardige URL's vanuit alle gegevens of bestanden gescand. Om de URL scanner te inschakelen, zetten de richtlijn `urlscanner` op true; Om het te uitschakelen, zetten dit richtlijn op false.

Noteren: Als de URL scanner wordt uitgeschakeld, zult u geen behoefte aan een van de richtlijnen in dit categorie te herzien (`urlscanner`), omdat geen van hen zal alles doen als dit is uitgeschakeld.

URL scanner API configuratie.

"lookup_hphosts"
- Inschakelt gebruik van de [hpHosts](http://hosts-file.net/) API wanneer zet op true. hpHosts nodig geen API sleutel voor het uitvoeren API verzoeken.

"google_api_key"
- Inschakelt gebruik van de Google Safe Browsing API wanneer de noodzakelijke API sleutel wordt gedefinieerd. Google Safe Browsing API nodig hebben een API sleutel, dat kan worden verkregen van [Hier](https://console.developers.google.com/).
- Noteren: De cURL uitbreiding is nodig om deze functie te gebruiken.

"maximum_api_lookups"
- Maximaal toelaatbaar aantal van de API verzoeken te voeren per individuele scan iteratie. Omdat elke extra API verzoek zullen toevoegen aan de totale tijd die nodig te voltooien elke scan iteratie, u kunt wensen om een beperking te specificeren teneinde versnellen het algehele scanproces. Wanneer ingesteld op 0, geen dergelijk maximaal toelaatbaar aantal wordt toegepast. Ingesteld op 10 standaard.

"maximum_api_lookups_response"
- Wat te doen als het maximaal toelaatbaar aantal van API verzoeken wordt overschreden? False = Niets doen (voortzetten de verwerking) [Standaard]; True = Merken/blokkeren het bestand.

"cache_time"
- Hoe lang (in seconden) moeten de resultaten van de API verzoeken worden gecached voor? Standaard is 3600 seconden (1 uur).

####"template_data" (Categorie)
Richtlijnen/Variabelen voor sjablonen en thema's.

Sjabloongegevens betreft op de HTML-uitvoer die wordt gegenereerd en gebruikt voor de "Upload Geweigerd" bericht getoond om de gebruikers wanneer een bestand upload is geblokkeerd. Als u gebruik aangepaste thema's voor phpMussel, HTML-uitvoer is afkomstig van de `template_custom.html` bestand, en alternatief, HTML-uitvoer is afkomstig van de `template.html` bestand. Variabelen geschreven om dit sectie van het configuratiebestand worden geïnterpreteerd aan de HTML-uitvoer door middel van het vervangen van variabelennamen omringd door accolades gevonden binnen de HTML-uitvoer met de bijbehorende variabele gegevens. Bijvoorbeeld, waar `foo="bar"`, elk geval van `<p>{foo}</p>` gevonden binnen de HTML-uitvoer `<p>bar</p>` zal worden.

"css_url"
- De sjabloonbestand voor aangepaste thema's maakt gebruik van externe CSS-eigenschappen, terwijl de sjabloonbestand voor het standaardthema maakt gebruik van interne CSS-eigenschappen. Om phpMussel instrueren om de sjabloonbestand voor aangepaste thema's te gebruiken, geef het openbare HTTP-adres van uw aangepaste thema's CSS-bestanden via de `css_url` variabele. Als u dit variabele leeg laat, phpMussel zal de sjabloonbestand voor de standaardthema te gebruiken.

---


###8. <a name="SECTION8"></a>HANDTEKENINGFORMAAT

####*BESTANDSNAAM HANDTEKENINGEN*
Alle bestandsnaam handtekeningen volgt het formaat:

`NAME:FNRX`

Waar NAME is de naam te noemen voor die handtekening en FNRX is de reguliere expressie patroon om bestandsnamen (ongecodeerde) te controleer tegen.

####*MD5 HANDTEKENINGEN*
Alle MD5 handtekeningen volgt het formaat:

`HASH:FILESIZE:NAME`

Waar HASH is de MD5 hash van een hele bestand, FILESIZE is de totale grootte van het bestand en NAME is de naam te noemen voor die handtekening.

####*ARCHIEF METADATA HANDTEKENINGEN*
Alle archief metadata handtekeningen volgt het formaat:

`NAME:FILESIZE:CRC32`

Waar NAME is de naam te noemen voor die handtekening, FILESIZE is de totale grootte (ongecomprimeerde) van een bestand vervat in het archief en CRC32 is de CRC32 checksum van die vervat bestand.

####*PE SECTIONELE HANDTEKENINGEN*
Alle PE sectionele handtekeningen volgt het formaat:

`SIZE:HASH:NAME`

Waar HASH is de MD5 hash van een sectie van een PE bestand, SIZE is de totale grootte van die sectie en NAME is de naam te noemen voor die handtekening.

####*PE UITGEBREIDE HANDTEKENINGEN*
Alle PE uitgebreide handtekeningen volgt het formaat:

`$VAR:HASH:SIZE:NAME`

Waar $VAR is de naam van de PE-variabele te controleer tegen, HASH is de MD5 hash van die variabele, SIZE is de totale grootte van die variabele en NAME is de naam te noemen voor die handtekening.

####*WHITELIST HANDTEKENINGEN*
Alle whitelist handtekeningen volgt het formaat:

`HASH:FILESIZE:TYPE`

Waar HASH is de MD5 hash van een hele bestand, FILESIZE is de totale grootte van het bestand en TYPE is het handtekeningen type het bestand van de whitelist is immuun tegen te zijn.

####*COMPLEXE UITGEBREIDE HANDTEKENINGEN*
Complexe uitgebreid handtekeningen zijn nogal verschillend van de andere handtekening typen mogelijk met phpMussel, doordat wat ze gecontroleerd tegen wordt bepaald door de handtekeningen zelf en ze kunnen controleer tegen meervoudig criteria. De controle criteria zijn begrensd door ";" en de controle type en de controle gegevens van elke controle criteria wordt begrensd door ":" zoals zo dat formaat voor deze handtekeningen heeft de neiging om een beetje uitzien als:

`$variable1:GEGEVENS;$variable2:GEGEVENS;Handtekeningnaam`

####*AL HET ANDERE*
Alle andere handtekeningen volgt het formaat:

`NAME:HEX:FROM:TO`

Waar NAME is de naam te noemen voor die handtekening en HEX is een hexadecimale gecodeerd segment van het bestand bestemd om te worden gecontroleerd door de gegeven handtekening. FROM en TO optioneel parameters zijn, aangeeft van waaruit en waaraan in de brongegevens om te controleren tegen.

####*REGEX*
Elke vorm van reguliere expressie begrepen en correct verwerkt door moet ook correct worden begrepen en verwerkt door phpMussel en handtekeningen. Echter, Ik stel voor het nemen van extreem voorzichtigheid bij het schrijven van nieuwe handtekeningen op basis van reguliere expressie, omdat, als u niet helemaal zeker wat u doet, kan er zeer onregelmatig en/of onverwachte resultaten worden. Neem een kijkje op de phpMussel broncode als u niet helemaal zeker over de context waarin regex verklaringen geïnterpreteerd worden. Ook, vergeet niet dat alle patronen (met uitzondering van bestandsnaam, archief metadata en MD5 patronen) moet hexadecimaal gecodeerd worden (voorgaande patroon syntaxis, natuurlijk)!

####*WAAR OM AANGEPASTE HANDTEKENINGEN TE ZETTEN?*

####*HANDTEKENINGEN OVERZICHT*
Het volgende is een overzicht van de soorten handtekeningen gebruikt door phpMussel:
- "Genormaliseerde ASCII handtekeningen". Gecontroleerd tegen de inhoud van elke niet-whitelist bestand gericht voor het scannen.
- "Complexe Uitgebreide handtekeningen". Gemengde soort van handtekeningen controleren.
- "ELF handtekeningen". Gecontroleerd tegen de inhoud van elke niet-whitelist bestand gericht voor het scannen en geïdentificeerd aan de ELF-formaat.
- "Portable Executable handtekeningen". Gecontroleerd tegen de inhoud van elke niet-whitelist bestand gericht voor het scannen en geïdentificeerd aan de PE-formaat.
- "Bestandsnaam handtekeningen". Gecontroleerd tegen het bestandsnamen van het bestanden gerichte voor het scannen.
- "Algemene handtekeningen". Gecontroleerd tegen de inhoud van elke niet-whitelist bestand gericht voor het scannen.
- "Grafische handtekeningen". Gecontroleerd tegen de inhoud van elke niet-whitelist bestand gericht voor het scannen en geïdentificeerd naar een bekende grafisch formaat.
- "Algemene commando's" (hex_general_commands.csv). Gecontroleerd tegen de inhoud van elke niet-whitelist bestand gericht voor het scannen.
- "Genormaliseerde HTML handtekeningen". Gecontroleerd tegen de inhoud van elke niet-whitelist HTML-bestand gericht voor het scannen.
- "Mach-O handtekeningen". Gecontroleerd tegen de inhoud van elke niet-whitelist bestand gericht voor het scannen en geïdentificeerd aan de Mach-O-formaat.
- "Email handtekeningen". Gecontroleerd tegen de inhoud van elke niet-whitelist EML-bestand gericht voor het scannen.
- "MD5 handtekeningen". Gecontroleerd tegen de MD5 hash van de inhoud en het bestandsgrootte van elke niet-whitelist bestand gericht voor het scannen.

- "OLE handtekeningen" (ole_*). Gecontroleerd tegen de inhoud van elke niet-whitelist OLE-object gericht voor het scannen.
- "PDF handtekeningen" (pdf_*). Gecontroleerd tegen de inhoud van elke niet-whitelist PDF-bestand gericht voor het scannen.
- "Portable executable sectionele handtekeningen" (pe_*). Gecontroleerd tegen de MD5 hash en de grootte van elke PE-sectie van elke niet-whitelist bestand gericht voor het scannen en geïdentificeerd aan de PE-formaat.
- "Portable executable uitgebreide handtekeningen" (pex_*). Gecontroleerd tegen de MD5 hash en de grootte van variabelen in elke niet-whitelist bestand gericht voor het scannen en geïdentificeerd aan de PE-formaat.
- "Shockwave handtekeningen" (swf_*). Gecontroleerd tegen de inhoud van elke niet-whitelist Shockwave-bestand gericht voor het scannen.
- "Whitelist handtekeningen" (whitelist_*). Gecontroleerd tegen de MD5 hash van de inhoud en het bestandsgrootte van elke bestand gericht voor het scannen. Gecontroleerd bestanden zal zijn immuun van gecontroleerd te worden door de soort van handtekening in hun whitelist binnenkomst.
(Bewust zijn van dat elk van deze handtekeningen gemakkelijk kunnen worden uitgeschakeld via `config.ini`).

---


###9. <a name="SECTION9"></a>BEKENDE COMPATIBILITEITSPROBLEMEN

####PHP en PCRE
- PHP en PCRE is vereist voor phpMussel te kunnen functioneren juist. Zonder PHP, of zonder de PCRE extensie van PHP, phpMussel zullen niet worden uitgevoerd of functioneren juist. U moet er zeker van uw systeem heeft zowel PHP en PCRE geïnstalleerd en beschikbaar voordat downloaden en installeren phpMussel.

####ANTI-VIRUS SOFTWARECOMPATIBILITEIT

Voor het grootste deel, phpMussel is algemeen compatibel met de meeste andere anti-virus software. Echter, conflictions geweest beschreven door een aantal gebruikers in het verleden. Deze informatie hieronder is afkomstig van VirusTotal.com, het beschrijven van een aantal fout-positieven gemeld door anti-virus programma's tegen phpMussel. Hoewel deze informatie is geen absolute garantie van wel of niet u zult compatibiliteitsproblemen ondervindt tussen phpMussel en uw anti-virus software, als uw anti-virus software wordt gemarkeerd tegen phpMussel, moet u ofwel overwegen uit te schakelen voorafgaand aan het werken met phpMussel of moeten overwegen alternatieve opties om ofwel uw anti-virus software of phpMussel.

Dit informatie werd laatst bijgewerkt 29 Augustus 2016 en is op de hoogte voor alle phpMussel publicaties van de twee meest recente mineur versies (v0.10.0-v1.0.0) op het moment van schrijven dit.

| Scanner              |  Resultaten                          |
|----------------------|--------------------------------------|
| Ad-Aware             |  Geen bekend problemen               |
| AegisLab             |  Geen bekend problemen               |
| Agnitum              |  Geen bekend problemen               |
| AhnLab-V3            |  Geen bekend problemen               |
| Alibaba              |  Geen bekend problemen               |
| ALYac                |  Geen bekend problemen               |
| AntiVir              |  Geen bekend problemen               |
| Antiy-AVL            |  Geen bekend problemen               |
| Arcabit              |  Geen bekend problemen               |
| Avast                |  Berichten "JS:ScriptSH-inf [Trj]"   |
| AVG                  |  Geen bekend problemen               |
| Avira                |  Geen bekend problemen               |
| AVware               |  Geen bekend problemen               |
| Baidu                |  Berichten "VBS.Trojan.VBSWG.a"      |
| Baidu-International  |  Geen bekend problemen               |
| BitDefender          |  Geen bekend problemen               |
| Bkav                 |  Berichten "VEXC640.Webshell", "VEXD737.Webshell", "VEX5824.Webshell", "VEXEFFC.Webshell"|
| ByteHero             |  Geen bekend problemen               |
| CAT-QuickHeal        |  Geen bekend problemen               |
| ClamAV               |  Geen bekend problemen               |
| CMC                  |  Geen bekend problemen               |
| Commtouch            |  Geen bekend problemen               |
| Comodo               |  Geen bekend problemen               |
| Cyren                |  Geen bekend problemen               |
| DrWeb                |  Geen bekend problemen               |
| Emsisoft             |  Geen bekend problemen               |
| ESET-NOD32           |  Geen bekend problemen               |
| F-Prot               |  Geen bekend problemen               |
| F-Secure             |  Geen bekend problemen               |
| Fortinet             |  Geen bekend problemen               |
| GData                |  Geen bekend problemen               |
| Ikarus               |  Geen bekend problemen               |
| Jiangmin             |  Geen bekend problemen               |
| K7AntiVirus          |  Geen bekend problemen               |
| K7GW                 |  Geen bekend problemen               |
| Kaspersky            |  Geen bekend problemen               |
| Kingsoft             |  Geen bekend problemen               |
| Malwarebytes         |  Geen bekend problemen               |
| McAfee               |  Berichten "New Script.c"            |
| McAfee-GW-Edition    |  Berichten "New Script.c"            |
| Microsoft            |  Geen bekend problemen               |
| MicroWorld-eScan     |  Geen bekend problemen               |
| NANO-Antivirus       |  Geen bekend problemen               |
| Norman               |  Geen bekend problemen               |
| nProtect             |  Geen bekend problemen               |
| Panda                |  Geen bekend problemen               |
| Qihoo-360            |  Geen bekend problemen               |
| Rising               |  Geen bekend problemen               |
| Sophos               |  Geen bekend problemen               |
| SUPERAntiSpyware     |  Geen bekend problemen               |
| Symantec             |  Geen bekend problemen               |
| Tencent              |  Geen bekend problemen               |
| TheHacker            |  Geen bekend problemen               |
| TotalDefense         |  Geen bekend problemen               |
| TrendMicro           |  Geen bekend problemen               |
| TrendMicro-HouseCall |  Geen bekend problemen               |
| VBA32                |  Geen bekend problemen               |
| VIPRE                |  Geen bekend problemen               |
| ViRobot              |  Geen bekend problemen               |
| Zillya               |  Geen bekend problemen               |
| Zoner                |  Geen bekend problemen               |

---


###10. <a name="SECTION10"></a>VEELGESTELDE VRAGEN (FAQ)

####Wat is een "vals positieve"?

De term "vals positieve" (*alternatief: "vals positieve fout"; "vals alarm"*; Engels: *false positive*; *false positive error*; *false alarm*), zeer eenvoudig beschreven, en een algemene context, wordt gebruikt bij het testen voor een toestand, om verwijst naar om de resultaten van die test, wanneer de resultaten positief zijn (d.w.z, de toestand wordt vastgesteld als "positief"), maar wordt verwacht "negatief" te zijn (d.w.z, de toestand in werkelijkheid is "negatief"). Een "vals positieve" analoog aan "huilende wolf" kan worden beschouwd (waarin de toestand wordt getest, is of er een wolf in de buurt van de kudde, de toestand is "vals" in dat er geen wolf in de buurt van de kudde, en de toestand wordt gerapporteerd als "positief" door de herder door middel van schreeuwen "wolf, wolf"), of analoog aan situaties in medische testen waarin een patiënt gediagnosticeerd als met een ziekte of aandoening, terwijl het in werkelijkheid, hebben ze geen ziekte of aandoening.

Enkele andere termen die worden gebruikt zijn "waar positieve", "waar negatieve" en "vals negatieve". Een "waar positieve" verwijst naar wanneer de resultaten van de test en de huidige staat van de toestand zijn beide waar (of "positief"), and a "waar negatieve" verwijst naar wanneer de resultaten van de test en de huidige staat van de toestand zijn beide vals (of "negatief"); En "waar positieve" of en "waar negatieve" wordt beschouwd als een "correcte gevolgtrekking" zijn. De antithese van een "vals positieve" is een "vals negatieve"; Een "vals negatieve" verwijst naar wanneer de resultaten van de test is negatief (d.w.z, de aandoening wordt vastgesteld als "negatief"), maar wordt verwacht "positief" te zijn (d.w.z, de toestand in werkelijkheid is "positief").

In de context van phpMussel, deze termen verwijzen naar de handtekeningen van phpMussel en de bestanden die ze blokkeren. Wanneer phpMussel blokkeert een bestand, als gevolg van slechte, verouderde of onjuiste handtekening, maar moet niet hebben gedaan, of wanneer het doet om de verkeerde redenen, we verwijzen naar deze gebeurtenis als een "vals positieve". Wanneer phpMussel niet in slaagt te blokkeren om een bestand dat had moeten worden geblokkeerd, als gevolg van onvoorziene bedreigingen, ontbrekende handtekeningen of tekorten in zijn handtekeningen, we verwijzen naar deze gebeurtenis als een "gemiste detectie" (dat is analoog aan een "vals negatieve").

Dit kan worden samengevat in de onderstaande tabel:

&nbsp; | phpMussel moet *NIET* een bestand te blokkeren | phpMussel *MOET* een bestand te blokkeren
---|---|---
phpMussel *NIET* doet blokkeren van een bestand | Waar negatieve (correcte gevolgtrekking) | Gemiste detectie (analoog aan vals negatieve)
phpMussel *DOET* blokkeren van een bestand | __Vals positieve__ | Waar positieve (correcte gevolgtrekking)

---


Laatste Bijgewerkt: 19 December 2016 (2016.12.19).
