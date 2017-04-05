# Project lokaal zetten

- Repository clonen van beanstalk, bvb: git@statik.git.beanstalkapp.com:/statik/PROJECT.git
- `git flow init` (standaard branch = develop).
- `composer install`.
- CMS map clonen, in het geval dat het project al live staat: `content-prod`.

```sh
cd application/data

# content-dev
git clone git@statik.git.beanstalkapp.com:/statik/PROJECT.git --single-branch --branch=content-dev cms

# content-prod
git clone git@statik.git.beanstalkapp.com:/statik/PROJECT.git --single-branch --branch=content-prod cms
```

- Lokale parameters instellen.
	- In `application/config/dev/parameters.json`.
	- Voorbeeld van lokale parameters.

```json
{
	// ALTIJD een unieke eigen offset gebruiken
    "cms.widget.offset": 475,
    "database.connection.project": "mysql://root:root@127.0.0.1/PROJECT",
    "google.auth.redirect.uri": "http://PROJECT.local.statik.be/login/google",
    "system.image": "gd"
}
```

- Database lokaal zetten.
	- Staging of production parameters zijn te vinden in `application/config/<prod|stag>/parameters.json`.
	- De lokale database krijgt normaal gezien de naam van het project in kleine letters.

- Optioneel: images van staging of productie halen: `application/data/upload/*`.

- Setup commands runnen.

```sh
# Boss alias
alias cli="php application/cli.php"

cli og --debug # orm generate
cli od --debug # orm define
cli cc # cache clear
```
