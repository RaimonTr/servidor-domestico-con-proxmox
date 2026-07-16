# Servidor doméstico con Proxmox VE

[📖 Leer el manual completo](./servidor-domestico-con-proxmox.md)

> Manual práctico para construir un servidor doméstico con Proxmox VE
> destinado a fotografías, películas, música y otros servicios
> autoalojados. No solo explica cómo hacerlo, sino también por qué se
> tomaron determinadas decisiones de arquitectura.

------------------------------------------------------------------------

## 🧠 Filosofía del proyecto

### ¿Por qué Proxmox VE?

La elección de Proxmox VE no responde a que Ubuntu Server sea insuficiente. Durante mucho tiempo fue la base del proyecto y demostró ser una plataforma sólida y estable. A medida que el servidor fue creciendo, Proxmox VE permitió aislar cada servicio en su propio entorno, simplificando el mantenimiento, las pruebas y las futuras ampliaciones.

Las razones principales fueron:

-   Separar el host de los servicios.
-   Aislar aplicaciones mediante contenedores LXC y máquinas virtuales.
-   Simplificar la administración de una infraestructura con varios
    servicios.
-   Facilitar el crecimiento sin reinstalar el sistema principal.
-   Reducir el impacto de futuras pruebas o experimentos.
-   Aprender virtualización utilizando una plataforma ampliamente
    implantada.

Proxmox no sustituye a Linux: se apoya en él y amplía sus posibilidades.

### Principios de diseño

-   **Simplicidad:** cada componente debe justificar su existencia.
-   **Estabilidad:** priorizar soluciones probadas frente a novedades
    innecesarias.
-   **Reconstrucción:** todo el sistema debe poder reconstruirse desde
    la documentación.
-   **Aislamiento:** separar servicios para reducir riesgos y facilitar
    el mantenimiento.
-   **Documentación:** la documentación forma parte de la
    infraestructura.
-   **Automatización:** automatizar tareas repetitivas siempre que
    aumente la fiabilidad.
-   **Mantenimiento mínimo:** configurar, verificar y dejar que el
    sistema trabaje por sí mismo.

------------------------------------------------------------------------

## 🗂️ Contenido

El manual recorre, entre otros, los siguientes temas:

-   Instalación de Proxmox VE
-   Configuración inicial
-   Almacenamiento
-   Redes
-   Contenedores LXC
-   Máquinas virtuales
-   Docker
-   Immich
-   Jellyfin
-   Navidrome
-   Backups
-   Automatización
-   Seguridad
-   Recuperación y reconstrucción del sistema

------------------------------------------------------------------------

## 👥 ¿A quién va dirigido?

Este manual está pensado para quien quiera montar un servidor doméstico
moderno con Proxmox VE sin necesidad de experiencia previa en
administración de sistemas.

El objetivo no es copiar una configuración concreta, sino comprender las
decisiones necesarias para construir una infraestructura propia,
mantenible y fácil de reconstruir.

------------------------------------------------------------------------

## 📜 Licencia y reconocimiento

Este manual se distribuye bajo la licencia **Creative Commons Atribución
4.0 Internacional (CC BY 4.0)**.

Eres libre de compartir, adaptar y utilizar este contenido, incluso con
fines comerciales, siempre que se mantenga la atribución
correspondiente.

Atribución recomendada:

> Basado en el trabajo de **[RaimonTr](https://github.com/RaimonTr/)**.

Los comandos, scripts y ejemplos de código incluidos en este repositorio
