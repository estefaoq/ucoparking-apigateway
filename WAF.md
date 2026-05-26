# WAF - UCO Parking

En produccion, delante de Kong se desplegaria un **Web Application Firewall** (por ejemplo AWS WAF, Cloudflare WAF o ModSecurity) para filtrar trafico malicioso antes de llegar al API Gateway.

## Demo local (capa basica)

En `uco-parking-apigateway/kong/kong.yml` esta activo el plugin **rate-limiting** de Kong:

- Limite: **120 peticiones por minuto** por cliente
- Protege contra abuso basico y fuerza bruta
- Complementa CORS ya configurado en el mismo gateway

## Capas de seguridad del proyecto

| Capa | Tecnologia | Funcion |
|------|------------|---------|
| WAF (prod) | AWS WAF / Cloudflare | Filtrar SQLi, XSS, bots |
| API Gateway | Kong 3.9 | Enrutamiento, CORS, rate limit |
| Autorizacion | Auth0 JWT | Validar tokens OAuth2 |
| Secretos | Infisical | Credenciales fuera del codigo |

Para la entrega academica: demostrar Kong con rate-limiting y documentar que en produccion se anadiria un WAF comercial delante de Kong.
