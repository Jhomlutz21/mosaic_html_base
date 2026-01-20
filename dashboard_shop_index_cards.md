# Dashboard Shop Index - propuesta de contenido (trader)

## Objetivo
Proponer contenido para cada card de `dashboard_shop_index.html` usando la data de `database_model_reference.md`, enfocado en ventas, fidelizacion y adquisicion para el trader.

## Fuente de datos
- `expert_advisors`, `licenses`, `broker_account_daily_results`, `expert_advisor_bundles`
- `courses`, `course_modules`, `course_lessons`, `course_enrollments`, `course_lesson_progresses`, `course_plan_entitlements`
- `billing_plans`, `billing_plan_entitlements`, `addons`
- `pay_charges`, `pay_subscriptions`
- `refer_visits`, `refer_referrals` (adquisicion)

## Indice
- Elementos globales
  - Page header
  - Search form
  - Filters
- Cards 1 (Video Courses)
  - Card 1: Curso mas vendido
  - Card 2: Curso con mayor finalizacion
  - Card 3: Curso mas reciente
  - Card 4: Curso recomendado para ti
- Cards 2 (Digital Goods)
  - Card 1: Expert Advisor mas usado
  - Card 2: Expert Advisor con mejor PnL 30d
  - Card 3: Herramienta/EA nuevo
  - Card 4: Expert Advisor con mejor retencion
- Cards 3 (Online Events)
  - Card 1: Sesion premium mas vendida
  - Card 2: Sesion con inicio mas cercano
  - Card 3: Curso premium destacado
  - Card 4: Addon promocional
- Cards 5 (Popular Categories)
  - Card 1: Expert Advisors (robots)
  - Card 2: Herramientas (EA tools)
  - Card 3: Cursos por categoria top
  - Card 4: Addons y bundles
- Cards 6 (Trending Now)
  - Card 1: EA con mas ventas recientes
  - Card 2: Curso con mas inscripciones nuevas
  - Card 3: Addon con mejor conversion
  - Card 4: Plan mas elegido

## Elementos globales

### Page header
Nombre HTML (comentario): <!-- Page header -->
Seccion HTML (comentario): N/A
Titulo sugerido: Encuentra el producto ideal para tu trading
Objetivo: adquisicion
Tipo: elemento global
Contenido sugerido:
- Titulo principal orientado a descubrimiento de productos.
CTA sugerido: N/A
Datos base: N/A

### Search form
Nombre HTML (comentario): <!-- Search form -->
Seccion HTML (comentario): N/A
Titulo sugerido: Buscar productos
Objetivo: adquisicion
Tipo: elemento global
Contenido sugerido:
- Placeholder: "Buscar Expert Advisors, cursos, addons o planes".
- Alcance: nombre de EA, titulo de curso, nombre de plan, key de addon.
CTA sugerido: Buscar
Datos base: `expert_advisors.name`, `courses.title_es`, `billing_plans.name`, `addons.key`

### Filters
Nombre HTML (comentario): <!-- Filters -->
Seccion HTML (comentario): N/A
Titulo sugerido: Filtros de catalogo
Objetivo: adquisicion
Tipo: elemento global
Contenido sugerido:
- Tabs: Ver todo, Cursos, Expert Advisors, Lanzamientos.
CTA sugerido: N/A
Datos base:
- Cursos -> `courses`
- Expert Advisors -> `expert_advisors`
- Lanzamientos -> `courses.published_at` y/o novedades de EA

## Cards 1 (Video Courses)

### Card 1
Nombre HTML (comentario): <!-- Card 1 -->
Seccion HTML (comentario): <!-- Cards 1 (Video Courses) -->
Titulo sugerido: Curso mas vendido
Objetivo: ventas
Tipo: producto curso
Contenido sugerido:
- Curso top por ingresos (ventas recientes).
- Rating basado en completados y enrollments.
- Precio desde plan o addon mas barato.
- Features: duracion total, # lecciones, # modulos, categoria.
CTA sugerido: Comprar curso
Datos base: `courses`, `course_enrollments`, `course_lesson_progresses`, `course_lessons`, `course_plan_entitlements`, `billing_plans`, `addons`, `pay_charges`

### Card 2
Nombre HTML (comentario): <!-- Card 2 -->
Seccion HTML (comentario): <!-- Cards 1 (Video Courses) -->
Titulo sugerido: Curso con mayor finalizacion
Objetivo: fidelizacion
Tipo: producto curso
Contenido sugerido:
- Curso con % de finalizacion mas alto.
- Mostrar avance promedio y tiempo estimado.
- Precio y rating como en el card 1.
CTA sugerido: Ver curso
Datos base: `courses`, `course_enrollments`, `course_lesson_progresses`, `course_lessons`, `course_plan_entitlements`, `billing_plans`

### Card 3
Nombre HTML (comentario): <!-- Card 3 -->
Seccion HTML (comentario): <!-- Cards 1 (Video Courses) -->
Titulo sugerido: Curso mas reciente
Objetivo: adquisicion
Tipo: producto curso
Contenido sugerido:
- Curso publicado recientemente (por `published_at`).
- Rating inicial basado en inscripciones tempranas.
- Precio desde el plan disponible.
CTA sugerido: Explorar curso
Datos base: `courses.published_at`, `course_enrollments`, `course_plan_entitlements`, `billing_plans`

### Card 4
Nombre HTML (comentario): <!-- Card 4 -->
Seccion HTML (comentario): <!-- Cards 1 (Video Courses) -->
Titulo sugerido: Recomendado para ti
Objetivo: fidelizacion
Tipo: producto curso
Contenido sugerido:
- Curso recomendado segun progreso actual (similar categoria o nivel).
- Mostrar % de avance si ya esta enrolado.
- Precio si no esta incluido en su plan.
CTA sugerido: Continuar curso / Ver curso
Datos base: `course_enrollments`, `courses.category`, `course_lesson_progresses`, `course_plan_entitlements`, `billing_plans`

## Cards 2 (Digital Goods)

### Card 1
Nombre HTML (comentario): <!-- Card 1 -->
Seccion HTML (comentario): <!-- Cards 2 (Digital Goods) -->
Titulo sugerido: Expert Advisor mas usado
Objetivo: ventas
Tipo: producto EA
Contenido sugerido:
- EA con mas licencias activas.
- Badge "Popular" si supera umbral.
- Precio desde plan o addon.
CTA sugerido: Comprar EA
Datos base: `expert_advisors`, `licenses`, `billing_plan_entitlements`, `billing_plans`, `addons`

### Card 2
Nombre HTML (comentario): <!-- Card 2 -->
Seccion HTML (comentario): <!-- Cards 2 (Digital Goods) -->
Titulo sugerido: Expert Advisor con mejor PnL 30d
Objetivo: ventas
Tipo: producto EA
Contenido sugerido:
- EA con mejor PnL medio 30d en cuentas activas.
- Rating basado en rendimiento y uso.
- Precio desde plan o addon.
CTA sugerido: Ver rendimiento
Datos base: `expert_advisors`, `broker_account_daily_results`, `licenses`, `billing_plan_entitlements`, `billing_plans`

### Card 3
Nombre HTML (comentario): <!-- Card 3 -->
Seccion HTML (comentario): <!-- Cards 2 (Digital Goods) -->
Titulo sugerido: Herramienta/EA nuevo
Objetivo: adquisicion
Tipo: producto EA
Contenido sugerido:
- EA o tool recientemente agregado.
- Mostrar beneficios clave del `description`.
- Precio desde plan o addon.
CTA sugerido: Explorar EA
Datos base: `expert_advisors`, `billing_plan_entitlements`, `billing_plans`, `addons`

### Card 4
Nombre HTML (comentario): <!-- Card 4 -->
Seccion HTML (comentario): <!-- Cards 2 (Digital Goods) -->
Titulo sugerido: Expert Advisor con mejor retencion
Objetivo: fidelizacion
Tipo: producto EA
Contenido sugerido:
- EA con mayor % de renovaciones (suscripciones activas y renovadas).
- Rating basado en retencion.
- Precio desde plan o addon.
CTA sugerido: Ver EA
Datos base: `expert_advisors`, `pay_subscriptions`, `pay_charges`, `licenses`, `billing_plan_entitlements`, `billing_plans`

## Cards 3 (Online Events)

### Card 1
Nombre HTML (comentario): <!-- Card 1 -->
Seccion HTML (comentario): <!-- Cards 3 (Online Events) -->
Titulo sugerido: Sesion premium mas vendida
Objetivo: ventas
Tipo: producto one_time
Contenido sugerido:
- Plan one_time con mas ventas recientes.
- Precio y cupos desde metadata si existe.
CTA sugerido: Comprar acceso
Datos base: `billing_plans` (kind one_time), `pay_charges`, `billing_plans.metadata`

### Card 2
Nombre HTML (comentario): <!-- Card 2 -->
Seccion HTML (comentario): <!-- Cards 3 (Online Events) -->
Titulo sugerido: Sesion con inicio mas cercano
Objetivo: adquisicion
Tipo: producto one_time
Contenido sugerido:
- Proxima sesion (fecha desde `billing_plans.metadata`).
- Precio y horario destacado.
CTA sugerido: Reservar cupo
Datos base: `billing_plans` (kind one_time), `billing_plans.metadata`

### Card 3
Nombre HTML (comentario): <!-- Card 3 -->
Seccion HTML (comentario): <!-- Cards 3 (Online Events) -->
Titulo sugerido: Curso premium destacado
Objetivo: fidelizacion
Tipo: producto curso
Contenido sugerido:
- Curso premium con alto engagement.
- Fecha destacada: publicado recientemente.
CTA sugerido: Ver curso premium
Datos base: `courses`, `course_lesson_progresses`, `courses.published_at`

### Card 4
Nombre HTML (comentario): <!-- Card 4 -->
Seccion HTML (comentario): <!-- Cards 3 (Online Events) -->
Titulo sugerido: Addon promocional
Objetivo: ventas
Tipo: producto addon
Contenido sugerido:
- Addon destacado con mejor conversion.
- Precio promocional si aplica.
CTA sugerido: Comprar addon
Datos base: `addons`, `billing_plans`, `pay_charges`

## Cards 5 (Popular Categories)

### Card 1
Nombre HTML (comentario): <!-- Card 1 -->
Seccion HTML (comentario): <!-- Cards 5 (Popular Categories) -->
Titulo sugerido: Expert Advisors (robots)
Objetivo: adquisicion
Tipo: categoria
Contenido sugerido:
- Categoria de EAs tipo robot.
CTA sugerido: Explorar
Datos base: `expert_advisors.ea_type` (ea_robot)

### Card 2
Nombre HTML (comentario): <!-- Card 2 -->
Seccion HTML (comentario): <!-- Cards 5 (Popular Categories) -->
Titulo sugerido: Herramientas (EA tools)
Objetivo: adquisicion
Tipo: categoria
Contenido sugerido:
- Categoria de EAs tipo tool.
CTA sugerido: Explorar
Datos base: `expert_advisors.ea_type` (ea_tool)

### Card 3
Nombre HTML (comentario): <!-- Card 3 -->
Seccion HTML (comentario): <!-- Cards 5 (Popular Categories) -->
Titulo sugerido: Cursos por categoria top
Objetivo: adquisicion
Tipo: categoria
Contenido sugerido:
- Categoria con mas cursos activos o mas inscripciones.
CTA sugerido: Explorar
Datos base: `courses.category`, `course_enrollments`

### Card 4
Nombre HTML (comentario): <!-- Card 4 -->
Seccion HTML (comentario): <!-- Cards 5 (Popular Categories) -->
Titulo sugerido: Addons y bundles
Objetivo: adquisicion
Tipo: categoria
Contenido sugerido:
- Categoria para addons y bundles de EA.
CTA sugerido: Explorar
Datos base: `addons`, `expert_advisor_bundles`

## Cards 6 (Trending Now)

### Card 1
Nombre HTML (comentario): <!-- Card 1 -->
Seccion HTML (comentario): <!-- Cards 6 (Trending Now) -->
Titulo sugerido: EA con mas ventas recientes
Objetivo: ventas
Tipo: tendencia producto
Contenido sugerido:
- EA con mayor cantidad de compras recientes.
CTA sugerido: Ver EA
Datos base: `pay_charges`, `billing_plan_entitlements`, `expert_advisors`

### Card 2
Nombre HTML (comentario): <!-- Card 2 -->
Seccion HTML (comentario): <!-- Cards 6 (Trending Now) -->
Titulo sugerido: Curso con mas inscripciones nuevas
Objetivo: adquisicion
Tipo: tendencia producto
Contenido sugerido:
- Curso con mayor crecimiento de inscripciones recientes.
CTA sugerido: Ver curso
Datos base: `course_enrollments`, `courses`

### Card 3
Nombre HTML (comentario): <!-- Card 3 -->
Seccion HTML (comentario): <!-- Cards 6 (Trending Now) -->
Titulo sugerido: Addon con mejor conversion
Objetivo: ventas
Tipo: tendencia producto
Contenido sugerido:
- Addon con mejor conversion a compra.
CTA sugerido: Ver addon
Datos base: `addons`, `pay_charges`, `billing_plans`

### Card 4
Nombre HTML (comentario): <!-- Card 4 -->
Seccion HTML (comentario): <!-- Cards 6 (Trending Now) -->
Titulo sugerido: Plan mas elegido
Objetivo: fidelizacion
Tipo: tendencia plan
Contenido sugerido:
- Plan con mas suscripciones activas.
CTA sugerido: Ver plan
Datos base: `billing_plans`, `pay_subscriptions`
