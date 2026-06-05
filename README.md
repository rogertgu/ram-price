# RAM Price/GB Dashboard

Dashboard web (una sola página, sin build) que muestra la evolución del **precio retail por GB** de memoria RAM **DDR3 / DDR4 / DDR5** entre **mayo 2024 y mayo 2026**, con foco en el shock de escasez de DRAM de la segunda mitad de 2025.

## Características

- 📈 Gráfico comparativo USD/GB de DDR3, DDR4 y DDR5.
- 🔁 Toggle de escala **lineal / logarítmica**.
- 🌗 Tema **claro / oscuro** (se recuerda en el navegador).
- 🟥 Banda sombreada marcando el periodo del shock (2H 2025).
- 📊 Gráfico de variación % (base 100 = may 2024) y spread DDR5 − DDR4.
- 🧮 Tabla mensual y **descarga CSV** de los datos.
- 📱 Diseño responsive.

## Datos

Los valores son estimaciones mensuales interpoladas a partir de data points públicos
(Tom's Hardware RAM Price Index, TrendForce, PCPartPicker, Pangoly, Wccftech, XDA, etc.).
Sirven para visualizar la **tendencia**, no para decisiones de compra exactas.
Para actualizar las series, edita los arrays `ddr3`, `ddr4` y `ddr5` en `index.html`.

## Desarrollo local

No requiere dependencias ni build. Abre `index.html` en el navegador, o sirve la carpeta:

```bash
python3 -m http.server 8000
# luego abre http://localhost:8000
```

## Publicación

Se publica automáticamente con **GitHub Pages** mediante GitHub Actions
(`.github/workflows/pages.yml`) en cada push.
