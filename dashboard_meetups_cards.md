# Dashboard Meetups - propuesta de contenido (trader)

## Objetivo
Proponer contenido para cada card y elemento global de `dashboard_meetups.html` usando la data de `database_model_reference.md`, enfocado en el trader.

## Fuente de datos
- `expert_advisors`, `expert_advisor_bundles`, `licenses`, `broker_account_daily_results`
- `billing_plans`, `billing_plan_entitlements`, `addons`
- `pay_charges`, `pay_subscriptions`

## Indice
- Elementos globales
  - Page header
  - Search form
  - Add meetup button
  - Filters
  - Total meetups
  - Pagination
- Cards (Meetups)
  - Item 1: Sniper Advanced Panel - Top ventas
  - Item 2: Pandora Box EA - Mas usado
  - Item 3: EA con mejor PnL 30d
  - Item 4: EA con mejor retencion
  - Item 5: EA nuevo destacado
  - Item 6: EA recomendado por tu uso
  - Item 7: EA con mejor desempeno en tu broker
  - Item 8: EA en trial mas activado

## Elementos globales

### Page header
Nombre HTML (comentario): <!-- Page header -->
Seccion HTML (comentario): N/A
Titulo sugerido: Descubre sesiones de Expert Advisors
Objetivo: adquisicion
Tipo: elemento global
Contenido sugerido:
- Titulo principal orientado a sesiones por EA.
CTA sugerido: N/A
Datos base: N/A

### Search form
Nombre HTML (comentario): <!-- Search form -->
Seccion HTML (comentario): <!-- Right: Actions -->
Titulo sugerido: Buscar Expert Advisors
Objetivo: adquisicion
Tipo: elemento global
Contenido sugerido:
- Placeholder: "Buscar Expert Advisors por nombre o tipo".
- Alcance: `expert_advisors.name`, `expert_advisors.ea_type`.
CTA sugerido: Buscar
Datos base: `expert_advisors`

### Add meetup button
Nombre HTML (comentario): <!-- Add meetup button -->
Seccion HTML (comentario): <!-- Right: Actions -->
Titulo sugerido: Solicitar sesion de EA
Objetivo: fidelizacion
Tipo: elemento global
Contenido sugerido:
- CTA para solicitar workshop de configuracion de EA.
CTA sugerido: Solicitar sesion
Datos base: N/A (requiere flujo de solicitud si aplica)

### Filters
Nombre HTML (comentario): <!-- Filters -->
Seccion HTML (comentario): N/A
Titulo sugerido: Filtros de sesiones por EA
Objetivo: adquisicion
Tipo: elemento global
Contenido sugerido:
- Tabs: Ver todo, Online, Local, Esta semana, Este mes, Siguiendo.
- Siguiendo: EAs con licencias activas del usuario.
CTA sugerido: N/A
Datos base: `licenses`, `expert_advisors`

### Total meetups
Nombre HTML (comentario): N/A (texto bajo filtros)
Seccion HTML (comentario): N/A
Titulo sugerido: Total de sesiones de EA
Objetivo: adquisicion
Tipo: elemento global
Contenido sugerido:
- Conteo de sesiones disponibles por EA.
CTA sugerido: N/A
Datos base: `expert_advisors` + sesiones en metadata de planes

### Pagination
Nombre HTML (comentario): <!-- Pagination -->
Seccion HTML (comentario): N/A
Titulo sugerido: Paginacion de sesiones
Objetivo: adquisicion
Tipo: elemento global
Contenido sugerido:
- Navegacion por paginas de sesiones.
CTA sugerido: N/A
Datos base: N/A

## Cards (Meetups)

### Item 1
Nombre HTML (comentario): <!-- Item 1 -->
Seccion HTML (comentario): <!-- Content -->
Titulo sugerido: Sniper Advanced Panel - Sesion de mejores resultados
Objetivo: ventas
Tipo: sesion EA
Contenido sugerido:
- Fecha: desde metadata del plan one_time del EA.
- Titulo: Sniper Advanced Panel - top ventas.
- Descripcion: configuracion ganadora y ajustes recomendados.
- Tag: Online Event.
- Avatares: usuarios con licencias activas de este EA.
CTA sugerido: Reservar cupo
Datos base: `expert_advisors.name`, `pay_charges`, `licenses`, `billing_plans.metadata`

### Item 2
Nombre HTML (comentario): <!-- Item 2 -->
Seccion HTML (comentario): <!-- Content -->
Titulo sugerido: Pandora Box EA - Sesion para usuarios activos
Objetivo: ventas
Tipo: sesion EA
Contenido sugerido:
- Fecha: proxima sesion del EA mas usado.
- Titulo: Pandora Box EA - configuracion avanzada.
- Descripcion: mejores practicas para cuentas activas.
- Tag: Online Event.
- Avatares: usuarios con licencias activas de este EA.
CTA sugerido: Unirme
Datos base: `expert_advisors.name`, `licenses`, `billing_plans.metadata`

### Item 3
Nombre HTML (comentario): <!-- Item 3 -->
Seccion HTML (comentario): <!-- Content -->
Titulo sugerido: EA con mejor PnL 30d - Taller de performance
Objetivo: ventas
Tipo: sesion EA
Contenido sugerido:
- Fecha: segun agenda del EA con mejor PnL.
- Titulo: taller del EA top por PnL 30d.
- Descripcion: parametros clave para mejorar rendimiento.
- Tag: Online Event.
- Avatares: usuarios con PnL positivo reciente.
CTA sugerido: Reservar cupo
Datos base: `expert_advisors`, `broker_account_daily_results`, `licenses`, `billing_plans.metadata`

### Item 4
Nombre HTML (comentario): <!-- Item 4 -->
Seccion HTML (comentario): <!-- Content -->
Titulo sugerido: EA con mejor retencion - Sesion de continuidad
Objetivo: fidelizacion
Tipo: sesion EA
Contenido sugerido:
- Fecha: proxima sesion de retencion.
- Titulo: EA con mayor renovacion.
- Descripcion: como mantener resultados estables.
- Tag: Online Event.
- Avatares: usuarios con suscripcion activa del EA.
CTA sugerido: Participar
Datos base: `expert_advisors`, `pay_subscriptions`, `pay_charges`, `licenses`, `billing_plans.metadata`

### Item 5
Nombre HTML (comentario): <!-- Item 5 -->
Seccion HTML (comentario): <!-- Content -->
Titulo sugerido: EA nuevo destacado - Sesion de lanzamiento
Objetivo: adquisicion
Tipo: sesion EA
Contenido sugerido:
- Fecha: lanzamiento del EA nuevo.
- Titulo: nuevo EA y casos de uso.
- Descripcion: overview y compatibilidad de brokers.
- Tag: Online Event.
- Avatares: early adopters del EA.
CTA sugerido: Ver lanzamiento
Datos base: `expert_advisors`, `billing_plans.metadata`, `licenses`

### Item 6
Nombre HTML (comentario): <!-- Item 6 -->
Seccion HTML (comentario): <!-- Content -->
Titulo sugerido: EA recomendado por tu uso - Sesion guiada
Objetivo: fidelizacion
Tipo: sesion EA
Contenido sugerido:
- Fecha: sesion para EAs similares a los que ya usas.
- Titulo: EA recomendado segun tu historial.
- Descripcion: mejoras frente al EA actual.
- Tag: Online Event.
- Avatares: usuarios con licencias similares.
CTA sugerido: Ver sesion
Datos base: `licenses`, `expert_advisors`, `billing_plans.metadata`

### Item 7
Nombre HTML (comentario): <!-- Item 7 -->
Seccion HTML (comentario): <!-- Content -->
Titulo sugerido: EA top en tu broker - Sesion por broker
Objetivo: ventas
Tipo: sesion EA
Contenido sugerido:
- Fecha: sesion enfocada en broker principal del usuario.
- Titulo: EA con mejor rendimiento en tu broker.
- Descripcion: ajustes por tipo de cuenta.
- Tag: Online Event.
- Avatares: usuarios con cuentas activas en ese broker.
CTA sugerido: Reservar cupo
Datos base: `broker_accounts.company`, `broker_account_daily_results`, `expert_advisors`, `licenses`, `billing_plans.metadata`

### Item 8
Nombre HTML (comentario): <!-- Item 8 -->
Seccion HTML (comentario): <!-- Content -->
Titulo sugerido: EA en trial mas activado - Sesion de activacion
Objetivo: adquisicion
Tipo: sesion EA
Contenido sugerido:
- Fecha: sesion para trials activos.
- Titulo: EA con mayor cantidad de trials.
- Descripcion: como activar y validar el EA.
- Tag: Online Event.
- Avatares: usuarios con `licenses.status=trial`.
CTA sugerido: Unirme
Datos base: `expert_advisors`, `licenses`, `billing_plans.metadata`

