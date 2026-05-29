# Dynamic Pricing Analyzer

Herramienta genérica y reusable de pricing dinámico. Subes una tabla de ventas
(CSV o Excel), valida su calidad, estima la elasticidad-precio por SKU, simula
escenarios y promociones, y entrega una recomendación por SKU con sus advertencias.

**App en vivo:** https://ncanudas-jpg.github.io/simulador-precios/

## Las 7 funciones
1. Cargar archivo CSV o Excel
2. Mapear columnas del archivo a las variables del modelo
3. Calcular precio, ingreso y margen base
4. Estimar elasticidad (regresión log-log) o usar la elasticidad cargada
5. Simular escenarios de precio (−10/−5/0/+5/+10%) y promociones (3x2, 2x1, 2do al 50%)
6. Recomendar acción por SKU (subir, bajar/promover, mantener, no recomendar)
7. Exportar resultados en CSV

## Archivos
- `index.html` — la aplicación (autónoma, sin dependencias que instalar)
- `assets/officemax-logo.svg` — logo usado en el encabezado visual
- `plantilla_input.csv` — esquema de datos de entrada
- `prueba_archivo_y_accesorios.csv`, `prueba_papel.csv`, `prueba_carpetas.csv` — archivos de prueba por pod

## Uso
Abre `index.html` en el navegador, o visita el link de la app en vivo. No requiere servidor.

## Metodología y límites
- Elasticidad: `log(unidades + 1) = α + β·log(precio)` por SKU.
- La recomendación solo se activa con elasticidad significativa (p < 0.10) y se limita a ±20%.
- Los márgenes son exploratorios si la base de costos tiene inconsistencias.
- No garantiza causalidad, no fija precios automáticamente, no modela competencia ni inventario.
  Validar con prueba A/B en 2–3 tiendas antes de cualquier rollout.
