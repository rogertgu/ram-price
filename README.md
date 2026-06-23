# RAM Price/GB Dashboard

Dashboard web (una sola página, sin build) que muestra la evolución del **precio retail por GB** de memoria RAM **DDR3 / DDR4 / DDR5** entre **mayo 2024 y junio 2026**, con foco en el shock de escasez de DRAM de la segunda mitad de 2025.

## Características

- 📈 Gráfico comparativo USD/GB de DDR3, DDR4 y DDR5.
- 🔁 Toggle de escala **lineal / logarítmica**.
- 🌗 Tema **claro / oscuro** (se recuerda en el navegador).
- 🟥 Banda sombreada marcando el periodo del shock (2H 2025).
- 📊 Gráfico de variación % (base 100 = may 2024) y spread DDR5 − DDR4.
- 🧮 Tabla mensual y **descarga CSV** de los datos.
- 📱 Diseño responsive.

## Datos

Los valores son estimaciones mensuales interpoladas a partir de data points públicos.
Sirven para visualizar la **tendencia**, no para decisiones de compra exactas.

### Cómo actualizar

1. Consulta las **fuentes primarias** (abajo) y anota el `USD/GB` del mes para DDR3, DDR4 y DDR5.
   Si una fuente da el precio de un módulo, divide entre su capacidad: kit 32 GB DDR5 a $120 → $3.75/GB.
2. En `index.html`, añade el mes nuevo al array `labels` (p. ej. `"Jun'26"`).
3. Añade el valor del mes al **final** de `ddr3`, `ddr4` y `ddr5` (los 4 arrays deben tener la misma longitud).
4. `git commit` + `git push` a la rama → GitHub Pages republica solo en ~1 min.

### Fuentes primarias (de aquí salen los números USD/GB)

| Fuente | Series | Tipo de dato | Cada cuánto |
|---|---|---|---|
| [Tom's Hardware — RAM Price Index](https://www.tomshardware.com/pc-components/ram/ram-price-index-2026-lowest-price-on-ddr5-and-ddr4-memory-of-all-capacities) | DDR4, DDR5 | Retail USD/GB por capacidad (referencia principal) | Mensual aprox. |
| [TrendForce — DRAM Spot Price](https://www.trendforce.com/price/dram/dram_spot) | DDR4, DDR5 | Spot mayorista (anticipa el retail) | Diario / semanal |
| [PCPartPicker — Memory Trends](https://pcpartpicker.com/trends/price/memory/) | DDR3, DDR4, DDR5 | Retail real (EE. UU.); útil para DDR3 | Continuo |
| [Pangoly — DDR5](https://pangoly.com/en/price-trends/ram/32gb-ddr5) | DDR5 | Histórico de módulos (÷ capacidad → USD/GB) | Continuo |

La lista completa de fuentes (incluido contexto y noticias) está al pie del propio dashboard.

## Desarrollo local

No requiere dependencias ni build. Abre `index.html` en el navegador, o sirve la carpeta:

```bash
python3 -m http.server 8000
# luego abre http://localhost:8000
```

## Publicación

Se publica automáticamente con **GitHub Pages** mediante GitHub Actions
(`.github/workflows/pages.yml`) en cada push.
