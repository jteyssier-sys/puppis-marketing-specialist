# Radar de Precios MELI (Nestlé y Royal Canin)

Panel: https://claude.ai/artifact/PBCb7Xp3369kzqFQkrTFbD

## Qué muestra

- Filtros: ventana de fechas (desde / hasta), portfolio (Nestlé, Royal Canin o ambos) y competidor.
- KPIs: unidades y revenue de Puppis, share de Puppis en las unidades rastreadas, unidades del líder de cada producto, en cuántos productos estamos más caros y la brecha mediana de precio frente al líder.
- Tabla por producto: petshop que más vende, sus unidades, reparto de la venta entre petshops (incluido Puppis), precio Puppis, precio del líder, brecha y links a la publicación del competidor y a la nuestra.
- Reparto de la venta por petshop (unidades y % sobre lo rastreado).
- Nuestro precio frente al líder, producto por producto.
- Performance por subcategoría (categoría · tipo · animal), en unidades o revenue.

## De dónde salen los datos

Todo se lee en vivo, vía el conector de Google Sheets, del Sheet
"Cálculo Precios Online (MELI - vTex)" (`1J3b786NcumVE9zk636eodrm1xR5opQRyT5EP4IPCovI`):

| Hoja | Rango | Uso |
|---|---|---|
| Competencia | A4:R2000 | Bajada de Nubimetrics: precio y unidades de la competencia, nuestro precio y unidades |
| MELI | A6:F1508 | Portfolio Nestlé + Royal Canin (marca, peso, PVP) |
| Costos y PVP | B, E, I:K | Categoría, animal y tipo (seco / húmedo) por SKU |

Portfolio por marca: Royal Canin Argentina = Royal Canin, Eukanuba, Pedigree, Performance, Kitekat, Champ, Whiskas, Premium. El resto de las marcas de la hoja MELI son Nestlé.

## Cómo cargar Nubimetrics para aprovechar todo el panel

La hoja Competencia hoy trae un solo competidor por SKU (el que más vende). El panel ya soporta más:

- **Varios petshops por producto**: una fila por SKU y por competidor (mismo SKU repetido). El reparto porcentual y el ranking de petshops se arman solos.
- **Ventana de tiempo**: completar "Ventana desde" y "Ventana hasta" (dd/mm/aaaa). Si están vacías se usa la fecha de la columna Fuente ("Nubimetrics dd/mm/aaaa"). Para ver evolución, pegar cada bajada nueva debajo de la anterior en lugar de pisarla.
- **Link a la publicación del competidor**: pegar el permalink de MELI en cualquier columna de la fila (por ejemplo en R, "Link competidor"). Si no hay link, el panel abre una búsqueda del producto en Mercado Libre.
- **Accesorios, piedras, etc.**: hoy Costos y PVP y Competencia son solo alimentos. Cuando se sumen esos SKUs, aparecen como subcategorías propias.
