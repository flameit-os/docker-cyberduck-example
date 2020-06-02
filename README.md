# CI/CD - Cyberduck CLI on Docker - Shoper.pl Example

Jak wdrożyć CI/CD szablonu w sklepie opartym o SaaS Shoper.pl

## Dokumentacja

Z powodu źle zaimplementowanej obsługi WebDAV na serwerach SaaS Shoper.pl musieliśmy troszkę nagimnastykować się aby w końcu ogarnąć integrację klienta konsolowego WebDAV (w tym przypadku Cyberduck) w Dockerze. Teraz możecie bez przeszkód uruchomić CI/CD dla szablonu sklepu.

Ten szkielet/przykład został przygotowany do obsługi na GitLabie. Jeżeli korzystasz z innych narzędzi nie będzie większych problemów aby przenieść to rozwiązanie do innego środowiska po analizie: [.gitlab-ci.yml ](.gitlab-ci.yml)

### Zmienne do ustawienia w projekcie:

```
DEV_WEBDAV_HOST
DEV_WEBDAV_PASS
DEV_WEBDAV_USER

PROD_WEBDAV_HOST = https://sklep.zielonafabryka.pl
PROD_WEBDAV_PASS
PROD_WEBDAV_USER
```

### Środowiska dla szablonu Shoper.pl

Dokąd wysyłane są szablony z branchy. Każdy szablon musi być wcześniej ręcznie utworzony w Shoperze! Nazwa musi się zgadzać z poniższymi:

* **Produkcyjne**: https://SHOP_URL/admin/configSkins/list

  * **master** --> Szablon o nazwie: **branch_master** - główny, produkcyjny szablon - **aktywny**
  * **staging** --> Szablon o nazwie: **branch_staging** - szablon wrzucony na produkcyjny serwer, niektywny (moliwość podglądu bez przełączania szablonów)

* **Testowym**: https://devshop-SHOP_URL/admin/configSkins/list

  * **dev** --> Szablon o nazwie: **branch_dev** - główny testowy szablon - **aktywny**
  * **BRANCH_NAME** --> Szablon o nazwie:  **branch_BRANCH_NAME** - 

### Shoper.pl

* Shoper.pl :: Theme Development: https://developers.shoper.pl/theme-development/index

### WebDAV

Do komunikacji z serwerami Shopera wykorzystywany jest protokół WebDAV.

Dokumentacja Shopera: https://www.shoper.pl/help/artykul/webdav/

**Co możemy zrobić ze strukturą szablonu:**

* pobierać i nadpisywać wszystkie widoczne pliki,
* dodawać/tworzyć pliki:
  * `js, less, sass, json, xml` do folderu `js`,
  * `less, sass, css` do folderu `styles`,
  * `gif, png, jpg, jpeg, ico, ttf, otf, woff, eot, swf, webp, webm` do folderu `images`,
* tworzyć podfoldery w `js, styles, images`,
* usuwać: `js, less, sass, json, xml, css, gif, png, jpg, jpeg, ico, ttf, otf, woff, eot, swf, webp, webm` z folderów `js, styles, images` (oprócz `main. css|js`).


## Autorzy

* Paweł 'felixd' Wojciechowski [Outsourcing IT - Konopnickiej.Com](https://www.konopnickiej.com)

# Copyright

© 2020 [Zielona Fabryka - dekoracje wnętrz i florystyka](https://sklep.zielonafabryka.pl)
