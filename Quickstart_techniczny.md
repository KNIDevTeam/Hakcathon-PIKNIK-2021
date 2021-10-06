# Instrukcja uruchomienia KNotes (quickstart)

## 1. Załóż konto na GitHub

https://github.com/join

## 2. Zainstaluj Git
https://git-scm.com/download/

Uruchom installer i przejdź przez proces instalacji, nie zmieniając żadnych zaznaczeń. Opcje domyślne powinny być wystarczające dla typowego użytkownika.

Następnie uruchom swoją ulubioną powłokę (cmd, powershell, git bash) i dokończ konfigurację gita:

```
git config --global user.name "Twoje Imie i Nazwisko lub Nickname"
git config --global user.email "Twoj adres email"
```

Opcjonalnie, możesz zainstalować interfejs graficzny do gita. Osobiście polecam Sourcetree:

https://www.sourcetreeapp.com/
    
## 3. Zainstaluj Node.js
https://nodejs.org/

Na powyższej stronie wybierz wersję LTS. W momencie pisania tego artykułu jest to wersja 14.17.5 i jest ona dostępna pod linkiem: https://nodejs.org/dist/v14.17.5/node-v14.17.5-x86.msi

Uruchom installer i przejdź przez proces instalacji, nie zmieniając żadnych zaznaczeń.
    
## 4a. Zainstaluj MongoDB lokalnie
https://www.mongodb.com/try/download/community

![](https://i.imgur.com/MfI10gP.png)

Na powyższej stronie wybierz wersję 5.0.2, w momencie pisania tego artykułu jest ona dostępna pod linkiem: https://fastdl.mongodb.org/windows/mongodb-windows-x86_64-5.0.2-signed.msi

https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/

Przed uruchomieniem installera utwórz folder C:/data/db
Będzie tam przechowywana Twoja baza danych.

Uruchom installer i na kolejnych stronach wybierz:
- Complete (all programs features will be installed)
- Install MongoD as a Service, resztę pól na tej stronie pozostaw domyślnie
- Install MongoDB Compass (interfejs graficzny do zarządzania bazami danych)

## 4b. Użyj instancji MongoDB w chmurze za darmo
Jeżeli nie chcesz instalować MongoDB lokalnie, możesz użyć darmowej instancji w MongoDB Atlas (https://www.mongodb.com/cloud/atlas)

Instrukcja video: https://www.youtube.com/watch?v=rPqRyYJmx2g


## 5. Sforkuj repozytorium
Po zalogowaniu się na nowo utworzone konto GitHub przejdź na stronę repozytorium KNOtes:
https://github.com/KNIDevTeam/knotes

Aby móc pracować na własnej kopii repozytorium, musisz je najpierw sforkować.
https://docs.github.com/en/get-started/quickstart/fork-a-repo

Najpierw, na stronie repozytorium, w prawym górnym rogu naciśnij przycisk Fork.
![](https://i.imgur.com/pxEkJ7W.png)
Po chwili zostaniesz przekierowany do swojej strony z kopią repozytorium KNotes.

Jeżeli pracujesz w zespole, dodaj członków zespołu do repozytorium:
https://docs.github.com/en/github/setting-up-and-managing-your-github-user-account/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository

Przejdź do ustawień nowoutworzonego repozytorium
![](https://i.imgur.com/IhAaZaj.png)

Przejdź do zakładki Manage access
![](https://i.imgur.com/u0v9Bel.png)

Naciśnij invite a collaborator.
![](https://i.imgur.com/7Pg8og2.png)

W polu wyszukiwania wpisz nickname na GitHub innego członka zespołu.
![](https://i.imgur.com/QBMWNdH.png)

Naciśnij dodaj *** do ***
![](https://i.imgur.com/rbduaUg.png)

Osoba zaproszona otrzyma maila, w którym musi potwierdzić zaproszenie!
Po zakończeniu procesu osoba ta będzie miała uprawnienia zapisu w Twoim repozytorium.

## 6. Sklonuj utworzone repozytorium
https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository-from-github/cloning-a-repository

Teraz potrzebujesz skopiować repozytorium na swój komputer, aby móc zacząć na nim pracę.
Przejdź na stronę repozytorium i naciśnij "Clone":
![](https://i.imgur.com/MgfX3U8.png)

Następnie wybierz "Clone with HTTPS" i skopiuj podany URL
![](https://i.imgur.com/3rlCW2J.png)

Otwórz Git bash w miejscu, gdzie chcesz umieścić repozytorium i uruchom komendę:

```
git clone <wklej skopiowany URL tutaj>
```

W danym katalogu powinien pojawić się kolejny katalog "knotes", zawierający kod repozytorium.
    
## 7. Zainstaluj IDE/edytor

Aby móc efektywnie pracować na kodzie aplikacji potrzebujesz jakiegoś edytora lub IDE. Osobiście, do prostych projektów polecam VS Code, ponieważ jest lekki i darmowy. Oczywiście, możesz pracować w czym chcesz.

https://code.visualstudio.com/

Po instalacji VS Code przejdź do plik->otwórz folder i wybierz folder repozytorium. Jeżeli pojawią Ci się komunikaty o wtyczkach rekomendowanych do instalacji - zrób to. 

## 8. Skonfiguruj bazę danych

Przejdź do folderu ze sklonowanym repozytorium i zduplikuj plik ".env.template" nazywając go ".env". Jeżeli Windows Ci na to nie pozwoli, będziesz musiał użyć Git bash. W tym celu uruchom git bash w folderze repozytorium (shift + prawy przycisk myszy -> open git bash here) oraz wpisz poniższą komendę:

```
cp .env.template .env
```

Otwórz nowy plik .env i zamień w nim wartości (po prawej stronie znaku =) poniższych właściwości:
- `KNOTES_MONGO_URL`:

a) Jeżeli zainstalowałeś MongoDB lokalnie, wpisz tutaj: `mongodb://localhost:27017/knotes`

b) Jeżeli zainstalowałeś MongoDB na Atlas, dostaniesz swój URL po wybraniu "Connect" a następnie "Connect your application"
![](https://i.imgur.com/BJKZo1c.png)
![](https://i.imgur.com/S0WjBBS.png)
![](https://i.imgur.com/aCzwrRT.png)

https://studio3t.com/knowledge-base/articles/connect-to-mongodb-atlas/

- `KNOTES_SECRET`:
Losowy ciąg znaków, używany do podpisywania ciasteczek sesji. Możesz go wygenerować np. na tej stronie: https://www.uuidgenerator.net/


## 9. Uruchom KNotes
Przejdź do folderu zawierającego pliki sklonowanego wcześniej repozytorium i wykonaj w terminalu (np. cmd, powershell, git bash):

```shell
npm install
npm run dev
```

Aplikacja powinna być dostępna pod adresem: http://localhost:8080/

## Materiały dodatkowe:
- https://learngitbranching.js.org/ - kurs gita
- https://lab.github.com/githubtraining/first-day-on-github - podstawowy kurs GitHuba
- https://lab.github.com/githubtraining/first-week-on-github - rozszerzony kurs GitHuba
