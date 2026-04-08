# Dealer Evaluation Frontend

Aplicación frontend para comparar precios de productos entre concesionarios. Este servicio consume dos APIs backend desplegadas en IBM Cloud Code Engine:

- `prodlist`: productos y concesionarios por producto.
- `dealerdetails`: precios por producto y concesionario.

## Tabla de contenidos

- [Descripción](#descripción)
- [Stack](#stack)
- [Estructura](#estructura)
- [Ejecución local](#ejecución-local)
- [Configuración de endpoints](#configuración-de-endpoints)
- [Despliegue en Code Engine](#despliegue-en-code-engine)
- [Verificación funcional](#verificación-funcional)
- [Documentación del proyecto](#documentación-del-proyecto)
- [Licencia](#licencia)

## Descripción

El objetivo del proyecto es ofrecer una UI sencilla para:

1. Seleccionar un producto.
2. Consultar los concesionarios que lo ofrecen.
3. Ver el precio para un concesionario específico o para todos.

## Stack

- Python 3
- Flask + Flask-CORS
- HTML + JavaScript (Axios)
- IBM Cloud Code Engine

## Estructura

- `app.py`: servidor Flask que expone `index.html`.
- `html/index.html`: interfaz y llamadas HTTP a los microservicios.
- `requirements.txt`: dependencias Python.
- `Dockerfile`: empaquetado para despliegue.
- `docs/ARCHITECTURE.md`: arquitectura y flujo de datos.

## Ejecución local

```bash
pip install -r requirements.txt
python app.py
```

Abrir `http://localhost:5001/`.

## Configuración de endpoints

En `html/index.html`, actualizar:

```javascript
let produrl = "https://prodlist.<subdomain>.us-south.codeengine.appdomain.cloud/"
let dealerurl = "https://dealerdetails.<subdomain>.us-south.codeengine.appdomain.cloud/"
```

Ambas URLs deben terminar en `/`.

## Despliegue en Code Engine

```bash
ibmcloud ce application create --name frontend --image us.icr.io/${SN_ICR_NAMESPACE}/frontend --registry-secret icr-secret --port 5001 --build-source .
```

Fallback de nombre si aparece `FAILED Wait failed for application 'frontend'`:

```bash
ibmcloud ce application create --name frontend1 --image us.icr.io/${SN_ICR_NAMESPACE}/frontend --registry-secret icr-secret --port 5001 --build-source .
```

## Verificación funcional

- Menú de productos poblado al cargar la página.
- Menú de concesionarios poblado al elegir producto.
- Precio mostrado al elegir concesionario.
- Tabla de precios al elegir `All Dealers`.

## Documentación del proyecto

- Guía de contribución: `CONTRIBUTING.md`
- Código de conducta: `CODE_OF_CONDUCT.md`
- Política de seguridad: `SECURITY.md`
- Uso responsable: `RESPONSIBLE_USE.md`
- Historial de cambios: `CHANGELOG.md`

## Licencia

Este proyecto se distribuye bajo licencia Apache 2.0. Ver `LICENSE`.