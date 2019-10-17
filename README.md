# Demo tesis

## Dependencias

- Debian 10.1
- Python 3
- pip y librerías

```shell
apt-get update -y
apt-get install python3.7 python3-pip -y
apt-get install python3.7-dev default-libmysqlclient-dev -y # [2]
pip install -r requirements.txt
```

## Despliegue

```shell
cp ejemploPython/.env.sample ejemploPython/.env
nano ejemploPython/.env
python manage.py migrate --no-input
python manage.py runserver 0.0.0.0:8080
```

## Referencias

[1] [Guía de instalación de Django](https://docs.djangoproject.com/en/2.2/intro/install/).
[2] [Conectores MySQL recomendados por Django](https://docs.djangoproject.com/en/2.2/ref/databases/#mysql-db-api-drivers) y [Dependencias del conector MySQL en Python](https://pypi.org/project/mysqlclient/).
