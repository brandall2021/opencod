# Conversión BIBUN → MARC21 para VuFind — Biblioteca FCN–UNT

Fuente: exportación BIBUN (CDS/ISIS) del 06/11/2026, codificación CP850.
El conversor decodifica CP850 → Unicode y genera MARC21 en UTF-8.

**Archivos generados** (carpeta `marc21\`):

| Archivo | Descripción |
|---|---|
| `20261106--fcn-unt--bibun.marc21.mrc` | 7.795 registros en ISO 2709 (MARC21 binario UTF-8) — **archivo para importar en VuFind** |
| `20261106--fcn-unt--bibun.marc21.xml` | Lo mismo en MARCXML (contenedor `<collection>`) — útil para revisar o integraciones |
| `mapeo_BIBUN_a_MARC21.md` | Tabla con lo que se hizo con cada campo BIBUN |
| `marc_local.properties` | Mapeos opcionales para los facetas de ejemplares |
| `informe_conversion.json` | Estadísticas y verificación de consistencia |
| `convert_bibun_marc21.py` | El conversor, por si hay que repetir el proceso con una exportación nova |

## 1. Copiar los mapeos locales

Copiar `marc_local.properties` a la configuración local de VuFind:

- Linux: `$VUFIND_LOCAL_DIR/import/marc_local.properties`
- Windows: `%VUFIND_LOCAL_DIR%\import\marc_local.properties`

Si no existe un `VUFIND_LOCAL_DIR`, puede colocarse en `$VUFIND_HOME/import/`.

## 2. Importar los registros

**Linux:**
```bash
cd /usr/local/vufind
./import-marc.sh /ruta/20261106--fcn-unt--bibun.marc21.mrc
```

**Windows:**
```
import-marc.bat C:\ruta\a\20261106--fcn-unt--bibun.marc21.mrc
```

El importador acepta `.mrc` (ISO 2709) o `.xml` (MARCXML) indistintamente.
La configuración de VuFind ya incluye `marc.to_utf_8 = true`, y los registros salen en UTF-8 (leader/09 = `a`).

## 3. Los ejemplares (holdings)

Cada registro lleva:

- `852` nivel bibliográfico: `a`=FCN-UNT, `b`=agencia (SNA, etc.), `c`=colección (PRES, etc.), `h`=signatura, `9`=Nº de ejemplares.
- Un `952` **por cada ejemplar**: `$b` ubicación, `$c`/`$8` colección, `$o` signatura, `$p` código de inventario/barcode, `$3` designación de copia ("ej. 2"), `$g` precio, `$z` notas, `$y` tipo de material.

Los facetas de institución/edificio/colección y el call number se indexan con las líneas incluidas en `marc_local.properties` (`952b`, `952c`, `9528`, `952o`).

> **Nota:** si el VuFind está integrado con un sistema de biblioteca (Koha, Aleph, etc.), las copias reales y sus estados provienen del ILS vía driver, no de los MARC. Los `952` sirven para importar los ejemplares al sistema o como respaldo visible en VuFind.

## 4. Números de la conversión

- 7.795 registros (4.820 monográficos · 2.937 analíticos · 31 series contenedoras · 7 otros)
- 12.106 registros de ejemplares en `952`
- 2.938 vínculos `773`: cada analítica apunta a su publicación contenedora vía `(FCN-UNT)SNA00000XXX`
- 1.396 notas `502` de tesis/seminarios
- ID único en `001` = `SNA00000XXX` (no hay duplicados)

## 5. Exportar de nuevo en el futuro

Si se recibe una exportación BIBUN actualizada (mismo formato, CP850), basta correr:

```bash
python convert_bibun_marc21.py
```
ajustando las rutas `IN_PATH` y `OUT_DIR` al inicio del script. Campos nuevos de BIBUN que no estén mapeados se reportan en el informe JSON.
