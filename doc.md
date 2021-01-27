# Opis sistema

Sistem koji se razvija predstavlja platformu za
rentiranje automobila. Platforma bi funkcionisala na
način da zadovolji potrebe pre svega klijenta koji potražuju
automobile od firmi. Klijenti bi imali mogućnost pretraživanja
firmi za rentiranje vozila na osnovu lokacije. 
Firme bi se zatim izlistavali po opadajućem redu u
zavisnosti od ocena. Pored toga nakon odabira firme
klijenti bi imali mogućnost pregleda asortimana vozila
koje imaju firme. Ove opcije kao krajnji ishod za cilj
imaju slanje upita o rentiranju određenog vozila. 
Nakon odobrenja rentiranja od strane firme klijent će
biti dužan da u okviru aplikacije izvrši uplatu od 20%
ukupnog iznosa. Klijent će na osnovu ovih podataka imati
kasnije evidenciju svih rentiranja. 

Firme će osim ovoga biti u mogućnosti da kroz ovu aplikaciju
izvršavaju kompletnu administraciju u okviru svoje firme
za rentiranjem automobila. Takođe aplikacija će menadžerima
firme pružati informacije o efikasnosti i statistici
poslovanja. Ovu statistiku menadžeri mogu iskoristiti
za unapređenje efikasnosti firme.


# Funkcionalni zahtevi

### Funkcionalni zahtevi
1. **Klijent**
	1. Klijent vrsi pretraživanje firmi sortiranih u zavisnosti od ocena
		u opadajućem nizu. Firme se ocenjuju od strane klijenta. 
	1. Klijent ima funkcionalnost plaćanja rentiranja
	1. Klijent ima mogućnost potraživanja odnosno slanja zahteva za rentiranje 
	1. Klijent ima mogućnost pregleda proteklih rezervacija  
2. **Menadžer**

	1. Menadžer je ovlašćen da može
		1. Dodavati zaposlene
		2. Brisati zaposlene ukoliko zaposleni prestane sa radom u firmi
		3. Ažurirati podatke o zaposlenima

	
	2. Menadžeru takođe, treba omogućiti uvid u statistiku poslovanja firme.
	Statistika treba prikazivati podatke

		1. Nedeljni,mesečni i godišnji izveštaj efikasnosti
		2. Infomacije koja vozila su najpopularnija.
		
3. **Administrativni radnik**

	1. Administrativnom radniku treba omogućiti mogućnost osnovnih operacija
	nad vozilima

		1. Dodavanje
		2. Brisanje
		3. Ažuriranje

	2. Administativnom radniku treba omogućiti opšti pregled vozila sa pratećim informacijama
		
		1. Informacije o brendu,nazivu,modelu i ceni.
		2. Podatak o tome da li je vozilo na servisu ili ne
		3. Podatak da li je vozilo trenutno zauzeto.
		4. Istoriju servisa koje je vozilo imalo.
	
	

### Nefunkcionalni zahtevi

1. Aplikacija mora štititi prava privatnosti 

2. Aplikacije mora biti pouzdana tako da svi
zahtevi o rentiranju stiže na vreme i bez sistemskih greški 

3. Za aplikaciju je potrebno obezbediti odgovarajući
server na kom ce ostvarivati propisane performanse

4.Sistem treba da omogući svim korisnicima sistema da vide jedino podatke koji su značajni za njih.

5.Sistem treba da onemogući prijavljivanje korisnika na 1h, nakon 5 uzastopnih neuspešnih pokušaja prijave korisnika u roku od 5 minuta.  

6.Sistem treba da automatski odjavi korisnika koji ne koristi sistem aktivno 45 minuta.

# Dijagram slučajeva korišćenja

<img src="https://firebasestorage.googleapis.com/v0/b/soy-smile-249718.appspot.com/o/Screenshot%20from%202021-01-27%2020-40-06.png?alt=media&token=f6490b37-7168-4b92-b0ac-148c0aa0c258" height="500px">

# Klijent

Opisani slučajevi scenarija za klijenta

|ID i naziv           | UC-1 Pretraga vozila                                  |
|---------------------|-------------------------------------------------------|
|Kreator              | Aleksa Lukić                                          |               
| Datum kreiranja     | 26.01.2021                                            |
|Pokretač             | Potencijalni klijent posećuje aplikaciju odnosno sajt |
|Opis                 | Klijentu treba omogućiti polje za unos teksta kako bi mogao da pretražuje naziv vozila ili naziv firme      |
|Primarni akter       | Klijent                                               |
|Preduslovi           | PRE-1 Postoji konekcija na internet. <br> PRE-2 Backend deo aplikacije je pokrenut i ostvarena je konekcija sa bazom |
|Normalni tok         | 1. Korisnik u polje za unos teksta upisuje naziv vozila ili naziv firme. <br> 2. Ukoliko postoje odgovarajući rezultati o vozilima oni će biti prikazani korisniku.|
|Alternativni tok     | Na stranici za filtriranje vozila korisnik umesto polja za unos može koristiti padajuće liste u kojima se nalaze podaci o brendu i modelu vozila |
|Izuzeci              | 1. Ne postoje rezultati. 2. Sistem će obavestiti korisnika o tome da za traženu pretragu ne postoje poklapanja. |
|Prioritet            | Srednji |
|Frekvencija upotrebe | U proseku 10 puta po satu. |

|ID i naziv           | UC-2 Pregled rezervacija                               |
|---------------------|--------------------------------------------------------|
|Kreator              |Aleksa Lukić                                            |
|Datum kreiranja      | 26.01.2021.                                            |
|Pokretač             |Klijent klikom na svoj profil otvara prozor za pregledavanje rezervacija |
|Opis                 |Klijentu treba omogućiti da se na osnovu njegovog korisničkog imena pronađu sve rezervacije koje je ostvario |
|Primarni akter       |Klijent  |
|Preduslovi           | PRE-1 iz UC-1,PRE-2 iz UC-2 + klijent je uspešno ulogovan na sistem |
|Normalni tok         | 1. Klijent se uspešno prijavljuje na sistem. <br> 2. Klijent otvara prozor sa pregledom rezervacija <br> 3. Na osnovu korisničkog imena pronalaze se sve njegove rezervacije |
|Alternativni tok     | Ne postoji alternativni tok |
|Izuzeci              | 1. Korisnik nije ulogovan na siste. 2. Korisnik nije ostvario ni jednu rezervaciju sa određenom firmom, u tom slučaju prikazaće mu se obaveštenje.  |
|Prioritet            | Niski |
|Frekvencija upotrebe | Jednom u sedam dana |


|ID i naziv           | UC-3 Ocenjivanje firmi                                  |
|---------------------|---------------------------------------------------------|
|Kreator              | Aleksa Lukić                                            |
|Datum kreiranja      | 26.01.2021                                              |
|Pokretač             | Klijent je ostvario poslovanje sa određenom firmom      |
|Opis                 | Nakon rentiranja automobila klijent može oceniti firmu ocenom od 1-5|
|Primarni akter       | Klijent                                                 |
|Preduslovi           | PRE-1 iz UC-1,PRE-2 iz UC-2 + klijent je uspešno ulogovan na sistem + klijent je ostvario poslovanje sa firmom |
|Normalni tok         | 1. Klijent se loguje na sistem <br> 2. Pronalazi firmu koju želi da oceni <br> 3. Nakon otvaranja firme, softver prepoznaje da li je korisnik imao poslovanje sa firmom ili ne.Ukoliko je ostvario poslovanje odobriće mu se ocenjivanje u suprotnom neće biti u mogućnosti da oceni firmu. |
|Alternativni tok     | Klijent pronalazi firmu, nakon klika na dugme "oceni", aplikacija će zahtevati da se klijent prvenstveno loguje na sistem kako bi sistem odlučio da li klijent ima ispunjene uslove za ocenjivanje. |
|Izuzeci              | Klijent ima ostvareno poslovanje sa firmom, ali poslednje rentiranje vozila izvšeno je pre više od mesec dana, te se smatra zastarelim i na taj način klijent ne ostvarujezahtevane uslove za ocenjivanje |
|Prioritet            | Srednji|
|Frekvencija upotrebe | Jednom u dve nedelje |


|ID i naziv           | UC-4 Slanje zahteva za rentiranje                      |
|---------------------|--------------------------------------------------------|
|Kreator              |Aleksa Lukić                                            |
|Datum kreiranja      |26.01.2021.                                             |
|Pokretač             |Klijentu je neophodan auto za rentiranje|
|Opis                 |Ovo predstavlja jednu od ključnih funkcionalnsoti aplikacije. Nakon uspešnog odabira vozila, klijent bi trebao odabrati željenu firmu sa kojom želi da obavi rentiranje i nakon toga uputi zahtev |
|Primarni akter       |Klijent |
|Preduslovi           | PRE-1 iz UC-1,PRE-2 iz UC-2 + klijent je uspešno ulogovan na sistem |
|Normalni tok         | 1. Klijent se loguje na sistem.<br> 2. Klijent pronalazi željeno vozilo [ALT 2] <br> 3.Klijent bira sa kojom firmom želi da ostvari poslovanje. Ovaj izobr se vrši kroz padajuću listu u kojoj su prikazane firme koje poseduju izabrano vozilo <br> 4.Klikom na dugme 'uputi zahtev', poslaće se zahtev odabranoj firmi. 5. Nakon uspešno poslatog zahteva neophodno je poslati avans od 20% iznosa kako bi firma utvrdila da zahtev nije greškom poslat. 
|Alternativni tok     | 1. Ukoliko klijent odabere vozilo,ali prethodno nije logovan na sistem, sistem ga treba odvesti na formu za logovanje kako bi mogao da nastavi proces rezervacije. 2.Klijent može vršiti odabir vozila kroz stranicu za filtriranje, gde će odabrati brend,model,cenu. 2.1 Klijent može odabrati vozilo unosom naziva vozila u polje za pretragu. 3.Pored toga, klijent je u mogućnosti da uplati unapred kompletan iznos putem aplikacije.  |
|Izuzeci              | Zahtev za rezervaciju neće biti uspešno poslat, ako klijent nema obaveznih 20% na svom računu kako bi uplatio neophodni avans. |
|Prioritet            | Najveći|
|Frekvencija upotrebe |  Svakodnevno|

# Administrativni radnik

Opisani slučajevi scenarija za administrativnog radnika


|ID i naziv           | UC-5 Pretraga vozila                                    |
|---------------------|---------------------------------------------------------|
|Kreator              |Aleksa Lukić                                             |
|Datum kreiranja      |26.01.2021.                                              |
|Pokretač             | Administrativni radnik želi da pronađe određeno vozilo. Razlozi mogu biti, uvid u informacije o servisima,ili ažuriranje podataka o vozilu |
|Opis                 | Administrativnom radniku treba omogućiti da preko polja za pretragu u okviru svog panela pronađe željeno vozilo  |
|Primarni akter       | Administrativni radnik                                  |
|Preduslovi           | Administativni radnik je ulogvan na sistem + PRE-1 iz UC-1,PRE-2 iz UC-2 |                                                                                            
|Normalni tok         | 1. Administrativni radnik se prijavljuje na sistem. <br> 2. Administrativni radnik otvara prozor sa svim vozilima <br> 3. Administrativni radnik u polje za pretragu unosi naziv vozila|
|Alternativni tok     | X|
|Izuzeci              | Traženo vozilo ne postoji. Sistem će vratiti praznu listu i na stranici će obavestiti administrativnog radnika da za traženu pretragu nema rezultata |
|Prioritet            | Visok |
|Frekvencija upotrebe | Česta - minimum 5 puta dnevno |

|ID i naziv           | UC-6 Infomarcije o popravkama                           |
|---------------------|---------------------------------------------------------|
|Kreator              |Aleksa Lukić                                             |
|Datum kreiranja      |26.01.2021.                                              |
|Pokretač             | Administrativni radnik želi da pogleda da li je određeno vozilo trenutno na servisu, ili želi da pogleda istoriju obavljenih servisa na vozilima |
|Opis                 | Ova opcije bi trebala biti dostupna u okviru opšteg pregleda vozila. Trebalo bi implementirati dugme sa naziv 'Uvid u servise' i nakon klika na dugme u novom prozoru treba prikazati neophodne podatke. |
|Primarni akter       | Administrativni radnik |
|Sekundardni akter    | Menadžer |
|Normalni tok         | 1. Administrativni radnik se loguje na sistem. <br> 2. Administrativni radnik otvara prozor sa vozilima. <br> 3. Administrativni radnik uspešno izvršava pretragu i pronalazi željeno vozilo <br> 4.Nakon otvaranja opšteg pregleda otvara prozor sa prikazom istorije serivsa. |
|Alternativni tok     | X |
|Izuzeci              | 1. Traženo vozilo ne posotji 2. Vozilo nema istoriju servisa |
|Prioritet            | Srednji |
|Frekvencija upotrebe | Jednom u dve nedelje |


|ID i naziv           | UC-7 CRUD vozila
|---------------------|---------------------------------------------------------|
|Kreator              |Aleksa Lukić                                             |
|Datum kreiranja      |26.01.2021.                                              |
|Pokretač             | Administrativni radnik želi da izvrši određenu CRUD operaciju nad određeni vozilom |
|Opis                 | Operacije je neophodno implementirati u okviru prozora 'Vozila' gde će nakon otvaranja pomenutog prozora sve operacije biti lako dostupne |
|Primarni akter       | Administrativni radnik                                  |
|Normalni tok         | 1. Administrativni radnik se prijavljuje na sistem. <br> 2. Administrativni radnik otvara prozor 'Vozila' <br> 3.Administrativni radnik bira jednu od ponuđenih opcija.<br> [OPT-1]-Dodavanje <br> [OPT-2]-Izmena <br> [OPT-3]-Brisanje. <br>   [OPT-1] - Na stranici u gornjem desnom uglu treba postaviti odgovarajuće dugme nakon čijeg će se klika otvoriti forma za dodavanje vozila. [EXC-1] <br> [OPT-2]-Izmena - Na istom prozor će se dinamički prikazati posotjeća vozila. Jedno vozilo će biti predstavljeno kao kartica tako da će pored naziva vozila sadržati tri dugmeta - pregled, **izmeni** i obriši. Klikom na dugme **izmeni** otvoriće se forma za izmenu vozila [EXC-3] <br> [OPT-3] - Na spomenutoj kartici na kojoj je prikazano jedno vozilo nalaziće se dugme **obriši** nakon klika na to dugme željeno vozilo biće obrisano.|  
|Alternativni tok     |x|
|Izuzeci              |[EXC-1] - Nevalidni unos prilikom pokušaja kreiranja novog vozila <br> [EXC-2]- Nevalidni unos prilikom pokušaja izmene vozila|
|Prioritet            | Visok |
|Frekvencija upotrebe | Jednom mesečno |

# Menedžer

Opisani slučajevi korišćenja.
Korisnik: Menadžer

|ID i naziv           | UC-8 Statistika poslovanja  
|---------------------|---------------------------------------------------------|
|Kreator              |Aleksa Lukić                                             |
|Datum kreiranja      |26.01.2021.                                              |
|Pokretač             |Menadžer želi da pogleda uspešnost kompanije i efikasnost vozila |
|Opis                 | Podatka o efikasnosti potrebno je grafički prikazati kako bi bili vizuelno upadljivi |
|Primarni akter       | Menadžer                                                |
|Normalni tok         | 1. Menadžer otvara prozor pod nazivom "Statistika" <br> 2. Nakon toga odabira jednu od ponuđenih opcija <br> [OPT-1] Periodična statistika (nedeljni,mesečni,godišnji izveštaj) <br> [OPT-2] 2.Efikasnosti vozila |
|Alternativni tok     | U zavisnsti od [OPT-] aplikacija nam pruža više alternativnih tokova. [ALT-1 - OPT-1]- Statistika za tekuću nedelju <br> [ALT-2 - OPT-1]-Mesečni prikaz. Menadžer je u mogućnosti da izabere određeni mesec za koji želi pregledati statistiku poslovanja <br> [ALT-3 OPT-1 ] - Odabir godine - Godišnja statistika <br> [ALT-1 OPT-2] - Menadžer nakon odabira željenog vozila može pogledati kompletno efikasnost vozila,koliko je puta bilo rentirano tokom godine. |
|Izuzeci               | Ukoliko menadžer odabere vozilo koje trenutno nikada nije bilo rentirano softver će ga obavestiti da ne postoji statistika za odabrano vozilo.|
|Prioritet             | Srednji|
|Frekvencija upotrebe  | Jednom nedeljno |


# Modeli procesa

<img src="https://firebasestorage.googleapis.com/v0/b/soy-smile-249718.appspot.com/o/Screenshot%20from%202021-01-27%2021-46-14.png?alt=media&token=07e24519-adb9-4995-a371-9d13bc99ee3a" height="500px">
Na slici je prikazan model proces klijenta.
# Baza podataka

<img src="https://firebasestorage.googleapis.com/v0/b/soy-smile-249718.appspot.com/o/Screenshot%20from%202021-01-27%2021-40-53.png?alt=media&token=8a76c0eb-9864-4a1d-a319-b3bd99f9abe4" height="500px">
# Klasni dijagram

Entitetske klase možemo uočiti kroz dijagram baze podataka.
Pošto na se na ovom projektu primenjuje REST arhitektura backend će biti odvojen od frontend dela aplikacije.
Na backend delu možemo primeniti šablon fabrike kako bi izblegli problem ponavljanja koda.

<img src="https://firebasestorage.googleapis.com/v0/b/soy-smile-249718.appspot.com/o/Screenshot%20from%202021-01-27%2021-56-35.png?alt=media&token=7df39928-5732-4f9f-9996-55e389629a9d" height="500px">


