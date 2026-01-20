# Dashboard Main - contenido de cards (vista actual)

## Objetivo
Registrar la informacion visible en cada card de `dashboard_main.html` sin modificarla.

## Alcance
- Solo contenido literal de la vista.
- Sin supuestos de periodos, comparativas o fuentes de datos.
- Solo bloques con chart (canvas).

## Orden visual (segun HTML)
1. Rendimiento mensual (PnL) - `fintech-card-01`
2. Licencias activas - `fintech-card-07`
3. Progreso de curso - `fintech-card-08`
4. Distribucion de balance - `fintech-card-09`
5. Cuentas broker - vinculadas - `fintech-card-10`
6. EAs - activos - `fintech-card-11`
7. Licencias - activas - `fintech-card-12`
8. Cursos - en progreso - `fintech-card-13`
9. Resumen de tu cuenta (tabla) - `fintech-card-14-a` a `fintech-card-14-e`

## Cards (detalle)

### 1) Rendimiento mensual (PnL)
Nombre HTML (comentario): <!-- Line chart (Portfolio Returns) -->
Titulo visible: Rendimiento mensual (PnL)
Tipo: Line chart
Canvas id: fintech-card-01
Legend id: fintech-card-01-legend
Contenido actual / Copy UI:
- Valor principal: "$1,284.60"
- Texto auxiliar: "USD 62.4 promedio diario"
- Leyenda: contenedor `fintech-card-01-legend` (lista vacia en HTML)
Metricas / Formula: N/A (contenido literal)
Fuentes: N/A
Reglas / Notas: N/A
CTA: none
Empty state: none

### 2) Licencias activas
Nombre HTML (comentario): <!-- Line chart (Portfolio Returns) -->
Titulo visible: Licencias activas
Tipo: Line chart
Canvas id: fintech-card-07
Legend id: none
Contenido actual / Copy UI:
- Texto: "Uso de licencia actual:"
- Valor: "2 de 3"
- Porcentaje: "67%"
- Nota: "Proxima renovacion: 12/03/2026"
Metricas / Formula: N/A (contenido literal)
Fuentes: N/A
Reglas / Notas: N/A
CTA: none
Empty state: none

### 3) Progreso de curso
Nombre HTML (comentario): <!-- Line chart (Growth Portfolio) -->
Titulo visible: Progreso de curso
Tipo: Line chart
Canvas id: fintech-card-08
Legend id: none
Contenido actual / Copy UI:
- Texto: "Tu curso en progreso:"
- Valor: "64% completado"
- Nota: "Curso: Gestion de riesgo"
Metricas / Formula: N/A (contenido literal)
Fuentes: N/A
Reglas / Notas: N/A
CTA: none
Empty state: none

### 4) Distribucion de balance
Nombre HTML (comentario): <!-- Pie chart (Portfolio Value) -->
Titulo visible: Distribucion de balance
Tipo: Pie chart
Canvas id: fintech-card-09
Legend id: fintech-card-09-legend
Contenido actual / Copy UI:
- Texto: "Balance combinado de cuentas:"
- Valor: "$12,480.75"
- Leyenda: contenedor `fintech-card-09-legend` (lista vacia en HTML)
Metricas / Formula: N/A (contenido literal)
Fuentes: N/A
Reglas / Notas: N/A
CTA: none
Empty state: none

### 5) Cuentas broker - vinculadas
Nombre HTML (comentario): <!-- Line charts (Stock graphs) -->
Titulo visible: Cuentas broker - vinculadas
Tipo: Line chart (mini)
Canvas id: fintech-card-10
Legend id: none
Contenido actual / Copy UI:
- Valor: "2"
- Variacion: "+1 (50%) - Hoy"
Metricas / Formula: N/A (contenido literal)
Fuentes: N/A
Reglas / Notas: N/A
CTA: none
Empty state: none

### 6) EAs - activos
Nombre HTML (comentario): <!-- Line charts (Stock graphs) -->
Titulo visible: EAs - activos
Tipo: Line chart (mini)
Canvas id: fintech-card-11
Legend id: none
Contenido actual / Copy UI:
- Valor: "4"
- Variacion: "+1 (33%) - Hoy"
Metricas / Formula: N/A (contenido literal)
Fuentes: N/A
Reglas / Notas: N/A
CTA: none
Empty state: none

### 7) Licencias - activas
Nombre HTML (comentario): <!-- Line charts (Stock graphs) -->
Titulo visible: Licencias - activas
Tipo: Line chart (mini)
Canvas id: fintech-card-12
Legend id: none
Contenido actual / Copy UI:
- Valor: "3"
- Variacion: "+0 (0%) - Hoy"
Metricas / Formula: N/A (contenido literal)
Fuentes: N/A
Reglas / Notas: N/A
CTA: none
Empty state: none

### 8) Cursos - en progreso
Nombre HTML (comentario): <!-- Line charts (Stock graphs) -->
Titulo visible: Cursos - en progreso
Tipo: Line chart (mini)
Canvas id: fintech-card-13
Legend id: none
Contenido actual / Copy UI:
- Valor: "2"
- Variacion: "+1 (100%) - Hoy"
Metricas / Formula: N/A (contenido literal)
Fuentes: N/A
Reglas / Notas: N/A
CTA: none
Empty state: none

### 9) Resumen de tu cuenta (tabla)
Nombre HTML (comentario): <!-- Table (Market Trends) -->
Titulo visible: Resumen de tu cuenta
Tipo: Table
Canvas id: fintech-card-14-a, fintech-card-14-b, fintech-card-14-c, fintech-card-14-d, fintech-card-14-e
Legend id: none
Contenido actual / Copy UI:
- Columnas: Area, Total, Tendencia, USD, Estado
- Filas:
  - Area: "Sniper Advanced Panel" (Vigentes), Total "3", Tendencia `fintech-card-14-a`, USD "$59.00", Estado "Activo"
  - Area: "PANDORA BOX EA" (Vigentes), Total "2", Tendencia `fintech-card-14-b`, USD "$0.00", Estado "Activo"
  - Area: "Cursos" (En progreso), Total "2", Tendencia `fintech-card-14-c`, USD "$149.00", Estado "En curso"
  - Area: "EA" (Activos), Total "1", Tendencia `fintech-card-14-d`, USD "$29.00", Estado "Activo"
  - Area: "Suscripcion" (Plan Pro), Total "1", Tendencia `fintech-card-14-e`, USD "$59.00", Estado "Renueva 12/03"
Metricas / Formula: N/A (contenido literal)
Fuentes: N/A
Reglas / Notas: N/A
CTA: none
Empty state: none
