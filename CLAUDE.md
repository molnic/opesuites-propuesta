# CLAUDE.md

Repositorio de **propuestas comerciales** de Molu Studio para el cliente **OPE Suites** (Gabriela "Gaby" y su equipo). Son páginas HTML estáticas, autocontenidas, en español, que se comparten como links con el cliente.

## Páginas (cada `.html` es una propuesta independiente con su propia URL)

| Archivo | Propuesta | URL de producción |
|---|---|---|
| `index.html` | Transformación digital inicial (CRM + Web). Tema azul/indigo. | `https://opesuites-propuesta.vercel.app/` |
| `retainer.html` | Retainer mensual "Partner de Producto". Tema indigo + dorado. | `https://opesuites-propuesta.vercel.app/retainer.html` |
| `desarrollos-adicionales.html` | Catálogo de desarrollos adicionales por niveles (S/M/L/XL). Mismo diseño que `retainer.html`. | `https://opesuites-propuesta.vercel.app/desarrollos-adicionales.html` |
| `cotizacion-salto-ks.html` | Cotización del desarrollo **Integración Salto KS** (cerraduras digitales). Nivel L, $1.600.000 COP, 1-2 semanas. Reutiliza el catálogo (modelo + niveles) pero la sección "catálogo" se reemplaza por el detalle completo de esta cotización (qué incluye / no incluye / requisitos / cerraduras offline a revisar). Mismo diseño que `desarrollos-adicionales.html`. | `https://opesuites-propuesta.vercel.app/cotizacion-salto-ks.html` |

Agregar un nuevo `.html` crea una propuesta nueva sin afectar las demás; cada archivo se sirve en su propia ruta.

## Sistema de diseño

Dos generaciones de diseño conviven:
- **`index.html`** (más antiguo): Plus Jakarta Sans, acento azul (`#3B82F6`), glassmorphism oscuro.
- **`retainer.html` y `desarrollos-adicionales.html`** (actual, preferido): Space Grotesk (display) + Inter (body) + Fraunces (serif itálico para acentos), colores `ink #060810` / `accent #6366F1` / `gold #E8C27A`, fondo "mesh", clases utilitarias propias (`.glass`, `.glass-strong`, `.glass-gold`, `.tgw/.tgp/.tgg`, `.sa`, `.lbl`, `.rv` para scroll-reveal, `.hc`). **Para páginas nuevas, copiar el `<head>` + `<style>` + scripts de `retainer.html`.**

Stack: Tailwind vía CDN, Lucide icons (`lucide.createIcons()`), sin build step. Todo inline en un solo archivo.

Convenciones: textos en español; precios en COP con separador de miles por punto (`$1.500.000`); CTA a WhatsApp `https://wa.me/573112634779`; marca "Molu Studio × OPE Suites".

## Despliegue (Vercel + Git integration)

- Repo GitHub: `molnic/opesuites-propuesta` (remoto `origin`).
- Proyecto Vercel: `opesuites-propuesta` (team `molnics-projects`), **con git integration**.
- **Push a `main` → deploy automático a producción.** No hay que crear proyecto ni usar el CLI; el MCP `deploy_to_vercel` solo da instrucciones, no despliega.
- Dominio de producción estable: `opesuites-propuesta.vercel.app`.
- Verificar deploy: `curl -s <url> | grep <texto>` o el MCP de Vercel (`list_deployments`).
- Nota: pushear a `main` requiere autorización explícita del usuario cada vez (soft block del clasificador).

## Contexto comercial (catálogo de desarrollos adicionales)

- El proyecto tiene un **retainer de $400.000 COP/mes** que cubre solo operación/funcionamiento de la plataforma. Los **desarrollos nuevos** (fuera del alcance inicial) se cobran aparte con el catálogo.
- Modelo de cobro: **por niveles, no por hora.** S ($250–400k), M ($600–900k), L ($1.5–2M), XL (desde $3M). Pago **50% al iniciar / 50% a la entrega**.
- Ítems cotizados actuales: PDF de reserva (S, $350k), depósitos/pagos parciales (M, $800k), flujo No-Show (M, $800k), cambio de identidad a **"KAZA LIVING"** (XL, desde $3.2M — antes se manejó como "Casa con Z").
- **Integración Salto KS** (cerraduras digitales, nivel L, $1.6M): cotización dedicada en `cotizacion-salto-ks.html`. Genera/revoca PINs automáticamente al check-in/check-out vía la Connect API de Salto. Cubre 18 habitaciones (15 Calle 100 + 3 Usaquén). Depende de que Salto entregue credenciales de su API (correo enviado a `techsupport.cala@saltosystems.com`). El costo de la licencia/API de Salto lo paga OPE directo a Salto, no está incluido.
- Channel manager del cliente: **Channex** (el ítem de rebranding incluye reconfigurar sus endpoints).
