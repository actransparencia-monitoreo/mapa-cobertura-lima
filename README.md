# mapa-cobertura-lima

Mapa público de cobertura de observación electoral en Lima Metropolitana.

**Ver el mapa:** https://actransparencia-monitoreo.github.io/mapa-cobertura-lima/

## Qué muestra

Cada punto es un **local de votación**. Su color dice si las mesas de ese local
tienen observadores asignados en los dos turnos:

| Color | Estado | Significa |
|---|---|---|
| 🟢 Verde | CUBIERTO | todas sus mesas tienen los dos turnos cubiertos |
| 🔵 Azul | EXCEDENTE | además hay voluntarios de más en alguna mesa |
| 🟡 Amarillo | PARCIAL | falta al menos un turno |
| 🔴 Rojo | NO_CUBIERTO | ningún turno cubierto |

El color de fondo de cada distrito es su porcentaje de turnos cubiertos, en una
escala **fija de 0 a 100%**. Es fija a propósito: con una escala que se ajusta a
los datos, un mapa al 0% y otro al 100% se ven iguales, y el avance no se puede
comparar entre días. Los distritos que no están en la muestra van en gris, que
significa "no aplica" y no "cobertura cero".

Un voluntario de más **se ve** (el local pasa a azul) pero **no sube** el
porcentaje del distrito: dos personas en el mismo turno cubren un turno, no dos.

La fecha del panel es la de la última publicación de los datos, no la del día en
que se abre la página. Si pasan tres días sin publicar, la fecha se resalta.

## Privacidad

Este repositorio contiene **solo datos agregados**. Nunca llegan aquí nombres,
apellidos, documentos de identidad, teléfonos ni números de mesa.

Lo que sí se publica, por local: identificador, nombre, distrito, coordenadas,
número de mesas, turnos requeridos, turnos cubiertos, ratio y estado. Y por
distrito: nombre y ratio.

## Qué hay en el repo

```
index.html                          el mapa completo (MapLibre GL JS), archivo único
data/locales.csv                    495 locales — lo actualiza el sistema de coordinación
data/mapa_distritos.csv             40 distritos con su ratio — igual
data/lima_callao_distritos.geojson  geometría de los distritos, estática
```

`index.html` une la geometría con los ratios **en el navegador**. Por eso la
actualización automática solo necesita escribir dos archivos pequeños.

## Cómo se actualiza

Los dos CSV los escribe un proceso automático desde la hoja de coordinación. La
página no se actualiza sola en pantalla: hay que refrescar (F5) para ver el
último estado publicado.

> ⚠ Este repositorio lo escribe un proceso externo. Haz `git pull` antes de
> editar `index.html` a mano.

## Créditos y licencia

Mantiene: **ACTransparencia.monitoreo**

Código bajo licencia MIT — ver [LICENSE](LICENSE).
Geometría de distritos: Instituto Geográfico Nacional (Perú).
