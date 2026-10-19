<!--suppress HtmlUnknownAnchorTarget, HtmlDeprecatedAttribute -->
<div id="top"></div>

<div align="center">
  <a href="https://github.com/wlgdev/template-repository/actions/workflows/secrets-update.yml">
    <img src="https://github.com/wlgdev/template-repository/actions/workflows/secrets-update.yml/badge.svg" alt="status"/>
  </a>
</div>
<h1 align="center">
  URL SHORTENER
</h1>

<p align="center">
   https://cc.wlg.tv/ - allows to shorten long urls
</p>

<div align="center">
  📦 :octocat: 🩳
</div>
<div align="center">
  <img src="./docs/shortener.jpg" alt="description"/>
</div>

<!-- TABLE OF CONTENT -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#-description">📃 Description</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#-getting-started">🪧 Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li>
      <a href="#%EF%B8%8F-how-to-use">⚠️ How to use</a>
      <ul>
        <li><a href="#possible-exceptions">Possible Exceptions</a></li>
      </ul>
    </li>
    <li><a href="#%EF%B8%8F-deployment">⬆️ Deployment</a></li>
    <li><a href="#-reference">🔗 Reference</a></li>
  </ol>
</details>

<br>

## 📃 Description
This repository allows creating short links for the long URLs
the benefit to have it:
* all long urls can be shortened to be remembered
* the number of visits can be easily exported
* helpful to wrap some advertisements

MariaDB runs as the `db` Compose service. Shlink connects to `db:3306` using database `shortener` and user `shortener`.

<p align="right">(<a href="#top">back to top</a>)</p>

### Built With
* [shlink](https://shlink.io/)

## 🪧 Getting Started
to start just execute docker compose deployment

### Prerequisites
docker to be installed

### Installation
to start just execute docker compose deployment

<p align="right">(<a href="#top">back to top</a>)</p>

## ⚠️ How to use
Shlink login requires an API key. Set `INITIAL_API_KEY` in your local environment or `.env` file before starting Docker Compose.
For production deployments, add the GitHub Actions secret `SHORTENER_INITIAL_API_KEY`; the workflow passes it to Shlink as `INITIAL_API_KEY`.
Shlink creates this initial admin key at startup only when the database has no API keys. Existing keys remain valid; changing the secret does not rotate them.

To generate an additional key manually, run `docker compose exec shortener shlink api-key:generate`.

### Possible Exceptions
some errors, if any

<p align="right">(<a href="#top">back to top</a>)</p>

## ⬆️ Deployment
Run `deploy-prod` manually from GitHub Actions. The [production workflow](.github/workflows/publish-release.yml) uses the [shared deploy action](https://github.com/wlgdev/deploy) to deploy the existing Shlink image and configure `cc.wlg.tv`.

Add the GitHub Actions secret `DEPLOY_TRIGGER_PAT` with Actions read/write access to `wlgdev/deploy`. Add `DB_ROOT_PASSWORD` for MariaDB's root account and `DB_USER_PASSWORD` for the `shortener` database user. Shlink receives only `DB_USER_PASSWORD`. Keep `SHORTENER_INITIAL_API_KEY` and the `SHORTENER_GEOLITE_KEY` variable available to the `PRODUCTION` job. The former `SHORTENER_DB_*` secrets are no longer used.

Shlink and MariaDB share the Compose default network. Shlink explicitly retains that network when the shared action adds the server's existing `proxy-network`. Server SSH and Nginx Proxy Manager settings are managed in `wlgdev/deploy`.

For local Compose runs, also set `DB_ROOT_PASSWORD` and `DB_USER_PASSWORD` in your environment or `.env` file. MariaDB stores its `/config` directory in the project-scoped Docker volume `mariadb_data`, which persists across normal container recreation and redeployment. Keep the same Compose project name to reuse it, and do not run `docker compose down --volumes` unless you intend to delete the database. These passwords initialize a fresh database and do not rotate credentials in existing data.

If you already have database data in `./mariadb`, migrate it to the named volume with MariaDB stopped before redeploying. Changing the mount does not copy existing folder data; an empty volume initializes a fresh database.

Shlink is pulled directly from `shlinkio/shlink:5.1.7`, so no Bun build or image publishing is needed. The workflow supplies the image coordinates through `SERVICE_IMAGE_NAME` and `SERVICE_IMAGE_TAG`; set these variables for local Compose runs too.

<p align="right">(<a href="#top">back to top</a>)</p>

## 🔗 Reference
* [shlink](https://shlink.io/)

<p align="right">(<a href="#top">back to top</a>)</p>
