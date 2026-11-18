# Diagnóstico OBD2 de presión atmosférica

Abra `index.html` desde un servidor local o HTTPS con Chrome/Edge. El proyecto usa solo APIs de navegador y Open-Meteo, sin claves ni backend.

La ECU se consulta con `01 33` (presión barométrica, un byte en kPa) y, como referencia auxiliar, `01 0B` (MAP). La comparación usa `surface_pressure` de Open-Meteo, expresada en hPa y convertida a kPa (`hPa / 10`), por lo que evita comparar por defecto contra `pressure_msl` (nivel medio del mar).

Limitaciones: el selector Bluetooth es controlado por el navegador, por privacidad no se puede listar dispositivos antes de abrirlo. La compatibilidad BLE varía por clon ELM327; Bluetooth clásico no está disponible en Web Bluetooth. Web Serial funciona si el sistema expone el adaptador como puerto serie. No se implementan comandos de escritura/calibración de ECU.
