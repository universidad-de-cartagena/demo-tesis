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
docker-compose up --build -d
docker-compose exec backend coverage run --source '.' --omit 'env/*' manage.py test #[5]
docker-compose exec backend coverage report --show-missing
docker-compose exec backend coverage html -d reports/htmlcov/
docker-compose exec backend coverage xml -o reports/coverage.xml
docker-compose exec backend rm .coverage
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
