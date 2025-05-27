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

it has a parallel running container: mariadb
* container host name: `clo0i9fui005krw9s39n760if`

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
to be able to login it requires access code to be generated from inside of docker container\
command: `docker exec -t container_name shlink api-key:generate`

### Possible Exceptions
some errors, if any

<p align="right">(<a href="#top">back to top</a>)</p>

## ⬆️ Deployment
run the deployment workflow in GitHub actions

<p align="right">(<a href="#top">back to top</a>)</p>

## 🔗 Reference
* [shlink](https://shlink.io/)

<p align="right">(<a href="#top">back to top</a>)</p>