# Pysaml2 demo #

![saml diagram](https://user-images.githubusercontent.com/17281733/35592180-3e76fe96-05da-11e8-8089-154c565e21f3.png)

**basado en:** https://github.com/rohe/pysaml2, https://pysaml2.readthedocs.io/en/latest/install.html

**comandos:**

```bash
cd example
sh all.sh start
```

**Archivo de Configuracion del idp (cd example/idp2/idp_conf.py):**

Este archivo tiene todas las configuraciones del idp en variables. 
Las unicas variables que deben modificarse son las siguientes:

* url del servidor 
```python

HOST = 'localhost'
PORT = 8088

BASE = "http://%s:%s" % (HOST, PORT)
```

* certificado para encriptacion
```python
"key_file": full_path("pki/mykey.pem"),
"cert_file": full_path("pki/mycert.pem"),
```

* metadata del sp (sera proporcionado por WA)
```python
"metadata": {
        "local": [full_path("../sp-wsgi/sp.xml")],
    },
```

* informacion de la organizacion (opcional)
```python
"organization": {
        "display_name": "Rolands Identiteter",
        "name": "Rolands Identiteter",
        "url": "http://www.example.com",
    },
    "contact_person": [
        {
            "contact_type": "technical",
            "given_name": "Roland",
            "sur_name": "Hedberg",
            "email_address": "technical@example.com"
        }, {
            "contact_type": "support",
            "given_name": "Support",
            "email_address": "support@example.com"
        },
    ],
```


Una vez se realicen estos cambios se debera generar la metadata del idp 
```python
python tools/make_metadata.py example/idp2/idp_conf.py
```

**Demostracion**

![ezgif com-optimize](https://user-images.githubusercontent.com/17281733/35593282-72c60928-05dd-11e8-9b28-eb32e2e31abe.gif)


