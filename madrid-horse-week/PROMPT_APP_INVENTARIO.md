# Prompt para Claude Code — App de Inventario de Bodega · Madrid Horse Week (IFEMA)

> Copia todo lo que hay debajo de la línea y pégalo en Claude Code.
> Antes, rellena o corrige los datos entre [corchetes].

---

## Contexto

Soy el responsable de la **bodega de bebidas** del catering **[Zalacaín]** en el evento **Madrid Horse Week**, en **IFEMA Madrid**, del **[fecha inicio] al [fecha fin]**. Desde la bodega se distribuye toda la bebida a las distintas **zonas de restauración** del evento. Una de mis tareas más importantes es **registrar y reportar el inventario de bebidas** de forma rápida y sin errores.

Quiero que construyas una **aplicación web móvil (PWA)** para usar desde mi teléfono dentro del pabellón, donde la cobertura puede ser mala.

## Usuarios

- **Jefe de bodega** (yo): acceso total, configura productos y zonas, cierra inventarios y genera reportes.
- **Ayudantes de bodega** ([número]): registran entradas, salidas a zonas y conteos.
- **Responsables de zona** (opcional): ven lo que se les ha entregado y confirman la recepción.

Acceso simple con PIN de 4 dígitos por persona; cada movimiento queda firmado con usuario, fecha y hora.

## Catálogo inicial

**Productos** (deben poder editarse desde la app e importarse desde Excel/CSV):
- Campos: nombre, categoría (agua, refresco, cerveza, vino blanco, vino tinto, cava/champán, destilado, zumo, café/otros), formato (lata 33 cl, botella 75 cl, barril 30 L, caja…), **unidades por caja**, proveedor, precio de coste (opcional) y stock mínimo.
- Ejemplos para precargar: [lista tus productos, p. ej. "Agua Solán de Cabras 50 cl – caja 24", "Mahou 5 Estrellas lata 33 cl – caja 24", "Ribera del Duero XXX 75 cl – caja 6"…].

**Ubicaciones:**
- Bodega central.
- Zonas de restauración: [p. ej. VIP, Restaurante, Barra pista principal, Food court, Palco, Zona jinetes/staff…].

## Funcionalidades

1. **Recepción de mercancía (entradas a bodega)**
   - Registrar lo que llega de proveedor: producto, cantidad en cajas + unidades sueltas, nº de albarán, foto opcional del albarán.
2. **Salidas / traspasos a zonas**
   - Elegir zona → añadir productos y cantidades → confirmar. Generar un vale de entrega (PDF o pantalla) con firma táctil de quien recibe.
3. **Devoluciones de zonas a bodega**
   - Al final del servicio, registrar lo que vuelve (lleno), y por separado envases vacíos y roturas/mermas con su motivo.
4. **Conteo de inventario (lo más importante)**
   - Modo conteo rápido: lista de productos agrupada por categoría, con botones grandes **+ / −** y campos para **cajas** y **unidades sueltas**; la app calcula el total en unidades.
   - Tipos de conteo: **inicial** (apertura del evento), **por turno/día** (apertura y cierre) y **final**.
   - Comparar el **stock teórico** (entradas − salidas + devoluciones − mermas) con el **stock contado** y mostrar las **diferencias** resaltadas en rojo.
   - Posibilidad de guardar un conteo a medias y continuarlo después.
5. **Panel en tiempo real**
   - Stock actual de la bodega por producto, alertas de **stock bajo** (por debajo del mínimo) y consumo por zona y por día.
6. **Reportes** (lo que tengo que entregar)
   - **Inventario de cierre diario**: stock inicial, entradas, salidas por zona, devoluciones, mermas, stock final teórico, stock contado, diferencia.
   - **Consumo por zona** y por día.
   - **Resumen final del evento**, con valoración económica si hay precios.
   - Exportar a **Excel (.xlsx)** y **PDF**, y botón para **compartir por WhatsApp o email**.
   - Cabecera con nombre del evento, fecha, turno y responsable.

## Requisitos técnicos

- **Mobile-first**, botones grandes, se tiene que poder usar con una mano y con prisa.
- **Funciona sin conexión (offline-first)**: guarda todo en el dispositivo y sincroniza cuando vuelva la red. Esto es crítico porque en IFEMA la cobertura falla.
- **Varios dispositivos a la vez** sincronizados (yo y los ayudantes). Propón el backend más sencillo y barato para esto (por ejemplo Supabase o Firebase) y explícame cómo configurarlo paso a paso.
- Instalable en el móvil como app (PWA), en **español**.
- **Historial de movimientos** (auditoría) con usuario, fecha y hora; no se borra nada: las correcciones se hacen con un movimiento de ajuste que lleva su motivo.
- Copia de seguridad: botón para exportar todos los datos a Excel/JSON.
- Opcional, si no complica mucho: lector de **códigos de barras** con la cámara para buscar productos.

## Cómo quiero que trabajes

1. Antes de programar, **hazme preguntas** sobre lo que no esté claro y propón la arquitectura y el modelo de datos (tablas: productos, ubicaciones, movimientos, conteos, usuarios).
2. Construye primero un **MVP** con: catálogo, salidas a zonas, conteo y reporte de cierre diario en Excel. Después añadimos lo demás.
3. Precarga **datos de ejemplo** para que pueda probarla enseguida.
4. Al terminar cada fase, dime cómo probarla en mi móvil y cómo **publicarla** (por ejemplo en Netlify o Vercel) con una URL para el equipo.
5. Explícamelo todo en lenguaje sencillo: no soy programador.
