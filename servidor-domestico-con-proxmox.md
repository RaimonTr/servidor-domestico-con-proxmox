# serviplan
## Libro técnico y humano de un servidor doméstico

---

## 📜 Copyright y Licencia

Este manual se distribuye bajo la licencia **Creative Commons Atribución 4.0 Internacional (CC BY 4.0)**. 

### Contenido técnico y literario
Eres libre de compartir, adaptar y utilizar este material para cualquier propósito, incluso comercial, siempre que se mantenga la atribución correspondiente al autor original:
> Basado en el trabajo de **[RaimonTr](https://github.com/RaimonTr/)**.

### Exención de responsabilidad
*El contenido de este manual se proporciona "tal cual", para fines educativos y sin garantías de ningún tipo. El autor no se hace responsable de pérdidas de datos, fallos de hardware o problemas de seguridad derivados de la aplicación de estas guías.*


---

# Índice general

- [Capítulo 0. El origen](#capítulo-0-el-origen)
- [Capítulo 1. Filosofía del proyecto](#capítulo-1-filosofía-del-proyecto)
- [Capítulo 2. Cronología técnica](#capítulo-2-cronología-técnica)
- [Capítulo 3. Inventario físico](#capítulo-3-inventario-físico)
- [Capítulo 4. Arquitectura lógica](#capítulo-4-arquitectura-lógica)
- [Capítulo 5. Red y comunicaciones](#capítulo-5-red-y-comunicaciones)
- [Capítulo 6. CT100 · Immich](#capítulo-6-ct100--immich)
- [Capítulo 7. CT101 · Multimedia](#capítulo-7-ct101--multimedia)
- [Capítulo 8. Backups y recuperación](#capítulo-8-backups-y-recuperación)
- [Capítulo 9. Operaciones de mantenimiento](#capítulo-9-operaciones-de-mantenimiento)
- [Capítulo 10. Reconstrucción tras desastre](#capítulo-10-reconstrucción-tras-desastre)
- [Capítulo 11. Incidencias históricas y lecciones](#capítulo-11-incidencias-históricas-y-lecciones)
- [Capítulo 12. Filosofía de operación](#capítulo-12-filosofía-de-operación)
- [Capítulo 13. Estado actual y pendientes](#capítulo-13-estado-actual-y-pendientes)
- [Capítulo 14. Hoja de ruta](#capítulo-14-hoja-de-ruta)
- [Capítulo 15. Epílogo](#capítulo-15-epílogo)

---


# Capítulo 0. El origen

> *«Un servidor no nace el día que se instala un sistema operativo. Nace mucho antes, la primera vez que alguien siente curiosidad por entender qué ocurre al otro lado de la pantalla.»*


## Índice

- [0.0 La pérdida de soberanía sobre los datos](#00-la-pérdida-de-soberanía-sobre-los-datos)

- [0.1 Un servidor que empezó mucho antes de existir](#01-un-servidor-que-empezó-mucho-antes-de-existir)

- [0.2 BASIC y la idea de que una máquina podía cambiarse](#02-basic-y-la-idea-de-que-una-máquina-podía-cambiarse)

- [0.3 MS-DOS, memoria convencional y disciplina técnica](#03-ms-dos-memoria-convencional-y-disciplina-técnica)

- [0.4 Los primeros servicios de red](#04-los-primeros-servicios-de-red)

- [0.5 Linux, Ubuntu y la libertad de comprender](#05-linux-ubuntu-y-la-libertad-de-comprender)

- [0.6 macOS y la separación pragmática de funciones](#06-macos-y-la-separación-pragmática-de-funciones)

- [0.7 La pérdida de soberanía sobre los datos](#07-la-pérdida-de-soberanía-sobre-los-datos)

- [0.8 La inteligencia artificial como acelerador](#08-la-inteligencia-artificial-como-acelerador)

- [0.9 El nacimiento de `serviplan`](#09-el-nacimiento-de-serviplan)

- [0.10 Por qué existe este libro](#010-por-qué-existe-este-libro)

- [0.11 Una infraestructura construida por una comunidad](#011-una-infraestructura-construida-por-una-comunidad)

- [0.12 El lector de dentro de veinticinco años](#012-el-lector-de-dentro-de-veinticinco-años)

- [0.13 Cierre](#013-cierre)


---

## 0.0 La pérdida de soberanía sobre los datos

Durante varios años fue creciendo una inquietud dentro de mí difícil de obviar.

La informática personal se hacía más cómoda, pero también más dependiente.

Fotografías, documentos, música, comunicaciones y credenciales empezaban a vivir en servicios gobernados por condiciones legales que podían cambiar unilateralmente y sin avisar.

El problema no era únicamente la privacidad.

Era más amplio.

Se había perdido soberanía sobre:

- quién utiliza los datos;
- cómo los utiliza;
- por qué los utiliza;
- para qué los utiliza;
- dónde viven;
- qué ocurre al abandonar el servicio;
- qué sucede si el proveedor desaparece.

La preocupación podía resumirse así:

> Habíamos dejado de ser dueños efectivos de nuestros datos y soberanos de quién, cómo, por qué y para qué se utilizaban.

Ante ello, la única alternativa real que me quedaba era montarme un servidor personal en mi propia casa, `serviplan`.

`serviplan`, no pretende eliminar a los proveedores comerciales de servicios como Google Photos, OneDrive, Spotify, Youtube...

Pretende conservar la capacidad de marcharme cómo y cuándo yo decida (aviso: ya me he ido).

No existe para sustituir cualquier servicio externo, sino para impedir que un cambio de condiciones, una decisión empresarial o una pérdida de confianza obliguen a permanecer donde ya no se desea estar.

La infraestructura propia no elimina la dependencia del mundo exterior.

Reduce el coste de abandonarla.


## 0.1 Un servidor que empezó mucho antes de existir

`serviplan` no nació el día en que se instaló Proxmox.

Tampoco nació cuando Ubuntu Server empezó a ejecutar Immich, Navidrome o Jellyfin, ni cuando apareció la idea concreta de dedicar un ordenador a almacenar fotografías, música y otros datos personales.

Su origen es anterior a cualquiera de esas decisiones.

Empieza en una forma de relacionarse con los ordenadores que se construyó durante décadas: comprender antes de aceptar, probar antes de dar algo por cerrado y aprender haciendo.

Si hoy se observa el ordenador marca MSI que actúa como host de [Proxmox](https://www.proxmox.com/en/)([Wikipedia](https://es.wikipedia.org/wiki/Proxmox_Virtual_Environment)), pueden describirse correctamente su hardware, el sistema operativo, los contenedores y los servicios.

Esa descripción explica qué es `serviplan`.

No explica por qué terminó existiendo.

Este capítulo responde a esa segunda pregunta.

---

## 0.2 BASIC y la idea de que una máquina podía cambiarse

Hubo una época en la que aprender informática significaba, casi inevitablemente, aprender a programar algo.

BASIC no aparecía como una especialización académica ni como una decisión profesional. Era una de las pocas formas disponibles de conseguir que un ordenador hiciera algo distinto de lo previsto por quien lo había fabricado.

Aquella experiencia dejó una idea que seguiría presente décadas después:

> Un ordenador no es únicamente una herramienta terminada. También es un sistema que puede modificarse.

Programar enseñaba a dividir problemas, probar soluciones, interpretar errores y comprender que una máquina no ejecuta deseos, sino instrucciones.

La misma disciplina reaparece hoy en Python, lenguaje M, Bash, `systemd`, Docker Compose o cualquier otro mecanismo de automatización.

Las herramientas han cambiado.

La relación con ellas, no tanto.

---

## 0.3 MS-DOS, memoria convencional y disciplina técnica

"_La **terminal** o **consola** es una forma generalizada de llamar a la interfaz de usuario de línea de comandos: una pantalla donde escribiendo **comandos** (*secuencias de palabras especiales*) ordenamos al sistema realizar acciones concretas_" ([Fuente](https://terminaldelinux.com/terminal/introduccion/que-es-terminal/)).

MS-DOS consolidó la familiaridad con la línea de comandos, tambien conocida como CMD o [PowerShell](https://learn.microsoft.com/es-es/powershell/scripting/overview?view=powershell-7.6) en entornos Windows, o Konsole/Terminal en entornos Linux/macOS.

En aquel contexto, la Terminal no era una alternativa avanzada a la interfaz gráfica.

Era el sistema. El único.

"_La barrera de los **640 KB** y el archivo **AUTOEXEC.BAT** son dos de los conceptos más icónicos de la era MS-DOS. Juntos representaban el límite de memoria del sistema y el archivo de texto que los usuarios debían "hackear" manualmente para liberar cada byte posible y poder ejecutar los exigentes juegos y programas de la época_" ([Fuente](https://www.youtube.com/watch?v=R7LPUxwPfMw&t=17s)). 

Optimizar `AUTOEXEC.BAT` y `CONFIG.SYS` para recuperar memoria convencional obligaba a comprender:

- qué cargaba el sistema;
- en qué orden;
- qué podía moverse a memoria alta;
- qué controlador era imprescindible`
- qué podía eliminarse;
- cuánto consumía cada componente.

No era solo una cuestión de rendimiento.

Era una escuela de administración de recursos.

De ahí procede buena parte de la importancia que el proyecto concede a:

- salidas legibles;
- logs;
- scripts reproducibles;
- nombres claros;
- procedimientos verificables;
- comprensión de cada paso.

La afinidad con la Terminal no nace de una moda reciente. Procede de una época en la que escribir comandos era la manera natural de trabajar.

---

## 0.4 Los primeros servicios de red

Antes de Android, del iPhone y de WhatsApp, ya existía la curiosidad por conectar máquinas y personas.

Uno de los primeros proyectos personales relevantes fue un servidor Windows utilizado para montar una aplicación de chat basada en IP.

La tecnología concreta importa menos que el cambio de perspectiva que produjo.

Un ordenador podía dejar de ser una máquina utilizada directamente y convertirse en infraestructura:

- escuchar;
- responder;
- almacenar;
- conectar;
- permanecer disponible.

`serviplan` hereda esa idea.

Aunque el hardware, el sistema operativo y los servicios sean distintos, el principio es el mismo: una máquina organizada para prestar servicios útiles de forma permanente.

---

## 0.5 Linux, Ubuntu y la libertad de comprender

La llegada de Linux abrió una etapa distinta.

Ubuntu, especialmente durante sus primeros años, produjo la sensación de estar ante algo extraordinario: un sistema completo, modificable, documentado y construido por una comunidad.

Permitía decidir:

- qué instalar;
- qué eliminar;
- cómo organizar el sistema;
- qué servicios ejecutar;
- qué automatizar;
- qué parte del sistema debía permanecer visible y comprensible.

La libertad no era únicamente económica.

Era técnica.

Linux demostraba que un sistema operativo podía comprenderse, adaptarse y reconstruirse sin depender de una única empresa.

Esa experiencia es esencial para entender por qué `serviplan` siguió apoyándose en Linux después de migrar a Proxmox.

La virtualización no sustituyó a Linux.

Proxmox amplió una base que ya se consideraba prácticamente ilimitada.

---

## 0.6 macOS y la separación pragmática de funciones

La relación con Linux nunca fue idealizada.

Con los años apareció también cansancio ante la fragmentación del ecosistema, determinadas inconsistencias y el tiempo necesario para mantener aspectos que, en un equipo de uso diario, debían resultar transparentes.

macOS terminó convirtiéndose en el entorno principal de trabajo personal.

La decisión no implicó abandonar Linux ni renunciar a lo aprendido.

Supuso separar funciones.

El Mac podía ofrecer:

- estabilidad cotidiana;
- herramientas de trabajo;
- integración con [Strongbox](https://strongboxsafe.com/) (un buen gestor de contraseñas para entornos Mac);
- administración remota;
- una Terminal Unix;
- comodidad como equipo personal.

Linux podía permanecer donde más valor aportaba:

- servidores;
- automatización;
- contenedores;
- servicios;
- infraestructura.

`serviplan` nace también de esa separación pragmática.

No existe una obligación ideológica de utilizar una única plataforma para todo.

Cada herramienta debe ocupar el lugar donde resuelve mejor el problema.

---

## 0.7 La pérdida de soberanía sobre los datos

Reconvertido a 0.0. Pensé que mejor lo ponía al principio.

---

## 0.8 La inteligencia artificial como acelerador

La inteligencia artificial fue el impulso que faltaba para convertir una idea madura en una infraestructura real.

Eso no significa que pudiera construir `serviplan` por sí sola.

Sin décadas de bagaje previo, el proyecto no habría existido.

La IA redujo fricción al:

- localizar documentación;
- comparar alternativas;
- explicar errores;
- proponer comandos;
- revisar scripts;
- estructurar procedimientos;
- transformar conversaciones en documentación.

Pero seguía siendo necesario:

- comprender;
- evaluar;
- decidir;
- detectar errores;
- validar;
- asumir la responsabilidad.

La IA no sustituyó el conocimiento.

Lo amplificó.

`serviplan` nació en la intersección entre dos trayectorias:

1. décadas de experiencia acumulada;
2. una herramienta nueva capaz de acelerar la materialización de esa experiencia.

---

## 0.9 El nacimiento de `serviplan`

La idea empezó a convertirse en sistema cuando aparecieron necesidades concretas:

- salir de Google Fotos;
- conservar una biblioteca musical propia;
- alojar contenido multimedia;
- realizar copias de seguridad;
- reducir dependencia de grandes plataformas;
- aprender Linux y administración de sistemas;
- divertirse [cacharreando](https://dle.rae.es/cacharrear?m=form).

El primer hogar fue Ubuntu Server.

Después llegó Proxmox.

El propósito, sin embargo, permaneció estable:

- soberanía tecnológica;
- independencia frente a proveedores;
- control sobre los datos;
- aprendizaje;
- diversión;
- capacidad de reconstrucción.

`serviplan` no es un proyecto terminado.

Es una plataforma desde la que seguir probando ideas sin reinstalar ni comprometer el sistema principal.

---

## 0.10 Por qué existe este libro

Este documento no es únicamente un manual.

Tampoco es una autobiografía.

Es el libro técnico y humano de `serviplan`.

Debe explicar:

- qué existe;
- cómo funciona;
- por qué se hizo así;
- qué errores se cometieron;
- qué se descartó;
- qué piezas proceden de la [Comunidad](https://es.wikipedia.org/wiki/Comunidad_del_software_libre);
- qué decisiones pertenecen al autor;
- cómo reconstruir todo el sistema.

El éxito del libro no consiste en que su autor pueda reconstruir el servidor.

Consiste en que pueda hacerlo otra persona sin haber hablado nunca con él.

Eso obliga a eliminar conocimientos implícitos.

No puede depender de frases como:

- «ya me acordaré»;
- «esto estaba en un chat»;
- «la ruta era parecida»;
- «creo que el servicio se llamaba así».

La documentación debe sustituir a la memoria cuando la memoria ya no esté disponible.

---

## 0.11 Una infraestructura construida por una comunidad

Si `serviplan` sigue funcionando dentro de veinticinco años, no será únicamente un éxito personal.

Será también un éxito de la comunidad.

El proyecto se apoya en trabajos creados por miles de personas:

- Linux;
- Debian;
- Ubuntu;
- Proxmox;
- Docker;
- Immich;
- Jellyfin;
- Navidrome;
- Tailscale;
- OpenSSH;
- `systemd`;
- `rclone`;
- Python;
- y muchas otras piezas.

El autor no ha inventado esos componentes.

Ha intentado combinarlos de forma coherente para resolver problemas personales reales.

Reconocer ese origen evita convertir el proyecto en un monumento individual.

`serviplan` es una construcción propia realizada con herramientas comunitarias.

---

## 0.12 El lector de dentro de veinticinco años

Si dentro de veinticinco años alguien encuentra el servidor funcionando, probablemente le sorprenderá la cantidad de tiempo dedicada a documentarlo.

Quizá piense:

> Vaya flipado, el flaco este.

No sería una conclusión injusta.

Pero si después puede:

- leer el libro;
- comprender la arquitectura;
- conectarse;
- identificar los servicios;
- recuperar las credenciales;
- mantener el sistema;
- reconstruirlo si falla;

entonces la documentación habrá cumplido su función.

No necesita parecer solemne.

Necesita ser útil.

---

## 0.13 Cierre

`serviplan` no nace de una tecnología concreta.

Nace de una continuidad.

BASIC enseñó a ordenar instrucciones.

MS-DOS enseñó a comprender recursos.

Los primeros servidores enseñaron a prestar servicios.

Linux enseñó libertad y control.

macOS enseñó pragmatismo y separación de funciones.

La inteligencia artificial redujo fricción.

La preocupación por los datos proporcionó el motivo.

Y la curiosidad hizo el resto.

La frase que mejor resume el origen del proyecto no es técnica:

> La mejor forma de aprender informática sigue siendo cacharreando.

Todo lo que aparece en los capítulos siguientes procede, de una forma u otra, de esa convicción.

---

# Capítulo 1. Filosofía del proyecto

> *«La tecnología cambia. Los principios permanecen.»*

## Índice

- [1.1 Qué pretende realmente `serviplan`](#11-qué-pretende-realmente-serviplan)

- [1.2 Lo que este proyecto no es](#12-lo-que-este-proyecto-no-es)

- [1.3 Soberanía tecnológica](#13-soberanía-tecnológica)

- [1.4 Independencia razonable frente a proveedores](#14-independencia-razonable-frente-a-proveedores)

- [1.5 Simplicidad como decisión técnica](#15-simplicidad-como-decisión-técnica)

- [1.6 Documentar para desaparecer](#16-documentar-para-desaparecer)

- [1.7 Estabilidad y experimentación](#17-estabilidad-y-experimentación)

- [1.8 El valor de eliminar](#18-el-valor-de-eliminar)

- [1.9 Reconstrucción antes que improvisación](#19-reconstrucción-antes-que-improvisación)

- [1.10 La comunidad como cimiento](#110-la-comunidad-como-cimiento)

- [1.11 Principios permanentes](#111-principios-permanentes)

- [1.12 Cierre](#112-cierre)

---

## 1.1 Qué pretende realmente `serviplan`

`serviplan` no pretende ser el servidor más potente, el más complejo ni el más espectacular.

Su objetivo es más sencillo y, al mismo tiempo, más exigente: disponer de una infraestructura personal que permita conservar el control sobre los propios datos, aprender continuamente y seguir disfrutando de la informática.

El proyecto persigue cuatro metas permanentes:

1. soberanía tecnológica;
2. independencia razonable frente a proveedores;
3. capacidad de reconstrucción;
4. diversión y aprendizaje.

Estas metas no dependen de una versión concreta de Proxmox, de un contenedor determinado ni de una aplicación específica.

Las herramientas pueden cambiar.

La intención del proyecto debe permanecer.

---

## 1.2 Lo que este proyecto no es

`serviplan` no es:

- un laboratorio donde cambiar el sistema operativo cada semana;
- una colección de contenedores «por si acaso»;
- un intento de sustituir todos los servicios de Internet;
- una infraestructura tan compleja que solo su autor pueda entender;
- una demostración de que cualquier cosa autoalojada es automáticamente mejor;
- una excusa para introducir tecnología sin una necesidad concreta.

La estabilidad forma parte del diseño.

La experimentación debe producirse alrededor del sistema estable, no sustituyéndolo.

---

## 1.3 Soberanía tecnológica

La motivación principal del proyecto es recuperar capacidad de decisión.

No significa dejar de utilizar servicios externos.

Significa poder abandonarlos cuando sea necesario sin empezar desde cero.

La infraestructura propia debe proporcionar una alternativa preparada para ese momento.

La soberanía no consiste en poseer físicamente cada componente.

Consiste en conservar control suficiente sobre:

- los datos;
- las credenciales;
- las copias;
- los formatos;
- los procedimientos;
- las dependencias;
- la ruta de salida.

---

## 1.4 Independencia razonable frente a proveedores

Las empresas cambian.

Las condiciones de uso cambian.

Los modelos de negocio cambian.

Los servicios desaparecen.

Cuando eso ocurra, `serviplan` debe permitir migrar con el menor coste posible.

No garantiza independencia absoluta.

Garantiza libertad para elegir.

Esa diferencia es importante.

Un proyecto doméstico no necesita fingir autosuficiencia total. Necesita impedir que una dependencia concreta se convierta en cautiverio.

---

## 1.5 Simplicidad como decisión técnica

Cada componente debe justificar su existencia.

Si un servicio deja de aportar valor, se elimina.

Si una capa no resuelve un problema concreto, no se añade.

Si dos soluciones son técnicamente válidas, se prefiere la que resulte más comprensible, mantenible y reconstruible.

La simplicidad no equivale a pobreza técnica.

Es una forma de control.

La complejidad solo es aceptable cuando resuelve un problema real y su coste operativo está comprendido.

---

## 1.6 Documentar para desaparecer

La documentación no existe únicamente para ayudar al autor.

Existe para que otra persona pueda comprender y mantener el sistema sin haber hablado nunca con él.

El éxito de este libro será que el servidor pueda seguir vivo aunque su creador no esté junto a ti.

Eso exige que la documentación incluya:

- estado vigente;
- historia;
- decisiones;
- dependencias;
- rutas;
- credenciales indirectas;
- procedimientos;
- pendientes;
- límites conocidos.

Documentar no es describir lo que se recuerda.

Es reducir la cantidad de memoria necesaria para reconstruir.

---

## 1.7 Estabilidad y experimentación

El host, los servicios principales y los backups deben permanecer estables.

Las nuevas ideas se prueban en LXC (tecnología de [virtualización a nivel de sistema operativo](https://es.wikipedia.org/wiki/LXC)) para [Linux](https://es.wikipedia.org/wiki/Linux_(núcleo)) o máquinas virtuales aisladas.

Así el proyecto puede evolucionar sin poner en riesgo lo que ya funciona.

La arquitectura debe separar dos zonas:

### Zona estable

- host Proxmox (el sistema operativo del portátil MSI);
- red;
- almacenamiento;
- CT100 (contenedor para fotos, mi Google Photos particular);
- CT101 (música, películas);
- acceso administrativo (acceder al ordenador sin tener que sentarme delante);
- backups;
- documentación.

### Zona experimental

- contenedores temporales ;
- máquinas virtuales de prueba (por ejemplo, montar un windows para jugar desde cualquier dispositivo);
- laboratorios (p. e. montar Kali, herramienta para pruebas de penetración y hacking);
- servicios candidatos (¿un servicio [autoalojado de contraseñas](https://bitwarden.com/es-la/self-hosted-password-manager-on-premises/)?);
- configuraciones desechables.

La curiosidad es parte del proyecto.

También lo es impedir que esa curiosidad destruya lo que ya funciona.

---

## 1.8 El valor de eliminar

En `serviplan`, eliminar no representa necesariamente un fracaso.

Puede representar una decisión consciente.

Los componentes sin utilidad desaparecen, la historia permanece documentada; la infraestructura no acumula lastre.

El tiempo invertido en una prueba no obliga a mantenerla indefinidamente.

Conservar algo solo porque costó trabajo construirlo es una forma de deuda técnica.

---

## 1.9 Reconstrucción antes que improvisación

Una configuración no se considera realmente comprendida mientras no pueda explicarse cómo reconstruirla.

El proyecto prioriza:

- procedimientos repetibles;
- rutas conocidas;
- dependencias explícitas;
- copias verificables;
- separación entre estado actual e historia;
- identificación clara de lo no confirmado.

La reconstrucción prevalece sobre la improvisación porque obliga a distinguir lo esencial de lo accesorio.

También evita que el sistema dependa de soluciones cuya lógica solo existe en la memoria de una persona.

---

## 1.10 La comunidad como cimiento

Vuelvo a insistir en otra de las revisiones de este manual: nada de este proyecto existiría sin el trabajo de miles de personas.

Linux, Debian, Proxmox, Docker, Immich, Jellyfin, Navidrome, Tailscale, OpenSSH, Python, `systemd`, `rclone` y muchas otras herramientas forman la base sobre la que se construye `serviplan`.

Este libro documenta cómo se combinan.

No pretende atribuirse su mérito.

El proyecto es personal.

Sus cimientos son comunitarios.

---

## 1.11 Principios permanentes

1. La documentación forma parte de la infraestructura.
2. Lo no verificado se marca como pendiente.
3. La reconstrucción prevalece sobre la improvisación.
4. La simplicidad tiene prioridad sobre la sofisticación.
5. La estabilidad y el aprendizaje pueden convivir.
6. Los datos pertenecen a quien los genera.
7. Cada componente debe justificar su existencia.
8. La historia se conserva, pero no se confunde con el estado vigente.
9. Los experimentos deben estar aislados.
10. El sistema debe seguir siendo divertido de mantener.

---

## 1.12 Cierre

La mejor definición de `serviplan` no es una lista de servicios.

Es una forma de entender la informática:

- construir;
- comprender;
- documentar;
- conservar el control;
- reducir dependencias;
- reconstruir;
- seguir aprendiendo.

Todo lo demás —hardware, sistemas operativos y aplicaciones— podrá cambiar con el tiempo.

---

# Capítulo 2. Cronología técnica
## Parte 1 · Del origen intelectual al primer `serviplan`

> **Función del capítulo**  
> Este capítulo explica cómo se formó la arquitectura actual de `serviplan`, qué decisiones condujeron a ella y qué hechos pertenecen ya a la historia. No sustituye al inventario ni a los procedimientos de reconstrucción: aporta el orden causal que permite comprenderlos.

## Índice del capítulo

- [2.1 Cómo leer esta cronología](#21-cómo-leer-esta-cronología)
- [2.2 Lo que ocurrió antes de `serviplan`](#22-lo-que-ocurrió-antes-de-serviplan)
- [2.3 La soberanía tecnológica como motivo](#23-la-soberanía-tecnológica-como-motivo)
- [2.4 La primera implantación sobre Ubuntu Server](#24-la-primera-implantación-sobre-ubuntu-server)
- [2.5 Cuando un servidor se convirtió en infraestructura](#25-cuando-un-servidor-se-convirtió-en-infraestructura)
- [2.6 El valor histórico de la etapa Ubuntu](#26-el-valor-histórico-de-la-etapa-ubuntu)

---

## 2.1 Cómo leer esta cronología

La historia de `serviplan` contiene tres clases de información que no deben mezclarse.

| Categoría | Qué contiene | Cómo debe interpretarse |
|---|---|---|
| **Historia** | Sistemas anteriores, pruebas, errores, componentes retirados y decisiones ya superadas | Explica cómo se llegó al presente, pero no debe reconstruirse automáticamente |
| **Estado canónico** | Arquitectura y decisiones vigentes | Describe lo que debe existir mientras no haya una revisión expresa |
| **Pendientes** | Capacidades no aprendidas, pruebas no completadas y decisiones aún abiertas | No deben presentarse como resueltas ni incorporadas |

Cuando no existe una fecha exacta confirmada, este capítulo conserva el orden relativo de los hechos sin inventar un día concreto.

---

## 2.2 Lo que ocurrió antes de `serviplan`

La instalación de Proxmox no fue el principio del proyecto. Tampoco lo fue la primera instalación de Ubuntu Server.

Antes de que existiera una máquina llamada `serviplan`, ya se había formado una manera concreta de trabajar con los ordenadores: comprender antes de aceptar, probar antes de dar por cerrado y documentar aquello que debía poder repetirse.

Décadas de experiencia con BASIC, MS-DOS, `AUTOEXEC.BAT`, `CONFIG.SYS`, programación, Windows Server, Linux, Ubuntu, macOS, redes, automatización, scripting y análisis de datos no constituyen todavía la historia operativa del servidor, pero explican por qué el proyecto pudo materializarse.

De esa trayectoria proceden varias ideas que después reaparecerían en la arquitectura:

1. un ordenador puede ser modificado y comprendido;
2. los recursos deben administrarse conscientemente;
3. un servidor es una pieza de infraestructura, no solo un equipo encendido;
4. la línea de comandos, los logs y los scripts reproducibles son instrumentos normales de trabajo;
5. una tecnología abandonada no implica necesariamente conocimiento perdido.

La inteligencia artificial redujo la fricción para localizar documentación, comparar alternativas, revisar comandos y transformar conversaciones en procedimientos. No sustituyó el criterio técnico acumulado ni la responsabilidad de validar cada cambio.

---

## 2.3 La soberanía tecnológica como motivo

Con el tiempo, la preocupación dejó de ser exclusivamente técnica.

Fotografías, música, documentos, credenciales y otros datos personales dependían cada vez más de servicios cuyas condiciones podían cambiar unilateralmente. El problema no era solo la privacidad, sino la pérdida de capacidad para decidir:

- dónde viven los datos;
- quién puede utilizarlos;
- cómo se recuperan;
- qué ocurre al abandonar un proveedor;
- qué sucede si el servicio desaparece;
- cuánto cuesta conservar una salida viable.

`serviplan` no nació con el propósito de sustituir todos los servicios externos. Nació para conservar la libertad de marcharse.

> La independencia absoluta no era el objetivo. La capacidad real de elegir sí lo era.

Esa motivación se concretó en necesidades prácticas:

- abandonar o reducir la dependencia de Google Fotos;
- conservar una biblioteca musical propia;
- alojar servicios multimedia;
- disponer de copias locales y externas;
- aprender administración de sistemas;
- construir una infraestructura útil y, al mismo tiempo, divertida de mantener.

---

## 2.4 La primera implantación sobre Ubuntu Server

El primer `serviplan` operativo se construyó sobre [Ubuntu Server](https://ubuntu.com/download/server) instalado directamente en el hardware.

_"Ubuntu Server es una variante del sistema operativo Ubuntu diseñada específicamente para entornos de servidor. Basado en el kernel de Linux, proporciona una plataforma estable para alojar sitios web, ejecutar aplicaciones y gestionar servicios de red._

_A diferencia de la versión de escritorio, Ubuntu Server no incluye una interfaz gráfica por defecto, lo que lo hace más liviano y eficiente para su uso como servidor._

_**Principales características de Ubuntu Server:**_

_- Interfaz de línea de comandos para una gestión remota eficiente._
_- Menores requisitos de recursos en comparación con las versiones de escritorio._
_- Funciones de seguridad integradas y actualizaciones de seguridad regulares._
_- Soporte para una amplia gama de aplicaciones y servicios de servidor._
_- Escalabilidad para satisfacer las necesidades crecientes de una empresa."_ [Fuente](https://contabo.com/blog/es/ubuntu-server-instalacion-configuracion-y-beneficios/).

La elección fue deliberadamente conservadora: una plataforma estable, ampliamente documentada y conocida. Sobre ella se consolidaron progresivamente:

- Docker;
- Immich;
- Navidrome;
- Jellyfin;
- Tailscale;
- scripts de mantenimiento;
- timers de `systemd`;
- copias de seguridad;
- procedimientos operativos;
- documentación inicial.

La arquitectura era monolítica en el sentido de que todos los servicios, automatizaciones y dependencias compartían el mismo sistema operativo base.

```text
Hardware
└── Ubuntu Server
    ├── Docker
    │   ├── Immich
    │   ├── Navidrome
    │   └── Jellyfin
    ├── Tailscale
    ├── scripts
    ├── timers
    └── backups
```

Esta etapa funcionó con solidez.

> **Hecho histórico confirmado**  
> Ubuntu Server no dejó de ser válido ni fue sustituido por haber fracasado.

La migración posterior no corrigió una plataforma defectuosa. Respondió a un deseo de aprender virtualización, separar responsabilidades y disponer de un entorno más preparado para crecer y experimentar.

---

## 2.5 Cuando un servidor se convirtió en infraestructura

Cada nuevo servicio parecía pequeño de manera aislada, pero el conjunto empezó a compartir ciclos de mantenimiento, almacenamiento, dependencias, acceso remoto y políticas de copia.

Immich, Jellyfin, Navidrome, los scripts, los timers y los backups dejaron de ser aplicaciones independientes instaladas en un equipo. Formaban un sistema.

Ese cambio fue conceptual antes que técnico.

A partir de ese momento, cualquier modificación importante debía evaluarse teniendo en cuenta:

- aislamiento;
- recuperación;
- dependencias;
- capacidad de ampliación;
- observabilidad;
- impacto sobre servicios ya estables;
- posibilidad de reconstrucción.

La pregunta dejó de ser «¿puede instalarse esta aplicación?» y pasó a ser «¿en qué capa debe vivir, cómo se mantiene y cómo se recupera?».

---

## 2.6 El valor histórico de la etapa Ubuntu

La etapa Ubuntu estableció la mayor parte de los servicios que después sobrevivirían a la migración.

También permitió aprender qué elementos eran realmente valiosos y cuáles podían reorganizarse:

| Elemento | Resultado histórico |
|---|---|
| Linux | Se confirmó como base permanente del proyecto |
| Docker | Se mantuvo como mecanismo de despliegue de aplicaciones |
| Immich | Se consolidó como servicio crítico |
| Navidrome y Jellyfin | Se consolidaron como ecosistema multimedia |
| Tailscale | Se mantuvo, pero cambió de ubicación arquitectónica |
| Scripts y timers | Se conservaron, adaptaron o reescribieron |
| Backups | Pasaron de estar ligados al servidor monolítico a dividirse por función |
| Documentación | Dejó de ser apoyo y se convirtió en parte de la infraestructura |

La conclusión de esta primera etapa fue doble:

1. el proyecto ya resolvía necesidades reales;
2. su siguiente evolución debía reorganizarlo sin destruir lo que funcionaba.

---

---

# Capítulo 2. Cronología técnica
## Parte 2 · La decisión de migrar y el Big Bang de Proxmox

## Índice de esta parte

- [2.7 El MSI reutilizado](#27-el-msi-reutilizado)
- [2.8 Por qué Proxmox](#28-por-qué-proxmox)
- [2.9 La sustitución del SSD](#29-la-sustitución-del-ssd)
- [2.10 La migración concentrada](#210-la-migración-concentrada)
- [2.11 Del sistema monolítico a las capas](#211-del-sistema-monolítico-a-las-capas)
- [2.12 CT100 · Immich](#212-ct100--immich)
- [2.13 CT101 · Multimedia](#213-ct101--multimedia)
- [2.14 Red, direccionamiento y arranque](#214-red-direccionamiento-y-arranque)
- [2.15 El host como infraestructura](#215-el-host-como-infraestructura)
- [2.16 Docker dentro de LXC](#216-docker-dentro-de-lxc)
- [2.17 Passthrough de la GPU](#217-passthrough-de-la-gpu)

---

## 2.7 El MSI reutilizado

El hardware elegido fue un MSI Modern 15 H C13M, más que nada poque estaba por casa (en un cajón, para más dato).

> Antes de comprar hardware nuevo, comprobar si el hardware existente ya resuelve el problema.

El equipo ofrecía potencia suficiente, consumo razonable, funcionamiento silencioso y una batería que podía actuar como una pequeña protección frente a cortes breves. Su formato de portátil introducía limitaciones, pero también ventajas operativas que justificaban reutilizarlo, como disponer de teclado, ratón y pantalla, algo importante cuando montas un servidor y no consigues configurar adecuadamente el acceso remoto o la conexion de red. 

---

## 2.8 Por qué Proxmox

La motivación principal de la migración fue aprender.

Proxmox ofrecía de forma integrada capacidades que podían haberse construido manualmente sobre Ubuntu, pero que resultaban más naturales dentro de una plataforma de virtualización:

- contenedores LXC;
- máquinas virtuales;
- administración centralizada;
- separación entre host e invitados;
- snapshots como capacidad futura;
- passthrough de hardware;
- ampliación sin reinstalar el sistema principal;
- laboratorios aislados.

No se pretendía sustituir Linux. Proxmox seguía siendo Linux y permitía ampliar la forma de utilizarlo.

La decisión buscaba mantener estable la infraestructura principal y trasladar la experimentación a espacios sustituibles.

---

## 2.9 La sustitución del SSD

La migración se realizó sobre un SSD nuevo.

La sustitución permitió preservar temporalmente la instalación anterior y reducir el riesgo de destruir el único sistema operativo funcional durante el cambio.

Esta decisión separó dos problemas:

1. construir la nueva arquitectura;
2. conservar una vía de retorno mientras se validaba.

El SSD anterior no se convirtió por ello en parte permanente de la arquitectura. Su valor fue histórico y transitorio: permitió migrar sin depender de una sobrescritura irreversible.

---

## 2.10 La migración concentrada

La mayor parte del cambio se realizó prácticamente en una sola jornada de principios de junio de 2026.

El orden general fue:

1. instalar Proxmox;
2. configurar el host;
3. crear CT100;
4. crear CT101;
5. configurar red e IP;
6. validar DNS y acceso LAN;
7. instalar y centralizar Tailscale;
8. publicar servicios con Tailscale Serve;
9. rehacer alias y acceso SSH;
10. integrar Strongbox como agente SSH;
11. adaptar scripts;
12. adaptar o crear timers;
13. reorganizar backups;
14. validar servicios.

Exteriormente, al final de la jornada se ofrecían casi las mismas funciones que antes.

Internamente, la organización había cambiado por completo.

```text
Ubuntu Server bare-metal
            ↓
Proxmox VE
            ↓
CT100 + CT101
            ↓
Tailscale centralizado
            ↓
Backups diferenciados
            ↓
Canon reconstruible
```

La elección de una migración Big Bang (enfoque en el que todos los datos o sistemas se transfieren al nuevo entorno en una sola operación simultánea) fue contextual. No debe interpretarse como recomendación universal.

---

## 2.11 Del sistema monolítico a las capas

La nueva arquitectura quedó organizada así:

```text
MSI Modern 15 H C13M
└── Proxmox VE
    ├── infraestructura del host
    ├── CT100
    │   └── Docker
    │       └── Immich
    └── CT101
        └── Docker
            ├── Navidrome
            └── Jellyfin
```

La capa adicional no se añadió por gusto por la complejidad.

El host debía ocuparse de:

- virtualización;
- red;
- almacenamiento;
- acceso remoto;
- backups del entorno;
- administración de invitados;
- configuración VFIO.

Los contenedores debían ocuparse de los servicios de usuario.

La separación reducía el alcance de cada problema, pero introducía una obligación documental: cualquier instrucción debía indicar con claridad si correspondía al host, a CT100 o a CT101.

---

## 2.12 CT100 · Immich

CT100 se creó como unidad funcional dedicada a Immich.

Immich no es un único proceso. Su stack incluye el servidor, machine learning, PostgreSQL, Valkey, biblioteca, configuración y base de datos. Agrupar el conjunto en un LXC permitía administrarlo y recuperarlo como una sola unidad sin dedicarle una máquina virtual completa.

### Configuración consolidada

| Parámetro | Valor |
|---|---:|
| Cores | 4 |
| RAM | 8 GB |
| Swap | 2 GB |
| Disco raíz | 60 GB |
| Tipo | LXC no privilegiado |
| Opciones | `nesting=1`, `keyctl=1` |
| Arranque automático | Sí |
| Orden de inicio | 10 |
| IP reservada | `192.168.1.101` |
| Puerto de Immich | `2283` |

> **Estado canónico**  
> CT100 corresponde a Immich. Esta asociación no debe alterarse durante una reconstrucción fiel sin una decisión expresa.

---

## 2.13 CT101 · Multimedia

CT101 se dedicó al ecosistema multimedia:

- Navidrome;
- Jellyfin;
- bibliotecas de música;
- películas;
- series;
- directorio de entrada.

Navidrome y Jellyfin compartían naturaleza, almacenamiento y mantenimiento. Separarlos en contenedores distintos habría aumentado el número de invitados, copias, configuraciones y puntos de diagnóstico sin una necesidad confirmada.

### Configuración consolidada

| Parámetro | Valor |
|---|---:|
| Cores | 4 |
| RAM | 4 GB |
| Swap | 1 GB |
| Disco | 400 GB |
| Tipo | LXC no privilegiado |
| Opciones | `nesting=1`, `keyctl=1` |
| Arranque automático | Sí |
| Orden de inicio | 20 |
| IP reservada | `192.168.1.102` |
| Navidrome | `4533` |
| Jellyfin | `8096` |

> **Estado canónico**  
> CT101 corresponde al ecosistema multimedia.

---

## 2.14 Red, direccionamiento y arranque

El host mantuvo el nombre `serviplan` y la IP LAN `192.168.1.99`.

Los contenedores quedaron dentro de un rango reconocible para servicios Proxmox:

```text
Host:   192.168.1.99
CT100:  192.168.1.101
CT101:  192.168.1.102
Rango reservado para servicios: 192.168.1.101-192.168.1.110
```

Los invitados utilizaban DHCP con reservas en el router. Esto mantenía direcciones estables sin fijarlas manualmente dentro de cada contenedor.

La red de Proxmox se articuló alrededor de `vmbr0`, conectado a Ethernet. El host utilizó `192.168.1.99/24` y gateway `192.168.1.1`. La Wi-Fi quedó fuera del camino operativo normal.

El orden de arranque se fijó así:

1. CT100, orden 10;
2. CT101, orden 20.

CT101 no dependía estrictamente de CT100. La secuencia evitaba un arranque simultáneo innecesario y dejaba una política comprensible para futuras ampliaciones.

---

## 2.15 El host como infraestructura

Una regla de diseño fue impedir que Proxmox se convirtiera en otro servidor monolítico.

El host podía contener:

- Proxmox;
- Tailscale;
- herramientas de administración;
- scripts de backup;
- configuración de red;
- VFIO;
- servicios estrictamente necesarios para operar la plataforma.

No debía ejecutar directamente:

- Immich;
- Navidrome;
- Jellyfin;
- stacks Docker de aplicaciones;
- servicios experimentales.

Esta frontera facilita actualizaciones, diagnósticos y reconstrucción.

---

## 2.16 Docker dentro de LXC

Docker no fue sustituido. Cambió el lugar donde se ejecutaba.

```text
Proxmox
└── LXC
    └── Docker
        └── aplicaciones
```

LXC separaba grupos funcionales y proporcionaba unidades administrables desde Proxmox.

Docker mantenía el mecanismo de despliegue habitual u oficial de las aplicaciones.

Ambas capas resolvían problemas diferentes. La combinación era aceptable mientras permaneciera documentada y validada.

---

## 2.17 Passthrough de la GPU

La iGPU Intel se preparó para passthrough mediante IOMMU y VFIO con el objetivo de permitir aceleración por hardware en servicios multimedia.

Esta parte del host era especialmente sensible porque combinaba:

- parámetros de arranque;
- módulos del kernel;
- VFIO;
- identificación del dispositivo;
- asignación al invitado;
- validación dentro del contenedor.

La corrección posterior de una entrada obsoleta confirmó que esta configuración no debía reconstruirse a partir de recetas antiguas. Solo debía utilizarse el estado vigente y comprobado.

---

---

# Capítulo 2. Cronología técnica
## Parte 3 · Consolidación: acceso, red privada y copias

## Índice de esta parte

- [2.18 La migración no terminó con el primer arranque](#218-la-migración-no-terminó-con-el-primer-arranque)
- [2.19 Tailscale como capa única de acceso remoto](#219-tailscale-como-capa-única-de-acceso-remoto)
- [2.20 HTTP dentro de la tailnet](#220-http-dentro-de-la-tailnet)
- [2.21 La normalización de SSH](#221-la-normalización-de-ssh)
- [2.22 Strongbox y el entorno de administración](#222-strongbox-y-el-entorno-de-administración)
- [2.23 CT102 y la utilidad de renunciar](#223-ct102-y-la-utilidad-de-renunciar)
- [2.24 Dos sistemas de backup, no uno](#224-dos-sistemas-de-backup-no-uno)
- [2.25 HDDBU](#225-hddbu)
- [2.26 SwissBackup](#226-swissbackup)
- [2.27 La recuperación como criterio de diseño](#227-la-recuperación-como-criterio-de-diseño)

---

## 2.18 La migración no terminó con el primer arranque

Conseguir que CT100 y CT101 arrancaran y que las interfaces web respondieran no bastaba para cerrar la migración.

Durante las jornadas siguientes se consolidaron decisiones menos visibles:

- centralización de Tailscale;
- publicación de servicios;
- normalización de SSH;
- integración con Strongbox;
- eliminación de CT102;
- adaptación de scripts;
- separación entre backup local y remoto;
- revisión de VFIO;
- clasificación de datos críticos y prescindibles;
- creación de un canon reconstruible.

Esta segunda fase convirtió una instalación funcional en una infraestructura operable.

---

## 2.19 Tailscale como capa única de acceso remoto

Tailscale quedó instalado exclusivamente en el host Proxmox.

Instalarlo en cada contenedor habría multiplicado nodos, claves, configuraciones y puntos de fallo. Centralizarlo permitía usar un único nodo de entrada y publicar los servicios internos mediante Tailscale Serve.

```text
Dispositivo remoto
└── Tailnet
    └── Host serviplan
        ├── 2283 → CT100 · Immich
        ├── 4533 → CT101 · Navidrome
        └── 8096 → CT101 · Jellyfin
```

La decisión proporcionó:

1. un solo punto de acceso remoto;
2. menos nodos y credenciales;
3. ningún puerto abierto públicamente en el router;
4. una ubicación única para revisar el estado;
5. servicios limitados a la tailnet.

> **Estado canónico**  
> Tailscale reside en el host. No debe desplegarse en CT100 ni CT101 durante una reconstrucción fiel.

---

## 2.20 HTTP dentro de la tailnet

Se estudió habilitar HTTPS interno para los servicios publicados por Tailscale Serve.

La mejora aparente introducía certificados, URL nuevas, mantenimiento adicional y más puntos de fallo. El transporte ya estaba cifrado por Tailscale y WireGuard, y los servicios no se exponían a Internet.

La decisión vigente fue conservar:

```text
http://serviplan:2283
http://serviplan:4533
http://serviplan:8096
```

No fue una renuncia genérica a HTTPS. Fue una decisión contextual: no añadir una capa sin una amenaza o necesidad concreta que justificara su coste.

---

## 2.21 La normalización de SSH

La migración obligó a sustituir accesos que ya no describían correctamente la nueva arquitectura.

Se consolidaron dos alias:

| Alias | Ruta |
|---|---|
| `serviplan` | Acceso a través de Tailscale |
| `serviplan_LAN` | Acceso directo por red local |

La duplicidad no era redundante. Permitía distinguir el camino remoto del camino local y diagnosticar cada uno por separado.

El acceso administrativo pasó a considerarse parte de la infraestructura y no un detalle del Mac.

---

## 2.22 Strongbox y el entorno de administración

Strongbox quedó establecido como agente SSH principal. Es un servicio de contraseñas que usa el formato libre [.kdbx](https://keepass.info/help/kb/kdbx.html) en contraposición al sistema cerrado de passwords.app de Apple. No rompemos unas barreras para meternos en otras.

### Comparativa rápida

| Característica                | Archivo KDBX (KeePass / KeePassXC)                           | Contraseñas de Apple (Passwords.app)                         |
| ----------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Tipo**                      | Aplicación independiente + base de datos local.              | Servicio integrado en el ecosistema Apple.                   |
| **Plataformas**               | Multiplataforma (Windows, macOS, Linux, iOS, Android).       | Exclusivo de Apple (iOS, macOS, visionOS).                   |
| **Almacenamiento**            | El usuario controla completamente la ubicación y las copias de la base de datos (local, en su propia nube o en un servidor). | Sincronizado mediante iCloud con cifrado de extremo a extremo (si iCloud está habilitado). También puede utilizarse sin sincronización. |
| **Código**                    | Fuente 100 % abierta (Open Source).                          | Código cerrado (propietario de Apple).                       |
| **Curva de aprendizaje**      | Media (requiere gestionar el archivo y elegir la aplicación que mejor se adapte). | Baja (integración nativa con el sistema).                    |
| **Autocompletado**            | Depende de la aplicación utilizada; normalmente requiere integración con el navegador o con el sistema. | Nativo y automático en Safari y en las aplicaciones del ecosistema Apple. |
| **Dependencia del proveedor** | Muy baja. El formato KDBX es un estándar abierto y puede utilizarse con múltiples aplicaciones. | Alta. Depende del ecosistema Apple y de la continuidad del servicio. |
| **Portabilidad de los datos** | Alta. La base de datos puede copiarse, trasladarse y abrirse con cualquier aplicación compatible con KDBX. | Limitada. Los datos están ligados al ecosistema Apple y a sus mecanismos de exportación. |
| **Control y auditoría**       | Total. El usuario puede inspeccionar, respaldar y gestionar directamente la base de datos. | Limitado. El usuario controla sus datos, pero no el funcionamiento interno ni el almacenamiento del servicio. |



La capacidad de administrar `serviplan` dependía de un flujo completo:

1. recuperar la base de Strongbox;
2. recuperar o reactivar la clave SSH;
3. restaurar el socket o enlace estable del agente;
4. reconstruir la configuración SSH;
5. validar los alias por LAN y por Tailscale.

La migración hizo visible que el sistema no vive únicamente dentro del MSI.

También depende de:

- el Mac de administración;
- Strongbox;
- la clave SSH;
- [Tailscale](https://tailscale.com/);
- [`rclone.conf`](https://rclone.org/);
- [kDrive](https://www.infomaniak.com/es/ksuite/kdrive) (una nube de almacenamiento europea, backup 1);
- los documentos canónicos de configuración y administración;
- [SwissBackup](https://www.infomaniak.com/es/swiss-backup) (backup 2);
- el HDD externo ([backup 3](https://www.kingston.com/es/blog/data-security/321-data-backup-method))

Un servidor intacto puede resultar inaccesible si se pierde el entorno desde el que se administra.

---

## 2.23 CT102 y la utilidad de renunciar

CT102 se creó para explorar un posible servicio DNS interno.

La idea era razonable y se realizaron pruebas, pero el contenedor no llegó a prestar una función necesaria dentro de la arquitectura estable.

El mismo junio de 2026 fue apagado y eliminado.

```text
No recrear CT102 salvo nueva decisión expresa.
```

Esta decisión evita que una futura reconstrucción confunda un experimento histórico con una pieza canónica.

> El historial conserva lo que ocurrió. El canon conserva lo que debe existir.

---

## 2.24 Dos sistemas de backup, no uno

La nueva arquitectura obligó a separar claramente dos sistemas que compartían el objetivo general de proteger datos, pero no la misma función.

| Sistema | Función principal | Ejecución |
|---|---|---|
| **BACKUP_SERVIPLAN** | Recuperación local rápida | Manual |
| **SwissBackup** | Copia externa cifrada | Automática mediante timer |
|  |  |  |

Omito deliberadamente kDrive, iCloud, el SSD interno; no aportaría nada aquí.

No debían documentarse como si fueran dos copias equivalentes, dado que tenían frecuencias, técnicas, alcance y límites diferentes.

---

## 2.25 BACKUP_SERVIPLAN

El HDD externo ya existía antes de Proxmox, pero su estructura fue rediseñada.

La política dejó de acumular generaciones históricas y pasó a mantener una única rama vigente, orientada a localizar rápidamente la copia utilizable.

### Tratamiento por componente

| Componente | Técnica |
|---|---|
| CT100 | `vzdump` |
| CT101 | `rsync` incremental |
| Host | Archivo `tar.zst` con configuración |
| Inventario | Manifiestos y sumas SHA256 |

### Decisiones operativas consolidadas

1. una única copia vigente;
2. ejecución manual;
3. frecuencia aproximada de una o dos semanas;
4. ausencia de timer;
5. CT100 mediante `vzdump`;
6. CT101 mediante `rsync`;
7. Jellyfin detenido brevemente durante su copia;
8. Navidrome copiado en caliente;
9. exclusión de WAL y SHM de Jellyfin;
10. retirada de `rsync -H`;
11. generación de manifiesto y hashes;
12. separación total respecto a SwissBackup.

El backup local dejó de ser una acumulación de archivos y pasó a representar estructuradamente el sistema.

---

## 2.26 SwissBackup

SwissBackup quedó como copia remota cifrada mediante `rclone` y un remoto `crypt`.

La ejecución se automatizó diariamente a las 02:00 con `systemd`.

El alcance documentado incluía:

- configuración e inventario del host;
- configuración de CT100;
- biblioteca de Immich;
- dump PostgreSQL;
- referencias asociadas a CT101.

> **Pendiente histórico documentado**  
> En el momento de consolidar el borrador, la integración remota completa de CT101 no tenía el mismo nivel de cierre que el resto. El sistema remoto funcionaba, pero ese alcance específico debía seguir marcado como pendiente de revisión.

Durante las pruebas apareció una lección de observabilidad: las copias server-side de objetos grandes en S3 podían parecer detenidas aunque siguieran trabajando.

Cuando se necesitara progreso visible, quedó anotada la opción:

```text
--disable Copy
```

No se convirtió en regla universal, sino en respuesta a una incidencia concreta.

---

## 2.27 La recuperación como criterio de diseño

La migración cambió la definición de una copia completa.

Guardar datos ya no bastaba. Debía existir una ruta comprensible para recuperar la capacidad de actuar.

El orden canónico de recuperación quedó expresado así:

1. Strongbox;
2. clave SSH;
3. Tailscale;
4. `rclone`;
5. Proxmox;
6. red del host;
7. CT100;
8. CT101;
9. Tailscale Serve;
10. SSH;
11. HHD BACKUP_SERVIPLAN;
12. SwissBackup;
13. validación.

Este orden revela dependencias reales.

La reconstrucción no empieza por instalar Proxmox. Empieza por recuperar credenciales y herramientas de acceso.

> Una copia de seguridad no está completa mientras no exista una ruta de recuperación comprensible.

---

---

# Capítulo 2. Cronología técnica
## Parte 4 · Incidencias, correcciones y madurez documental

## Índice de esta parte

- [2.28 VFIO y la eliminación de una configuración obsoleta](#228-vfio-y-la-eliminación-de-una-configuración-obsoleta)
- [2.29 La batería y el límite de lo razonable](#229-la-batería-y-el-límite-de-lo-razonable)
- [2.30 Windows queda fuera](#230-windows-queda-fuera)
- [2.31 Snapshots: capacidad disponible, aprendizaje pendiente](#231-snapshots-capacidad-disponible-aprendizaje-pendiente)
- [2.32 La restauración completa aún no probada](#232-la-restauración-completa-aún-no-probada)
- [2.33 Observabilidad y servicios `oneshot`](#233-observabilidad-y-servicios-oneshot)
- [2.34 Canon, historia y pendientes](#234-canon-historia-y-pendientes)
- [2.35 La documentación como cierre real de la migración](#235-la-documentación-como-cierre-real-de-la-migración)
- [2.36 Servicios críticos y datos prescindibles](#236-servicios-críticos-y-datos-prescindibles)
- [2.37 Estabilidad y experimentación](#237-estabilidad-y-experimentación)

---

## 2.28 VFIO y la eliminación de una configuración obsoleta

El 9 de junio de 2026 se detectó en `/etc/modules` una entrada obsoleta:

```text
vfio_virqfd
```

Antes de modificar el archivo se creó:

```text
/etc/modules.backup_20260709_1901
```

La configuración vigente quedó reducida a:

```text
vfio
vfio_iommu_type1
vfio_pci
```

La corrección fue pequeña, pero fijó una regla editorial y operativa:

> El canon no debe conservar una configuración antigua solo porque alguna vez funcionó.

La historia puede registrar lo retirado. Los procedimientos de reconstrucción deben contener únicamente el estado validado.

---

## 2.29 La batería y el límite de lo razonable

El MSI permanece normalmente conectado a la corriente, por lo que se estudió limitar la carga para reducir degradación.

En el modelo no estaban disponibles las interfaces estándar:

```text
charge_control_start_threshold
charge_control_end_threshold
```

La ausencia de una solución directa no justificaba escribir de manera insegura sobre el controlador embebido ni introducir herramientas sin soporte confirmado.

El criterio quedó fijado así:

1. utilizar BIOS/UEFI cuando exista una opción válida;
2. utilizar interfaces estándar de Linux;
3. aceptar herramientas Linux solo con soporte expreso para el modelo;
4. no utilizar Windows, ni siquiera temporalmente;
5. no modificar el EC (Embedded Controller) sin documentación y soporte confirmados.

La limitación quedó documentada en lugar de sustituirse por un workaround de riesgo superior al problema original.

---

## 2.30 Windows queda fuera

Windows no forma parte de la arquitectura.

No se contempla como máquina virtual permanente ni como herramienta temporal para configurar hardware, ejecutar utilidades del fabricante o salvar limitaciones del MSI.

La decisión no nace de una imposibilidad técnica, sino de coherencia con una infraestructura basada en Linux y procedimientos reproducibles.

Las soluciones futuras deben priorizar:

1. BIOS/UEFI;
2. interfaces estándar de Linux;
3. herramientas Linux con soporte confirmado;
4. documentación verificable.

Una posible máquina virtual Linux para pruebas o juegos pertenece al ámbito experimental y no modifica esta decisión.

---

## 2.31 Snapshots: capacidad disponible, aprendizaje pendiente

Proxmox abrió la posibilidad de utilizar snapshots.

Sin embargo, disponer de una función no equivale a haberla incorporado con criterio a las operaciones normales.

> **Pendiente**  
> En el momento de cerrar esta fase, el uso sistemático de snapshots seguía pendiente de aprendizaje y validación.

No debe reconstruirse la historia como si existiera ya una política consolidada de snapshots.

---

## 2.32 La restauración completa aún no probada

Una infraestructura recuperable debe probarse.

La restauración integral exigía almacenamiento, tiempo y un entorno adecuado. En ese momento no se disponía de capacidad suficiente para ejecutar una prueba completa sin adquirir hardware específicamente para ella.

La prueba se aplazó conscientemente.

> **Estado exacto**  
> Existían procedimientos y copias validadas de forma parcial, pero no una restauración integral confirmada de extremo a extremo.

Documentar esta limitación evita convertir una expectativa razonable en un hecho falso.

---

## 2.33 Observabilidad y servicios `oneshot`

Durante la consolidación de backups surgieron dos lecciones operativas.

### Progreso visible

Un proceso técnicamente correcto puede resultar difícil de operar si no muestra qué está haciendo. Por ello se valoran:

- logs legibles;
- códigos de salida;
- manifiestos;
- hashes;
- progreso visible cuando sea posible;
- separación clara entre ejecución, éxito y fallo.

### `inactive (dead)` no significa necesariamente error

Un servicio `oneshot` puede finalizar correctamente y quedar como:

```text
inactive (dead)
```

El diagnóstico debe revisar:

- código de salida;
- `ExecMainStatus`;
- logs;
- resultado real de la operación.

Confundir «ya terminó» con «falló» produce incidentes ficticios y pérdida de tiempo.

---

## 2.34 Canon, historia y pendientes

La documentación dispersa entre notas, scripts y conversaciones dificultaba saber qué seguía vigente.

El canónico unificado introdujo tres categorías explícitas.

### Estado canónico

Incluye:

- arquitectura actual;
- rutas vigentes;
- servicios activos;
- versiones confirmadas;
- procedimientos de reconstrucción;
- decisiones que deben preservarse.

### Historia

Incluye:

- pruebas;
- errores;
- configuraciones retiradas;
- componentes eliminados;
- nombres anteriores;
- lecciones aprendidas.

### Pendientes

Incluye:

- pruebas aún no realizadas;
- capacidades no aprendidas;
- datos sin validar;
- decisiones abiertas.

La clasificación evita dos fallos opuestos:

1. borrar la historia y perder conocimiento;
2. reconstruir configuraciones antiguas creyendo que siguen vigentes.

---

## 2.35 La documentación como cierre real de la migración

Los servicios podían funcionar y, aun así, la migración no estar terminada.

El cierre exigía poder explicar:

- qué había en el host;
- qué vivía en CT100;
- qué vivía en CT101;
- cómo se accedía;
- cómo se publicaban los servicios;
- cómo se respaldaba cada parte;
- qué se había eliminado;
- qué seguía pendiente;
- cómo reconstruir el conjunto.

Una configuración dejó de considerarse realmente canónica si no respondía a la pregunta:

> ¿Cómo se reconstruye?

El 10 de junio de 2026 se generó el canónico unificado vigente de aquella etapa. El 11 de junio comenzó la redacción del libro técnico y humano.

La documentación no fue un epílogo. Fue el último componente de la migración.

---

## 2.36 Servicios críticos y datos prescindibles

La consolidación permitió clasificar los datos según su importancia real.

### Críticos

- credenciales;
- claves SSH;
- configuración de Tailscale;
- configuración de `rclone`;
- documentos canónicos;
- biblioteca de Immich;
- configuraciones y bases de datos;
- música considerada irremplazable.

### No críticos salvo revisión posterior

- películas;
- contenido fácilmente recuperable;
- cachés;
- datos temporales.

Esta clasificación evita gastar capacidad, tiempo y dinero como si todos los datos tuvieran el mismo valor.

---

## 2.37 Estabilidad y experimentación

Proxmox formalizó una separación que se convirtió en principio de operación.

### Debe permanecer estable

- host;
- red;
- CT100;
- CT101;
- acceso administrativo;
- backups;
- documentación.

### Puede ser experimental

- LXC temporales;
- máquinas virtuales Linux;
- laboratorios aislados;
- servicios de prueba;
- entornos que puedan eliminarse sin afectar al resto.

La infraestructura principal no debe cambiar cada semana, pero debe permitir que la curiosidad viva alrededor sin comprometerla.

---

---

# Capítulo 2. Cronología técnica
## Parte 5 · Hitos confirmados, estado resultante y cierre

## Índice de esta parte

- [2.38 Cronología resumida de hitos confirmados](#238-cronología-resumida-de-hitos-confirmados)
- [2.39 Qué significó realmente «funciona todo»](#239-qué-significó-realmente-funciona-todo)
- [2.40 La primera arquitectura estable](#240-la-primera-arquitectura-estable)
- [2.41 Decisiones que deben conservarse](#241-decisiones-que-deben-conservarse)
- [2.42 Decisiones revisables](#242-decisiones-revisables)
- [2.43 Pendientes al cierre de la etapa](#243-pendientes-al-cierre-de-la-etapa)
- [2.44 Qué no debe deducirse](#244-qué-no-debe-deducirse)
- [2.45 El resultado humano](#245-el-resultado-humano)
- [2.46 Conclusión del capítulo](#246-conclusión-del-capítulo)

---

## 2.38 Cronología resumida de hitos confirmados

### Etapa previa

Durante décadas se acumuló experiencia con programación, administración de sistemas, Linux, redes, automatización y scripting.

No existe una fecha única que marque esta etapa y no debe inventarse.

### Maduración de la idea

Durante varios años creció la preocupación por la dependencia de proveedores y la pérdida de soberanía sobre los datos.

La inteligencia artificial actuó como acelerador de una idea ya madura.

### Primera implantación

`serviplan` se construyó inicialmente sobre Ubuntu Server bare-metal.

Se consolidaron Docker, Immich, Navidrome, Jellyfin, Tailscale, scripts, timers, backups y procedimientos de mantenimiento.

### Decisión de migrar

La motivación principal fue aprender virtualización, separar responsabilidades y preparar el crecimiento futuro.

Ubuntu Server no había fallado.

### Migración a Proxmox · junio de 2026

La mayor parte del cambio se concentró prácticamente en un día:

- instalación de Proxmox;
- creación de CT100 y CT101;
- red y direccionamiento;
- Tailscale y Tailscale Serve;
- acceso SSH y Strongbox;
- adaptación de scripts y timers;
- reorganización de backups;
- validación.

### 7 de junio de 2026

CT102 fue apagado y eliminado.

```text
No recrear CT102 salvo nueva decisión expresa.
```

### 8 de junio de 2026

Se confirmó una ejecución correcta del backup local HDDBU:

```text
Inicio: 2026-07-08 12:08:17 CEST
Fin:    2026-07-08 12:20:21 CEST
Estado: success
```

También se confirmó una ejecución correcta de SwissBackup:

```text
Inicio: 2026-07-08 02:00:03 CEST
Fin:    2026-07-08 02:20:56 CEST
Estado: SUCCESS
```

La auditoría confirmó:

- CT100 operativo;
- CT101 operativo;
- cero unidades fallidas;
- Immich sano;
- Jellyfin sano;
- Navidrome en ejecución;
- timer de SwissBackup activo;
- servicio manual HDDBU correctamente inactivo fuera de ejecución.

### 9 de junio de 2026

Se retiró `vfio_virqfd` de `/etc/modules` y se conservó una copia previa.

También quedaron documentados:

- ausencia de interfaces estándar para limitar la carga de batería;
- exclusión de Windows;
- descarte de HTTPS interno sobre Tailscale Serve;
- aplazamiento de la restauración integral.

### 10 de junio de 2026

Se generó el canónico unificado de la arquitectura.

### 11 de junio de 2026

Comenzó la redacción del libro técnico y humano de `serviplan`.

---

## 2.39 Qué significó realmente «funciona todo»

La expresión no significaba únicamente que tres páginas web respondieran.

Implicaba que:

- el host arrancaba;
- CT100 estaba operativo;
- CT101 estaba operativo;
- Immich funcionaba;
- Navidrome funcionaba;
- Jellyfin funcionaba;
- la LAN funcionaba;
- Tailscale funcionaba;
- SSH funcionaba por LAN y tailnet;
- HDDBU había completado una ejecución;
- SwissBackup había completado una ejecución;
- no había unidades fallidas;
- CT102 ya no existía;
- no había puertos abiertos en el router;
- la arquitectura podía explicarse.

Ese conjunto definió el éxito operativo de la migración.

---

## 2.40 La primera arquitectura estable

```text
MSI Modern 15 H C13M
└── Proxmox VE
    ├── Host
    │   ├── red y vmbr0
    │   ├── Tailscale
    │   ├── Tailscale Serve
    │   ├── SSH
    │   ├── VFIO
    │   └── backups del entorno
    ├── CT100 · Immich
    └── CT101 · Multimedia
        ├── Navidrome
        └── Jellyfin
```

Tailscale residía solo en el host.

Los servicios se publicaban dentro de la tailnet.

Strongbox actuaba como agente SSH.

HDDBU y SwissBackup permanecían separados.

CT102 había desaparecido.

La arquitectura era deliberadamente pequeña. La virtualización se utilizó para introducir orden y capacidad de crecimiento, no para multiplicar capas sin necesidad.

---

## 2.41 Decisiones que deben conservarse

Una reconstrucción fiel debe preservar estas decisiones mientras no exista una revisión expresa:

1. el host se llama `serviplan`;
2. la IP LAN del host es `192.168.1.99`;
3. CT100 corresponde a Immich;
4. CT101 corresponde a multimedia;
5. CT102 no debe recrearse;
6. Tailscale reside únicamente en el host;
7. no se abren puertos en el router;
8. Tailscale Serve publica los servicios dentro de la tailnet;
9. Strongbox actúa como agente SSH;
10. existen los alias `serviplan` y `serviplan_LAN`;
11. HDDBU y SwissBackup son sistemas distintos;
12. HDDBU permanece manual y sin timer;
13. SwissBackup se ejecuta mediante timer diario;
14. `/etc/modules` no contiene `vfio_virqfd`;
15. Windows queda fuera;
16. HTTPS interno no se habilita sin una necesidad concreta;
17. los datos no verificados se marcan como pendientes;
18. el canon describe el presente;
19. la historia se conserva separada;
20. una reconstrucción no debe eliminar datos sin autorización expresa.

---

## 2.42 Decisiones revisables

Otros elementos pertenecen al estado actual, pero no son dogmas:

- tamaños de disco;
- asignación de RAM;
- número de cores;
- imágenes y versiones Docker;
- versiones de Proxmox y kernel;
- clientes móviles;
- scripts;
- mecanismos de snapshot;
- proveedor de backup remoto;
- distribución futura de servicios.

El canon debe registrar sus valores actuales. La filosofía debe permitir sustituirlos cuando cambien las necesidades.

---

## 2.43 Pendientes al cierre de la etapa

La migración quedó operativa, pero no cerró todas las líneas de trabajo.

Permanecían pendientes:

1. aprender snapshots con criterio;
2. ejecutar una restauración integral;
3. revisar la integración definitiva de CT101 en SwissBackup;
4. mantener inventarios y documentación actualizados;
5. revisar futuras necesidades de virtualización;
6. resolver, si aparece una vía segura, el límite de carga de batería.

La existencia de pendientes no invalida el sistema. Lo importante es que estén identificados y no se presenten como resueltos.

---

## 2.44 Qué no debe deducirse

Esta cronología no afirma que:

- Proxmox sea siempre mejor que Ubuntu Server;
- un portátil sea siempre mejor que un servidor dedicado;
- dos LXC sean adecuados para cualquier entorno;
- Tailscale sea la única forma válida de acceso remoto;
- una migración Big Bang sea siempre recomendable;
- un backup manual sea superior a uno automático;
- mantener una sola copia local sea una política universal.

Cada decisión respondió al contexto de `serviplan`.

El valor de la historia no está en copiarla, sino en comprender por qué cada elección tenía sentido dentro de este sistema.

---

## 2.45 El resultado humano

La migración fue técnicamente satisfactoria: los servicios volvieron a funcionar, la arquitectura quedó más limpia y aumentó la capacidad de ampliación.

Pero hubo otro resultado que también pertenece a la historia.

El proceso concentró aquello que había dado origen al proyecto:

- aprender;
- trabajar en Terminal;
- tocar hardware;
- entender una tecnología nueva;
- equivocarse;
- corregir;
- reconstruir;
- terminar con algo útil.

La frase que mejor resume esa etapa fue:

> Funcionó todo, quedó mejor preparado para crecer y me lo pasé de puta madre haciéndolo.

No existe una métrica técnica para esa clase de éxito, pero omitirla produciría una historia incompleta.

---

## 2.46 Conclusión del capítulo

Ubuntu Server no se quedó pequeño y Linux no dejó de ser suficiente.

Lo que cambió fue la forma de organizar el aprendizaje, el riesgo y el crecimiento.

Proxmox convirtió `serviplan` en una plataforma donde:

- la estabilidad permanece en el host y los contenedores principales;
- los datos se protegen mediante sistemas de backup diferenciados;
- la curiosidad puede vivir en invitados aislados;
- la reconstrucción actúa como criterio de verdad;
- la documentación conserva tanto el presente como la historia.

La migración terminó cuando el sistema pudo explicarse.

A partir del capítulo siguiente, el libro abandona la secuencia histórica y describe qué existe físicamente, cómo está organizado y qué debe conservarse para reconstruirlo.

---

---

# Capítulo 3. Inventario físico

## Índice

- [3.1 Función de este capítulo](#31-función-de-este-capítulo)
- [3.2 Criterio de elección del hardware](#32-criterio-de-elección-del-hardware)
- [3.3 Host físico](#33-host-físico)
- [3.4 Procesador](#34-procesador)
- [3.5 Memoria RAM](#35-memoria-ram)
- [3.6 Almacenamiento principal](#36-almacenamiento-principal)
- [3.7 GPU integrada y passthrough](#37-gpu-integrada-y-passthrough)
- [3.8 Alimentación y batería](#38-alimentación-y-batería)
- [3.9 Refrigeración y temperaturas](#39-refrigeración-y-temperaturas)
- [3.10 Conectividad física](#310-conectividad-física)
- [3.11 BIOS / UEFI y comportamiento de la tapa](#311-bios--uefi-y-comportamiento-de-la-tapa)
- [3.12 Limitaciones conocidas](#312-limitaciones-conocidas)
- [3.13 Inventario físico resumido](#313-inventario-físico-resumido)
- [3.14 Datos pendientes de verificación](#314-datos-pendientes-de-verificación)
- [3.15 Cierre](#315-cierre)

---

## 3.1 Función de este capítulo

Este capítulo describe el hardware físico sobre el que existe `serviplan`.

No explica todavía cómo se distribuyen los servicios ni cómo se reconstruye el sistema. Su objetivo es más básico: identificar con precisión la máquina, sus componentes, las funciones que cumple cada uno y las limitaciones que condicionan la arquitectura.

La información se divide en tres categorías:

| Categoría | Significado |
|---|---|
| **Confirmado** | Dato observado y consolidado en el canon |
| **Histórico** | Dato relevante para comprender decisiones pasadas |
| **Pendiente** | Dato no confirmado que no debe inventarse |

---

## 3.2 Criterio de elección del hardware

El hardware de `serviplan` no fue elegido por prestigio ni por deseo de construir un laboratorio espectacular.

El MSI Modern 15 H C13M ya existía y permanecía prácticamente sin uso. Antes de comprar un servidor dedicado se evaluó si podía cubrir las necesidades reales del proyecto.

La respuesta fue afirmativa.

Las razones principales fueron:

1. potencia suficiente para Proxmox y los dos LXC principales;
2. 32 GB de RAM;
3. almacenamiento NVMe rápido;
4. consumo relativamente reducido;
5. poco ruido;
6. batería integrada;
7. pantalla y teclado disponibles para emergencias;
8. ausencia de necesidad inmediata de adquirir otro equipo.

La decisión resume un principio permanente del proyecto:

> Reutilizar antes que comprar.

El MSI no actúa como solución provisional.

Es el host físico de `serviplan`.

---

## 3.3 Host físico

### Estado confirmado

| Campo | Valor |
|---|---|
| Fabricante | MSI |
| Modelo | Modern 15 H C13M |
| Rol | Host físico de Proxmox VE |
| Hostname | `serviplan` |
| RAM instalada | 32 GB |
| SSD principal | WD_BLACK SN850X de 1 TB |
| Sistema actual | Proxmox VE |

Sobre este equipo se ejecuta toda la infraestructura descrita en el libro.

```text
MSI Modern 15 H C13M
└── Proxmox VE
    ├── CT100 · Immich
    └── CT101 · Multimedia
```

El formato de portátil introduce algunas peculiaridades:

- batería interna;
- pantalla y teclado integrados;
- tapa abatible;
- refrigeración diseñada para uso portátil;
- menor capacidad de expansión que un servidor convencional.

Esas características no invalidan el equipo. Simplemente deben formar parte del diseño y del mantenimiento.

---

## 3.4 Procesador

### Estado confirmado

- Intel Core de 13.ª generación;
- virtualización operativa;
- VT-x / VT-d operativos;
- IOMMU operativo;
- iGPU Intel integrada.

La CPU ofrece margen suficiente para:

- Proxmox;
- CT100;
- CT101;
- nuevos LXC de prueba;
- máquinas virtuales ocasionales;
- tareas multimedia con apoyo de la GPU integrada.

### Pendiente

El modelo comercial exacto del procesador no está consolidado en el borrador y no debe inventarse.

Hasta verificarlo, el canon debe conservar únicamente la descripción confirmada:

```text
Intel Core de 13.ª generación
```

---

## 3.5 Memoria RAM

### Estado confirmado

```text
RAM total instalada: 32 GB
```

Asignación actual:

| Sistema | RAM | Swap |
|---|---:|---:|
| CT100 · Immich | 8 GB | 2 GB |
| CT101 · Multimedia | 4 GB | 1 GB |
| Host y margen libre | Resto disponible | Gestionado por el host |

La memoria no se ha repartido de forma exhaustiva.

Existe margen deliberado para:

- el host;
- cachés;
- picos de uso;
- nuevos invitados;
- cambios futuros.

La ausencia de sobreasignación agresiva forma parte del criterio conservador del proyecto.

---

## 3.6 Almacenamiento principal

### Estado confirmado

| Campo | Valor |
|---|---|
| Modelo | WD_BLACK SN850X |
| Capacidad nominal | 1 TB |
| Tecnología | NVMe |
| Función | Almacenamiento principal del host y de los invitados |

El SSD se instaló durante la migración a Proxmox.

La sustitución permitió conservar temporalmente la instalación anterior y reducir el riesgo de perder el único sistema funcional durante el cambio.

### Distribución lógica actual

- `local`;
- `local-lvm`.

La distribución exacta, los volúmenes y el uso se documentan en los capítulos de arquitectura y reconstrucción.

### Estado actual conocido

- `local`: aproximadamente 98 GB;
- `local-lvm`: aproximadamente 794,30 GB;
- CT100: disco de 60 GB;
- CT101: disco de 400 GB.

### Pendiente

El informe SMART completo del SSD no está incorporado todavía como dato canónico.

No debe confundirse la ausencia de ese informe con un fallo conocido.

---

## 3.7 GPU integrada y passthrough

### Estado confirmado

| Campo | Valor |
|---|---|
| GPU | Intel UHD Graphics |
| Familia | Raptor Lake-P |
| PCI ID | `8086:a7a8` |
| Función prevista | Aceleración multimedia mediante passthrough |

La iGPU está preparada para passthrough con VFIO.

Módulos vigentes:

```text
vfio
vfio_iommu_type1
vfio_pci
```

La entrada siguiente pertenece al historial y no debe recuperarse:

```text
vfio_virqfd
```

Su eliminación se documenta en el capítulo de incidencias.

### Importancia operativa

La GPU permite descargar de la CPU determinadas tareas multimedia, especialmente en Jellyfin, siempre que el passthrough y la aceleración estén correctamente configurados.

No debe asumirse que «GPU detectada» equivale automáticamente a «aceleración validada». Son comprobaciones distintas.

---

## 3.8 Alimentación y batería

El MSI permanece normalmente conectado a la red eléctrica.

### Cargador

No existe todavía una ficha canónica con:

- modelo;
- potencia;
- número de serie;
- especificaciones exactas.

Esos datos quedan pendientes de verificación.

### Batería

Estado conocido:

| Campo | Valor |
|---|---:|
| Capacidad aproximada | 92 % |
| Ciclos registrados | 0 |
| Uso normal | Equipo conectado a corriente |

La batería se conserva porque aporta:

- protección frente a microcortes;
- autonomía breve ante pérdida de alimentación;
- margen para apagar ordenadamente;
- una pequeña función semejante a la de un SAI local.

No sustituye a un SAI para el router, el switch o el resto de la red.

### Límite de carga

El objetivo es limitar la carga alrededor del 60 % para reducir degradación.

En el modelo no están disponibles las interfaces estándar:

```text
charge_control_start_threshold
charge_control_end_threshold
```

La política vigente es:

1. utilizar BIOS/UEFI si aparece una opción válida;
2. utilizar interfaces estándar de Linux;
3. aceptar herramientas Linux solo con soporte expreso para el modelo;
4. no utilizar Windows;
5. no escribir sobre el controlador embebido sin soporte confirmado.

---

## 3.9 Refrigeración y temperaturas

Temperaturas observadas durante el funcionamiento normal:

```text
Rango general observado: 44–54 °C
CPU habitual:            51–52 °C
```

No se han detectado problemas térmicos.

El equipo funciona dentro de valores razonables para su carga actual.

### Pendiente

Existe como línea futura:

- monitorización permanente de temperaturas;
- registro histórico;
- alertas;
- correlación con carga y temperatura ambiente.

Hasta disponer de ese sistema, las cifras anteriores deben interpretarse como observaciones puntuales, no como una serie histórica completa.

---

## 3.10 Conectividad física

### Estado canónico

| Elemento | Valor |
|---|---|
| Enlace principal | Ethernet |
| Bridge de Proxmox | `vmbr0` |
| IP del host | `192.168.1.99/24` |
| Gateway | `192.168.1.1` |
| Wi-Fi | Fuera del funcionamiento normal |

Ethernet constituye el camino estable de red.

La Wi-Fi no forma parte de la arquitectura operativa normal y no debe convertirse en dependencia durante una reconstrucción.

---

## 3.11 BIOS / UEFI y comportamiento de la tapa

### Confirmado

- virtualización habilitada;
- IOMMU habilitado;
- arranque de Proxmox operativo.

### Comportamiento de la tapa

El host debe continuar funcionando con la tapa cerrada.

La configuración consolidada es:

```text
HandleLidSwitch=ignore
```

Este comportamiento se aplica mediante `systemd-logind`.

### Pendiente

No están todavía consolidados:

- versión exacta de BIOS;
- fecha de BIOS;
- listado completo de opciones modificadas;
- capturas o exportación de configuración.

Una reconstrucción futura debe validar esas opciones en la propia máquina y no asumir valores no documentados.

---

## 3.12 Limitaciones conocidas

El hardware actual tiene limitaciones claras:

1. un único host físico;
2. ausencia de alta disponibilidad;
3. SSD principal como punto único de fallo;
4. batería solo para el portátil, no para toda la red;
5. capacidad de expansión limitada;
6. ausencia de control de carga estándar confirmado;
7. dependencia de refrigeración propia de portátil;
8. necesidad de mantener limpia la ventilación;
9. ausencia de inventario completo del cargador;
10. ausencia de ficha BIOS completa.

Estas limitaciones no convierten el sistema en inadecuado.

Definen el contexto en el que debe operarse.

---

## 3.13 Inventario físico resumido

```text
Host físico
└── MSI Modern 15 H C13M
    ├── CPU Intel Core de 13.ª generación
    ├── 32 GB RAM
    ├── SSD WD_BLACK SN850X de 1 TB
    ├── Intel UHD Graphics Raptor Lake-P [8086:a7a8]
    ├── Ethernet
    ├── batería interna
    ├── pantalla integrada
    ├── teclado integrado
    └── cargador pendiente de inventario detallado
```

### Tabla maestra

| Componente | Estado | Observación |
|---|---|---|
| Chasis | Confirmado | MSI Modern 15 H C13M |
| CPU | Parcialmente confirmado | Falta modelo comercial exacto |
| RAM | Confirmado | 32 GB |
| SSD | Confirmado | WD_BLACK SN850X 1 TB |
| GPU | Confirmado | Intel UHD Raptor Lake-P `8086:a7a8` |
| Ethernet | Confirmado | Enlace principal |
| Wi-Fi | Confirmado | No usada normalmente |
| Batería | Confirmado | 92 % aprox., 0 ciclos |
| Cargador | Pendiente | Modelo y potencia |
| BIOS | Parcialmente confirmado | Falta versión y detalle completo |
| Temperaturas | Observadas | 44–54 °C |

---

## 3.14 Datos pendientes de verificación

Quedan pendientes:

1. modelo exacto de CPU;
2. modelo y potencia del cargador;
3. versión y fecha de BIOS;
4. listado completo de opciones BIOS modificadas;
5. informe SMART completo;
6. sistema permanente de monitorización térmica;
7. posible mecanismo seguro de límite de carga.

Estos datos deben incorporarse cuando se verifiquen.

Hasta entonces, el libro debe conservar la incertidumbre de forma explícita.

---

## 3.15 Cierre

El hardware de `serviplan` no es excepcional.

Esa es una de sus virtudes.

Un portátil reutilizado, correctamente dimensionado y bien documentado ha demostrado ser suficiente para alojar una infraestructura estable, silenciosa y ampliable.

El valor del sistema no procede de la espectacularidad del equipo.

Procede de la coherencia entre:

- necesidades;
- recursos;
- arquitectura;
- copias;
- documentación;
- capacidad de reconstrucción.

---

# Capítulo 4. Arquitectura lógica

## Índice

- [4.1 Visión general](#41-visión-general)
- [4.2 Principios de diseño](#42-principios-de-diseño)
- [4.3 Capas de la infraestructura](#43-capas-de-la-infraestructura)
- [4.4 Host Proxmox](#44-host-proxmox)
- [4.5 CT100 · Immich](#45-ct100--immich)
- [4.6 CT101 · Multimedia](#46-ct101--multimedia)
- [4.7 Docker dentro de LXC](#47-docker-dentro-de-lxc)
- [4.8 Tailscale en el host](#48-tailscale-en-el-host)
- [4.9 Almacenamiento lógico](#49-almacenamiento-lógico)
- [4.10 Dependencias externas](#410-dependencias-externas)
- [4.11 Elementos que no forman parte del canon](#411-elementos-que-no-forman-parte-del-canon)
- [4.12 Diagrama lógico completo](#412-diagrama-lógico-completo)
- [4.13 Estado, historia y pendientes](#413-estado-historia-y-pendientes)
- [4.14 Cierre](#414-cierre)

---

## 4.1 Visión general

La arquitectura actual de `serviplan` es deliberadamente pequeña.

```text
MSI Modern 15 H C13M
└── Proxmox VE
    ├── Host
    │   ├── red
    │   ├── almacenamiento
    │   ├── Tailscale
    │   ├── Tailscale Serve
    │   ├── SSH
    │   ├── VFIO
    │   └── backups del entorno
    ├── CT100 · Immich
    │   └── Docker
    │       └── stack de Immich
    └── CT101 · Multimedia
        └── Docker
            ├── Navidrome
            └── Jellyfin
```

La virtualización no se utiliza para multiplicar componentes.

Se utiliza para separar responsabilidades.

---

## 4.2 Principios de diseño

La arquitectura responde a varios principios:

1. el host debe permanecer limpio;
2. los servicios de usuario viven fuera del host;
3. los servicios relacionados se agrupan;
4. las capas deben tener una función clara;
5. el acceso remoto se centraliza;
6. los backups se separan por propósito;
7. los experimentos no deben comprometer lo estable;
8. la reconstrucción debe poder seguir el mismo orden lógico.

---

## 4.3 Capas de la infraestructura

La arquitectura puede dividirse en cinco capas.

| Capa | Función |
|---|---|
| Física | MSI, CPU, RAM, SSD, GPU, red y batería |
| Virtualización | Proxmox VE |
| Invitados | CT100 y CT101 |
| Aplicaciones | Immich, Navidrome y Jellyfin |
| Acceso y protección | SSH, Tailscale, HDDBU y SwissBackup |

Estas capas no son independientes.

Cada una depende de la anterior.

La documentación de reconstrucción debe respetar ese orden.

---

## 4.4 Host Proxmox

El host se ocupa de la infraestructura común.

### Debe contener

- Proxmox VE;
- configuración de red;
- `vmbr0`;
- almacenamiento;
- LXC;
- Tailscale;
- Tailscale Serve;
- SSH;
- VFIO;
- scripts y servicios necesarios para backups;
- herramientas administrativas.

### No debe contener

- Immich;
- Navidrome;
- Jellyfin;
- stacks Docker de aplicaciones;
- servicios experimentales permanentes;
- una colección de utilidades sin función clara.

La frontera evita que el host termine reproduciendo el monolito anterior.

---

## 4.5 CT100 · Immich

CT100 está dedicado a Immich.

### Configuración canónica

| Parámetro | Valor |
|---|---:|
| ID | 100 |
| Función | Immich |
| IP | `192.168.1.101` |
| Cores | 4 |
| RAM | 8 GB |
| Swap | 2 GB |
| Disco | 60 GB |
| Tipo | LXC no privilegiado |
| Opciones | `nesting=1`, `keyctl=1` |
| Arranque | Automático |
| Orden | 10 |

Dentro de CT100 se ejecuta Docker con el stack de Immich y sus dependencias.

CT100 se considera una unidad funcional.

---

## 4.6 CT101 · Multimedia

CT101 agrupa los servicios multimedia.

### Configuración canónica

| Parámetro | Valor |
|---|---:|
| ID | 101 |
| Función | Multimedia |
| IP | `192.168.1.102` |
| Cores | 4 |
| RAM | 4 GB |
| Swap | 1 GB |
| Disco | 400 GB |
| Tipo | LXC no privilegiado |
| Opciones | `nesting=1`, `keyctl=1` |
| Arranque | Automático |
| Orden | 20 |

Dentro de CT101 se ejecutan:

- Navidrome;
- Jellyfin;
- bibliotecas multimedia;
- directorios asociados.

La agrupación evita separar servicios que comparten naturaleza, almacenamiento y mantenimiento.

---

## 4.7 Docker dentro de LXC

Docker no fue eliminado durante la migración.

Cambió de ubicación.

```text
Proxmox
└── LXC
    └── Docker
        └── aplicaciones
```

LXC proporciona:

- separación funcional;
- unidad de backup;
- control de recursos;
- arranque independiente;
- gestión desde Proxmox.

Docker proporciona:

- despliegue de aplicaciones;
- aislamiento de servicios;
- configuración reproducible;
- compatibilidad con stacks oficiales.

Ambas capas resuelven problemas distintos.

La combinación es válida mientras esté documentada y comprendida.

---

## 4.8 Tailscale en el host

Tailscale reside únicamente en el host.

No se instala en CT100 ni CT101.

La publicación se realiza mediante Tailscale Serve:

```text
Host serviplan
├── :2283 → CT100:2283 · Immich
├── :4533 → CT101:4533 · Navidrome
└── :8096 → CT101:8096 · Jellyfin
```

Ventajas:

1. un solo nodo de tailnet;
2. una sola configuración;
3. menos claves;
4. menos puntos de fallo;
5. ningún puerto abierto en el router;
6. servicios limitados a la tailnet.

---

## 4.9 Almacenamiento lógico

El host utiliza:

- `local`;
- `local-lvm`.

Los invitados disponen de discos propios dentro de esa estructura.

| Invitado | Disco |
|---|---:|
| CT100 | 60 GB |
| CT101 | 400 GB |

La estrategia de backup no trata ambos invitados de la misma forma:

- CT100: `vzdump`;
- CT101: `rsync`.

Esta diferencia responde a la naturaleza y tamaño de los datos.

---

## 4.10 Dependencias externas

Aunque `serviplan` sea autoalojado, depende de elementos externos:

- router;
- red LAN;
- acceso a Internet;
- tailnet;
- Strongbox;
- Mac de administración;
- kDrive;
- SwissBackup;
- HDD externo;
- `rclone`;
- credenciales.

Estas dependencias deben documentarse porque forman parte de la capacidad real de administrar y reconstruir.

---

## 4.11 Elementos que no forman parte del canon

No forman parte de la arquitectura vigente:

- CT102;
- Windows;
- servicios Docker ejecutados directamente en el host;
- HTTPS interno sin necesidad concreta;
- Tailscale dentro de cada LXC;
- Wi-Fi como camino principal;
- `vfio_virqfd`.

CT102 existió como experimento DNS y fue eliminado.

No debe recrearse durante una reconstrucción fiel.

---

## 4.12 Diagrama lógico completo

```text
Internet
└── Router
    └── LAN 192.168.1.0/24
        └── serviplan · 192.168.1.99
            ├── Proxmox VE
            ├── Tailscale
            ├── Tailscale Serve
            ├── SSH
            ├── local
            ├── local-lvm
            ├── CT100 · 192.168.1.101
            │   └── Docker
            │       └── Immich
            └── CT101 · 192.168.1.102
                └── Docker
                    ├── Navidrome
                    └── Jellyfin

Protección
├── HDDBU · backup local manual
└── SwissBackup · backup remoto cifrado

Administración
└── Mac
    ├── SSH
    ├── Strongbox
    ├── Tailscale
    ├── rclone
    └── documentación canónica
```

---

## 4.13 Estado, historia y pendientes

### Estado vigente

- Proxmox como host;
- CT100 para Immich;
- CT101 para multimedia;
- Tailscale en el host;
- Docker dentro de LXC;
- HDDBU y SwissBackup separados.

### Historia

- Ubuntu Server bare-metal;
- CT102;
- `vfio_virqfd`;
- intentos de HTTPS interno;
- configuraciones anteriores de SSH.

### Pendientes

- aprendizaje sistemático de snapshots;
- restauración integral;
- revisión de la integración completa de CT101 en SwissBackup;
- posibles nuevos invitados experimentales.

---

## 4.14 Cierre

La arquitectura de `serviplan` no busca maximizar el número de tecnologías.

Busca asignar una función clara a cada capa.

El host administra.

Los LXC separan.

Docker despliega.

Tailscale conecta.

Los backups protegen.

La documentación permite reconstruir.

Esa división es la base del resto del libro.

---

# Capítulo 5. Red y comunicaciones

## Índice

- [5.1 Función de la red en `serviplan`](#51-función-de-la-red-en-serviplan)
- [5.2 Topología general](#52-topología-general)
- [5.3 Direccionamiento LAN](#53-direccionamiento-lan)
- [5.4 Bridge de Proxmox](#54-bridge-de-proxmox)
- [5.5 Reservas DHCP](#55-reservas-dhcp)
- [5.6 Resolución de nombres](#56-resolución-de-nombres)
- [5.7 Acceso administrativo por SSH](#57-acceso-administrativo-por-ssh)
- [5.8 Tailscale](#58-tailscale)
- [5.9 Tailscale Serve](#59-tailscale-serve)
- [5.10 Servicios publicados](#510-servicios-publicados)
- [5.11 Por qué no se abren puertos en el router](#511-por-qué-no-se-abren-puertos-en-el-router)
- [5.12 HTTP dentro de la tailnet](#512-http-dentro-de-la-tailnet)
- [5.13 Caminos de acceso](#513-caminos-de-acceso)
- [5.14 Dependencias de red](#514-dependencias-de-red)
- [5.15 Diagnóstico básico](#515-diagnóstico-básico)
- [5.16 Estado, historia y pendientes](#516-estado-historia-y-pendientes)
- [5.17 Cierre](#517-cierre)

---

## 5.1 Función de la red en `serviplan`

La red no es una capa auxiliar.

Es el mecanismo que conecta:

- el host;
- los contenedores;
- el Mac de administración;
- los clientes móviles;
- la tailnet;
- los servicios;
- los sistemas de backup;
- Internet.

Una infraestructura puede estar intacta físicamente y, sin embargo, resultar inaccesible por una configuración de red incorrecta.

Por eso este capítulo distingue entre:

- red local;
- acceso remoto;
- resolución de nombres;
- publicación de servicios;
- administración;
- dependencias externas.

---

## 5.2 Topología general

```text
Internet
└── Router Movistar
    └── LAN 192.168.1.0/24
        ├── serviplan · 192.168.1.99
        │   ├── CT100 · 192.168.1.101
        │   └── CT101 · 192.168.1.102
        └── Mac · 192.168.1.33
```

Sobre la LAN existe una segunda capa de acceso:

```text
Tailnet
├── Mac
├── iPhone
└── serviplan
```

Los servicios internos se publican desde el host mediante Tailscale Serve.

---

## 5.3 Direccionamiento LAN

### Estado canónico

| Elemento | Dirección |
|---|---|
| Router / gateway | `192.168.1.1` |
| Host `serviplan` | `192.168.1.99` |
| CT100 · Immich | `192.168.1.101` |
| CT101 · Multimedia | `192.168.1.102` |
| Mac | `192.168.1.33` |

Rango reservado conceptualmente para servicios Proxmox:

```text
192.168.1.101-192.168.1.110
```

La separación ayuda a reconocer rápidamente qué direcciones pertenecen a invitados.

---

## 5.4 Bridge de Proxmox

El host utiliza `vmbr0` como bridge principal.

### Configuración lógica

```text
Interfaz física Ethernet
└── vmbr0
    ├── host Proxmox
    ├── CT100
    └── CT101
```

El host usa:

```text
IP:      192.168.1.99/24
Gateway: 192.168.1.1
```

La Wi-Fi no forma parte del camino operativo normal.

El bridge permite que los contenedores aparezcan como equipos independientes dentro de la LAN.

---

## 5.5 Reservas DHCP

CT100 y CT101 utilizan DHCP con reservas en el router.

Ventajas:

1. dirección estable;
2. configuración centralizada;
3. menor riesgo de conflicto;
4. reconstrucción más sencilla;
5. posibilidad de sustituir un contenedor sin reconfigurar toda la red.

La reserva DHCP forma parte del sistema.

No basta con configurar el contenedor si el router no conserva la asociación correspondiente.

### Estado conocido

| Equipo | IP reservada |
|---|---|
| CT100 | `192.168.1.101` |
| CT101 | `192.168.1.102` |
| Mac | `192.168.1.33` |

---

## 5.6 Resolución de nombres

El nombre principal del host es:

```text
serviplan
```

El sistema debe poder resolverlo tanto en el entorno local como dentro de la tailnet según el camino utilizado.

La resolución estable evita depender de direcciones IP escritas manualmente en cada cliente.

### Pendiente

La estrategia definitiva de DNS interno no está completamente cerrada en el canon.

CT102 se creó para explorar esa función y fue eliminado.

No debe recrearse únicamente para resolver nombres sin una decisión nueva y documentada.

---

## 5.7 Acceso administrativo por SSH

El acceso administrativo se realiza mediante dos alias diferenciados:

| Alias | Camino |
|---|---|
| `serviplan` | Tailscale |
| `serviplan_LAN` | Red local |

Esta separación permite:

- trabajar remotamente;
- acceder directamente por LAN;
- diagnosticar si falla Tailscale;
- distinguir problemas de red local y tailnet.

Strongbox actúa como agente SSH.

La clave no debe considerarse un archivo aislado.

Forma parte de un flujo que incluye:

1. base de Strongbox;
2. clave SSH;
3. agente;
4. configuración SSH;
5. alias;
6. validación de acceso.

---

## 5.8 Tailscale

Tailscale reside únicamente en el host Proxmox.

No se instala dentro de CT100 ni CT101.

### Razones

1. un único nodo;
2. una única clave;
3. menor superficie de configuración;
4. menos puntos de fallo;
5. publicación centralizada;
6. administración más sencilla.

Tailscale proporciona acceso remoto cifrado mediante WireGuard sin exponer servicios directamente a Internet.

---

## 5.9 Tailscale Serve

Tailscale Serve publica servicios internos desde el host.

```text
serviplan:2283 → 192.168.1.101:2283
serviplan:4533 → 192.168.1.102:4533
serviplan:8096 → 192.168.1.102:8096
```

Esta publicación mantiene separados:

- el nodo visible en la tailnet;
- los servicios alojados en los contenedores;
- la red LAN interna.

El host actúa como punto de entrada.

---

## 5.10 Servicios publicados

| Servicio | Contenedor | IP interna | Puerto | URL lógica |
|---|---|---|---:|---|
| Immich | CT100 | `192.168.1.101` | 2283 | `http://serviplan:2283` |
| Navidrome | CT101 | `192.168.1.102` | 4533 | `http://serviplan:4533` |
| Jellyfin | CT101 | `192.168.1.102` | 8096 | `http://serviplan:8096` |

Estas URL pertenecen al uso dentro de la tailnet.

No implican exposición pública.

---

## 5.11 Por qué no se abren puertos en el router

La arquitectura evita publicar servicios directamente a Internet.

Ventajas:

- menor superficie de ataque;
- ausencia de NAT manual;
- menos reglas en el router;
- servicios limitados a dispositivos autorizados;
- configuración más fácil de auditar.

La decisión no impide abrir un puerto en el futuro si existiera una necesidad real.

Simplemente establece que no se hace por defecto.

---

## 5.12 HTTP dentro de la tailnet

Los servicios se mantienen mediante HTTP dentro de la tailnet.

El transporte entre dispositivos está cifrado por Tailscale y WireGuard.

Añadir HTTPS interno habría introducido:

- certificados;
- renovación;
- nuevas URL;
- mantenimiento;
- más puntos de fallo.

La decisión vigente es conservar HTTP mientras:

1. los servicios permanezcan dentro de la tailnet;
2. no exista exposición pública;
3. no aparezca una necesidad concreta que justifique HTTPS.

No es una afirmación universal sobre seguridad.

Es una decisión contextual.

---

## 5.13 Caminos de acceso

### Acceso local

```text
Mac
└── LAN
    └── serviplan_LAN
```

### Acceso remoto

```text
Mac / iPhone
└── Tailscale
    └── serviplan
```

### Acceso a servicios

```text
Cliente
└── Tailnet
    └── serviplan
        ├── :2283
        ├── :4533
        └── :8096
```

Disponer de dos caminos administrativos evita que un fallo de Tailscale bloquee completamente la gestión mientras exista acceso LAN.

---

## 5.14 Dependencias de red

La red depende de:

- router;
- cable Ethernet;
- interfaz del MSI;
- `vmbr0`;
- reservas DHCP;
- DNS;
- Tailscale;
- configuración SSH;
- estado de CT100 y CT101.

Un diagnóstico debe localizar la capa exacta del fallo.

Ejemplo:

```text
Servicio no responde
├── ¿resuelve el nombre?
├── ¿responde el host?
├── ¿responde el contenedor?
├── ¿está abierto el puerto?
├── ¿funciona Tailscale Serve?
└── ¿funciona la aplicación?
```

---

## 5.15 Diagnóstico básico

Orden recomendado:

1. comprobar conectividad LAN;
2. comprobar IP del host;
3. comprobar resolución de `serviplan`;
4. comprobar Tailscale;
5. comprobar estado del contenedor;
6. comprobar puerto interno;
7. comprobar Tailscale Serve;
8. comprobar aplicación.

La red debe diagnosticarse de abajo arriba.

No conviene empezar reinstalando aplicaciones cuando el problema puede estar en DNS o en el bridge.

---

## 5.16 Estado, historia y pendientes

### Estado vigente

- Ethernet;
- `vmbr0`;
- host `192.168.1.99`;
- CT100 `192.168.1.101`;
- CT101 `192.168.1.102`;
- Tailscale en el host;
- Tailscale Serve;
- sin puertos abiertos;
- HTTP dentro de la tailnet;
- alias SSH separados.

### Historia

- configuración anterior sobre Ubuntu Server;
- alias antiguos;
- pruebas de HTTPS interno;
- CT102 como experimento DNS.

### Pendientes

- consolidar DNS interno;
- documentar reservas DHCP con todos sus identificadores;
- inventariar configuración exacta de Tailscale Serve;
- validar periódicamente resolución LAN y tailnet.

---

## 5.17 Cierre

La red de `serviplan` busca ser sencilla de comprender.

La LAN proporciona estabilidad local.

Tailscale proporciona acceso remoto.

Tailscale Serve publica servicios.

SSH administra.

El router no expone puertos.

La separación entre caminos permite diagnosticar sin convertir cada incidencia en una reconstrucción completa.

---

# Capítulo 6. CT100 · Immich

## Índice

- [6.1 Función de CT100](#61-función-de-ct100)
- [6.2 Configuración del contenedor](#62-configuración-del-contenedor)
- [6.3 Arquitectura interna](#63-arquitectura-interna)
- [6.4 Servicios del stack](#64-servicios-del-stack)
- [6.5 Red y acceso](#65-red-y-acceso)
- [6.6 Almacenamiento](#66-almacenamiento)
- [6.7 Base de datos](#67-base-de-datos)
- [6.8 Machine learning](#68-machine-learning)
- [6.9 Arranque y operación](#69-arranque-y-operación)
- [6.10 Backup local](#610-backup-local)
- [6.11 Backup remoto](#611-backup-remoto)
- [6.12 Recuperación](#612-recuperación)
- [6.13 Validación](#613-validación)
- [6.14 Incidencias y lecciones](#614-incidencias-y-lecciones)
- [6.15 Estado actual y pendientes](#615-estado-actual-y-pendientes)
- [6.16 Cierre](#616-cierre)

---

## 6.1 Función de CT100

CT100 es el contenedor dedicado a Immich.

No contiene servicios multimedia generales ni herramientas experimentales.

Su función es alojar el ecosistema completo de fotografías y vídeo personal.

```text
CT100
└── Docker
    └── Immich
        ├── server
        ├── machine learning
        ├── PostgreSQL
        ├── Valkey
        └── biblioteca
```

La separación permite administrar Immich como una unidad funcional.

---

## 6.2 Configuración del contenedor

### Estado canónico

| Parámetro | Valor |
|---|---:|
| ID | 100 |
| Nombre lógico | CT100 · Immich |
| IP | `192.168.1.101` |
| Cores | 4 |
| RAM | 8 GB |
| Swap | 2 GB |
| Disco | 60 GB |
| Tipo | LXC no privilegiado |
| Opciones | `nesting=1`, `keyctl=1` |
| Arranque automático | Sí |
| Orden de arranque | 10 |

El contenedor se inicia antes que CT101.

No existe una dependencia estricta entre ambos, pero el orden evita un arranque simultáneo innecesario.

---

## 6.3 Arquitectura interna

Immich se ejecuta mediante Docker Compose dentro del LXC.

Capas:

```text
Proxmox
└── CT100
    └── Docker
        └── stack de Immich
```

La capa LXC proporciona:

- aislamiento respecto al host;
- recursos asignados;
- unidad de backup;
- administración desde Proxmox.

Docker proporciona:

- despliegue del stack;
- dependencias;
- actualización;
- red interna;
- configuración reproducible.

---

## 6.4 Servicios del stack

El stack incluye, al menos:

- Immich Server;
- Immich Machine Learning;
- PostgreSQL;
- Valkey;
- biblioteca de archivos;
- configuración Docker Compose.

Cada componente cumple una función distinta.

### Immich Server

Gestiona:

- API;
- usuarios;
- álbumes;
- subida;
- metadatos;
- coordinación del resto del stack.

### Machine Learning

Gestiona tareas como:

- reconocimiento facial;
- búsqueda semántica;
- clasificación;
- procesamiento de modelos.

### PostgreSQL

Almacena:

- usuarios;
- álbumes;
- referencias;
- metadatos;
- estado interno.

### Valkey

Actúa como servicio auxiliar para colas y caché.

---

## 6.5 Red y acceso

CT100 utiliza:

```text
IP:     192.168.1.101
Puerto: 2283
```

Acceso dentro de la tailnet:

```text
http://serviplan:2283
```

El contenedor no ejecuta Tailscale.

El host publica Immich mediante Tailscale Serve.

### Flujo

```text
Cliente
└── Tailscale
    └── serviplan:2283
        └── CT100:2283
            └── Immich
```

---

## 6.6 Almacenamiento

CT100 dispone de un disco de 60 GB.

El almacenamiento incluye:

- sistema del contenedor;
- configuración;
- Docker;
- biblioteca;
- base de datos;
- archivos generados;
- miniaturas;
- modelos;
- temporales.

No todo el contenido tiene el mismo valor.

### Crítico

- biblioteca original;
- base de datos;
- configuración;
- credenciales;
- archivos necesarios para reconstrucción.

### Regenerable

- determinadas miniaturas;
- cachés;
- modelos descargables;
- temporales.

La estrategia de backup debe distinguir ambas categorías.

---

## 6.7 Base de datos

PostgreSQL es una pieza crítica.

Una copia de archivos sin dump de la base de datos no constituye necesariamente una recuperación completa.

El backup remoto incluye un dump PostgreSQL.

La restauración debe respetar:

1. versión compatible;
2. orden correcto;
3. permisos;
4. variables de entorno;
5. coherencia entre base de datos y biblioteca.

### Incidencia histórica

El verificador de backups detectó en algún momento:

```text
system is starting up
```

durante `pg_dump`.

La lección es que el backup no debe asumir que PostgreSQL está listo únicamente porque el contenedor haya arrancado.

---

## 6.8 Machine learning

Immich Machine Learning forma parte del stack.

Puede consumir CPU, RAM y almacenamiento para modelos.

Su presencia justifica parte de los 8 GB asignados a CT100.

Los modelos pueden ser regenerables, pero la configuración y la integración con el stack deben conservarse.

No debe confundirse el funcionamiento de la interfaz con la salud del componente de machine learning.

---

## 6.9 Arranque y operación

El contenedor arranca automáticamente.

Orden lógico:

1. Proxmox;
2. CT100;
3. Docker;
4. PostgreSQL;
5. Valkey;
6. Immich Server;
7. Machine Learning.

La validación no debe limitarse a que CT100 figure como `running`.

Debe comprobarse:

- estado de contenedores Docker;
- salud de Immich;
- acceso web;
- base de datos;
- subida;
- procesamiento;
- almacenamiento disponible.

---

## 6.10 Backup local

CT100 se protege localmente mediante `vzdump`.

Ventajas:

- copia del LXC como unidad;
- restauración desde Proxmox;
- preservación de configuración;
- recuperación rápida.

El backup local se almacena en HDDBU.

### Política

- ejecución manual;
- frecuencia aproximada de una o dos semanas;
- una única copia vigente;
- manifiesto;
- hash SHA256.

El backup local no sustituye al remoto.

---

## 6.11 Backup remoto

SwissBackup protege de forma remota:

- configuración;
- inventario;
- biblioteca;
- dump PostgreSQL;
- elementos necesarios para reconstrucción.

La copia se cifra mediante `rclone crypt`.

La ejecución es automática mediante timer diario.

El backup remoto debe considerarse una protección frente a:

- pérdida del host;
- pérdida del SSD;
- pérdida del HDD local;
- desastre físico local.

---

## 6.12 Recuperación

Existen dos caminos principales.

### Restauración desde HDDBU

1. instalar Proxmox;
2. configurar almacenamiento;
3. localizar `vzdump`;
4. restaurar CT100;
5. arrancar;
6. validar red;
7. validar Docker;
8. validar Immich.

### Reconstrucción desde SwissBackup

1. reconstruir CT100;
2. instalar Docker;
3. recuperar Compose y variables;
4. recuperar biblioteca;
5. restaurar PostgreSQL;
6. arrancar servicios;
7. validar coherencia.

La restauración desde `vzdump` es más directa.

La reconstrucción desde datos remotos exige más pasos y más documentación.

---

## 6.13 Validación

Una validación completa debe comprobar:

1. CT100 en ejecución;
2. IP correcta;
3. Docker operativo;
4. contenedores sanos;
5. interfaz accesible;
6. usuarios presentes;
7. biblioteca visible;
8. subida de archivo;
9. creación de álbum;
10. procesamiento;
11. base de datos;
12. espacio disponible;
13. backup reciente.

No basta con que aparezca la pantalla de inicio.

---

## 6.14 Incidencias y lecciones

Lecciones acumuladas:

1. una aplicación puede responder aunque una dependencia esté degradada;
2. PostgreSQL necesita validación explícita;
3. biblioteca y base de datos deben recuperarse coherentemente;
4. el estado `running` del LXC no garantiza salud del stack;
5. el backup debe incluir dump de base de datos;
6. la publicación remota pertenece al host, no a CT100;
7. los datos regenerables no deben tratarse igual que los originales.

---

## 6.15 Estado actual y pendientes

### Estado vigente

- CT100 operativo;
- IP `192.168.1.101`;
- Immich en puerto 2283;
- Tailscale Serve desde el host;
- `vzdump` local;
- backup remoto cifrado;
- arranque automático.

### Pendientes

- prueba integral de restauración;
- verificación periódica del dump PostgreSQL;
- documentación exacta de rutas internas;
- inventario completo de volúmenes Docker;
- validación estable del acceso desde iPhone por Tailscale;
- revisión de crecimiento del disco.

---

## 6.16 Cierre

CT100 contiene uno de los servicios más importantes de `serviplan`.

Su valor no está solo en ejecutar Immich.

Está en reunir en una unidad claramente identificada:

- aplicación;
- base de datos;
- machine learning;
- biblioteca;
- backup;
- recuperación.

Immich debe poder sustituirse en el futuro.

Las fotografías y la capacidad de reconstruir no.

---

# Capítulo 7. CT101 · Multimedia

## Índice

- [7.1 Función de CT101](#71-función-de-ct101)
- [7.2 Configuración del contenedor](#72-configuración-del-contenedor)
- [7.3 Arquitectura interna](#73-arquitectura-interna)
- [7.4 Navidrome](#74-navidrome)
- [7.5 Jellyfin](#75-jellyfin)
- [7.6 Bibliotecas multimedia](#76-bibliotecas-multimedia)
- [7.7 Red y acceso](#77-red-y-acceso)
- [7.8 Almacenamiento](#78-almacenamiento)
- [7.9 GPU y aceleración](#79-gpu-y-aceleración)
- [7.10 Arranque y operación](#710-arranque-y-operación)
- [7.11 Backup local](#711-backup-local)
- [7.12 Backup remoto](#712-backup-remoto)
- [7.13 Recuperación](#713-recuperación)
- [7.14 Validación](#714-validación)
- [7.15 Incidencias y lecciones](#715-incidencias-y-lecciones)
- [7.16 Estado actual y pendientes](#716-estado-actual-y-pendientes)
- [7.17 Cierre](#717-cierre)

---

## 7.1 Función de CT101

CT101 agrupa el ecosistema multimedia de `serviplan`.

Su función principal es alojar:

- Navidrome;
- Jellyfin;
- biblioteca musical;
- películas;
- series;
- directorios de entrada;
- datos de configuración asociados.

La decisión de agrupar estos servicios responde a que comparten naturaleza, almacenamiento y mantenimiento.

No existe una necesidad confirmada que justifique separarlos en varios LXC.

---

## 7.2 Configuración del contenedor

### Estado canónico

| Parámetro | Valor |
|---|---:|
| ID | 101 |
| Nombre lógico | CT101 · Multimedia |
| IP | `192.168.1.102` |
| Cores | 4 |
| RAM | 4 GB |
| Swap | 1 GB |
| Disco | 400 GB |
| Tipo | LXC no privilegiado |
| Opciones | `nesting=1`, `keyctl=1` |
| Arranque automático | Sí |
| Orden de arranque | 20 |

CT101 arranca después de CT100.

No depende técnicamente de Immich, pero la secuencia evita un arranque simultáneo innecesario y mantiene una política predecible.

---

## 7.3 Arquitectura interna

CT101 utiliza Docker dentro del LXC.

```text
Proxmox
└── CT101
    └── Docker
        ├── Navidrome
        └── Jellyfin
```

La separación de capas es la misma que en CT100:

- Proxmox administra el invitado;
- LXC separa el entorno;
- Docker despliega las aplicaciones.

La diferencia está en la naturaleza de los datos y en la estrategia de backup.

---

## 7.4 Navidrome

Navidrome gestiona la biblioteca musical.

### Estado conocido

| Campo | Valor |
|---|---|
| Servicio | Navidrome |
| Puerto | `4533` |
| Contenedor Docker | `navidrome` |
| Estado esperado | En ejecución |

El servicio expone la biblioteca a clientes compatibles.

La música forma parte de los datos de mayor valor del contenedor.

### Principios operativos

1. la biblioteca debe permanecer legible desde el contenedor;
2. la ruta debe ser estable;
3. los permisos deben ser reproducibles;
4. el escaneo no debe confundirse con la existencia física de los archivos;
5. la base de datos y la configuración deben conservarse.

### Rescan

Navidrome puede requerir un reescaneo completo de la biblioteca.

El mecanismo concreto debe documentarse según la versión vigente.

No debe reutilizarse un comando histórico sin comprobar que corresponde a la instalación Docker actual.

---

## 7.5 Jellyfin

Jellyfin gestiona vídeo y otros contenidos multimedia.

### Estado conocido

| Campo | Valor |
|---|---|
| Servicio | Jellyfin |
| Puerto | `8096` |
| Contenedor Docker | `jellyfin` |
| Salud esperada | `healthy` |

Jellyfin depende de:

- biblioteca;
- configuración;
- base de datos;
- metadatos;
- cachés;
- acceso a GPU si se utiliza aceleración.

No todos esos elementos tienen el mismo valor.

### Crítico

- configuración;
- usuarios;
- base de datos;
- estructura de biblioteca;
- información no regenerable.

### Regenerable

- parte de las cachés;
- miniaturas;
- metadatos descargables;
- transcodificaciones temporales.

---

## 7.6 Bibliotecas multimedia

CT101 puede contener:

- música;
- música aparcada;
- películas;
- series;
- contenido de entrada;
- configuraciones.

La política de protección no trata todo por igual.

### Música

La música se considera prioritaria y debe estar respaldada.

La carpeta de música aparcada también se considera dentro del alcance de backup.

### Películas y series

No se consideran críticas por defecto.

Pueden excluirse de algunos backups si son recuperables y si el coste de protegerlas no compensa su valor.

La clasificación debe mantenerse explícita para no consumir almacenamiento remoto de forma indiscriminada.

---

## 7.7 Red y acceso

CT101 utiliza:

```text
IP: 192.168.1.102
```

Servicios:

```text
Navidrome: 4533
Jellyfin:  8096
```

Acceso dentro de la tailnet:

```text
http://serviplan:4533
http://serviplan:8096
```

Tailscale no se ejecuta dentro del contenedor.

El host publica ambos servicios mediante Tailscale Serve.

---

## 7.8 Almacenamiento

CT101 dispone de un disco de 400 GB.

La mayor parte del almacenamiento se dedica a bibliotecas multimedia.

### Estado conocido

El uso observado ha superado el 70 % en distintos momentos.

Esto obliga a vigilar:

- crecimiento;
- espacio libre;
- contenido pendiente de mover;
- ficheros de gran tamaño;
- equilibrio entre datos críticos y prescindibles.

La regla de operación es mantener margen razonable y evitar llegar al límite antes de actuar.

---

## 7.9 GPU y aceleración

La iGPU Intel del host está preparada para passthrough.

Jellyfin puede utilizarla para aceleración de hardware.

El flujo conceptual es:

```text
iGPU del host
└── VFIO
    └── CT101
        └── Jellyfin
```

Deben distinguirse tres estados:

1. GPU detectada por el host;
2. dispositivo asignado al LXC;
3. aceleración realmente utilizada por Jellyfin.

Solo el tercer estado confirma funcionamiento completo.

---

## 7.10 Arranque y operación

Orden lógico:

1. Proxmox;
2. CT101;
3. Docker;
4. Navidrome;
5. Jellyfin.

La validación debe comprobar:

- CT101 en ejecución;
- IP correcta;
- Docker operativo;
- Navidrome accesible;
- Jellyfin accesible;
- bibliotecas montadas;
- espacio disponible;
- permisos;
- estado de GPU si se utiliza;
- backup reciente.

---

## 7.11 Backup local

CT101 no se protege mediante `vzdump` como método principal.

Se utiliza `rsync`.

La decisión responde al tamaño del contenedor y a la naturaleza de los datos.

### Política

- ejecución manual;
- frecuencia aproximada de una o dos semanas;
- copia incremental;
- una única rama vigente;
- manifiesto;
- hashes;
- separación respecto a SwissBackup.

### Tratamiento de servicios

Durante el backup:

- Jellyfin puede detenerse brevemente;
- Navidrome puede copiarse en caliente;
- WAL y SHM de Jellyfin se excluyen;
- `rsync -H` no se utiliza.

Estas decisiones proceden de pruebas y de problemas observados.

---

## 7.12 Backup remoto

La integración completa de CT101 en SwissBackup no tiene el mismo nivel de cierre que el resto del sistema.

### Estado exacto

- el sistema remoto funciona;
- existen referencias y alcance parcial;
- la cobertura definitiva de CT101 requiere revisión.

No debe afirmarse que todo CT101 está completamente protegido en remoto si esa validación no se ha cerrado.

### Prioridad

La música y la configuración tienen mayor prioridad que películas y series.

---

## 7.13 Recuperación

La recuperación de CT101 se basa principalmente en reconstrucción y copia de datos.

### Flujo general

1. crear CT101;
2. asignar recursos;
3. configurar red;
4. instalar Docker;
5. restaurar Compose;
6. restaurar configuraciones;
7. restaurar bibliotecas;
8. arrancar Navidrome;
9. arrancar Jellyfin;
10. validar permisos;
11. validar escaneos;
12. validar GPU.

La restauración debe evitar mezclar datos regenerables y críticos.

---

## 7.14 Validación

### Navidrome

1. servicio en ejecución;
2. acceso web;
3. biblioteca visible;
4. reproducción;
5. escaneo;
6. clientes externos;
7. permisos.

### Jellyfin

1. contenedor sano;
2. acceso web;
3. usuarios;
4. bibliotecas;
5. reproducción directa;
6. transcodificación;
7. aceleración;
8. metadatos;
9. espacio disponible.

---

## 7.15 Incidencias y lecciones

Lecciones acumuladas:

1. un comando válido fuera de Docker puede fallar dentro de la arquitectura actual;
2. no debe asumirse la ruta de un binario dentro del LXC;
3. los contenedores Docker deben identificarse antes de ejecutar;
4. el almacenamiento requiere vigilancia;
5. la GPU debe validarse en todas sus capas;
6. Jellyfin y Navidrome no necesitan el mismo tratamiento durante backup;
7. las películas no deben protegerse como si fueran irreemplazables;
8. la música sí forma parte del núcleo de datos personales.

---

## 7.16 Estado actual y pendientes

### Estado vigente

- CT101 operativo;
- IP `192.168.1.102`;
- Navidrome en 4533;
- Jellyfin en 8096;
- Docker;
- arranque automático;
- backup local por `rsync`;
- publicación por Tailscale Serve.

### Pendientes

1. integración definitiva de CT101 en SwissBackup;
2. política formal de espacio libre;
3. validación documentada de aceleración;
4. documentación exacta de rutas;
5. procedimiento canónico de full rescan de Navidrome;
6. revisión periódica de bibliotecas y datos prescindibles.

---

## 7.17 Cierre

CT101 concentra la parte multimedia de `serviplan`.

Su diseño no busca aislar cada aplicación por separado.

Busca agrupar servicios que comparten almacenamiento y operación sin convertir el sistema en una colección innecesaria de invitados.

La prioridad no es conservar cada archivo multimedia.

Es conservar lo importante, saber qué puede regenerarse y poder reconstruir el servicio.

---

# Capítulo 8. Backups y recuperación

## Índice

- [8.1 La función real de un backup](#81-la-función-real-de-un-backup)
- [8.2 Principios de protección](#82-principios-de-protección)
- [8.3 Clasificación de datos](#83-clasificación-de-datos)
- [8.4 Arquitectura de copias](#84-arquitectura-de-copias)
- [8.5 HDDBU](#85-hddbu)
- [8.6 SwissBackup](#86-swissbackup)
- [8.7 Backup del host](#87-backup-del-host)
- [8.8 Backup de CT100](#88-backup-de-ct100)
- [8.9 Backup de CT101](#89-backup-de-ct101)
- [8.10 Manifiestos, hashes y logs](#810-manifiestos-hashes-y-logs)
- [8.11 Frecuencias](#811-frecuencias)
- [8.12 Recuperación local](#812-recuperación-local)
- [8.13 Recuperación remota](#813-recuperación-remota)
- [8.14 Validación](#814-validación)
- [8.15 Limitaciones conocidas](#815-limitaciones-conocidas)
- [8.16 Orden de reconstrucción](#816-orden-de-reconstrucción)
- [8.17 Cierre](#817-cierre)

---

## 8.1 La función real de un backup

Un backup no existe para demostrar que se han copiado archivos.

Existe para permitir recuperar una capacidad.

La capacidad puede ser:

- volver a acceder a fotografías;
- recuperar música;
- restaurar una configuración;
- reconstruir un contenedor;
- recuperar credenciales;
- reinstalar el host;
- volver a administrar el sistema.

Una copia que no puede localizarse, comprenderse o restaurarse no está completa.

---

## 8.2 Principios de protección

La estrategia de `serviplan` se basa en varios principios:

1. distinguir copia local y remota;
2. no tratar todos los datos igual;
3. conservar al menos una vía rápida de recuperación;
4. cifrar la copia externa;
5. generar evidencia de cada ejecución;
6. documentar qué cubre cada sistema;
7. no asumir que copiar equivale a restaurar;
8. mantener procedimientos comprensibles.

---

## 8.3 Clasificación de datos

### Críticos

- credenciales;
- claves SSH;
- configuración de Tailscale;
- configuración de `rclone`;
- documentación canónica;
- biblioteca de Immich;
- base de datos de Immich;
- configuración de servicios;
- música irremplazable;
- música aparcada.

### Importantes pero reconstruibles

- stacks Docker;
- archivos Compose;
- configuraciones;
- inventarios;
- scripts;
- timers.

### Regenerables

- miniaturas;
- cachés;
- modelos descargables;
- metadatos recuperables;
- transcodificaciones temporales.

### Prescindibles por defecto

- películas;
- series;
- contenido fácilmente recuperable.

La clasificación debe revisarse cuando cambie el valor real de los datos.

---

## 8.4 Arquitectura de copias

```text
serviplan
├── HDDBU
│   ├── backup local manual
│   ├── recuperación rápida
│   └── una copia vigente
└── SwissBackup
    ├── backup remoto
    ├── cifrado
    ├── automatizado
    └── protección ante desastre local
```

Los dos sistemas no son equivalentes.

Se complementan.

---

## 8.5 HDDBU

HDDBU es el nombre operativo del HDD externo identificado como `BACKUP_SERVIPLAN`.

### Función

- recuperación cercana;
- restauración rápida;
- copia del estado vigente;
- independencia de Internet.

### Política

1. ejecución manual;
2. frecuencia aproximada de una o dos semanas;
3. una única copia vigente;
4. manifiesto;
5. hashes SHA256;
6. sin timer;
7. estructura organizada por componente.

### Tratamiento

| Componente | Método |
|---|---|
| CT100 | `vzdump` |
| CT101 | `rsync` |
| Host | `tar.zst` |
| Inventario | Manifiestos y hashes |

---

## 8.6 SwissBackup

SwissBackup es la copia remota cifrada.

Se utiliza `rclone` con remoto `crypt`.

### Función

- protección frente a pérdida física local;
- copia externa;
- recuperación de datos críticos;
- automatización diaria.

### Estado operativo

- timer `systemd`;
- ejecución diaria;
- hora consolidada: 02:00;
- cifrado antes de almacenar.

### Alcance confirmado

- configuración e inventario del host;
- datos de CT100;
- biblioteca de Immich;
- dump PostgreSQL;
- elementos de configuración asociados.

### Alcance pendiente

La integración completa de CT101 requiere revisión.

---

## 8.7 Backup del host

El host necesita una copia de su configuración, no una imagen completa obligatoriamente.

Debe incluir:

- red;
- almacenamiento;
- configuración Proxmox;
- LXC;
- Tailscale;
- Tailscale Serve;
- SSH;
- VFIO;
- scripts;
- timers;
- inventarios;
- documentación técnica relevante.

El backup local se empaqueta en un archivo comprimido.

La reconstrucción del host sigue basándose en reinstalar Proxmox y restaurar configuración, no en clonar ciegamente todo el disco.

---

## 8.8 Backup de CT100

### Local

```text
vzdump
```

Ventajas:

- unidad restaurable;
- integración con Proxmox;
- recuperación directa.

### Remoto

Incluye:

- biblioteca;
- configuración;
- dump PostgreSQL;
- datos necesarios para reconstrucción.

La coherencia entre biblioteca y base de datos es crítica.

---

## 8.9 Backup de CT101

### Local

```text
rsync
```

Razones:

- tamaño;
- naturaleza de los datos;
- control granular;
- recuperación por reconstrucción.

### Reglas

- Jellyfin puede detenerse;
- Navidrome puede copiarse en caliente;
- excluir WAL y SHM de Jellyfin;
- no usar `rsync -H`;
- conservar configuración y biblioteca prioritaria.

### Remoto

Pendiente de cierre definitivo.

---

## 8.10 Manifiestos, hashes y logs

Cada backup debe dejar evidencia.

### Manifiesto

Debe indicar:

- fecha;
- origen;
- destino;
- componentes;
- tamaño;
- resultado;
- exclusiones;
- observaciones.

### Hashes

SHA256 permite detectar corrupción o cambios no esperados.

### Logs

Deben registrar:

- inicio;
- fin;
- duración;
- errores;
- código de salida;
- resultado.

La ausencia de errores visibles no equivale a éxito.

---

## 8.11 Frecuencias

### HDDBU

- manual;
- aproximadamente cada una o dos semanas;
- también antes de cambios importantes.

### SwissBackup

- automático;
- diario;
- 02:00.

Las frecuencias responden a objetivos diferentes.

El backup local prioriza control y recuperación rápida.

El remoto prioriza continuidad y protección fuera del domicilio.

---

## 8.12 Recuperación local

Orden general:

1. montar HDDBU;
2. verificar estructura;
3. revisar manifiesto;
4. verificar hashes;
5. identificar copia vigente;
6. restaurar host o contenedor;
7. arrancar;
8. validar.

### CT100

Restaurar `vzdump`.

### CT101

Recrear contenedor y aplicar `rsync`.

### Host

Reinstalar Proxmox y recuperar configuración.

---

## 8.13 Recuperación remota

Orden:

1. recuperar credenciales;
2. recuperar `rclone.conf`;
3. acceder al remoto cifrado;
4. descargar documentación;
5. recuperar configuración;
6. recuperar datos críticos;
7. reconstruir servicios;
8. restaurar bases de datos;
9. validar.

SwissBackup no sustituye a la documentación.

Sin procedimientos, la copia remota es solo un conjunto cifrado de objetos.

---

## 8.14 Validación

Una ejecución se considera correcta cuando:

1. termina con código de salida válido;
2. genera log;
3. crea o actualiza destino;
4. genera manifiesto;
5. genera hashes;
6. conserva estructura esperada;
7. permite localizar los datos;
8. no omite componentes críticos.

### Validación periódica

Debe incluir:

- listar contenido;
- verificar hashes;
- comprobar tamaño;
- revisar fecha;
- restaurar una muestra;
- revisar dump PostgreSQL.

---

## 8.15 Limitaciones conocidas

1. no existe prueba integral de restauración;
2. CT101 remoto no está completamente cerrado;
3. HDDBU mantiene una única copia vigente;
4. el HDD local es un dispositivo físico único;
5. el backup remoto depende de credenciales;
6. `rclone.conf` es crítico;
7. una mala clasificación puede excluir datos importantes;
8. un servicio `oneshot` puede aparecer `inactive (dead)` después de terminar correctamente.

Las limitaciones deben conocerse para no atribuir al sistema garantías que no tiene.

---

## 8.16 Orden de reconstrucción

El orden canónico es:

1. credenciales;
2. Strongbox;
3. SSH;
4. Tailscale;
5. `rclone`;
6. Proxmox;
7. red;
8. CT100;
9. CT101;
10. Tailscale Serve;
11. HDDBU;
12. SwissBackup;
13. validación.

Este orden refleja dependencias reales.

La recuperación empieza antes de instalar el servidor.

Empieza por recuperar la capacidad de acceder y autenticarse.

---

## 8.17 Cierre

La estrategia de backup de `serviplan` no se basa en una única herramienta.

Se basa en combinar:

- copia local;
- copia remota;
- cifrado;
- clasificación;
- manifiestos;
- hashes;
- logs;
- documentación;
- procedimientos de recuperación.

El objetivo no es guardar todo para siempre.

Es poder recuperar lo importante y reconstruir lo necesario.

---

# Capítulo 9. Operaciones de mantenimiento

## Índice

- [9.1 Finalidad del mantenimiento](#91-finalidad-del-mantenimiento)
- [9.2 Principios operativos](#92-principios-operativos)
- [9.3 Frecuencias y ritmos](#93-frecuencias-y-ritmos)
- [9.4 Revisión del host](#94-revisión-del-host)
- [9.5 Revisión de CT100](#95-revisión-de-ct100)
- [9.6 Revisión de CT101](#96-revisión-de-ct101)
- [9.7 Actualizaciones](#97-actualizaciones)
- [9.8 Espacio y almacenamiento](#98-espacio-y-almacenamiento)
- [9.9 Backups](#99-backups)
- [9.10 Red y acceso remoto](#910-red-y-acceso-remoto)
- [9.11 Temperaturas y batería](#911-temperaturas-y-batería)
- [9.12 Logs y servicios](#912-logs-y-servicios)
- [9.13 Mantenimiento antes de cambios importantes](#913-mantenimiento-antes-de-cambios-importantes)
- [9.14 Comprobaciones posteriores](#914-comprobaciones-posteriores)
- [9.15 Registro de incidencias](#915-registro-de-incidencias)
- [9.16 Estado, historia y pendientes](#916-estado-historia-y-pendientes)
- [9.17 Cierre](#917-cierre)

---

## 9.1 Finalidad del mantenimiento

El mantenimiento de `serviplan` no busca intervenir constantemente.

Busca evitar que pequeños problemas acumulados se conviertan en fallos graves.

La infraestructura debe funcionar con poca atención, pero no sin observación.

El principio general es:

> El mejor sistema es el que casi no necesita ejecutarse, pero cuando se ejecuta deja claro qué ha ocurrido.

El mantenimiento debe ser:

- periódico;
- comprensible;
- proporcionado;
- verificable;
- documentado;
- no destructivo por defecto.

---

## 9.2 Principios operativos

Las operaciones de mantenimiento siguen estas reglas:

1. comprobar antes de modificar;
2. registrar el estado previo;
3. hacer una sola clase de cambio cada vez;
4. validar después;
5. no eliminar datos sin autorización expresa;
6. no aplicar workarounds inseguros;
7. no confundir una hipótesis con un hecho;
8. mantener separado el host de los servicios;
9. revisar backups antes de cambios de riesgo;
10. actualizar la documentación cuando cambie el sistema.

---

## 9.3 Frecuencias y ritmos

No todas las tareas necesitan la misma periodicidad.

### Diarias

- SwissBackup;
- revisión automática de su resultado;
- comprobación básica de servicios si existe automatización.

### Semanales o quincenales

- HDDBU;
- revisión de espacio;
- revisión de actualizaciones;
- inspección de logs relevantes;
- comprobación de temperaturas;
- revisión de servicios fallidos.

### Antes de cambios importantes

- backup local;
- inventario;
- estado de contenedores;
- espacio disponible;
- documentación de la configuración vigente.

### Después de cambios

- reinicio controlado si procede;
- validación de red;
- validación de CT100;
- validación de CT101;
- validación de acceso remoto;
- validación de backups;
- actualización del canon.

---

## 9.4 Revisión del host

La revisión del host debe comprobar:

- versión de Proxmox;
- kernel;
- repositorios;
- estado de servicios;
- unidades fallidas;
- almacenamiento;
- LXC;
- red;
- Tailscale;
- VFIO;
- temperatura;
- uso de memoria;
- estado de backups.

### Estado actual conocido

| Elemento | Estado |
|---|---|
| Proxmox | Operativo |
| Hostname | `serviplan` |
| IP | `192.168.1.99` |
| CT100 | Operativo |
| CT101 | Operativo |
| Tailscale | Centralizado en host |
| Repositorios enterprise | Desactivados |
| Repositorio no-subscription | Activado |

La revisión debe centrarse en cambios respecto al estado esperado.

---

## 9.5 Revisión de CT100

CT100 requiere comprobar:

1. estado del LXC;
2. uso de disco;
3. uso de memoria;
4. estado de Docker;
5. salud de Immich;
6. PostgreSQL;
7. Valkey;
8. machine learning;
9. acceso web;
10. última copia;
11. dump de base de datos;
12. crecimiento de biblioteca.

La aplicación puede responder aunque exista una dependencia degradada.

Por eso la interfaz web no es una prueba suficiente.

---

## 9.6 Revisión de CT101

CT101 requiere comprobar:

1. estado del LXC;
2. uso de disco;
3. Docker;
4. Navidrome;
5. Jellyfin;
6. bibliotecas;
7. permisos;
8. espacio libre;
9. GPU;
10. escaneo de música;
11. reproducción;
12. última copia.

El crecimiento del almacenamiento merece especial atención.

La revisión debe identificar:

- archivos grandes;
- contenido prescindible;
- bibliotecas duplicadas;
- directorios de entrada;
- margen disponible.

---

## 9.7 Actualizaciones

Las actualizaciones deben tratarse por capas.

### Host

- Proxmox;
- kernel;
- paquetes del sistema.

### LXC

- sistema base;
- Docker;
- dependencias.

### Aplicaciones

- Immich;
- Jellyfin;
- Navidrome;
- imágenes Docker.

No debe actualizarse todo simultáneamente sin una razón clara.

La secuencia preferente es:

1. revisar changelog;
2. comprobar backups;
3. actualizar una capa;
4. validar;
5. continuar con la siguiente.

### Precaución

Las etiquetas `latest` facilitan actualización, pero reducen control de versión.

El uso de imágenes concretas debe revisarse cuando la estabilidad lo justifique.

---

## 9.8 Espacio y almacenamiento

El espacio debe vigilarse en:

- `local`;
- `local-lvm`;
- CT100;
- CT101;
- HDDBU;
- SwissBackup.

La regla práctica es evitar operar cerca del límite.

El almacenamiento libre no debe verse como capacidad desaprovechada.

Es margen para:

- crecimiento;
- backups temporales;
- actualizaciones;
- snapshots;
- reconstrucciones;
- incidencias.

La regla de los tercios puede utilizarse como criterio orientativo: conservar aproximadamente un tercio libre cuando sea razonable.

---

## 9.9 Backups

La revisión de backups debe comprobar:

### HDDBU

- fecha;
- manifiesto;
- hashes;
- estructura;
- tamaño;
- ejecución manual reciente;
- montaje correcto del HDD.

### SwissBackup

- última ejecución;
- código de salida;
- logs;
- tamaño;
- contenido esperado;
- dump PostgreSQL;
- cifrado;
- timer activo.

No basta con que el timer exista.

Debe comprobarse que la ejecución produjo datos válidos.

---

## 9.10 Red y acceso remoto

La revisión debe validar:

- LAN;
- resolución de `serviplan`;
- SSH por LAN;
- SSH por Tailscale;
- Tailscale;
- Tailscale Serve;
- acceso a Immich;
- acceso a Navidrome;
- acceso a Jellyfin.

La existencia de dos caminos administrativos permite aislar fallos.

Si funciona LAN pero no Tailscale, el problema no está necesariamente en el servidor.

---

## 9.11 Temperaturas y batería

### Temperaturas

Valores observados:

```text
44–54 °C
CPU habitual: 51–52 °C
```

Deben revisarse tendencias, no solo cifras aisladas.

Aumentos sostenidos pueden indicar:

- polvo;
- ventilación obstruida;
- carga anómala;
- ventilador degradado;
- temperatura ambiente elevada.

### Batería

Estado conocido:

```text
Capacidad aproximada: 92 %
Ciclos: 0
```

No existe todavía un mecanismo canónico de límite de carga.

La revisión debe evitar soluciones no soportadas.

---

## 9.12 Logs y servicios

Los logs deben utilizarse para confirmar hechos.

Un servicio `oneshot` puede aparecer:

```text
inactive (dead)
```

después de terminar correctamente.

La revisión debe considerar:

- `ExecMainStatus`;
- código de salida;
- tiempo de ejecución;
- logs;
- resultado producido.

No debe diagnosticarse un fallo solo por el estado posterior del servicio.

### Unidades fallidas

La ausencia de unidades fallidas es una señal útil, pero no sustituye a la validación funcional.

---

## 9.13 Mantenimiento antes de cambios importantes

Antes de:

- actualizar Proxmox;
- cambiar kernel;
- modificar VFIO;
- ampliar discos;
- cambiar red;
- actualizar Immich;
- modificar backups;
- alterar Tailscale;

debe realizarse:

1. inventario;
2. backup;
3. revisión de espacio;
4. copia de archivos de configuración;
5. registro del estado;
6. identificación de la ruta de retorno.

No se debe depender de la memoria para revertir.

---

## 9.14 Comprobaciones posteriores

Después de un cambio:

1. comprobar host;
2. comprobar red;
3. comprobar almacenamiento;
4. comprobar CT100;
5. comprobar CT101;
6. comprobar Tailscale;
7. comprobar SSH;
8. comprobar Tailscale Serve;
9. comprobar backups;
10. actualizar documentación.

La validación debe seguir la arquitectura de abajo arriba.

---

## 9.15 Registro de incidencias

Cada incidencia relevante debe registrar:

- fecha;
- síntoma;
- impacto;
- hipótesis;
- pruebas;
- causa confirmada;
- solución;
- estado final;
- lección;
- cambios en el canon.

El objetivo no es crear burocracia.

Es impedir que el mismo problema vuelva a investigarse desde cero.

---

## 9.16 Estado, historia y pendientes

### Estado vigente

- mantenimiento manual y periódico;
- SwissBackup diario;
- HDDBU manual;
- revisión por capas;
- validación posterior;
- documentación como parte del cierre.

### Historia

- scripts anteriores de Ubuntu Server;
- configuraciones obsoletas;
- pruebas eliminadas;
- ajustes de VFIO;
- problemas de observabilidad.

### Pendientes

1. monitorización térmica automática;
2. política formal de alertas;
3. snapshots;
4. restauración integral;
5. consolidación de CT101 remoto;
6. revisión periódica de CVE relevantes;
7. automatización de verificaciones sin aumentar complejidad innecesaria.

---

## 9.17 Cierre

El mantenimiento de `serviplan` no consiste en tocar constantemente.

Consiste en saber cuándo intervenir, qué comprobar y cómo demostrar que el sistema sigue sano.

Un mantenimiento correcto deja tres resultados:

- el sistema sigue funcionando;
- el cambio puede explicarse;
- la documentación sigue representando la realidad.

---

# Capítulo 10. Reconstrucción tras desastre

## Índice

- [10.1 Qué significa reconstruir](#101-qué-significa-reconstruir)
- [10.2 Escenarios de desastre](#102-escenarios-de-desastre)
- [10.3 Prioridades](#103-prioridades)
- [10.4 Dependencias previas](#104-dependencias-previas)
- [10.5 Material necesario](#105-material-necesario)
- [10.6 Recuperación de credenciales](#106-recuperación-de-credenciales)
- [10.7 Preparación del hardware](#107-preparación-del-hardware)
- [10.8 Instalación de Proxmox](#108-instalación-de-proxmox)
- [10.9 Configuración del host](#109-configuración-del-host)
- [10.10 Red](#1010-red)
- [10.11 Almacenamiento](#1011-almacenamiento)
- [10.12 Tailscale y SSH](#1012-tailscale-y-ssh)
- [10.13 Restauración de CT100](#1013-restauración-de-ct100)
- [10.14 Reconstrucción de CT101](#1014-reconstrucción-de-ct101)
- [10.15 Publicación de servicios](#1015-publicación-de-servicios)
- [10.16 Restauración de backups](#1016-restauración-de-backups)
- [10.17 Validación integral](#1017-validación-integral)
- [10.18 Qué no debe hacerse](#1018-qué-no-debe-hacerse)
- [10.19 Estado de las pruebas](#1019-estado-de-las-pruebas)
- [10.20 Cierre](#1020-cierre)

---

## 10.1 Qué significa reconstruir

Reconstruir no significa únicamente volver a encender un servidor.

Significa recuperar la capacidad completa de:

- administrar;
- acceder;
- servir datos;
- restaurar servicios;
- realizar backups;
- continuar operando.

La reconstrucción debe ser posible desde un SSD vacío.

El objetivo del libro es que pueda realizarla una persona que no haya participado en la instalación original.

---

## 10.2 Escenarios de desastre

Este capítulo cubre varios escenarios.

### Fallo del SSD

- hardware intacto;
- pérdida del sistema;
- recuperación desde HDDBU o SwissBackup.

### Pérdida del host

- sustitución del MSI;
- nueva instalación;
- posible cambio de hardware.

### Pérdida del HDD local

- host operativo;
- dependencia de SwissBackup.

### Pérdida local completa

- host y HDD destruidos;
- recuperación remota.

### Pérdida del Mac

- necesidad de recuperar Strongbox;
- SSH;
- Tailscale;
- `rclone`;
- documentación.

La reconstrucción debe considerar tanto el servidor como el entorno de administración.

---

## 10.3 Prioridades

Orden de prioridad:

1. credenciales;
2. documentación;
3. acceso;
4. red;
5. host;
6. CT100;
7. CT101;
8. publicación;
9. backups;
10. validación.

Los datos más valiosos deben recuperarse antes que los servicios prescindibles.

---

## 10.4 Dependencias previas

Antes de instalar Proxmox deben localizarse:

- base de Strongbox;
- contraseña principal;
- clave SSH;
- credenciales de Tailscale;
- `rclone.conf`;
- credenciales de SwissBackup;
- documentación canónica;
- acceso a kDrive;
- HDD local si existe;
- acceso al router.

Sin estos elementos, la instalación puede completarse, pero la infraestructura no.

---

## 10.5 Material necesario

### Hardware

- MSI o equipo sustituto;
- SSD;
- cargador;
- cable Ethernet;
- acceso al router;
- HDD HDDBU si existe.

### Software y datos

- ISO de Proxmox;
- documentación;
- credenciales;
- backups;
- configuración SSH;
- Tailscale;
- `rclone`;
- archivos Compose;
- dumps;
- inventarios.

### Pendiente

El libro debe mantener una lista actualizada de versiones compatibles.

Las versiones exactas cambian y no deben fijarse sin revisión.

---

## 10.6 Recuperación de credenciales

La reconstrucción empieza por Strongbox.

Orden:

1. recuperar la base;
2. abrirla;
3. localizar credenciales;
4. localizar clave SSH;
5. validar acceso a servicios externos;
6. recuperar `rclone.conf`;
7. comprobar Tailscale.

La clave SSH no debe considerarse separada del agente y de la configuración del Mac.

---

## 10.7 Preparación del hardware

Antes de instalar:

1. verificar SSD;
2. conectar Ethernet;
3. revisar BIOS/UEFI;
4. habilitar virtualización;
5. habilitar IOMMU;
6. comprobar orden de arranque;
7. documentar cualquier diferencia de hardware.

No deben copiarse opciones BIOS no confirmadas.

Solo deben aplicarse las necesarias y verificables.

---

## 10.8 Instalación de Proxmox

Instalar Proxmox sobre el SSD vacío.

Datos canónicos:

```text
Hostname: serviplan
IP:       192.168.1.99/24
Gateway:  192.168.1.1
```

Después:

1. actualizar;
2. desactivar repositorio enterprise;
3. activar no-subscription;
4. revisar almacenamiento;
5. comprobar red;
6. comprobar acceso web;
7. comprobar SSH.

---

## 10.9 Configuración del host

Restaurar o reconstruir:

- red;
- `vmbr0`;
- almacenamiento;
- usuarios;
- SSH;
- Tailscale;
- Tailscale Serve;
- VFIO;
- scripts;
- timers;
- backups.

El host no debe recibir aplicaciones de usuario.

Su función sigue siendo administrar la infraestructura.

---

## 10.10 Red

Validar:

```text
Host:  192.168.1.99
CT100: 192.168.1.101
CT101: 192.168.1.102
```

Comprobar:

1. reservas DHCP;
2. gateway;
3. DNS;
4. resolución de `serviplan`;
5. LAN;
6. Internet;
7. tailnet.

No avanzar a servicios si la red no es estable.

---

## 10.11 Almacenamiento

Recrear o validar:

- `local`;
- `local-lvm`;
- espacio;
- volúmenes;
- capacidad para CT100;
- capacidad para CT101.

Valores canónicos actuales:

```text
CT100: 60 GB
CT101: 400 GB
```

Si el hardware cambia, los tamaños pueden revisarse, pero la decisión debe documentarse.

---

## 10.12 Tailscale y SSH

### Tailscale

1. instalar en el host;
2. autenticar;
3. validar nodo;
4. validar resolución;
5. no instalar en LXC.

### SSH

1. restaurar configuración del Mac;
2. activar Strongbox como agente;
3. validar alias `serviplan_LAN`;
4. validar alias `serviplan`;
5. confirmar acceso.

Ambos caminos deben funcionar antes de continuar.

---

## 10.13 Restauración de CT100

### Opción A · HDDBU

1. montar HDDBU;
2. verificar hash;
3. localizar `vzdump`;
4. restaurar CT100;
5. asignar red;
6. arrancar;
7. validar Docker;
8. validar Immich.

### Opción B · SwissBackup

1. crear CT100;
2. asignar 4 cores;
3. asignar 8 GB RAM;
4. asignar 2 GB swap;
5. asignar 60 GB;
6. configurar `nesting=1`;
7. configurar `keyctl=1`;
8. instalar Docker;
9. recuperar Compose;
10. recuperar variables;
11. recuperar biblioteca;
12. restaurar PostgreSQL;
13. arrancar;
14. validar.

CT100 debe conservar el ID 100 durante una reconstrucción fiel.

---

## 10.14 Reconstrucción de CT101

1. crear CT101;
2. asignar 4 cores;
3. asignar 4 GB RAM;
4. asignar 1 GB swap;
5. asignar 400 GB;
6. configurar LXC no privilegiado;
7. habilitar `nesting=1`;
8. habilitar `keyctl=1`;
9. configurar IP `192.168.1.102`;
10. instalar Docker;
11. recuperar Navidrome;
12. recuperar Jellyfin;
13. restaurar música;
14. restaurar configuraciones;
15. restaurar otros datos según prioridad;
16. validar permisos;
17. validar GPU.

CT101 debe conservar el ID 101.

---

## 10.15 Publicación de servicios

Recrear Tailscale Serve:

```text
2283 → CT100:2283
4533 → CT101:4533
8096 → CT101:8096
```

Validar:

```text
http://serviplan:2283
http://serviplan:4533
http://serviplan:8096
```

No abrir puertos en el router.

No habilitar HTTPS interno salvo decisión nueva.

---

## 10.16 Restauración de backups

Después de recuperar servicios:

1. restaurar script HDDBU;
2. restaurar servicio manual;
3. comprobar montaje;
4. restaurar SwissBackup;
5. restaurar timer;
6. validar `rclone`;
7. ejecutar prueba;
8. revisar logs;
9. revisar manifiestos.

Un sistema reconstruido sin backups activos sigue incompleto.

---

## 10.17 Validación integral

### Host

- Proxmox;
- red;
- almacenamiento;
- Tailscale;
- SSH;
- VFIO;
- unidades fallidas.

### CT100

- LXC;
- Docker;
- Immich;
- PostgreSQL;
- biblioteca;
- subida;
- acceso remoto.

### CT101

- LXC;
- Docker;
- Navidrome;
- Jellyfin;
- bibliotecas;
- reproducción;
- GPU.

### Backups

- HDDBU;
- SwissBackup;
- logs;
- hashes;
- timer.

### Documentación

- registrar diferencias;
- actualizar inventario;
- actualizar versiones;
- cerrar pendientes surgidos.

---

## 10.18 Qué no debe hacerse

Durante la reconstrucción:

1. no borrar datos sin autorización;
2. no recrear CT102;
3. no instalar Tailscale dentro de CT100 o CT101;
4. no ejecutar servicios de usuario en el host;
5. no introducir Windows;
6. no recuperar `vfio_virqfd`;
7. no abrir puertos por comodidad;
8. no asumir rutas no verificadas;
9. no ocultar pendientes;
10. no confundir una restauración parcial con una validación integral.

---

## 10.19 Estado de las pruebas

### Confirmado

- backups locales completados;
- SwissBackup completado;
- CT100 operativo;
- CT101 operativo;
- Tailscale operativo;
- servicios publicados;
- procedimientos documentados.

### No confirmado

No se ha ejecutado una restauración integral de extremo a extremo sobre hardware vacío.

Esta limitación debe permanecer visible hasta que se realice la prueba.

---

## 10.20 Cierre

La reconstrucción de `serviplan` no depende de una imagen mágica ni de una única copia.

Depende de:

- credenciales;
- documentación;
- red;
- Proxmox;
- contenedores;
- datos;
- backups;
- validación.

El sistema estará realmente reconstruido cuando vuelva a poder administrarse, operar y protegerse.

No antes.

---

# Capítulo 11. Incidencias históricas y lecciones aprendidas

## Índice

- [11.1 Por qué conservar las incidencias](#111-por-qué-conservar-las-incidencias)
- [11.2 Ubuntu Server no fue un fracaso](#112-ubuntu-server-no-fue-un-fracaso)
- [11.3 La migración Big Bang](#113-la-migración-big-bang)
- [11.4 CT102 y el valor de eliminar](#114-ct102-y-el-valor-de-eliminar)
- [11.5 `vfio_virqfd`](#115-vfio_virqfd)
- [11.6 HTTPS interno sobre Tailscale](#116-https-interno-sobre-tailscale)
- [11.7 Batería y ausencia de interfaces estándar](#117-batería-y-ausencia-de-interfaces-estándar)
- [11.8 Backup local y `rsync -H`](#118-backup-local-y-rsync--h)
- [11.9 WAL y SHM de Jellyfin](#119-wal-y-shm-de-jellyfin)
- [11.10 Servicios `oneshot` e interpretación de estados](#1110-servicios-oneshot-e-interpretación-de-estados)
- [11.11 PostgreSQL «system is starting up»](#1111-postgresql-system-is-starting-up)
- [11.12 Operaciones S3 sin progreso visible](#1112-operaciones-s3-sin-progreso-visible)
- [11.13 Rutas y contexto de ejecución](#1113-rutas-y-contexto-de-ejecución)
- [11.14 Diferenciar host, LXC y Docker](#1114-diferenciar-host-lxc-y-docker)
- [11.15 Documentación desactualizada](#1115-documentación-desactualizada)
- [11.16 Resumen de lecciones permanentes](#1116-resumen-de-lecciones-permanentes)
- [11.17 Cierre](#1117-cierre)

---

## 11.1 Por qué conservar las incidencias

Una incidencia técnica no termina cuando el servicio vuelve a funcionar.

Termina cuando quedan claros:

- el síntoma;
- el contexto;
- la causa;
- la solución;
- el estado final;
- la lección;
- el cambio necesario en la documentación.

Conservar incidencias no significa llenar el libro de anécdotas.

Significa evitar que el mismo problema vuelva a investigarse desde cero.

Este capítulo recoge aquellas situaciones que modificaron la forma de operar `serviplan`.

---

## 11.2 Ubuntu Server no fue un fracaso

### Situación

La arquitectura original funcionaba sobre Ubuntu Server bare-metal.

### Riesgo de interpretación

La migración a Proxmox podía leerse como consecuencia de:

- inestabilidad;
- falta de capacidad;
- mala elección inicial;
- necesidad de abandonar Ubuntu.

### Hecho confirmado

Ubuntu Server funcionaba correctamente.

La migración respondió a:

- aprendizaje;
- virtualización;
- separación;
- crecimiento;
- experimentación.

### Lección

> Sustituir una arquitectura no convierte automáticamente en errónea la arquitectura anterior.

La documentación debe conservar el motivo real de cada cambio.

---

## 11.3 La migración Big Bang

### Situación

La mayor parte de la migración a Proxmox se concentró prácticamente en una jornada.

### Ventajas

- cambio rápido;
- arquitectura nueva disponible enseguida;
- menor periodo de convivencia;
- validación inmediata.

### Riesgos

- muchas variables cambiaron a la vez;
- dependencia de memoria reciente;
- posibilidad de confundir causas;
- necesidad de documentación posterior intensiva.

### Lección

Una migración Big Bang puede ser válida en un entorno doméstico pequeño si:

1. existe copia;
2. el sistema anterior se conserva temporalmente;
3. el hardware permite retorno;
4. los servicios pueden validarse;
5. la documentación se consolida después.

No debe elevarse a regla universal.

---

## 11.4 CT102 y el valor de eliminar

### Situación

CT102 se creó para explorar un posible servicio DNS interno.

### Resultado

No llegó a aportar una función necesaria dentro de la arquitectura estable.

### Decisión

El 7 de junio de 2026 se apagó y eliminó.

```text
No recrear CT102 salvo nueva decisión expresa.
```

### Lección

Un experimento no adquiere derecho de permanencia por haber consumido tiempo.

La historia conserva la prueba.

El canon conserva únicamente lo que debe existir.

---

## 11.5 `vfio_virqfd`

### Situación

En `/etc/modules` permanecía:

```text
vfio_virqfd
```

La entrada correspondía a una configuración obsoleta.

### Acción

Se creó una copia previa:

```text
/etc/modules.backup_20260709_1901
```

Después se eliminó la línea.

### Estado vigente

```text
vfio
vfio_iommu_type1
vfio_pci
```

### Lección

No debe conservarse una receta antigua porque alguna vez funcionó.

Una configuración obsoleta puede:

- generar errores;
- introducir ruido;
- confundir una reconstrucción;
- ocultar el estado real.

El canon debe representar el presente.

---

## 11.6 HTTPS interno sobre Tailscale

### Situación

Se valoró habilitar HTTPS interno para Immich, Navidrome y Jellyfin.

### Beneficio aparente

- URL con HTTPS;
- capa adicional;
- apariencia de mayor seguridad.

### Coste real

- certificados;
- renovación;
- mantenimiento;
- más puntos de fallo;
- nuevas rutas;
- complejidad sin necesidad confirmada.

### Decisión

Mantener HTTP dentro de la tailnet:

```text
http://serviplan:2283
http://serviplan:4533
http://serviplan:8096
```

### Lección

> La seguridad no consiste en añadir capas indiscriminadamente.

Debe identificarse:

1. qué amenaza existe;
2. qué capa la reduce;
3. cuánto cuesta operar esa capa;
4. si el beneficio compensa la complejidad.

---

## 11.7 Batería y ausencia de interfaces estándar

### Situación

Se buscó limitar la carga del MSI para reducir degradación.

### Interfaces esperadas

```text
charge_control_start_threshold
charge_control_end_threshold
```

### Resultado

No estaban disponibles.

### Riesgo

Buscar una solución agresiva mediante:

- escritura sobre EC;
- utilidades sin soporte;
- Windows temporal;
- métodos no documentados.

### Decisión

Aceptar la limitación mientras no exista una vía segura.

### Lección

No todo problema debe resolverse inmediatamente.

A veces, documentar una limitación es mejor que introducir un riesgo mayor.

---

## 11.8 Backup local y `rsync -H`

### Situación

La copia de CT101 utilizaba `rsync`.

La opción:

```text
-H
```

intentaba preservar hardlinks.

### Problema

Aumentaba consumo y complejidad sin un beneficio justificado para el caso real.

### Decisión

Retirar `rsync -H`.

### Lección

Una opción técnicamente correcta puede ser operacionalmente inadecuada.

No debe conservarse un parámetro solo porque parezca más completo.

Debe justificar su coste.

---

## 11.9 WAL y SHM de Jellyfin

### Situación

Durante la copia de Jellyfin aparecían archivos asociados a SQLite:

- WAL;
- SHM.

### Riesgo

Copiarlos mientras la aplicación escribe puede producir una instantánea incoherente.

### Decisión

- detener Jellyfin brevemente;
- excluir WAL y SHM;
- copiar la base principal en estado consistente.

### Lección

Copiar archivos de una aplicación activa no equivale a copiar un estado restaurable.

La estrategia debe conocer cómo persiste datos cada servicio.

---

## 11.10 Servicios `oneshot` e interpretación de estados

### Situación

Un servicio ejecutado manualmente terminaba y aparecía como:

```text
inactive (dead)
```

### Interpretación errónea

Asumir que el servicio había fallado.

### Interpretación correcta

Un servicio `oneshot` puede quedar inactivo después de completar correctamente.

### Validación

Debe revisarse:

- código de salida;
- `ExecMainStatus`;
- logs;
- archivos producidos;
- manifiesto;
- resultado real.

### Lección

El estado de `systemd` debe interpretarse según el tipo de unidad.

No todas las unidades correctas permanecen activas.

---

## 11.11 PostgreSQL «system is starting up»

### Situación

Durante un `pg_dump` apareció:

```text
system is starting up
```

### Causa operativa

PostgreSQL todavía no estaba listo aunque el entorno general hubiese arrancado.

### Riesgo

Dar por válido un backup incompleto.

### Lección

El arranque del contenedor no garantiza disponibilidad de la base de datos.

El backup debe:

1. comprobar readiness;
2. esperar;
3. reintentar;
4. fallar de forma visible si no puede generar el dump.

---

## 11.12 Operaciones S3 sin progreso visible

### Situación

Algunas copias server-side de objetos grandes podían parecer detenidas.

### Realidad

La operación seguía ejecutándose en el backend.

### Consecuencia

La falta de progreso visible generaba dudas sobre:

- bloqueo;
- fallo;
- actividad real.

### Opción documentada

Cuando se necesitara progreso más visible:

```text
--disable Copy
```

### Lección

La observabilidad forma parte de la operación.

Un proceso correcto pero opaco puede resultar difícil de administrar.

La opción no debe aplicarse como regla universal.

---

## 11.13 Rutas y contexto de ejecución

### Situación

Un comando válido en una arquitectura podía fallar en otra.

Ejemplo conceptual:

- ejecutar un binario directamente en el LXC;
- cuando el servicio real vive dentro de Docker.

### Riesgo

Inventar rutas, asumir binarios o mezclar capas.

### Lección

Antes de ejecutar debe identificarse:

1. host;
2. LXC;
3. contenedor Docker;
4. nombre real del servicio;
5. ruta real;
6. usuario;
7. permisos.

La arquitectura debe preceder al comando.

---

## 11.14 Diferenciar host, LXC y Docker

### Situación

`serviplan` tiene tres niveles de ejecución:

```text
Host Proxmox
└── LXC
    └── Docker
```

### Problema recurrente

Confundir dónde vive:

- un servicio;
- un binario;
- una configuración;
- un volumen;
- un log.

### Lección

Toda instrucción técnica debe indicar explícitamente el contexto.

Ejemplo:

```text
Ejecutar en SERVIPLAN / HOST PROXMOX
```

o:

```text
Ejecutar dentro de CT101
```

o:

```text
Ejecutar dentro del contenedor Docker jellyfin
```

La omisión del contexto convierte un comando correcto en una fuente de errores.

---

## 11.15 Documentación desactualizada

### Situación

La migración generó:

- nombres antiguos;
- rutas anteriores;
- configuraciones temporales;
- scripts históricos;
- decisiones superadas.

### Riesgo

Reconstruir el pasado en lugar del presente.

### Solución

Clasificar cada dato como:

- estado actual;
- historia;
- pendiente.

### Lección

La documentación no debe limitarse a acumular información.

Debe mantener jerarquía y vigencia.

---

## 11.16 Resumen de lecciones permanentes

1. No inventar rutas.
2. Identificar siempre la capa de ejecución.
3. Un estado aparente no sustituye a la validación.
4. Los backups deben probar coherencia.
5. La observabilidad importa.
6. Una opción más completa no siempre es mejor.
7. No mantener componentes sin función.
8. No recuperar configuraciones obsoletas.
9. No añadir seguridad sin amenaza concreta.
10. Documentar límites es mejor que ocultarlos.
11. Una migración exitosa no invalida la arquitectura anterior.
12. El canon debe describir el presente.
13. La historia debe conservar las causas.
14. Los pendientes no deben presentarse como resueltos.
15. La reconstrucción es la prueba última de comprensión.

---

## 11.17 Cierre

Las incidencias de `serviplan` no forman una colección de fallos aislados.

Forman una secuencia de aprendizaje.

Cada una obligó a mejorar:

- la arquitectura;
- los scripts;
- los backups;
- la observabilidad;
- la documentación;
- el criterio operativo.

El valor de una incidencia no está en haberla sufrido.

Está en impedir que vuelva a repetirse sin conocimiento.

---

# Capítulo 12. Filosofía de operación

## Índice

- [12.1 Operar no es intervenir constantemente](#121-operar-no-es-intervenir-constantemente)
- [12.2 Comprender antes de ejecutar](#122-comprender-antes-de-ejecutar)
- [12.3 Una cosa cada vez](#123-una-cosa-cada-vez)
- [12.4 No borrar sin autorización](#124-no-borrar-sin-autorización)
- [12.5 La reconstrucción como criterio de verdad](#125-la-reconstrucción-como-criterio-de-verdad)
- [12.6 Simplicidad operativa](#126-simplicidad-operativa)
- [12.7 Estado actual, historia y pendientes](#127-estado-actual-historia-y-pendientes)
- [12.8 Logs y evidencia](#128-logs-y-evidencia)
- [12.9 Automatización proporcionada](#129-automatización-proporcionada)
- [12.10 Estabilidad frente a curiosidad](#1210-estabilidad-frente-a-curiosidad)
- [12.11 Seguridad contextual](#1211-seguridad-contextual)
- [12.12 Coste, tiempo y energía](#1212-coste-tiempo-y-energía)
- [12.13 El papel de la inteligencia artificial](#1213-el-papel-de-la-inteligencia-artificial)
- [12.14 Cómo tomar decisiones](#1214-cómo-tomar-decisiones)
- [12.15 Principios operativos permanentes](#1215-principios-operativos-permanentes)
- [12.16 Cierre](#1216-cierre)

---

## 12.1 Operar no es intervenir constantemente

Un servidor doméstico no debe convertirse en una obligación diaria.

La operación correcta busca:

- estabilidad;
- previsibilidad;
- mantenimiento razonable;
- capacidad de diagnóstico;
- pocas intervenciones;
- buena documentación.

El objetivo no es tocar el sistema continuamente.

Es saber qué hacer cuando realmente necesita atención.

---

## 12.2 Comprender antes de ejecutar

Ningún comando debe ejecutarse únicamente porque parece plausible.

Antes hay que comprender:

- dónde se ejecuta;
- qué modifica;
- qué depende de ello;
- qué salida se espera;
- cómo se valida;
- cómo se revierte.

La secuencia correcta es:

```text
comprender → ejecutar → observar → validar → documentar
```

No:

```text
ejecutar → esperar → improvisar
```

---

## 12.3 Una cosa cada vez

Cuando una operación tiene varios pasos, se ejecutan de uno en uno.

Ventajas:

1. se identifica qué acción produjo cada resultado;
2. se reduce el alcance de errores;
3. se puede detener el proceso;
4. se conserva contexto;
5. se evita mezclar síntomas.

Esta regla es especialmente importante en:

- red;
- almacenamiento;
- VFIO;
- backups;
- restauraciones;
- actualizaciones;
- permisos.

---

## 12.4 No borrar sin autorización

La eliminación es irreversible o costosa.

Por eso:

- no se borran datos por defecto;
- no se eliminan configuraciones sin copia;
- no se destruyen contenedores sin confirmar;
- no se limpian backups sin autorización;
- no se utilizan comandos destructivos por comodidad.

El principio no contradice el valor de eliminar componentes inútiles.

Distingue entre:

- una decisión consciente y autorizada;
- una acción accidental o no comprendida.

---

## 12.5 La reconstrucción como criterio de verdad

Una configuración se considera comprendida cuando puede reconstruirse.

La reconstrucción obliga a conocer:

- dependencias;
- orden;
- credenciales;
- rutas;
- versiones;
- datos;
- validaciones;
- límites.

Por eso el canon no se limita a describir «lo que hay».

Debe explicar cómo volver a crearlo.

---

## 12.6 Simplicidad operativa

La simplicidad se mide por:

- número de capas;
- número de puntos de fallo;
- facilidad de diagnóstico;
- coste de mantenimiento;
- claridad de reconstrucción.

Ejemplos de decisiones simples:

- Tailscale solo en el host;
- dos LXC principales;
- sin puertos abiertos;
- HTTP dentro de la tailnet;
- backup local y remoto separados;
- sin Windows;
- CT102 eliminado.

La simplicidad no significa ausencia de tecnología.

Significa que cada tecnología tiene una función clara.

---

## 12.7 Estado actual, historia y pendientes

Toda documentación operativa debe separar:

### Estado actual

Lo que debe existir.

### Historia

Lo que ocurrió y explica decisiones.

### Pendientes

Lo que no está resuelto o validado.

Esta separación evita:

- ejecutar configuraciones antiguas;
- ocultar incertidumbre;
- creer que una idea ya está implementada;
- perder lecciones.

---

## 12.8 Logs y evidencia

La operación debe dejar evidencia suficiente.

Se valoran:

- logs;
- códigos de salida;
- manifiestos;
- hashes;
- fechas;
- tamaños;
- estados previos y posteriores.

La evidencia evita respuestas ambiguas como:

- «creo que terminó»;
- «parecía funcionar»;
- «no dio error»;
- «seguramente copió todo».

La operación correcta puede demostrarse.

---

## 12.9 Automatización proporcionada

No todo debe automatizarse.

La automatización se justifica cuando:

- reduce trabajo repetitivo;
- disminuye errores;
- produce evidencia;
- es comprensible;
- es fácil de detener;
- tiene una ruta de recuperación.

HDDBU permanece manual porque su función y frecuencia lo permiten.

SwissBackup es automático porque la regularidad diaria aporta valor.

La automatización debe ajustarse a la necesidad, no al entusiasmo.

---

## 12.10 Estabilidad frente a curiosidad

`serviplan` debe permitir experimentar sin poner en riesgo lo estable.

### Estable

- host;
- red;
- CT100;
- CT101;
- backups;
- acceso;
- documentación.

### Experimental

- LXC temporales;
- máquinas virtuales;
- laboratorios;
- servicios candidatos;
- pruebas de seguridad.

La curiosidad es parte del proyecto.

El aislamiento es lo que permite conservarla.

---

## 12.11 Seguridad contextual

La seguridad debe responder a amenazas reales.

Ejemplos:

- no abrir puertos;
- usar Tailscale;
- cifrar SwissBackup;
- usar Strongbox;
- mantener el host limpio;
- limitar servicios;
- revisar CVE relevantes.

No se añaden capas solo por apariencia.

HTTPS interno se descartó porque no resolvía una necesidad concreta dentro de la tailnet.

La seguridad debe ser:

- comprensible;
- proporcionada;
- verificable;
- mantenible.

---

## 12.12 Coste, tiempo y energía

`serviplan` es un proyecto doméstico.

Las decisiones deben considerar:

- presupuesto;
- consumo;
- tiempo;
- fatiga;
- capacidad real de mantenimiento;
- valor de los datos.

No todo merece máxima redundancia.

No todo dato merece backup remoto.

No toda mejora técnica compensa el coste humano de mantenerla.

La infraestructura debe servir a la vida.

No sustituirla.

---

## 12.13 El papel de la inteligencia artificial

La IA puede ayudar a:

- analizar;
- comparar;
- documentar;
- revisar;
- estructurar;
- diagnosticar.

No debe:

- inventar;
- ocultar dudas;
- ejecutar sin contexto;
- sustituir validación;
- convertir hipótesis en hechos.

La responsabilidad final permanece en quien administra el sistema.

La IA es una herramienta de amplificación.

No una fuente automática de verdad.

---

## 12.14 Cómo tomar decisiones

Una decisión técnica debe responder a estas preguntas:

1. ¿Qué problema resuelve?
2. ¿Es un problema real?
3. ¿Qué coste introduce?
4. ¿Qué dependencias crea?
5. ¿Cómo se mantiene?
6. ¿Cómo se revierte?
7. ¿Cómo se reconstruye?
8. ¿Cómo se valida?
9. ¿Merece la pena?

Si no puede responderse, la decisión no está madura.

---

## 12.15 Principios operativos permanentes

1. Comprender antes de ejecutar.
2. Ejecutar de uno en uno.
3. No borrar sin autorización.
4. Hacer copia antes de modificar.
5. Validar después de cada cambio.
6. Registrar evidencia.
7. Separar host, LXC y Docker.
8. Mantener limpio el host.
9. Automatizar solo lo que aporte valor.
10. No ocultar pendientes.
11. Conservar la historia.
12. No reconstruir configuraciones obsoletas.
13. Evitar dependencias innecesarias.
14. Mantener la curiosidad aislada.
15. Tratar la documentación como infraestructura.
16. Priorizar la reconstrucción.
17. Mantener el sistema proporcionado al contexto.
18. No confundir complejidad con calidad.

---

## 12.16 Cierre

La filosofía de operación de `serviplan` puede resumirse así:

- tocar poco;
- comprender mucho;
- registrar lo importante;
- proteger lo valioso;
- experimentar sin comprometer;
- reconstruir sin depender de la memoria.

Un buen sistema doméstico no es el que impresiona más.

Es el que sigue funcionando, puede explicarse y no esclaviza a quien lo mantiene.

---

# Capítulo 13. Estado actual y pendientes

## Índice

- [13.1 Función de este capítulo](#131-función-de-este-capítulo)
- [13.2 Estado general del sistema](#132-estado-general-del-sistema)
- [13.3 Host Proxmox](#133-host-proxmox)
- [13.4 Red y acceso](#134-red-y-acceso)
- [13.5 CT100 · Immich](#135-ct100--immich)
- [13.6 CT101 · Multimedia](#136-ct101--multimedia)
- [13.7 Backups](#137-backups)
- [13.8 Documentación](#138-documentación)
- [13.9 Seguridad](#139-seguridad)
- [13.10 Limitaciones conocidas](#1310-limitaciones-conocidas)
- [13.11 Pendientes técnicos](#1311-pendientes-técnicos)
- [13.12 Pendientes documentales](#1312-pendientes-documentales)
- [13.13 Pendientes no urgentes](#1313-pendientes-no-urgentes)
- [13.14 Qué no debe considerarse pendiente](#1314-qué-no-debe-considerarse-pendiente)
- [13.15 Cierre](#1315-cierre)

---

## 13.1 Función de este capítulo

Este capítulo ofrece una fotografía operativa del sistema en el momento de cerrar esta edición.

No sustituye a los capítulos técnicos.

Su función es responder rápidamente a cuatro preguntas:

1. ¿qué está funcionando?;
2. ¿qué está confirmado?;
3. ¿qué sigue pendiente?;
4. ¿qué limitaciones se aceptan conscientemente?

La información debe actualizarse cuando cambie el sistema.

---

## 13.2 Estado general del sistema

### Estado global

```text
serviplan: operativo
```

La infraestructura principal está compuesta por:

- host Proxmox;
- CT100;
- CT101;
- Tailscale;
- Tailscale Serve;
- SSH;
- HDDBU;
- SwissBackup;
- documentación canónica.

### Resumen

| Elemento | Estado |
|---|---|
| Host | Operativo |
| CT100 | Operativo |
| CT101 | Operativo |
| Immich | Operativo |
| Navidrome | Operativo |
| Jellyfin | Operativo |
| Tailscale | Operativo |
| SSH LAN | Operativo |
| SSH tailnet | Operativo |
| HDDBU | Validado |
| SwissBackup | Validado |
| Restauración integral | Pendiente |

---

## 13.3 Host Proxmox

### Estado confirmado

| Campo | Valor |
|---|---|
| Hostname | `serviplan` |
| IP | `192.168.1.99` |
| Hardware | MSI Modern 15 H C13M |
| RAM | 32 GB |
| SSD | WD_BLACK SN850X 1 TB |
| Proxmox | Operativo |
| Kernel conocido | `7.0.14-3-pve` |
| `pve-manager` conocido | `9.2.4` |

### Repositorios

- enterprise: desactivado;
- no-subscription: activado.

### Almacenamiento conocido

| Recurso | Estado conocido |
|---|---|
| `local` | Aproximadamente 98 GB |
| `local-lvm` | Aproximadamente 794,30 GB |
| CT100 | 60 GB |
| CT101 | 400 GB |

### VFIO

Módulos vigentes:

```text
vfio
vfio_iommu_type1
vfio_pci
```

No debe recuperarse:

```text
vfio_virqfd
```

---

## 13.4 Red y acceso

### LAN

```text
Host:  192.168.1.99
CT100: 192.168.1.101
CT101: 192.168.1.102
Mac:   192.168.1.33
```

### Acceso administrativo

| Alias | Estado |
|---|---|
| `serviplan` | Acceso por Tailscale |
| `serviplan_LAN` | Acceso por LAN |

Strongbox actúa como agente SSH.

### Servicios publicados

```text
http://serviplan:2283
http://serviplan:4533
http://serviplan:8096
```

No existen puertos abiertos en el router para estos servicios.

---

## 13.5 CT100 · Immich

### Configuración

| Campo | Valor |
|---|---|
| ID | 100 |
| IP | `192.168.1.101` |
| Cores | 4 |
| RAM | 8 GB |
| Swap | 2 GB |
| Disco | 60 GB |
| Arranque | Automático |
| Orden | 10 |

### Estado

- LXC operativo;
- Docker operativo;
- Immich operativo;
- acceso mediante Tailscale Serve;
- backup local mediante `vzdump`;
- backup remoto con biblioteca y dump PostgreSQL.

### Pendientes propios

- restauración integral;
- inventario exacto de volúmenes;
- validación periódica del dump;
- revisión de crecimiento.

---

## 13.6 CT101 · Multimedia

### Configuración

| Campo | Valor |
|---|---|
| ID | 101 |
| IP | `192.168.1.102` |
| Cores | 4 |
| RAM | 4 GB |
| Swap | 1 GB |
| Disco | 400 GB |
| Arranque | Automático |
| Orden | 20 |

### Estado

- LXC operativo;
- Docker operativo;
- Navidrome operativo;
- Jellyfin operativo;
- backup local mediante `rsync`;
- publicación mediante Tailscale Serve.

### Pendientes propios

- cierre de la integración completa en SwissBackup;
- validación documentada de GPU;
- procedimiento canónico de full rescan de Navidrome;
- vigilancia de espacio;
- documentación exacta de rutas internas.

---

## 13.7 Backups

### HDDBU

- manual;
- aproximadamente quincenal;
- una copia vigente;
- CT100 mediante `vzdump`;
- CT101 mediante `rsync`;
- host mediante archivo comprimido;
- manifiestos;
- hashes.

### SwissBackup

- remoto;
- cifrado;
- automático;
- timer diario;
- hora consolidada: 02:00.

### Estado conocido de validaciones

Se confirmaron ejecuciones correctas de ambos sistemas durante junio de 2026.

### Limitación principal

No se ha ejecutado una restauración integral de extremo a extremo.

---

## 13.8 Documentación

### Estado

Existe:

- canónico unificado;
- libro técnico y humano;
- capítulos separados;
- procedimientos de reconstrucción;
- historial;
- pendientes;
- decisiones operativas.

### Riesgo

La documentación puede degradarse si el sistema cambia y no se actualiza.

### Regla

Todo cambio relevante debe modificar:

1. el sistema;
2. el canon;
3. el capítulo afectado;
4. la lista de pendientes;
5. el historial si corresponde.

---

## 13.9 Seguridad

### Estado vigente

- sin puertos abiertos;
- acceso remoto mediante Tailscale;
- cifrado de SwissBackup;
- Strongbox para credenciales y SSH;
- host limpio;
- servicios aislados en LXC;
- Windows fuera;
- HTTP limitado a la tailnet.

### Pendiente de revisión

- CVE-2026-31431;
- revisión periódica de kernel y Proxmox;
- política formal de alertas;
- revisión de credenciales y rotación cuando sea necesaria.

---

## 13.10 Limitaciones conocidas

1. un único host físico;
2. un único SSD principal;
3. ausencia de alta disponibilidad;
4. batería sin límite de carga confirmado;
5. router y red como dependencias externas;
6. restauración integral pendiente;
7. cobertura remota de CT101 incompleta;
8. ausencia de monitorización térmica histórica;
9. snapshots no incorporados;
10. algunas rutas internas aún no están consolidadas en el libro.

Estas limitaciones no se ocultan.

Forman parte del estado real.

---

## 13.11 Pendientes técnicos

### Prioridad alta

1. verificar CVE-2026-31431;
2. analizar el bloqueo de desmontaje de `/mnt/backup_serviplan`;
3. revisar el fallo ocasional de `pg_dump`;
4. validar la estabilidad de Immich desde iPhone por Tailscale;
5. confirmar la cobertura remota de CT101.

### Prioridad media

1. monitorizar temperaturas;
2. probar snapshots;
3. documentar GPU;
4. revisar DNS interno;
5. consolidar full rescan de Navidrome;
6. revisar alternativas a LibreWolf cuando corresponda.

### Prioridad baja

1. laboratorio vulnerable aislado;
2. entorno Linux experimental;
3. límite de batería si aparece una solución segura;
4. automatizaciones adicionales no urgentes.

---

## 13.12 Pendientes documentales

1. modelo exacto de CPU;
2. cargador;
3. versión de BIOS;
4. opciones BIOS modificadas;
5. SMART completo del SSD;
6. rutas exactas de CT100;
7. rutas exactas de CT101;
8. inventario de volúmenes Docker;
9. identificadores completos de reservas DHCP;
10. versión exacta de cada imagen Docker;
11. procedimiento probado de restauración integral.

---

## 13.13 Pendientes no urgentes

No deben desplazar trabajo más importante:

- nuevos servicios;
- laboratorios;
- snapshots;
- experimentos con GPU;
- mejoras cosméticas;
- automatizaciones de conveniencia;
- cambio de hardware sin necesidad.

La infraestructura funciona.

No necesita evolucionar constantemente para justificar su existencia.

---

## 13.14 Qué no debe considerarse pendiente

No son fallos pendientes:

- usar HTTP dentro de la tailnet;
- no tener Windows;
- mantener HDDBU manual;
- conservar solo dos LXC principales;
- no abrir puertos;
- haber eliminado CT102;
- no usar Wi-Fi;
- no automatizar todo.

Son decisiones vigentes.

Solo deben reabrirse si cambia el contexto.

---

## 13.15 Cierre

El estado actual de `serviplan` es estable y funcional.

No es perfecto.

No está terminado.

No está completamente probado frente a desastre total.

Pero dispone de:

- arquitectura clara;
- servicios operativos;
- copias locales y remotas;
- acceso redundante;
- documentación;
- pendientes identificados.

La diferencia entre un sistema inmaduro y uno mantenible no es la ausencia de pendientes.

Es saber exactamente cuáles son.

---

# Capítulo 14. Hoja de ruta

## Índice

- [14.1 Función de la hoja de ruta](#141-función-de-la-hoja-de-ruta)
- [14.2 Criterios de prioridad](#142-criterios-de-prioridad)
- [14.3 Prioridad 1 · Libertad y necesidad personal](#143-prioridad-1--libertad-y-necesidad-personal)
- [14.4 Prioridad 2 · Riesgos reales](#144-prioridad-2--riesgos-reales)
- [14.5 Prioridad 3 · Mejoras no urgentes](#145-prioridad-3--mejoras-no-urgentes)
- [14.6 Seguridad](#146-seguridad)
- [14.7 Backups](#147-backups)
- [14.8 Observabilidad](#148-observabilidad)
- [14.9 Red](#149-red)
- [14.10 Virtualización y laboratorio](#1410-virtualización-y-laboratorio)
- [14.11 Documentación](#1411-documentación)
- [14.12 Hardware](#1412-hardware)
- [14.13 Servicios](#1413-servicios)
- [14.14 Proyectos aparcados](#1414-proyectos-aparcados)
- [14.15 Cómo cerrar una línea de trabajo](#1415-cómo-cerrar-una-línea-de-trabajo)
- [14.16 Cierre](#1416-cierre)

---

## 14.1 Función de la hoja de ruta

La hoja de ruta no es una lista de deseos.

Es un mecanismo para impedir que el proyecto se convierta en una sucesión interminable de tareas técnicas.

Debe ayudar a decidir:

- qué merece atención inmediata;
- qué puede esperar;
- qué no debe hacerse;
- qué aporta valor real;
- qué consume energía sin resolver un problema.

---

## 14.2 Criterios de prioridad

Las prioridades permanentes son:

### Prioridad 1

Libre y necesario:

- leer;
- pensar;
- descansar;
- cambiar de tema;
- evitar monotemas;
- conservar energía.

### Prioridad 2

Urgente:

- datos;
- backups;
- seguridad;
- fallos reales;
- pérdida de acceso;
- almacenamiento crítico.

### Prioridad 3

No urgente:

- manuales;
- laboratorios;
- nuevas aplicaciones;
- mejoras;
- experimentos;
- migraciones sin riesgo inmediato.

La infraestructura existe para servir a la vida.

La prioridad 1 no es ocio residual.

Es una parte explícita de la operación sostenible.

---

## 14.3 Prioridad 1 · Libertad y necesidad personal

La primera prioridad es no convertir `serviplan` en un monotema permanente.

Reglas:

1. alternar proyectos;
2. dejar reposar problemas complejos;
3. no trabajar por inercia;
4. detener mejoras no urgentes;
5. recuperar perspectiva;
6. no confundir curiosidad con obligación.

Un proyecto divertido puede dejar de serlo si se transforma en mantenimiento continuo.

---

## 14.4 Prioridad 2 · Riesgos reales

### Tareas activas

1. revisar backups;
2. verificar CVE-2026-31431;
3. investigar `/mnt/backup_serviplan`;
4. revisar `pg_dump`;
5. comprobar espacio de CT101;
6. confirmar acceso remoto a Immich;
7. mantener documentación recuperable.

Estas tareas tienen prioridad porque afectan a:

- datos;
- recuperación;
- seguridad;
- estabilidad.

---

## 14.5 Prioridad 3 · Mejoras no urgentes

1. snapshots;
2. monitorización;
3. laboratorio vulnerable;
4. límite de batería;
5. nuevas máquinas virtuales;
6. nuevos servicios;
7. automatizaciones;
8. experimentos multimedia;
9. perfeccionamiento editorial adicional.

Pueden esperar semanas o meses.

La ausencia de urgencia debe respetarse.

---

## 14.6 Seguridad

### Próximas líneas

1. revisar CVE relevantes;
2. confirmar kernel afectado o no;
3. actualizar cuando corresponda;
4. mantener puertos cerrados;
5. revisar Tailscale;
6. revisar claves y credenciales;
7. mantener Windows fuera;
8. aislar laboratorios.

### No objetivo

Convertir el entorno doméstico en una infraestructura empresarial sobredimensionada.

La seguridad debe ser proporcional.

---

## 14.7 Backups

### Prioridad inmediata

- revisar HDDBU;
- revisar SwissBackup;
- validar dump PostgreSQL;
- revisar CT101 remoto;
- mantener música aparcada dentro del alcance.

### Objetivo futuro

Ejecutar una restauración integral en un entorno adecuado.

### Condición

No comprar hardware únicamente para una prueba salvo que el riesgo o el valor de los datos lo justifiquen.

---

## 14.8 Observabilidad

Posibles mejoras:

- script de temperaturas;
- estado de servicios;
- espacio;
- alertas;
- resumen diario o semanal;
- comprobación de backups.

Criterio:

> Automatizar solo si reduce incertidumbre sin crear otra plataforma que mantener.

---

## 14.9 Red

Pendientes:

1. confirmar resolución estable;
2. revisar DNS interno;
3. mantener reservas DHCP;
4. documentar Tailscale Serve;
5. validar clientes móviles;
6. conservar acceso LAN y tailnet.

CT102 no debe volver por inercia.

Si se necesita DNS interno, debe diseñarse de nuevo y justificar su existencia.

---

## 14.10 Virtualización y laboratorio

### Posibilidades futuras

- laboratorio vulnerable;
- VM Linux;
- distribución orientada a juegos;
- pruebas de seguridad;
- nuevos servicios.

### Reglas

1. aislamiento;
2. sin datos personales;
3. sin acceso innecesario a LAN;
4. sin afectar al host;
5. eliminación sencilla;
6. documentación mínima.

La virtualización existe para permitir experimentar.

No para llenar el servidor.

---

## 14.11 Documentación

### Próximos objetivos

1. integrar esta edición editorial;
2. revisar contradicciones;
3. completar rutas;
4. registrar versiones;
5. consolidar procedimientos;
6. mantener capítulos separados;
7. generar índice maestro;
8. preparar exportación futura a PDF.

La documentación debe evolucionar junto al sistema, no detrás de él.

---

## 14.12 Hardware

### Pendientes

- CPU exacta;
- cargador;
- BIOS;
- SMART;
- batería;
- ventilación;
- posible SAI futuro;
- almacenamiento.

### Regla de compra

No adquirir hardware por entusiasmo.

Comprar cuando:

- exista un cuello de botella;
- falte capacidad;
- aumente el riesgo;
- una prueba tenga valor suficiente;
- el equipo actual deje de resolver.

---

## 14.13 Servicios

Los servicios actuales cubren las necesidades principales:

- Immich;
- Navidrome;
- Jellyfin.

No existe obligación de añadir más.

Un servicio nuevo debe justificar:

1. utilidad;
2. mantenimiento;
3. backup;
4. seguridad;
5. recursos;
6. reconstrucción;
7. permanencia.

---

## 14.14 Proyectos aparcados

Pueden permanecer aparcados:

- manual «Servidor doméstico pragmático»;
- servidor base clonable;
- migraciones no urgentes;
- nuevas automatizaciones;
- laboratorios;
- mejoras de clientes multimedia.

Aparcar no significa abandonar.

Significa asignar una prioridad realista.

---

## 14.15 Cómo cerrar una línea de trabajo

Una tarea se considera cerrada cuando:

1. el problema está resuelto;
2. el estado final está validado;
3. el backup se ha revisado;
4. la documentación se ha actualizado;
5. los restos temporales están identificados;
6. los pendientes derivados están registrados;
7. no queda una dependencia oculta.

Cerrar correctamente evita arrastrar tareas falsas.

---

## 14.16 Cierre

La hoja de ruta no busca mantener ocupado al administrador.

Busca proteger:

- datos;
- tiempo;
- atención;
- energía;
- curiosidad.

`serviplan` ya funciona.

El siguiente paso no siempre es añadir algo.

A veces es no tocar nada.

---

# Capítulo 15. Conclusiones

## Índice

- [15.1 Qué es finalmente `serviplan`](#151-qué-es-finalmente-serviplan)
- [15.2 Lo que se construyó](#152-lo-que-se-construyó)
- [15.3 Lo que se aprendió](#153-lo-que-se-aprendió)
- [15.4 Lo que permanece](#154-lo-que-permanece)
- [15.5 Lo que puede cambiar](#155-lo-que-puede-cambiar)
- [15.6 El valor de la documentación](#156-el-valor-de-la-documentación)
- [15.7 La soberanía posible](#157-la-soberanía-posible)
- [15.8 El equilibrio entre técnica y vida](#158-el-equilibrio-entre-técnica-y-vida)
- [15.9 El lector futuro](#159-el-lector-futuro)
- [15.10 Cierre final](#1510-cierre-final)

---

## 15.1 Qué es finalmente `serviplan`

`serviplan` es un servidor doméstico.

También es:

- una infraestructura;
- un laboratorio;
- una biblioteca personal;
- una herramienta de soberanía;
- un proyecto de aprendizaje;
- una colección de decisiones;
- un sistema que puede reconstruirse.

No es una plataforma empresarial.

No pretende serlo.

Su valor no depende de parecer más complejo de lo que necesita.

---

## 15.2 Lo que se construyó

La arquitectura final de esta etapa puede resumirse así:

```text
MSI Modern 15 H C13M
└── Proxmox VE
    ├── CT100 · Immich
    └── CT101 · Multimedia
        ├── Navidrome
        └── Jellyfin
```

Alrededor existen:

- Tailscale;
- Tailscale Serve;
- SSH;
- Strongbox;
- HDDBU;
- SwissBackup;
- documentación;
- procedimientos;
- inventarios;
- historial.

La parte visible son los servicios.

La infraestructura real incluye todo lo necesario para acceder, proteger y reconstruir.

---

## 15.3 Lo que se aprendió

El proyecto confirmó varias ideas.

### Linux seguía siendo suficiente

La migración a Proxmox no corrigió un límite de Linux.

Cambió la forma de organizarlo.

### La virtualización aporta orden

No por multiplicar máquinas, sino por separar funciones.

### Los backups necesitan recuperación

Copiar no basta.

### La documentación es infraestructura

Sin ella, el sistema depende de la memoria.

### Eliminar puede ser una mejora

CT102 desapareció y la arquitectura mejoró.

### La seguridad debe ser contextual

Más capas no significan automáticamente más seguridad.

### La curiosidad necesita límites

Experimentar es valioso cuando no compromete lo estable.

---

## 15.4 Lo que permanece

Aunque cambien las herramientas, deben permanecer:

1. control sobre los datos;
2. capacidad de salida;
3. reconstrucción;
4. simplicidad;
5. documentación;
6. separación entre estable y experimental;
7. honestidad sobre pendientes;
8. mantenimiento proporcional;
9. respeto por el tiempo;
10. diversión.

Estos principios son más importantes que cualquier versión concreta.

---

## 15.5 Lo que puede cambiar

Pueden cambiar:

- hardware;
- Proxmox;
- kernel;
- Docker;
- Immich;
- Jellyfin;
- Navidrome;
- Tailscale;
- proveedor de backup;
- estructura de contenedores;
- clientes;
- scripts.

El libro no debe convertir el estado actual en dogma.

Debe conservar el razonamiento que permite cambiarlo sin perder coherencia.

---

## 15.6 El valor de la documentación

El sistema puede fallar.

El SSD puede morir.

El MSI puede desaparecer.

Un proveedor puede cerrar.

Una aplicación puede quedar abandonada.

La documentación permite distinguir entre:

- perder una máquina;
- perder el proyecto.

Mientras existan:

- credenciales;
- datos;
- copias;
- procedimientos;
- conocimiento;

la infraestructura puede reconstruirse.

Ese es el sentido último del libro.

---

## 15.7 La soberanía posible

La soberanía absoluta no existe.

`serviplan` depende de:

- hardware;
- electricidad;
- red;
- software libre;
- proveedores;
- comunidad;
- tiempo.

Pero existe una soberanía razonable:

- elegir;
- migrar;
- conservar;
- comprender;
- rechazar;
- reconstruir.

No se trata de vivir sin dependencias.

Se trata de que las dependencias no eliminen la libertad.

---

## 15.8 El equilibrio entre técnica y vida

Un servidor doméstico puede convertirse fácilmente en otro trabajo.

Este proyecto intenta evitarlo.

Debe poder:

- funcionar sin atención constante;
- detenerse cuando no sea prioritario;
- esperar;
- convivir con lectura, descanso y otros intereses;
- seguir siendo divertido.

La infraestructura debe aportar autonomía.

No consumirla.

---

## 15.9 El lector futuro

Dentro de veinticinco años, quizá el hardware resulte arcaico.

Las aplicaciones actuales pueden haber desaparecido.

Los formatos pueden haber cambiado.

Pero el lector futuro debería poder comprender:

- qué se intentó proteger;
- por qué se eligió cada solución;
- cómo estaba organizado;
- qué errores se cometieron;
- cómo continuar.

Si ese lector puede reconstruir el sistema o trasladar sus datos a otra arquitectura, el libro habrá cumplido su función.

---

## 15.10 Cierre final

`serviplan` empezó mucho antes de existir.

Empezó con BASIC.

Con MS-DOS.

Con servidores anteriores.

Con Linux.

Con la necesidad de comprender.

Con la incomodidad de depender demasiado.

Con la curiosidad.

La tecnología proporcionó las herramientas.

La comunidad proporcionó los cimientos.

La inteligencia artificial redujo fricción.

Pero el proyecto existe porque alguien decidió que sus datos, su aprendizaje y su libertad merecían una infraestructura propia.

La mejor definición final sigue siendo sencilla:

> Construir, comprender, documentar, conservar el control y seguir aprendiendo.

Todo lo demás podrá cambiar.

---
