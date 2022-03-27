Django
======
Django je pomerne komplexný webový framework, ktorý ponúka všetko, čo budú naši užívatelia potrebovať.

Django za nás prevezme správu databázy, poskytne veľa užitočných funkcií a ponúkne svoju perfektnú administráciu.

Inštalácia
----------

Počítame s tým, že Python máte nainštalovaný. Django nainštalujeme nasledujúcim príkazom, ktorý vložíme do príkazového riadku. Ak nie ste s príkazovým riadkom zoznámenie, otvorte ponuku Štart a napíšte "cmd". Na nájdenú aplikáciu "Príkazový riadok" vpravo kliknite myšou. Ak nepoužívate Windows, predpokladám, že viete kde má váš systém terminál :) Zadajte príkaz:

..code-block:: console

	py -m pip install Django==2.0.4

Ak používate Anaconda / MiniConda distribúciu Pythone, upravte si príkazy pre inštalácie ako:

..code-block:: console

	conda install django

Aktuálne číslo verzie, nájdete na https://www.djangoproject.com/

Adresárová štruktúra Django projektu
------------------------------------

Obsah zložky vyzerá nasledovne:

..code-block:: console

	mysite/
		mysite/
			__init__.py
			settings.py
			urls.py
			wsgi.py
		manage.py

Jednotlivé súbory si teraz popíšeme:

* **settings.py** - Tu sa nachádza konfigurácia projektu a tu tiež inštalujeme svoje aplikácie, viď ďalej.
* **urls.py** - Tu je uložené schéma, ktoré hovorí ako sa má spracovať URL adresa, ktorú užívateľ do prehliadača zadá. Definujeme tu aké adresy smerujú na aké časti našej aplikácie. Tomuto mechanizmu sa hovorí routovanie.
* **wsgi.py** - Konfigurácia rozhrania pre nasadenie webové aplikácie na server.
* **manage.py** - O zložku vyššie sa nachádza manage.py, pre nás najdôležitejšia súbor. Umožňuje nám spúšťať rôzne príkazy. Použijeme ho napr. K migrácii databázy, vytváranie aplikácií, zberu statických súborov a ďalším podobným účely.

Spustenie servera
-----------------

Spustenie servera prevedieme spustením príkazu cez súbor manage.py.
K tomu potrebujeme otvoriť príkazový riadok v priečinku mysite, kde sa tento súbor nachádza.

Zadáme príkaz:

.. code-block:: console

	py manage.py runserver

Vytvorenie aplikácie (modulu)
-----------------------------

Projekt môže obsahovať viac aplikácií.
Tie fungujú ako moduly, typicky máme napr. Zvlášť administráciu od hlavnej aplikácie. Asi ste sa asi skôr stretli s pojmami aplikácie a modul než s projekt a aplikácie, význam je ale úplne rovnaký.

Vytvoríme si teda v projekte aplikácii (modul) s názvom "ahoj_svete" príkazom:

.. code-block:: console

	py manage.py startapp ahoj_svete

Adresárová štruktúra aplikácie (modulu)
---------------------------------------

Django za nás všetko potrebné vytvorí, to je jeho výhoda oproti napr. Flask frameworku. V priečinku projektu sa nám vytvorí nový adresár, jeho obsah vyzerá nasledovne:

.. code-block::

	mysite/
		ahoj_svete/
			__init__.py
			admin.py
			apps.py
			models.py
			tests.py
			# urls.py
		# Ostatní zůstává stejné

Jednotlivé súbory:

* admin.py - Administrácia jednotlivé aplikácie.
* apps.py - Konfigurácia jednotlivej aplikácie.
* models.py - Správa modelov databázy, Django ORM, viď ďalej v kurze.
* tests.py - Testy aplikácie.
* urls.py - Tento súbor sa nevytvorí, musíme ho vytvoriť manuálne. Budú tu odkazy na Python skripty, ktoré požiadavky zaslané cez danej URL adresy spracujú

Inštalácia aplikácie (modulu)
-----------------------------

V súbore ``NAZOV_PROJEKTU/NAZOV_PROJEKTU/settings.py`` aplikáciu "nainštalujeme".
Django musí mať prehľad o tom, kde má svoje aplikácie a koľko ich má. U tejto aplikácie inštalácia nie je nutná, ale je lepšie si zvyknúť inštalovať všetky naše aplikácie, už len z princípu Django frameworku.

**Inštaláciu** vykonáme pripísaním názvu aplikácie do ``settings.py``, do časti označenej komentárom # Application definition :

.. code-block:: console

	INSTALLED_APPS = [
		'helloWorld',
		...
		...
	]

Routovanie
----------

Dostávame sa do bodu, kedy musíme zabezpečiť, aby otvorenie URL adresy servera otvorilo aplikáciu ``helloWorld``. Keďže postup je zložitejší, vysvetlíme si hneď na začiatku čoho potrebujeme docieliť.

Adresu servera (http://localhost:8000/) postupne napojíme zo súboru ``urls.py`` projektu, cez súbor ``urls.py`` aplikácie (modulu), až na našu prvú Python metódu, ktorá užívateľovi pošle "Hello world!" hlášku späť do prehliadača.

Routovanie projektu (modulu)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

V súbore ``NAZOV_PROJEKTU/NAZOV_PROJEKTU/settings.py`` pridáme route na našej aplikácii. Keďže táto ruta bude definovaná v routách aplikácie, teda v súbore ``NAZOV_PROJEKTU/helloWorld/urls.py``, tento súbor sem iba naincludujeme, aby sme ju nemuseli písať 2x. Všetky ruty definované v aplikácii sa potom samy prenesú do rout projektu a budú fungovať.

Keďže budeme chcieť, aby sa aplikácia ``helloWorld`` spustila priamo po otvorení adresy servera ``localhost:8000/``, namiesto adresy uvedieme len prázdny reťazec ''. Do súboru ``urls.py`` si pridajte route na helloWorld.urls. Nezabudnite pridať aj import pre **include**:

.. code-block::

	from django.contrib import admin
	from django.urls import path, include

	urlpatterns = [
		path('admin/', admin.site.urls),
		path('', include("ahoj_svete.urls")),
	]

Routovanie aplikácie
^^^^^^^^^^^^^^^^^^^^

Všetky routy budeme už definovať len v priečinku aplikácie. Prejdite do priečinka ``mysite/ahoj_svete/`` a tu vytvorte súbor ``urls.py``. Tam pridáme URL adresu našej prvej stránky. Tu už adresu prekryjeme cez tzv. **View**. To je Python metóda, ktorá požiadavku spracuje a vráti užívateľovi výsledok.

.. note::

	Ak poznáte **MVC** architektúru, aj tu Python používa iné názvoslovie.

Obsah súboru tu ``urls.py`` bude nasledujúce:

.. code-block::

	from django.urls import path
	from . import views

	urlpatterns = [
		path("", views.index, name="index"),
	]

Pridanie view
^^^^^^^^^^^^^

**View** je teda posledná časť reťazca, ktorá požiadavku užívateľa zachytí a odpovie na neho. Jedná sa o Python metódu. Rôzne URL adresy napojujeme na rôzne views, teda rôzne metódy. My máme v aplikácii teraz len jednu, aby toho nebolo na začiatok moc.

Vytvoríme si teda view pre zobrazenie hlášky "Ahojte všetci!".

Prejdeme do súboru ``mysite/ahoj_svete/views.py``, kde si vytvoríme metódu index().
Jej parametrom bude request, požiadavka, ktorý prišiel cez URL adresu.
Našu hlášku nezobrazíte ako HTML stránku, ale len ako text vrátením inštancia typu HttpResponse. Kód danej metódy je nasledovné, nezabudnite si pridať aj **HttpResponse** na prvom riadku.

.. code-block::

	from django.shortcuts import render, HttpResponse

	def index(request):
		return HttpResponse("Ahoj světe!")

Všetko si uložte a otvorte adresu aplikácie v prehliadači. Prejdite na http://localhost:8000/.

.. warning::

	Nezabudnite, že musíte mať spustený aj server, viď vyššie.

MVC
---

MVC je veľmi obľúbený architektonický vzor, ktorý sa uchytil najmä na webe, hoci pôvodne vznikol na desktopoch. Je súčasťou populárnych webových frameworkov, akými sú napr. **Zend** alebo Nette pre PHP, Ruby On Rail pre Ruby alebo MVC pre ASP .NET. Osobne si bez neho (alebo nejakého podobného princípu) nedokážem predstaviť zložitejšie web.

Motivácia
^^^^^^^^^

Základnou myšlienkou **MVC** architektúry je oddelenie logiky od výstupu. Rieši teda problém tzv. "Špagetového kódu", kedy máme v jednom súbore (triede) logické operácie a zároveň renderovanie výstupu. Súbor teda obsahuje databázové dotazy, logiku (volanie Python príkazov) a rôzne pohádzané HTML tagy. Všetko je zamotané do seba ako špagety.

Kód sa samozrejme zle udržuje, nieto rozširuje. Je zle highlightovaný, pretože si s ním IDE nevie rady, HTML nie je správne naformátované, strácame sa v jeho stromovej štruktúre. Naším cieľom je, aby zdrojový kód s logikou vyzeral ako zdrojový kód (Python) a výstup vyzeral ako HTML stránka s čo najmenšou prímesou ďalšieho kódu.

Komponenty
^^^^^^^^^^

Celá aplikácia je rozdelená na komponenty 3 typov, hovoríme o modeli, View (pohľadoch) a Controller (kontroléry), od toho MVC. Označenie pohľad sa budem snažiť vyhýbať, pretože mi príde mätúce, že takto preloženej nekorešponduje s označením V. Neexistuje žiadna striktná definícia architektúry a tak sa môžete stretnúť s viacerými výklady. Zameral som sa na ten najrozšírenejší.

Komponenty Model a Controller sú samozrejme triedy. View je HTML šablóna.

Model
^^^^^

Model obsahuje logiku a všetko, čo do nej spadá. Môžu to byť výpočty, databázové dotazy, validácie a podobne. Model vôbec nevie o výstupe. Jeho funkcia spočíva v prijatí parametrov zvonku a vydanie dát von. Zdôrazním, že parametre nemyslím URL adresu ani žiadne iné parametre od užívateľa. Model nevie, odkiaľ dáta v parametroch prišli a ani ako budú výstupné dáta naformátovaná a vypísane.

Keďže budeme používať tzv. ORM (Objektovo-Relačná Mapovanie), naše modely budú priamo korešpondovať s databázovými tabuľkami. Budeme teda mať napr. Model Uzivatel, Komentar alebo Clanok. Instance modelov budú samozrejme obsahovať atribúty z databázy. Instance modelu Uzivatel bude mať napr. Atribút meno. Triede môžeme definovať inštančný metódy, napr. Takú, ktorá vypočíta vek používateľa podľa jeho dátumu narodenia. Metódy týkajúce sa všeobecne užívateľov (teda triedny) často vkladáme do modelu ako statické, napr. Overenie správnej dĺžky a znakov hesla (teda jeho validáciu, pretože heslo overujeme ešte predtým, než je inštancia používateľa vytvorená a zároveň s užívateľom logicky súvisí).

View
^^^^

.. warning::

	V Django v MVC architektúre má VIEW iný význam. V tejto sekcii budeme teda hovoriť o všeobecnej komponente, nie o Django.

Pohľad (View) sa stará o zobrazenie výstupu užívateľovi. Jedná sa o html šablónu, obsahujúci HTML stránku a tagy značkovacieho jazyka Django, ktorý umožňuje do šablóny vkladať premenné, prípadne vykonávať iterácie (cykly) a podmienky. Pohľad uzivatel teda vypíše detaily o používateľovi, pohľad clanek vypíše obsah článku.

Pohľadov máme veľa, napr. Pre funkcionalitu s entitou užívateľa: uzivatel_registrace, uzivatel_prihlaseni, uzivatel_profil a podobne. Pohľad uzivatel_profil je ale už spoločný všetkým užívateľom a sú do neho posielané rôzne dáta, vždy podľa toho, koho zrovna zobrazujeme. Tieto dáta sú potom dosadená do HTML elementov šablóny.

Šablóny možno samozrejme vkladať do seba, aby sme sa neopakovali (šablóna s layoutom stránky, šablóna s menu a šablóna s článkom).

.. note::

	View nie je len šablóna, ale zobrazovač výstupu. Obsahuje teda minimálne množstvo logiky, ktorá je pre výpis nutná (napr. Kontrola, či si užívateľ vyplnil prezývku pred jej vypísaním alebo cyklus s komentármi, ktoré sa vypisujú).

View podobne ako Model vôbec nevie, odkiaľ mu dáta prišla, stará sa len o ich zobrazenie užívateľovi.

Controller
^^^^^^^^^^

Controller je teraz onen chýbajúci prvok, ktorý osvetlí funkčnosť celého vzoru. Ide o akéhosi prostredníka, s ktorým komunikuje užívateľ, model i view. Drží teda celý systém pohromade a komponenty prepája. Jeho funkciu pochopíme z ukážky životného cyklu stránky. Opäť existuje veľa rôznych prístupov, najčastejšie má každá entita (Resource) jeden controller, máme teda UserController, PostController a tak podobne.

Životný cyklus stránky
^^^^^^^^^^^^^^^^^^^^^^

Životný cyklus začína používateľ, ktorý zadá do prehliadača adresu webu a parametre, ktorými nám oznámi, ktorú podstránku si želá zobraziť. Budeme chcieť zobraziť detail uzivatele s id 15. Urobme si ukážku URL adresy:

.. code-block::

	http://www.domena.cz/uzivatel/detail/15

Požiadavku ako prvý zachytí tzv. **Router**. S ruty sme sa už zoznámili. Ten podľa definovaných rout spozná, ktorý controller voláme. V našom prípade voláme UserController.

Daný controller podľa parametrov spozná, čo sa po ňom chce, teda že má zobraziť detail užívateľa. Zavolá model, ktorý používateľa vyhľadá v databáze a vráti jeho údaje. Ďalej zavolá ďalšiu metódu modelu, ktorá napr. Vypočíta vek používateľa. Tieto údaje si controller ukladá do premenných. Nakoniec vyrenderuje view (Template). Názov pohľadu poznáme podľa akcie, ktorú vykonávame. View sú odovzdané premenné s príslušnými dátami. Controller(view) teda poslúchol užívateľa, obstaral podľa parametrov dotazu dáta od modelu a odovzdal ich view(templetu).

View(templete) prijme dáta od Controlleru(view) a vloží ich do pripravenej šablóny. Hotová stránka je zobrazená užívateľovi, ktorý často o celej tejto kráse ani netušia :)

MVC architektúra nám uľahčuje aj myslenia pri vývoji projektu. Keď píšem logiku, patrí do modelu, formátovanie a štýlovanie výstupu riešim v šablóne, to čo užívateľ chce z parametrov zisťujem v Controlleru. 3 rôzne problémy na 3 rôznych miestach, oddelené tak, aby do seba nezasahovali a nerobili nám vývoj zložitejši.

MVT = MVC
^^^^^^^^^

Framework **Django** implementuje MVC architektúru presne tak, ako sme si ju popísali. Jednotlivé komponenty ale nazýva po svojom a bohužiaľ názov jednej prehodil, čo môže byť mätúce.

**Modely** - Modelom hovorí Django ``modely``.
**Views** - pohľadom hovorí Django ``Templates``, čo je v preklade šablóny.
**Controllers** - kontrolérom Django hovorí ``Views``.

Nenechajte sa teda zmiasť, ked tvoríme nový **View**, nie je to **HTML šablóna**, ale onen **Controller** medzi Modelom a Šablónou (templetom). V minulej aplikácii sme svoje prvé view implementovati ako metódu index(). Tá ešte nepoužívala model ani šablónu, ale iba vrátila textovú odpoveď užívateľmi.

Statické súbory
---------------

Teraz sa vrhneme do **static files**, to jest úložisko súborov, ktoré budeme používať v našich templates.
Povedzme, že si budeme chcieť do svojho **index.html** pridať obrázok a uvádzať k nemu absolútnu cestu nie je práve rozumné. Preto má Django podporu pre statické súbory. Každá aplikácia má svoju zložku static, kde sú tieto súbory uložené.
Rovnako ako tomu bolo pri template, aj tu Django po spustení servera pristupuje ku zložkám static ako k jednej zložke.
Je len na vás do akéj aplikácie si daný obrázok / súbor vložíte, ale ak bude obrázok pre aplikáciu ``moviebook``, tak je oveľa lepší obrázok uložiť do ``/mysite/moviebook/static/moviebook/obrazek.jpg``.

.. note::

	Zložku so static files e potrebné nastaviť v ``/mysite/mysite/settings.py`` :
	::

		STATIC_ROOT = os.path.join(BASE_DIR, "static/")

Keď už máme nastavené, je potreba súbory zhromaždiť. Túto akciu vykonáme príkazom:

.. code-block::

	py manage.py collectstatic

Teraz si môžeme tento obrázok vložiť do nášho template :

.. code-block::

	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>MovieBook</title>
	</head>
	<body>
		{% load static %} <!-- Slouží pro načtení statických souborů -->
		Název filmu: {{nazev_filmu}} <br>
		Žánr: {{zanr}} <br>
		Hodnocení: {{hodnoceni}} <br>
		Náš obrázek: <br>
		<img src={% static 'moviebook/obrazek.jpg' %} alt=""> <!-- Zde vkládáme obrázek -->
	</body>
	</html>

Databáza
--------

Ako databáze budeme používať **SQLite**, ktorá je v Django už prednastavené a nemusí sa na rozdiel od iných databáz inštalovať ani konfigurovať.
Ak by ste v budúcnosti vytvárali komplexnejšie aplikácie, je vhodnejšie použiť napr. databázu `MySQL<https://www.itnetwork.sk/mysql>`_.

Modely
^^^^^^

S databázou budeme pracovať pomocou tzv. **ORM** (Objektovo-Relačná Mapovanie).
To znamená, že budeme pracovať s objektmi, a toto počínanie nám bude Django na pozadí automaticky prevádzať na databázové príkazy.

K vytvoreniu databázových tabuliek teda nespustíte zakladacia SQL príkazy, ako ste možno boli zvyknutí, ale vytvoríme triedy reprezentujúci databázové entity. Korešpondujúce tabuľky budú neskôr založené automaticky. Vytvorme si entity Film a Zanr.

Prejdeme do súboru ``mysite/moviebook/models.py`` a upravime jeho obsah do nasledujúcej podoby:

.. code-block::

	from django.db import models

	class Film(models.Model):
		nazov = models.CharField(max_length=200)
		recenzie = models.CharField(max_length=180)

	class Zaner(models.Model):
		film = models.ForeignKey(Film, on_delete=models.CASCADE)
		nazov_zanru = models.CharField(max_length=80)

Migrácia
^^^^^^^^

Úprave databázy tak, aby zodpovedala definícii modelov v našej aplikácii, sa hovorí **migrácie**.
Tento proces musíme spustiť zakaždým, keď vykonáme zmenu v definícii dátové štruktúry a potrebujeme, aby **Django** na jej základe databázu upravilo, v našom prípade dokonca vytvorilo.

Databázovú migráciu najprv vytvoríme príkazom:

.. code-block:: console

	py manage.py makemigrations [nazov aplikacie]

Potom migráciu spustíme:

.. code-block:: console

	py manage.py migrate

Django API
^^^^^^^^^^

Teraz si ukážeme prácu s **Django API**, teda ako do databázy vkladať nové riadky ako objekty a ako objekty z databázy tiež získavať.

Ukážku vykonáme v interaktívnom shellu, ktorý spustíme pomocou:

.. code-block:: console

	py manage.py shell

A do neho napíšeme nasledujúci kód:

.. code-block:: console

	from moviebook.models import Film, Zanr
	muj_film = Film(nazev="Strazci Galaxie", rezie="James Gunn") # Vytvoříme si nový film
	muj_film.nazev # Zobrazí název filmu
	muj_film.save() # Uloží film do DB

	Film.objects.all() # Zobrazí všechny existující filmy
	muj_film.zanr_set.all() # Zobrazí všechny žánry k danému filmu
	muj_film.zanr_set.create(nazev_zanru="Fantasy/Action") # Vytvoří nový žánr k tomuto filmu

Rozšírenie modelov
^^^^^^^^^^^^^^^^^^

Upravime naše modely tak, aby nám vracali názov a meno režiséra. Podobne upravíme aj žáner.

.. code-block::

	from django.db import models

	class Zaner(models.Model):
		nazov_zanru = models.CharField(max_length=80)

		def __str__(self):
			return "Nazov_zanru: {0}".format(self.nazov_zanru)

	class Film(models.Model):
		nazov = models.CharField(max_length=200)
		rezie = models.CharField(max_length=180)
		zaner = models.ForeignKey(Zaner, on_delete=models.SET_NULL, null=True)

		def __str__(self):
			return "Nazov: {0} | Rezie: {1} | Zaner: {2}".format(self.nazov, self.rezie, self.zaner.nazov_zanru)

Administrácia databázy
^^^^^^^^^^^^^^^^^^^^^^

Konečne sa dostávame k administrácii. Superuser máme vytvoreného.

Najprv je potrebné naše modely do administrácie zaregistrovať a to úpravou súboru ``/mysite/moviebook/admin.py`` :

.. code-block::

	from django.contrib import admin
	from .models import Film, Zaner #Importujeme si modely

	#Modely registrujeme
	admin.site.register(Film)
	admin.site.register(Zaner)

Nasledne si spustíme server a zamierime si to na adresu ``http://localhost:8000/admin/``.

Meta
^^^^

Meta, slúži na ukladanie / nastavenie informácií navyše, ako je v tomto prípade názov množného čísla entity nastaviteľný pomocou ``verbose_name_plural`. Upravime súbor ``/mysite/moviebook/models.py`` :


.. code-block::

	from django.db import models

	class Zaner(models.Model):
		nazov_zanru = models.CharField(max_length=80, verbose_name="Žáner")

		def __str__(self):
			return "Nazov_zanru: {0}".format(self.nazov_zanru)

		class Meta:
			verbose_name="Žáner"
			verbose_name_plural="Žánre"

	class Film(models.Model):
		nazov = models.CharField(max_length=200, verbose_name="Názov Filmu")
		rezie = models.CharField(max_length=180, verbose_name="Režia")
		zaner = models.ForeignKey(Zaner, on_delete=models.SET_NULL, null=True, verbose_name="Žáner")

		def __str__(self):
			return "Nazov: {0} | Rezie: {1} | Zaner: {2}".format(self.nazov, self.rezie, self.zaner.nazov_zanru)

		class Meta:
			verbose_name="Film"
			verbose_name_plural="Filmy"


Generic views
-------------

Generic views sú predpripravené views pre jednoduché akcie, ktoré sa vo webových aplikáciách často používajú. Práve tie využijeme pre pridávanie a editáciu záznamov v našej databáze, aby sme nemuseli písať všetko znova.

ListView
^^^^^^^^

Ako prvý generic view si vyskúšame **ListView**, ktoré vypíše zoznam položiek. V našom prípade si ním samozrejme necháme vypísať všetky filmy z databázy. Súbor ``/mysite/moviebook/views.py`` upravíme do nasledujúcej podoby:

.. code-block::

	class FilmIndex(generic.ListView):

    template_name = "moviebook/film_index.html" # cesta k templatu ze složky templates (je možné sdílet mezi aplikacemi)
    context_object_name = "filmy" # pod tímto jménem budeme volat list objektů v templatu

	# tato funkce nám získává list filmů seřazených od největšího id (9,8,7...)
		def get_queryset(self):
			return Film.objects.all().order_by("-id")

Ako prvé je potrebné naimportovať generic views a samotné modely.

**View** teraz už nie je tvorené obyčajnou metódou, ale triedou dedičov z generic.ListView, prípadne z iného generického pohľadu. Keď sa nad tým zamyslíte, je to logické, pretože práve dedičnosťou sa nám do view dostane predpripravená funkčnosť.

* Generic view nastavíme šablónu a ako sa má premenná s jednotlivými prvkami zoznamu v šablóne vymenovať.
* Následne definujeme metódu pre získanie všetkých filmov, ktoré si zoradíme od posledne pridaných po tie najstaršie.

Na tento view si vytvoríme odkaz v ``/mysite/moviebook/urls.py`` :

.. code-block::

	from django.urls import path
	from . import views

	urlpatterns = [
		path("film_index/", views.FilmIndex.as_view(), name="filmovy_index"),
	]

Template pre náš prvý generic view ListView bude v súbore ``/mysite/moviebook/templates/moviebook/film_index.html`` s nasledujúcim obsahom:

.. code-block::

	<!DOCTYPE html>
	<html lang="cs">
	<head>
		<meta charset="UTF-8">
	</head>
	<body>
		{% for film in filmy %}
			Název: {{film.nazov}} <br>
		{% endfor %}
	</body>
	</html>

DetailView
^^^^^^^^^^

Teraz by bolo dobré vytvoriť si aj view pre detail vybraného filmu. K tomu nám pomôže **DetailView**, ktoré nám o filme zobrazia všetky podrobnosti.

Na koniec ``/mysite/moviebook/views.py`` pridáme:

.. code-block::

	class CurrentFilmView(generic.DetailView):

		model = Film
		template_name = "moviebook/film_detail.html"

**View** je opäť trieda, odděděná z generického predka.

.. note::

	V prípade detaile nastavujeme len model a názov šablóny.

Šablóna
^^^^^^^

Šablónu pre view vytvoríme v ``/mysite/moviebook/templates/moviebook/film_detail.html``, ktorý sme v detail view vyššie nastavili. Všimnite si pomenovanie súborov, kedy je názov zložený z názvu entity, podčiarknutia a názvu generic view. Obsah šablóny je nasledujúci:

.. code-block::

	<!DOCTYPE html>
	<html lang="cs">
	<head>
		<meta charset="UTF-8">
	</head>
	<body>
		<h1> {{ film.nazov }} </h1><small> {{ film.rezie }} </small>
		<h3> {{film.zaner.nazov_zanru}} </h3>
	</body>
	</html>

Každý DetailView potrebuje poznať ID / PK (primárny kľúč) konkrétneho filmu, pre ktorý nám bude zobrazovať všetky informácie, aby si ho mohol z databázy načítať. Odkaz na film preto bude obsahovať aj PK konkrétneho filmu.

Upravíme súbor ``/mysite/moviebook/urls.py`` :

.. code-block::

	path("<int:pk>/film_detail/", views.CurrentFilmView.as_view(), name="film_detail"),

Tým sme Dajngo vysvetlili, že keď niekto zadá URL adresu na detail filmu, je to číslo pred ňou primárny kľúč (ID) tohto filmu.

Teraz odkaz na film pridáme do výpisu filmov, teda do šablóny ``/mysite/moviebook/templates/moviebook/film_index.html``.

Obyčajný užívateľ sa totiž zatiaľ stále nemá ako dostať na stránku s informáciami o filme. Do odkazu nezadáme absolútnu adresu, ale použijeme názov URL, ktorý sme v routách uviedli (v tomto prípade name="filmovy_detail"), ako parameter odovzdáme ID / PK. URL je takto jednoduchšie a keby sa adresa pohľadu niekedy zmenila, táto zmena sa prejaví bez nutnosti šablónu upraviť.

Pridajme teda odkaz do ``film_detail.html`` :

.. code-block::

	<!DOCTYPE html>
	<html lang="cs">
	<head>
		<meta charset="UTF-8">
	</head>
	<body>
		{% for film in filmy %}
		   <a href={% url "filmovy_detail" film.id %}> Název: {{film.nazev}} <br> </a>
		{% endfor %}
	</body>
	</html>

Formulár
^^^^^^^^

Filmy vieme vypisovať a zobrazovať ich detail. Pridanie filmu urobíme pomocou triedy ModelForm.

Formulár by sme samozrejme mohli vytvoriť oldschool cestou len ako čisté HTML, ako sme to robili v kalkulačke, ale Django tu máme práve preto, aby sme sa naučili ako si s ním uľahčiť prácu.

Vytvoríme si nový modul ``/mysite/moviebook/forms.py``, v ktorom sa bude nachádzať náš formulár:

.. code-block::

	from django import forms
	from .models import Film

	class FilmForm(forms.ModelForm):

		class Meta:
			model = Film
			fields=["nazov", "rezie", "zaner"]

Asi vás neprekvapí, že ako ďalší krok si vytvoríme view, ktoré bude stránku s formulárom obsluhovať.
Do view ``/mysite/moviebook/views.py`` pridáme nový import práve na náš formulár:

.. code-block::

	from django.shortcuts import render, redirect, render_to_response
	from django.views import generic

	from .models import Film
	from .forms import FilmForm #Nový import

	# ...

CreateView
^^^^^^^^^^

Okrem importu na koniec súboru pridáme obsluhu formulára, ktorú si vzápätí vysvetlíme.

Použijeme pre ňu generic view CreateView. Vidíme ako môžeme z Django prevziať veľa funkcionality, ktorú by sme inak museli implementovať sami.

.. code-block::

	# ...

	class CreateFilm(generic.edit.CreateView):

		form_class = FilmForm
		template_name = "moviebook/create_film.html"

	# Metoda pro GET request, zobrazí pouze formulář
		def get(self, request):
			form = self.form_class(None)
			return render(request, self.template_name, {"form":form})

	# Metoda pro POST request, zkontroluje formulář; pokud je validní, vytvoří nový film; pokud ne, zobrazí formulář s chybovou hláškou
		def post(self, request):
			form = self.form_class(request.POST)
			if form.is_valid():
				form.save(commit=True)
			return render(request, self.template_name, {"form":form})

View nastavujeme formulár a šablónu.

Ďalej obsahuje 2 akcie, get() formulár iba zobrazuje a post() ho spracováva v prípade, že už bol odoslaný.

Všimnite si, že v oboch akciách formulár odovzdávame pomocou listu do šablóny, aby sme ho tam mohli vykresliť. Určite by sme sa nemali v metóde post() zabudnúť opýtať, či bol formulár validný vyplnený. Keďže formulár vie aký model spracúva, pre uloženie filmu na ňom stačí zavolať len metódu save() a je hotovo.

Pre nových view a teda novú adresu si ako vždy pridáme route v ``/mysite/moviebook/urls.py`` :

.. code-block::

	from django.urls import path
	from . import views

	urlpatterns = [
		path("film_index/", views.FilmIndex.as_view(), name="filmovy_index"),
		path("<int:pk>/film_detail/", views.CurrentFilmView.as_view(), name="filmovy_detail"),
		path("create_film/", views.CreateFilm.as_view(), name="novy_film"),
	]

Šablóna
^^^^^^^

Vytvoríme si template ``/mysite/moviebook/templates/moviebook/create_film.html`` pre náš form :

.. code-block::

	<!DOCTYPE html>
	<html lang="cs">
	<head>
		<meta charset="UTF-8">
	</head>
	<body>
		<form method="POST">
			{% csrf_token %} <!-- Django požaduje ověření proti útoku csrf  -->
			{{ form }}
			<input type="submit">
		</form>
	</body>
	</html>

Po odoslaní validného formulára sa vytvorí nový film. Po prechode na http://localhost:8000/moviebook/film_index si môžete vyskúšať, že sa medzi filmami naozaj zobrazí.

Internationalization
--------------------

Pred vygenerovanim multijazycnych suborov je potrebne upravit subor ``settings.py`` :

::

	LOCALE_PATHS = [
		os.path.join(BASE_DIR, "locale")
	]

Vytvorte súbor správ:

* Z hlavnej ponuky vyberte Tools | Spustite úlohu manage.py (⌥ R) .
* V okne úlohy manage.py zadajte
.. code-block::
	makemessages --locale <názov prostredia>

Tento krok zopakujte pre každé miestne nastavenie, ktoré chcete vytvoriť.

Ak sú na lokalizáciu označené reťazce, PyCharm vytvorí adresár a súbor **django.po** pre každé miestne nastavenie:

PyCharm provides a dedicated intention action to wrap strings in Django templates in {%trans%}, or {%blocktrans%} tags.

Pri prvom volani je potrebne do sablony dotiahnut `` {% load i18n%} ``

Compile a message file

Povytvoreni lokalizacnych suborov je potrebne subory skompilovat :

.. code-block:: console

	py manage.py compilemessages
