El siguiente modelo es el propuesto para el trabajo de QA. Mientras se tiene una naturaleza linear, cualquier fase puede ser trabajada individualmente si se necesita - mientras que todas las fases eventualmente son revisadas.


## Fase 1: Revision basica

- Todo el codigo debe adherirse a nuestras guias de contribucion
- Anotar todas las areas que necesitan ser mejoradas (mentalmente o en el codigo)
- Crear TODOs y asignarse de ser posible

## Fase 2: Revision de espesificaciones /  Implementacion / Documentacion de codigo

- Completa las revisiones de espesificaiones por modulos; ejemplo: Streaming, I2PControl, etc.
  - El codigo debe estar en-linea con las partes escenciales de las espesificaciones que se mantendran iguales (o en mejores) niveles de anonimato que provee java I2P
  - Refactorizar/implementar/parchear donde/cuando se necesite.
- Asegurarse implementacion acorde con C++11/14
  - Fase 2 de revision si se necesita
- Resolver todo lo relacionado a los TODOs
- Documentar el codigo tanto como sea posible con comentarios en-linea y Doxygens
  - El codigo debe ser entendible desde programadores novatos a experimentados
  - El codigo debe guiar al lector a un mejor entendimiento de I2P
    - I2P es un codigo muy largo y complejo, asi que el nuestro debe ser un reemplazo de de documentacion y no simplemente un suplemento (esto puede ser un objetivo tedioso pero muy beneficioso en terminos de mantenimiento y vida del software)

## Fase 3: Revision criptografica / auditoria de seguridad

- Asegurarse que la criptografia este al dia y correctamente implementada
- Establecer cada vector para explotaciones conocidas
  - Mantener esos vectores en mente cuando se escriban pruebas
- Romper Kovri en cada forma posible
  - Arreglar lo que rompes
- Sempre usa librerias de confianza, y bien escritas cuando sea posible
  - Evita codigo hecho-en-casa, ad-hoc, *Yo se mas que la comunidad, por eso mi codigo es mejor*
- Busca una segunda, tercera y mas opiniones, antes de proceder a la siguiente fase

## Fase 4: Arreglar bugs / Pruebas / Profiling

- Resolver los bugs/issues de prioridad
- Escribir pruebas de unit-test para cada modulo
  - Correr pruebas, y correrlas de nuevo
  - Revisa los resultados por complet. Parchea si se necesita, refactoriza si es necesario
- Asegurate que la automatizacion este corriendo a intervalos regulares
  - Parchea si es necesario, refactoriza si es necesario

## Fase 5: Conferir

- Conferir con colegas y la comunidad
  - Conferir debe ser publicamente via tickes, reuniones, y/o IRC
- Aceptar toda retroalimentacion y, en respuesta, producir resultados tangibles
- Si se satisface, proceder con la siguiente fase, si no repetir esta fase, (o comenzar de una fase previa)

- Confer with colleagues and the community
  - Conferring should be done publicly via ticket, meetings, and/or IRC
- Accept all feedback and, in response, produce tangible results
- If satisfied, proceed with next Fase, else repeat this Fase (or start from a previous Fase)

## Fase 6: Repetir todo desde el inicio