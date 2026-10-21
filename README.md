# Visor de seguridad del Observatorio

Dashboard web estático y responsivo publicado mediante GitHub Pages. Incluye un resumen ejecutivo común para Delitos priorizados, Ley STOP y STOP; además incorpora vistas detalladas, comparación de prefectura y mapa urbano de cuadrantes con los sectores rurales separados.

## Actualización semanal

1. Verifica que el nuevo `Dataset depurado_... hasta DD-MM-AA.xlsx` esté guardado y cerrado en la carpeta histórica institucional.
2. Verifica que los 18 libros de `Datos prefectura/Ley Stop` y `Datos prefectura/STOP` estén actualizados y cerrados.
3. Ejecuta `actualizar_visor_integrado_GITHUB.R` completo en RStudio.
4. Confirma en la consola la fecha de corte, la semana detectada y la cobertura geográfica.
5. En GitHub Desktop escribe `Actualización semanal SXX`, presiona **Commit to main** y luego **Push origin**.

El script modifica siempre este mismo `index.html`, por lo que la dirección pública del visor no cambia.

## Fuentes automáticas

- Dataset depurado: se elige por la fecha final más avanzada escrita después de `hasta` en el nombre del archivo.
- Prefectura: se leen los libros institucionales de las carpetas `Ley Stop` y `STOP`.
- Mapa: se usan los polígonos de `cuadrantes.rds` y la columna `cuadra_dep` del Dataset depurado. San Enrique se excluye y SRA, SRB y SRC se informan fuera del mapa urbano.

El actualizador se detiene ante duplicados, archivos temporales abiertos, fechas inconsistentes, cambios de estructura o fuentes faltantes.
