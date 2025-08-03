# warta-plan

Etapy 

## 1. Kontrola jakości 100% nagrań z wykorzystaniem gotowej checklisty
   - Od teraz dla każdej rozmowy
   - Cała baza historyczna
     
Cel: Automatyczne wykrycie rozmow/doradcow, ktorzy nie stosuja sie do checklisty


## 2. Model Machine Learning - czy pola z checklisty koreluja ze sprzedaza? Co najbardziej?

Model ML, target: czy rozmowa skonwertowala
zmienne: checklista + kontekst doradcy (% hit rate do tej pory) + kontekst klienta + kontekst rozmowy

Cel: zrozumienie zmiennych wyjaśniających sprzedaż, żeby można było na nich zrobić zoom-in

## 3. Automatyczne generowanie zmiennych do checklisty z wykorzystaniem LLM

Chodzi o to, zeby
a. Katalog: Wydobyc nowe taktyki / style (hipoteza: pewnie o wiekszym stopniu zlozonosci niz dot. checklista) - kandydatow do werfyikacji czy dobrze wplywaja na sprzedaz
b. Scoring: Przygotowac te zmienne dla wszystkich rozmow z bazy
b. Rozszerzyc model z punktu 2. i sprawdzic, czy nowe zmienne z a. wplywaja na sprzedaz

Potencjalne strategie na a:
- losowo wybierac 3 rozmowy "1" i 3 rozmowy "0", podawac do llma i prosic o wyodrebneinie roznic (uczenie kontrastowe). Na koniec podsumowac wszystkie wydobyte strategie.
- porownywac najlepszych doradcow z najgorszymi - prawdodpobonie dobrzy doradcy wciaz stosuja skuteczne strategie
- przygotowac liste hipotez z organizacji ktorych nie obejmuje dot. checklista - np. rozmowa z najlepszymi doradcami ("jak klient mowi ze drogo, to ja zawsze mowie X")

## 4. Spergonalizowana pomoc dla doradcy i real-time podpowiedzi

Trudne, bo wymaga infrastruktury real-time (zupelnie inny poziom skomplikowania niz analiza na danych historycznych)
- real time speech to text
- real time call LLM api (trzeba zdecydowac kiedy wysylamy kontekst, poczkeac 4-5 seknd na odpowiedz LLM, a w rozmowie trzeba reagowac blyskawicznie)

Co robic jako 1. etap, jezeli okaze sie ze taktyki / kombinacja klienta dzialaja: spersonalizowane przygotowanie / argumenty dla danego klienta przed rozmowa, jezeli na podstawie jego kontesktu mozna przewidziec jego obiekcje (historyczne obiekcje, typowe obiekcje dla podobnych klientow, etc). => Automatyczne wydobywanie historycznych obiekcji klienta, automatyczna analiza jak przebiegaly rozmowy historyczne. 

## 5. Analiza eksploracyjna danych - on top

- Obiekcje - Reakcje - najczestsze / co dziala / nie dzia;a
- Sentyment wyciagant z tonu glosu (a nie samej tresci)
