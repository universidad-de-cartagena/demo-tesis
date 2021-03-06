# Demo tesis

## Dependencias

- Docker
  - Debian 10.1
  - Python 3
  - pip y librerías
- docker-compose

```shell
docker-compose build
```

## Pruebas

```shell
nano docker-compose.yml
docker-compose -f docker-compose.test.yml run --rm backend
```

## Despliegue

```shell
nano docker-compose.yml
docker-compose up -d
```

## Referencias

- [1] [Guía de instalación de Django](https://docs.djangoproject.com/en/2.2/intro/install/).
- [2] [Conectores MySQL recomendados por Django](https://docs.djangoproject.com/en/2.2/ref/databases/#mysql-db-api-drivers) y [Dependencias del conector MySQL en Python](https://pypi.org/project/mysqlclient/).
- [3] [Script para esperar puertos](https://github.com/ufoscout/docker-compose-wait).
- [4] [Pruebas automáticas en Django](https://docs.djangoproject.com/en/2.2/topics/testing/)
- [5] [Coverage](https://coverage.readthedocs.io/en/v4.5.x/index.html)
