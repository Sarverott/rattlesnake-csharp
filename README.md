# rattlesnake
Cute yet powerfull tool in c#, for admin work acceleration in chill easy interaction and to automate developer's tasks with colorfull console interfacing

---

> DEVNOTES:

nowa odsłona istniejącego już projektu: https://github.com/Sarverott/rattlesnake
##### about
pierwotnie projekt miał służyć do czego innego, ale funkcjonalność jako uniwersalny zestaw do prostego i szybgiego komponowania narzędzi dla administratorów i deweloperów okazał się o wiele ciekawszym projektem.

począdkowo był to program w c++ który dla danej aktualnej ścieżki operacyjnej w FS realizował swoje zadania korzystając z konfiguracji plikami ini, plików tekstowych, wykonywania komend i drzewa katalogów jako otwarcia submenu poprostu zmieniając aktualną ścieżkę i robiąc pętlę. 

Miało to całkiem spory potencjał, bo mocno usprawniało prace w projektach gdzie funkcjonalność `npm run <command>` byłaby przydatna lecz występowanie `package.json` niewskazane z powodu braku zasadności - **skoro to nie projekt javascriptowy lub pokrewny to byłby tutaj dupy**.


##### klarowanie pomysłu
- zamiast c++ użyjmy c#
- Spectre jest fajne i prostsze niż gołe strumienie cpp z kolorowaniem używając escapecodes
- jako default sterowanie strzałkami, wybieranie opcji
- podsumowanie bazowej podstawowej funkcjonalności:
	- command exec - wymagane rozbicie
		- shell_exec
		- run_script
		- open_link
	- print text file content
	- open submenu
	- exit
- zastąpmy surowe TXT plikami markdown
	- albo lepiej, wspierajmy oba formaty, czemu by nie
- konfiguracja zaczyna się od ustawień tego submenu
	- title - nagłówek
	- description - opis
	- ~~on_beforeopen - komenda wykonana gdy to menu się otwiera~~ wstępnie olejmy eventowanie by uprościć pliki konfiguracyjne w naszym podstawowym mindsecie
- format plików konfiguracyjnych zależny od wyboru usera, lista wg. kolejności priorytetu implementacji:
	1. INI - klasycznie
	2. JSON - powszechnie używany
	3. YAML - zyskuje na popularności za czytelność
	4. TOML - by puścić oczko do społeczności wydawców z PyPi (python packages using pip)
- ustalmy, że domyślnie konfiguracja to plik z nazwą wg wzoru `.rattlesnake.*` z końcówką należącą do powyższych ERGO: `.rattlesnake.ini` lub `.rattlesnake.json` lub `.rattlesnake.yaml` lub `.rattlesnake.toml`
- c# otwiera nam drogę zabawy z powershellem, można spróbować integracji
	- najpierw CMDLET
	- potem jako moduł DLL
	- wątek zgodności użytych bibliotek jako moduł powershellowski
	- testy jaka jest różnica
		- jeśli formatka jest ważna to dodać tryb zgodności powershellowski
	- manifesty, instalatory, manuale etc. 
- przy starcie programu `PlaySound` 2sek fragment piosenki **King Gizzard & The Lizard Wizard - Rattlesnake** (https://youtu.be/Q-i1XZc8ZwA) zawierającego wypowiadane w piosence słowo "**Rattlesnake**"
- pakowanie uzbrojenia - jeśli widzi `.sss.zip` to zanim sprawdza istnienie plików konfiguracyjnych otwiera archiwum i traktuje je jakby było folderem **z wykluczeniem command exec** dla uproszczenia wszystkim życia
	- wątek innych formatów poza `zip`
	- użycie szyfrowanych archiwów `zip`
		- unikalne hasło zaszyte w kodzie programu
- z powodu że spectre jest takie fajne
	- tree view ścieżki
	- ładny REPL
	- input z buforem jako pamięć podręczną albo plik w TEMP, dostępne potem jako `%rattlesnake%` lub `$rattlesnake`
	- temat tabel w konsoli... feachery priorytetyzowane wg. kolejności
		1. csv
		2. sqlite
		3. sql database
		4. postgre
		5. plik excel
- funkcje sieciowe
	- port scan
	- LAN chat
	- konsolowy online canvas paint
	- zdalne sterowanie
- narzędzie do user-friendly tworzenia konfiguracji i prasowania do ZIP
- autoaktualizator
- 
