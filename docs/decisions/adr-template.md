---
# These are optional metadata elements. Feel free to remove any of them.
status: "{proposed | rejected | accepted | deprecated | … | superseded by ADR-0123"
date: {YYYY-MM-DD when the decision was last updated}
decision-makers: {list everyone involved in the decision}
consulted: {list everyone whose opinions are sought (typically subject-matter experts); and with whom there is a two-way communication}
informed: {list everyone who is kept up-to-date on progress; and with whom there is a one-way communication}
---

#  ADR 0001: Estilo arquitectónico para la lógica de negocio

## Context and Problem Statement

Debemos migrar un monolito de tres capas a una solución escalable y mantenible. Las capas de presentación, lógica de negocio y acceso a datos están fuertemente acopladas, lo que dificulta el desarrollo, las pruebas y el escalado independiente. Necesitamos aislar la lógica de dominio de la UI, el transporte y la persistencia.  


<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

Adoptar microservicios hexagonales  


## Considered Options
- Monolito de tres capas  cambio mínimo, mantiene la pila actual.  
- Microservicios en capas  rompe en servicios separados pero conserva la estructura por capas.  
- Microservicios hexagonales – cada servicio encapsula dominio, puertos y adaptadores para UI, persistencia y mensajería.  



## Decision Outcome

Chosen option:: Microservicios hexagonales porque aseguran separación estricta entre el dominio y los mecanismos externos, mejorando la testabilidad y la independencia de despliegue.  

<!-- This is an optional element. Feel free to remove. -->
### Consequences

- Límites claros por capacidad de negocio, haciendo explícitas las reglas de dominio.  
- Facilita el cambio de adaptadores (por ejemplo, pasar de Postgres a otro) sin tocar la lógica central.  
- Aumenta la complejidad: cada servicio requiere su propio montaje de puertos y adaptadores.  
- Requiere inversión en un framework o plantillas para estandarizar los puertos y adaptadores. 
<!-- numbers of consequences can vary -->

<!-- This is an optional element. Feel free to remove. -->
### Confirmation

{Describe how the implementation of/compliance with the ADR can/will be confirmed. Are the design that was decided for and its implementation in line with the decision made? E.g., a design/code review or a test with a library such as ArchUnit can help validate this. Not that although we classify this element as optional, it is included in many ADRs.}

<!-- This is an optional element. Feel free to remove. -->
## Pros and Cons of the Options

### {title of option 1}

<!-- This is an optional element. Feel free to remove. -->
{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
<!-- use "neutral" if the given argument weights neither for good nor bad -->
* Neutral, because {argument c}
* Bad, because {argument d}
* … <!-- numbers of pros and cons can vary -->

### {title of other option}

{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
* Neutral, because {argument c}
* Bad, because {argument d}
* …

<!-- This is an optional element. Feel free to remove. -->
## More Information

{You might want to provide additional evidence/confidence for the decision outcome here and/or document the team agreement on the decision and/or define when/how this decision the decision should be realized and if/when it should be re-visited. Links to other decisions and resources might appear here as well.}
