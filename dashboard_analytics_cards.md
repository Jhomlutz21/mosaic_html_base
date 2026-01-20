# Dashboard Analytics - plan de cards para trader

## Objetivo
Definir informacion util para el trader final en cada card del dashboard de analytics y ordenar por prioridad (arriba -> abajo).

## Supuestos base
- Audiencia: trader final.
- Ventana por defecto: ultimos 30 dias, con comparacion vs 30 dias previos.
- Atajos: 7 y 90 dias.
- Zona horaria: `users.time_zone` si existe; si no, UTC.
- Moneda: `pay_charges.currency` o preferencia del usuario.
- Estado sin datos: mostrar "Sin datos suficientes" y ocultar comparativas.
- Balance: 60% EA/trading, 40% cursos.
- Cursos: metricas solo del usuario actual (no global).

## Prioridad y orden sugerido (arriba -> abajo)
1. Rendimiento diario (Line chart - Analytics) [EA]
2. EAs activos ahora (Line chart - Active Users Right Now) [EA]
3. Resultados por EA (Stacked bar - Acquisition Channels) [EA]
4. Top cursos por avance (Horizontal bar - Audience Overview) [Cursos]
5. Top EAs por ganancia (Report card - Top Channels) [EA]
6. Ultimas lecciones vistas (Report card - Top Pages) [Cursos]
7. Licencias por vencer (Report card - Top Countries) [EA]
8. Estado de cursos (Doughnut - Sessions By Device) [Cursos]
9. Tiempo de estudio por categoria (Doughnut - Visit By Age Category) [Cursos]
10. Tipo de EA en uso (Polar - Sessions By Gender) [EA]

## Reordenamiento visual
- El orden actual en `dashboard_analytics.html` ya coincide con esta prioridad.
- Si se reordena, mantener la secuencia listada arriba.

## Cards (detalle)

### 1) Rendimiento diario [EA]
Nombre HTML (comentario): <!-- Line chart (Analytics) -->
Titulo visible: Rendimiento diario
Tipo: Line chart
Canvas id: analytics-card-01
Legend id: none
Contenido actual / Copy UI:
- Subtitulo: PnL neto y evolucion 30d.
- KPIs: PnL 30d, PnL acumulado, Dias positivos, Drawdown max.
- Tooltip: PnL neto = suma de resultados diarios; Drawdown max = mayor caida desde el pico.
Metricas / Formula:
- PnL diario = sum(`broker_account_daily_results.result_value`) agrupado por dia local.
- PnL 30d = sum(PnL diario) en ventana de 30 dias.
- PnL acumulado = suma acumulada del PnL diario.
- Dias positivos (%) = count(PnL diario > 0) / count(dias con datos).
- Drawdown max = max(peak_acumulado - acumulado_actual) en la ventana.
Fuentes: `broker_account_daily_results` -> `broker_accounts` -> `licenses` -> `expert_advisors`.
Reglas / Notas:
- Filtrar por `licenses.user_id`.
- Consolidar multiples cuentas por licencia.
- Permitir filtro por cuenta real/demo.
CTA: Ver detalle de rendimiento.
Empty state: Sin datos suficientes.

### 2) EAs activos ahora [EA]
Nombre HTML (comentario): <!--  Line chart (Active Users Right Now) -->
Titulo visible: EAs activos ahora
Tipo: Line chart
Canvas id: analytics-card-02
Legend id: none
Contenido actual / Copy UI:
- Subtitulo: Actividad en los ultimos 30 min.
- KPIs: Licencias activas 30m, Cuentas activas hoy.
- Tabla: EA | Cuentas activas.
Metricas / Formula:
- Licencias activas 30m = count(distinct `licenses.id`) con `status` en (active, trial) y `last_synced_at` >= now - 30m.
- Cuentas activas hoy = count(distinct `broker_accounts.id`) con resultado en las ultimas 24h.
- Tabla = group by `expert_advisors.name` con conteo de cuentas activas en 24h.
Fuentes: `licenses.last_synced_at`, `broker_accounts`, `expert_advisors`.
Reglas / Notas:
- Si falta `last_synced_at`, usar cuentas con resultado registrado hoy como proxy.
CTA: Ver actividad.
Empty state: Sin actividad reciente.

### 3) Resultados por EA [EA]
Nombre HTML (comentario): <!-- Stacked bar chart (Acquisition Channels) -->
Titulo visible: Resultados por EA
Tipo: Stacked bar chart
Canvas id: analytics-card-03
Legend id: analytics-card-03-legend
Contenido actual / Copy UI:
- Subtitulo: PnL 30d por EA y tipo de cuenta.
- Leyenda: Real, Demo.
Metricas / Formula:
- PnL 30d por EA y cuenta = sum(result_value) en 30d, agrupado por EA y `account_type`.
- Total por EA = sum(PnL real + PnL demo).
Fuentes: `broker_account_daily_results`, `broker_accounts.account_type`, `expert_advisors`.
Reglas / Notas:
- Mostrar top 5-7 EAs por PnL y un bucket "Otros".
CTA: none
Empty state: Sin resultados en el periodo.

### 4) Top cursos por avance [Cursos]
Nombre HTML (comentario): <!-- Horizontal bar chart (Audience Overview) -->
Titulo visible: Top cursos por avance
Tipo: Horizontal bar chart
Canvas id: analytics-card-04
Legend id: analytics-card-04-legend
Contenido actual / Copy UI:
- Subtitulo: Cursos en progreso.
- Eje/tooltip: Avance (%).
Metricas / Formula:
- Avance por curso = `course_enrollments.progress_percent` (0..100).
Fuentes: `course_enrollments` -> `courses`.
Reglas / Notas:
- Filtrar por `course_enrollments.user_id`.
- Mostrar top 6-8 cursos en progreso.
- Ordenar por avance desc y ocultar completados si hay muchos.
CTA: none
Empty state: No hay cursos en progreso.

### 5) Top EAs por ganancia [EA]
Nombre HTML (comentario): <!-- Report card (Top Channels) -->
Titulo visible: Top EAs por ganancia
Tipo: Report card
Canvas id: none
Legend id: none
Contenido actual / Copy UI:
- Subtitulo: PnL neto 30d.
- Tabla: EA | PnL 30d.
Metricas / Formula:
- PnL 30d por EA = sum(result_value) en 30d, agrupado por EA.
- Variacion = (PnL 30d - PnL 30d previo) / abs(PnL 30d previo) si previo != 0.
Fuentes: `broker_account_daily_results`, `expert_advisors`.
Reglas / Notas:
- Mostrar variacion vs periodo anterior si hay datos.
CTA: Ver detalle por EA.
Empty state: Sin PnL en el periodo.

### 6) Ultimas lecciones vistas [Cursos]
Nombre HTML (comentario): <!-- Report card (Top Pages) -->
Titulo visible: Ultimas lecciones vistas
Tipo: Report card
Canvas id: none
Legend id: none
Contenido actual / Copy UI:
- Subtitulo: Retoma donde quedaste.
- Tabla: Leccion | Progreso.
Metricas / Formula:
- Orden = `course_lesson_progresses.last_watched_at` desc.
- Progreso % = min(100, progress_seconds / duration_seconds * 100) si `duration_seconds` > 0.
- Progreso min = progress_seconds / 60 si no hay `duration_seconds`.
Fuentes: `course_lesson_progresses` -> `course_lessons` -> `courses`.
Reglas / Notas:
- Filtrar por `course_lesson_progresses.user_id`.
- Si no hay lecciones, mostrar CTA "Ver cursos".
CTA: Ver cursos.
Empty state: Aun no hay lecciones vistas.

### 7) Licencias por vencer [EA]
Nombre HTML (comentario): <!-- Report card (Top Countries) -->
Titulo visible: Licencias por vencer
Tipo: Report card
Canvas id: none
Legend id: none
Contenido actual / Copy UI:
- Subtitulo: Evita interrupciones.
- Tabla: EA | Vence en.
Metricas / Formula:
- Fecha vencimiento = coalesce(`trial_ends_at`, `expires_at`).
- Dias restantes = date(fecha_vencimiento) - hoy.
Fuentes: `licenses.expires_at`, `licenses.trial_ends_at`, `expert_advisors`.
Reglas / Notas:
- Filtrar por `licenses.user_id`.
- Orden ascendente por dias restantes.
CTA: Renovar licencia.
Empty state: No hay vencimientos cercanos.

### 8) Estado de cursos [Cursos]
Nombre HTML (comentario): <!-- Doughnut chart (Sessions By Device) -->
Titulo visible: Estado de cursos
Tipo: Doughnut chart
Canvas id: analytics-card-08
Legend id: analytics-card-08-legend
Contenido actual / Copy UI:
- Subtitulo: Balance de cursos.
- Leyenda: No iniciado, En progreso, Completado.
Metricas / Formula:
- No iniciado = `progress_percent` = 0 y `completed_at` is null.
- En progreso = `progress_percent` entre 1 y 99 y `completed_at` is null.
- Completado = `completed_at` no null o `progress_percent` >= 100.
Fuentes: `course_enrollments`.
Reglas / Notas:
- Contar solo cursos enrolados del usuario.
CTA: none
Empty state: Sin cursos enrolados.

### 9) Tiempo de estudio por categoria [Cursos]
Nombre HTML (comentario): <!-- Doughnut chart (Visit By Age Category) -->
Titulo visible: Tiempo de estudio por categoria
Tipo: Doughnut chart
Canvas id: analytics-card-09
Legend id: analytics-card-09-legend
Contenido actual / Copy UI:
- Subtitulo: Distribucion de minutos 30d.
- Leyenda: categorias del curso.
Metricas / Formula:
- Minutos 30d por categoria = sum(progress_seconds) / 60, agrupado por `courses.category`.
Fuentes: `course_lesson_progresses.progress_seconds` -> `course_lessons` -> `course_modules` -> `courses`.
Reglas / Notas:
- Filtrar por `course_lesson_progresses.user_id`.
- Agrupar categorias con poco peso en "Otros".
CTA: none
Empty state: Sin tiempo de estudio reciente.

### 10) Tipo de EA en uso [EA]
Nombre HTML (comentario): <!-- Polar chart (Sessions By Gender) -->
Titulo visible: Tipo de EA en uso
Tipo: Polar chart
Canvas id: analytics-card-10
Legend id: analytics-card-10-legend
Contenido actual / Copy UI:
- Subtitulo: Robots vs tools en uso.
- Leyenda: EA robot, EA tool.
Metricas / Formula:
- Distribucion por tipo = count(distinct `licenses.id`) por `expert_advisors.ea_type`.
Fuentes: `expert_advisors.ea_type`, `licenses.status`.
Reglas / Notas:
- Contar solo `active` y `trial`.
CTA: none
Empty state: Sin licencias activas.
