# Arquitectura

## Componentes

- **Frontend**: aplicación Flask que sirve `html/index.html`.
- **Backend 1 (`prodlist`)**: lista de productos y concesionarios.
- **Backend 2 (`dealerdetails`)**: precios por producto/concesionario.

## Flujo principal

1. El usuario abre la UI.
2. La UI consulta `produrl + "products"` para poblar productos.
3. Al seleccionar producto, consulta `produrl + "getdealers/<producto>"`.
4. Al seleccionar concesionario:
   - `dealerurl + "price/<dealer>/<producto>"` o
   - `dealerurl + "allprice/<producto>"` para todos.

## Consideraciones técnicas

- La UI depende de CORS habilitado en servicios backend.
- Las URLs de backend deben configurarse en `html/index.html`.
- El frontend se expone por defecto en puerto `5001`.
