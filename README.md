Sistema operativo utilizado: Windows 10 / 11.

1. ¿Por qué la temperatura suele aparecer como "No disponible" en Windows?

Respuesta: Porque la clase de WMI encargada de proveer la temperatura (MSAcpi_ThermalZoneTemperature) requiere permisos de administrador elevados y que, además, la placa base y los sensores de hardware del equipo expongan dicha información al sistema operativo de forma compatible.

2. ¿Por qué el script de PowerShell nunca debe incluir datos que vengan del usuario?

Respuesta: Porque al utilizar funciones como shell_exec(), si se concatenaran datos provenientes de entradas del usuario (formularios, parámetros URL, etc.) sin sanitizar, se expondría la aplicación a una vulnerabilidad crítica de inyección de comandos, permitiendo la ejecución arbitraria de código malicioso en el servidor.

3. ¿Qué riesgo tiene dejar /api/metrics sin autenticación en un servidor real?

Respuesta: Expone información interna y sensible de la infraestructura del servidor (como capacidad de disco, memoria disponible, nombre del equipo y uso de CPU) a cualquier persona en internet sin control de acceso, facilitando tareas de reconocimiento para posibles ataques.

4. Con polling cada 5 segundos, ¿cuántos pedidos por minuto recibe el servidor si hay 50 personas mirando?

Respuesta: Cada persona realiza 12 peticiones por minuto (60 segundos / 5 segundos). Con 50 usuarios conectados simultáneamente, el servidor recibirá un total de 600 pedidos por minuto ($50 \times 12$), incluso si los datos del sistema no han cambiado.

5. Si una app solo necesita la temperatura, ¿qué datos recibe de más al llamar a /api/metrics?

Respuesta: Recibe toda la estructura completa del JSON: el nombre del equipo (hostname), la versión del sistema operativo, la versión de PHP, el estado completo del disco, la memoria RAM, el porcentaje de uso de CPU y el tiempo de actividad (uptime). Este inconveniente en el que se transfieren más datos de los necesarios se conoce como over-fetching.