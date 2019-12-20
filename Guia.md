# Guía de publicación de datos geográficos enlazados dentro del marco de la IDEE <!-- omit in toc -->

Autores: David Portolés Rodríguez (Coordinador), F. J. López Pellicer, Oscar Corcho, Luis M. Vilches-Blázquez

- [Introducción y contexto](#introducción-y-contexto)
- [Proceso de publicación de datos geográficos enlazados](#proceso-de-publicación-de-datos-geográficos-enlazados)
  - [Especificación](#especificación)
  - [Modelado](#modelado)
  - [Generación](#generación)
  - [Publicación](#publicación)
- [Guía de alineamiento entre conjuntos de datos espaciales para su publicación como Datos Geográficos Enlazados](#guía-de-alineamiento-entre-conjuntos-de-datos-espaciales-para-su-publicación-como-datos-geográficos-enlazados)
  - [Selección del Conjunto de Datos Espaciales (CDE) a alinear con otro CDE con un modelo INSPIRE bien documentado](#selección-del-conjunto-de-datos-espaciales-cde-a-alinear-con-otro-cde-con-un-modelo-inspire-bien-documentado)
  - [Alineamiento entre la ontología y el modelo INSPIRE del CDE](#alineamiento-entre-la-ontología-y-el-modelo-inspire-del-cde)
    - [Emparejamientos entre clases (CL)](#emparejamientos-entre-clases-cl)
    - [Emparejamientos entre atributos (AT)](#emparejamientos-entre-atributos-at)
    - [Emparejamientos entre listas controladas de valores (codelist) completas (ENUM)](#emparejamientos-entre-listas-controladas-de-valores-codelist-completas-enum)
    - [Emparejamientos entre algunos valores de listas controladas (codelist) (VAL)](#emparejamientos-entre-algunos-valores-de-listas-controladas-codelist-val)
    - [Emparejamientos entre clases y atributos con valor de lista controlada (CL-AT)](#emparejamientos-entre-clases-y-atributos-con-valor-de-lista-controlada-cl-at)
    - [Emparejamientos entre instancias (CL)](#emparejamientos-entre-instancias-cl)
  - [Representar el CDE en RDF utilizando el alineamiento anterior](#representar-el-cde-en-rdf-utilizando-el-alineamiento-anterior)
    - [Obtención del RDF mediante diferentes técnicas o herramientas](#obtención-del-rdf-mediante-diferentes-técnicas-o-herramientas)
    - [Serialización del RDF](#serialización-del-rdf)
  - [Recomendaciones y buenas prácticas](#recomendaciones-y-buenas-prácticas)
- [Bibliografía](#bibliografía)

## Introducción y contexto

En 2019 se ha creado un Subgrupo de Trabajo del Grupo de Trabajo de la Infraestructura de Datos Espaciales de España (GT IDEE) dedicado a datos geográficos enlazados (DGE), cuya misión es impulsar el desarrollo de los datos enlazados de carácter geográfico en España dentro del marco de la IDEE.

Entre las acciones previstas en dicho Subgrupo de Trabajo está la elaboración de una guía de publicación de conjuntos de datos espaciales como DGE.
El presente documento es el resultado que se corresponde con la citada acción.

En la guía se han tenido en consideración los distintos perfiles que
pueden tener relación con los DGE, a saber:

- Publicador: pone a disposición de terceros los datos de su ámbit competencial o propiedad.
- Reutilizador: únicamente realiza consultas sobre los datos.
- Integrador: usa los datos en combinación con otros datos.

Las dos principales tareas de las acciones realizadas en el contexto de la creación de esta guía se basan en una identificación del proceso global de generación y publicación de datos geográficos enlazados, basados en las experiencias previas de los miembros del grupo de trabajo en este contexto (descrito en la [sección 2](#proceso-de-publicación-de-datos-geográficos-enlazados)), así como en el concepto de mapeo o alineamiento entre distintos modelos de datos para poder establecer relaciones entre ellos (descrito en la [sección 3](#guía-de-alineamiento-entre-conjuntos-de-datos-espaciales-para-su-publicación-como-datos-geográficos-enlazados)).

## Proceso de publicación de datos geográficos enlazados

La generación de datos geográficos enlazados es un proceso que involucra varias actividades y decisiones para obtener un conjunto de datos de alta calidad.
En el contexto de la generación de este tipo de datos en España, ya se han realizado algunas experiencias sostenibles de publicación de datos, que se han descrito en las siguientes publicaciones, entre otras:

- \[[1](#1)\] P. Espinoza-Arias, M. García-Delgado, O. Corcho, P. Vivas-White, y H. Potti-Manjavacas, «A sustainable process and toolbox for geographical linked data generation and publication: a case study with BTN100», *Open Geospatial Data, Softw. Stand.*, vol. 4, n. 1, p. 2, 2019. Disponible como *open access* en: <https://doi.org/10.1186/s40965-019-0060-4>
- \[[2](#2)\] L. M. Vilches-Blázquez, B. Villazón-Terrazas, O. Corcho, y A. Gómez-Pérez, «Integrating geographical information in the Linked Digital Earth», *Int. J. Digit. Earth*, vol. 7, n. 7, pp. 554-575, ago. 2014. Disponible en: <https://doi.org/10.1080/17538947.2013.783127>.
- \[[3](#3)\] A. de León, V. Saquicela, L. M. Vilches, B. Villazón-Terrazas, F. Priyatna, y O. Corcho, «Geographical linked data: a Spanish use case», en *Proceedings of the 6th International Conference on Semantic Systems - I-SEMANTICS ’10*, 2010. Disponible como *open access* en: <http://oa.upm.es/6167/>.
- \[[4](#4)\] L. Vilches-Blázquez, B. Villazón-Terrazas, O. Corcho, y A. Gómez-Pérez, «GeoLinked Data. An application case/Un caso de aplicación», *I Jornadas Ibéricas Infraestructuras Datos Espac. (JIIDE 2010)*, pp. 1-9, 2010. Disponible como *open access* en: <http://oa.upm.es/6166/>.

Asimismo, se debe hacer mención a la nota sobre buenas prácticas en la publicación de datos espaciales en la Web del grupo de trabajo “Spatial Data on the Web”, y que está publicada en <https://www.w3.org/TR/sdw-bp/>.

De manera general, en estos trabajos se siguen las pautas metodológicas para publicar datos enlazados gubernamentales \[[5](#5)\], que ya habían sido propuestas en el pasado, que dieron lugar a las buenas prácticas en publicación de datos enlazados también publicadas como nota del grupo de trabajo del W3C sobre [Government Linked Data](https://www.w3.org/TR/ld-bp/).

Estas pautas cubren ampliamente los pasos y detalles necesarios para las actividades involucradas: especificación, modelado, generación, publicación y explotación.
Cada actividad implica una o más tareas y algunas técnicas para llevarlas a cabo.
A continuación, se resumen dichas tareas (para más información y detalle se pueden consultar las referencias anteriores), junto con algunos ejemplos procedentes de la transformación de la fuente de datos BTN100\[1\].

### Especificación

La primera tarea de esta actividad se centra en la identificación de las fuentes de datos, formatos, información dentro de los conjuntos de datos y requisitos generales para el conjunto de datos vinculado resultante.
En este ejemplo, como se mencionaba con anterioridad, se utiliza la BTN100 como fuente de datos. Esta fuente contiene información geográfica sobre datos topográficos y temáticos y fue diseñada siguiendo las directivas INSPIRE.
BTN100 agrupa sus datos en los siguientes temas: unidades administrativas, zonas protegidas, edificios y entidades de población, redes de transporte, energía y conducción, vértices geodésicos, altimetría e hidrografía.

También una tarea de diseño de URI está involucrada en esta actividad.
En nuestro caso, definimos los identificadores de recursos uniforme o URI de manera persistente de acuerdo con las mejores prácticas de datos espaciales en la Web descritas en “Spatial Data on the Web” y la Norma Técnica de Interoperabilidad para la reutilización de información \[[6](#6)\].
La URI base para todos los elementos adopta la siguiente estructura <https://datos.ign.es>.
Asimismo, se sigue una estrategia *UpperCamelCase* para nombrar clases y una estrategia de *lowerCamelCase* para propiedades y recursos de objetos y datos.
En la Tabla 1 presentamos nuestro diseño de patrón de URI.

*Tabla 1. Definición de URI.*

| Elemento         | URI
| ---------------- | ---
| Ontología        | `https://datos.ign.es/def/{nombre_ontología}`
| Clase            | `https://datos.ign.es/def/{nombre_ontología}\#{Clase}`
| Propiedad objeto | `https://datos.ign.es/def/{nombre_ontología}\#{propiedadObjeto}`
| Propiedad dato   | `https://datos.ign.es/def/{nombre_ontología}\#{propiedadDato}`
| SKOS             | `https://datos.ign.es/kos/{tema}/{nombre_SKOS}`
| Recurso          | `https://datos.ign.es/recurso/{conjunto_dato_enlazado}/{tipo_recurso}/{identificador_recurso}`

La tarea final de esta actividad es la definición de la licencia del conjunto de datos vinculado.
Decidimos reutilizar la licencia IGN para el BTN100 ya que es una licencia *Creative Common Attribution 4.0 International* (CC BY 4.0).

### Modelado

Para representar todos los temas del conjunto de datos, generamos una ontología, que reemplaza a la anterior ontología utilizada para <http://geo.linkeddata.es> (que ya no está en producción, al haberse sustituido por los datos enlazados que se describen aquí).
El desarrollo de la ontología se realizó siguiendo la metodología [Linked Open Terms](http://lot.linkeddata.es/).
En esta actividad fue importante la reutilización de ontologías, para lo que realizamos un análisis de los vocabularios espaciales comunes recomendados por *Spatial Data on the Web Best Practices* del W3C.

Decidimos reutilizar el vocabulario [GeoSPARQL](<https://www.opengeospatial.org/standards/geosparql>) para representar datos geoespaciales, ya que permite utilizar funciones especializadas para geometrías.
El vocabulario GeoSPARQL no permite representar elementos tales como identificadores de recursos, etiquetas para objetos geográficos, altitud, etc.
Para abordar estas deficiencias, desarrollamos la ontología *btn100*.
Este modelo representa todos los objetos geográficos de nuestro conjunto de datos.
La ontología *btn100* tiene enlaces a los tesauros SKOS (*Simple Knowledge Organization System*) que se desarrollaron para representar algunas categorías de elementos en nuestro conjunto de datos; por ejemplo, tipo de acceso a la autopista, tipo de carretera, etc.
Estos tesauros se vincularán en el futuro a los que se mantienen en el registro INSPIRE.
Todos los archivos generados durante el desarrollo de la ontología, incluidos los requisitos, ontologías, tesauros y documentación están disponibles en un repositorio de Github, concretamente en <https://github.com/oeg-upm/ontology-BTN100>.

### Generación

Al principio, extraímos todos los archivos del origen de datos BTN100 y los descomprimimos para obtener los archivos de forma para cada tema.
Tras ello, realizamos algunas transformaciones de datos y obtuvimos como resultado un archivo RDF.
Finalmente, vinculamos el conjunto de datos resultante a otros recursos y obtuvimos el conjunto de datos vinculado.
Como se presentó anteriormente, almacenamos todos los archivos involucrados en este proceso en un repositorio de Github disponible en <https://github.com/oeg-upm/btn100>.

Para hacer frente a las tareas de transformación utilizamos la herramienta [GeoKettle](https://live.osgeo.org/archive/10.5/es/overview/geokettle_overview.html).
Con esta herramienta creamos un archivo de transformación para cada archivo asociado a los datos originales y configuramos un flujo de trabajo para realizar las actividades que se describen a continuación.
Primero, limpiamos los datos, por ejemplo, corrección de tipos de datos malformados / incompatibles. Luego, asignamos los datos a sus equivalentes correspondientes en los conceptos SKOS.
Después, convertimos los sistemas de referencia ETRS89 y REGCAN95 a WGS84 para representar datos en el estándar GeoSPARQL.
Por último, transformamos los datos, a través del complemento [TripleGeo](https://github.com/oeg-upm/geo.linkeddata.es-TripleGeoKettle), en tripletas RDF de acuerdo con el modelo definido en la ontología *btn100*.

TripleGeo convierte las características geoespaciales en una serialización RDF, en nuestro caso en archivos Turtle.
De esta manera, utilizamos TripleGeo como complemento de Geokettle para proporcionar una generación precisa de la información semántica; por ejemplo, una definición correcta de URI.
Más detalles sobre los parámetros de configuración de TripleGeo están disponibles en su [wiki](https://github.com/oeg-upm/geo.linkeddata.es-TripleGeoKettle/wiki).

Finalmente, para la tarea de vinculación utilizamos la relación *owl:sameAs* para alinear nuestros recursos con DBpedia y otros recursos del portal de datos abiertos del gobierno español.
Todos los archivos generados durante la tarea de vinculación también están disponibles en el repositorio de GitHub.

### Publicación

Este paso tiene como objetivo proporcionar acceso al conjunto de datos resultante.
Almacenamos los archivos RDF en un *triple store* Virtuoso, que proporciona un punto de acceso SPARQL, disponible en <https://datos.ign.es/sparql>.
Algunos casos de uso con sus consultas SPARQL están disponibles en <https://datos.ign.es/casos-de-uso.html>.

Los metadatos para nuestro conjunto de datos se basan en el archivo de metadatos BTN100 del portal de datos abiertos del gobierno español.
Este archivo fue generado de acuerdo con el vocabulario DCAT.

## Guía de alineamiento entre conjuntos de datos espaciales para su publicación como Datos Geográficos Enlazados

### Selección del Conjunto de Datos Espaciales (CDE) a alinear con otro CDE con un modelo INSPIRE bien documentado

El primer paso a realizar es la selección del Conjunto de Datos Espaciales (CDE) que se desea enlazar con otro CDE.
En ambos casos es recomendable que ambos CDE consten de un modelo bien documentado para poder establecer las relaciones de forma adecuada.

La documentación del modelo de datos puede ser variada, si bien lo preferible es disponer de documentación formal, tales como: vocabularios, ontologías, listas controladas, diagramas de clases, etc.

En el caso de la presente guía se va a mostrar algunas relaciones de ejemplo entre el CDE de la BTN100 con el tema Transporte (TN) de INSPIRE con el propósito de mostrar ejemplos de aplicación práctica, si bien se podría realizar con cualesquiera otros CDE de interés.

De partida se ha de disponer:

- Ontología del CDE. En el caso de la BTN100 se dispone de una ontología publicada en <https://datos.ign.es/def/btn100>, como ya se describió en la sección anterior, que incluye toda la documentación necesaria para poder realizar los pasos siguientes.
- Conceptos registrados en el Registro de INSPIRE. En el caso de TN, la documentación sobre el tema TN de INSPIRE se encuentra disponible, de forma general, en <https://inspire.ec.europa.eu/id/document/tg/tn>. De forma más específica, también ha sido de interés el consultar los [modelos UML de INSPIRE](https://inspire.ec.europa.eu/data-model/approved/r4618-ir/html/index.htm?goto=2:1:9:3:7453).

Se dispone también de vocabularios en RDF generados en el proyecto ARE3NA, si bien apenas ha resultado de interés su consulta ya que se quedan en un nivel muy general - *Common Transport Elements* - y sirven sólo como recopilación de URI ya disponibles en INSPIRE.
El vocabulario ARE3NA asociado al tema TN se encuentra disponible en
<https://github.com/inspire-eu-rdf/inspire-rdf-vocabularies/blob/master/tn/tn.ttl>.
De forma adicional, el vocabulario anterior se considera como un borrador y, en el momento de redacción de la presente guía, no se ha actualizado desde Julio de 2017.
El principal aporte de estos RDF de ARE3NA ha sido el proporcionar el conocimiento de la ontología de TN, ya que no se ha localizado dicha referencia en otro lugar.

### Alineamiento entre la ontología y el modelo INSPIRE del CDE

En esta fase se deben establecer los alineamientos entre los modelos seleccionados en el apartado anterior.
Para ello se buscarán fenómenos, clases y propiedades que puedan tener alguna relación semántica y emparejarlos.

Teniendo en cuenta que el W3C no ha definido aún un conjunto de buenas prácticas y que se han identificado en la literatura algunos problemas con el uso de las propiedades *owl:sameAs*, *owl:equivalentClass* o *owl:equivalentProperty* \[[7](#7)\], se considera que una buena aproximación es utilizar un vocabulario como SKOS, como el vocabulario con el que se anotan los alineamientos entre URI que se refieren a las mismas entidades o conceptos, pero en diferentes contextos.

Si se desea indicar que se tiene un alto grado de confianza de que dos conceptos se pueden usar de forma intercambiable, se deberían relacionar ambos mediante la propiedad *skos:exactMatch*.
Esta propiedad es transitiva y simétrica por lo que si:

```turtle
<A> skos:exactMatch <B> .  
<B> skos:exactMatch <C> .
```

Entonces se infiere que:  

```turtle
<A> skos:exactMatch <C> .  
<C> skos:exactMatch <A> .  
<B> skos:exactMatch <A> .  
<C> skos:exactMatch <B> .
```

Si se desea indicar que dos conceptos son suficientemente similares y que pueden ser utilizados de forma intercambiable únicamente en algunas aplicaciones, entonces se deberían relacionar ambos mediante la propiedad *skos:closeMatch*, que es simétrica pero no transitiva.

Las propiedades *skos:broadMatch* y *skos:narrowMatch* se utilizan para establecer un alineamiento jerárquico entre dos conceptos, mientras que la propiedad *skos:relatedMatch* se utiliza para establecer un alineamiento asociativo entre dos conceptos.

En el caso del ejemplo entre BTN100 y el tema TN de INSPIRE se han localizado al menos los emparejamientos que se indican a continuación.
Es importante destacar que esta lista no es exhaustiva, sino que lo que busca es mostrar los casos más representativos, así como diferentes posibles tipologías de emparejamientos.
Asimismo, en lo posible se refleja la URI de cada elemento (si existe).

#### Emparejamientos entre clases (CL)

Ejemplos de emparejamiento entre clases de BTN100 y de TN de INSPIRE pueden ser los siguientes:

Ejemplo CL.1: Zonas Aeroportuarias y Área de aeródromo

**BTN100 Zona Aeroportuaria.**

- URI: <https://datos.ign.es/def/btn100#ZonaAeroportuaria>.
- Descripción: Estación o terminal situada en un terreno llano que cuenta con pistas, instalaciones y servicios destinados al tráfico de aviones.

**INSPIRE FC Área de aeródromo.**

- URI: <https://inspire.ec.europa.eu/featureconcept/AerodromeArea>
- Descripción: Zona definida, sobre tierra o agua (incluidos eventuales edificios, instalaciones y equipos), cuyo propósito es ser utilizada total o parcialmente para la llegada, salida y movimiento en superficie de aeronaves y/o helicópteros.

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100: <https://datos.ign.es/def/btn100#> .
@prefix inspire: <https://inspire.ec.europa.eu/featureconcept/> .
btn100:ZonaAeroportuaria skos:exactMatch inspire:AerodromeArea .
```

Ejemplo CL.2:

**BTN100 Instalación Ferroviaria.**

- URI: <https://datos.ign.es/def/btn100#InstalacionFerroviaria>
- Descripción: Instalaciones necesarias para el funcionamiento del ferrocarril en todas sus facetas y que según el nivel de prestaciones va a recibir una u otra denominación.

**INSPIRE FC Nodo ferroviario.**

- URI: <https://inspire.ec.europa.eu/featureconcept/RailwayNode>.
- Descripción: Objeto espacial puntual que representa un punto significativo a lo largo de la red ferroviaria o define una intersección de vías férreas, utilizado para describir su conectividad.

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100: <https://datos.ign.es/def/btn100#> .
@prefix inspire: <https://inspire.ec.europa.eu/featureconcept/> .

btn100:InstalacionFerroviaria skos:closeMatch inspire:RailwayNode .
```

Ejemplo CL.3:

**BTN100 Estación de ferrocarril.**

- URI: <https://datos.ign.es/def/btn100#EstacionDeFerrocarril>.
- Descripción: Lugar conectado a una vía de FFCC, donde alguno de los trenes que circula por dicha vía tiene establecida una parada, ya sea para descarga de mercancías o de viajeros.

**INSPIRE FC Nodo de estación ferroviaria.**

- URI: <https://inspire.ec.europa.eu/featureconcept/RailwayStationNode>.
- Descripción: A railway node which represents the location of a railway station along the railway network.

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100: <https://datos.ign.es/def/btn100#> .
@prefix inspire: <https://inspire.ec.europa.eu/featureconcept/> .

btn100:EstacionDeFerrocarril skos:exactMatch inspire:RailwayStationNode .
```

En ocasiones es posible emparejar una clase de un modelo con la
agregación de varias en el otro, como por ejemplo:

Ejemplo CL.4:

**BTN100 Zona Aeroportuaria.**

- URI: <https://datos.ign.es/def/btn100#PistaDeAterrizaje>
- Descripción: Espacio dentro de las instalaciones de un aeropuerto, donde circulan los aviones y otros aparatos de navegación aérea, y desde donde se realiza el despegue/aterrizaje.

**INSPIRE FC Área de pista + Área de calle de rodaje.**

- URI: <https://inspire.ec.europa.eu/featureconcept/RunwayArea> + <<https://inspire.ec.europa.eu/featureconcept/TaxiwayArea>
- Descripción: Área rectangular definida en un aeródromo/helipuerto terrestre preparada para el aterrizaje y el despegue de aeronaves + Vía definida en un aeródromo/helipuerto, establecida para el rodaje de aeronaves/helicópteros y destinada a proporcionar enlace entre dos partes del aeródromo.

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100: <https://datos.ign.es/def/btn100#> .
@prefix inspire: <https://inspire.ec.europa.eu/featureconcept/> .

btn100:PistaDeAterrizaje skos:broadMatch inspire:RunwayArea , inspire:TaxiwayArea .
```

#### Emparejamientos entre atributos (AT)

Ejemplos de emparejamiento entre atributos de BTN100 y de TN de INSPIRE pueden ser los siguientes:

Ejemplo AT.1:

**BTN100 Situación de vía.**

- URI: <https://datos.ign.es/def/btn100#situacionDeVia>
- Descripción: Disposición del tramo de vía sobre la superficie.

**INSPIRE Atributo Posición vertical.**

- URI: <http://inspire.ec.europa.eu/ont/tn#VerticalPosition.verticalPosition>
- Descripción: Relative vertical position of the transport element.

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100: <https://datos.ign.es/def/btn100#> .
@prefix tn: <http://inspire.ec.europa.eu/ont/tn#> .

btn100:situacionDeVia skos:exactMatch tn:VerticalPosition.verticalPosition.
```

Ejemplo AT.2:

**BTN100 Código IATA.**

- URI: <https://datos.ign.es/def/btn100#codigoIATA>
- Descripción: N/A

**INSPIRE Atributo designatorIATA.**

- URI:<http://inspire.ec.europa.eu/ont/tn#AerodromeNode.designatorIATA>
- Descripción: The three letter IATA designator of the aerodrome (airport/heliport).

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100: <https://datos.ign.es/def/btn100#> .
@prefix tn: <http://inspire.ec.europa.eu/ont/tn#> .

btn100:codigoIATA skos:exactMatch tn:AerodromeNode.designatorIATA .
```

Ejemplo AT.3:

**BTN100 Código ICAO.**

- URI <https://datos.ign.es/def/btn100#codigoICAO>
- Descripción: N/A

**INSPIRE Atributo locationIndicatorICAO.**

- URI: <http://inspire.ec.europa.eu/ont/tn#AerodromeNode.locationIndicatorICAO>
- Descripción: The four letter ICAO location indicator of the aerodrome (airport/heliport), as listed in ICAO DOC 7910.

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100: <https://datos.ign.es/def/btn100#> .
@prefix tn: <http://inspire.ec.europa.eu/ont/tn#> .

btn100:codigoICAO skos:exactMatch tn:AerodromeNode.locationIndicatorICAO .
```

Ejemplo AT.4:

**BTN100 Código de Vía.**

- URI: <https://datos.ign.es/def/btn100#codigoDeVia>
- Descripción: Código de la vía (según ADIF).

**INSPIRE Atributo railwayLineCode.**

- URI: <http://inspire.ec.europa.eu/ont/tn#RailwayLine.railwayLineCode>
- Descripción: A code assigned to a railway line which is unique within a Member State.

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100: <https://datos.ign.es/def/btn100#> .
@prefix tn: <http://inspire.ec.europa.eu/ont/tn#> .

btn100:codigoDeVia skos:exactMatch tn:RailwayLine.railwayLineCode .
```

En algunos casos, la relación entre atributos no es inmediata pero se puede llegar a inferir como, por ejemplo, en este caso:

Ejemplo AT.5:

**BTN100 Calzada.**

- URI: <https://datos.ign.es/def/btn100#calzada>
- Descripción: Número de calzadas y sentido de circulación del tramo de vía.

**INSPIRE Atributo minMaxNumberOfLanes.**

- URI: <http://inspire.ec.europa.eu/ont/tn#NumberOfLanes.minMaxNumberOfLanes>
- Descripción: Indicates if the number of lanes is counted as minimum or maximum value.

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#>
@prefix btn100: <https://datos.ign.es/def/btn100#> .
@prefix tn: <http://inspire.ec.europa.eu/ont/tn#> .

btn100:calzada skos:related inspire:NumberOfLanes.minMaxNumberOfLanes .
```

#### Emparejamientos entre listas controladas de valores (codelist) completas (ENUM)

Un ejemplo de emparejamiento entre *codelist* completas entre BTN100 y de TN de INSPIRE puede ser el siguiente:

Ejemplo ENUM.1:

**BTN100 Situación de la vía.**

- URI: <https://datos.ign.es/kos/transportes/situacion-via>
- Descripción: Tipología que define la disposición del tramo de la vía sobre la superficie.
- Tipo: skos:ConceptScheme

**INSPIRE Posición vertical.**

- URI: <http://inspire.ec.europa.eu/enumeration/VerticalPositionValue>
- Descripción: Posición vertical relativa de un objeto espacial.

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100_sv: <https://datos.ign.es/kos/transportes/situacion-via/> .
@prefix inspire_vpv: <http://inspire.ec.europa.eu/enumeration/VerticalPositionValue/> .

btn100_sv: skos:exactMatch inspire_vpv: .
btn100_sv:superficial skos:exactMatch inspire_vpv:onGroundSurface .
btn100_sv:elevada skos:exactMatch inspire_vpv:suspendedOrElevanted .
btn100_sv:subterranea skos:exactMatch inspire_vpv:underground .
```

También puede ocurrir que haya una correspondencia parcial de algunos valores de una en la otra, pero falten otros.
Por ejemplo:

Ejemplo ENUM.2:

**BTN100 Tipo de acceso a la vía.**

- URI: <https://datos.ign.es/kos/transportes/tipo-acceso>
- Descripción: Acceso libre o de peaje.

**INSPIRE Restricciones del acceso.**

- URI: <http://inspire.ec.europa.eu/codelist/AccessRestrictionValue>
- Descripción: Tipos de restricciones del acceso para un elemento de transporte.

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100_tte: <https://datos.ign.es/kos/transportes/> .
@prefix inspire_codelist: <http://inspire.ec.europa.eu/codelist/> .
btn100_tte:tipo-acceso skos:narrower inspire_codelist:AccessRestrictionValue.
```

#### Emparejamientos entre algunos valores de listas controladas (codelist) (VAL)

A veces pueden establecerse emparejamientos únicamente entre algunos valores aislados que forman parte de listas controladas.
Un ejemplo de este caso puede ser:

Ejemplo VAL.1:

**BTN100 Militar.**

- URI: <https://datos.ign.es/kos/transportes/competencia-aeroportuaria/militar>
- Descripción: Competencia militar.

**INSPIRE Valor reserved for military.**

- URI: <http://inspire.ec.europa.eu/codelist/AirUseRestrictionValue/reservedForMilitary>
- Descripción: The air network object is exclusively for military use.

**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100_ca: <https://datos.ign.es/kos/transportes/competencia-aeroportuaria/> .
@prefix inspire_aurv: <http://inspire.ec.europa.eu/codelist/AirUseRestrictionValue/> .

btn100_ca:militar skos:closeMatch inspire_aurv:reservedForMilitary.
```

EJEMPLO VAL.2:

**BTN100 De peaje.**

- URI: <https://datos.ign.es/page/kos/transportes/tipo-acceso/de-peaje>
- Descripción: Acceso de peaje.

**INSPIRE Valor toll.**

- URI: <http://inspire.ec.europa.eu/codelist/AccessRestrictionValue/toll>
- Descripción: Access to the transport element is subject to toll.
  
**Alineamiento.**

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix btn100_ta: <https://datos.ign.es/page/kos/transportes/tipo-acceso/> .
@prefix inspire_arv: <http://inspire.ec.europa.eu/codelist/AccessRestrictionValue/> .

btn100_ta:de-peaje skos:exactMatch inspire_arv:toll .
```

#### Emparejamientos entre clases y atributos con valor de lista controlada (CL-AT)

Hay casos en los que la relación se establece mediante el valor de una lista controlada en un atributo de una clase de un CDE y una clase del otro CDE.

Ejemplo CL-AT.1:

Un ejemplo de este tipo es que una carretera autonómica es una clase en BTN100 (<https://datos.ign.es/def/btn100#CarreteraAutonomica>), mientras que en TN este aspecto se modela con un atributo (FunctionalRoadClass::functionalClass) el cual podría, probablemente, corresponder con el tercer nivel (<http://inspire.ec.europa.eu/enumeration/FunctionalRoadClassValue/secondClass>).

**BTN100 Carretera Autonómica.**

- URI: <https://datos.ign.es/def/btn100#CarreteraAutonomica>
- Descripción: Tramo de carretera convencional de competencia autonómica o de cualquier otra administración inferior a ésta.
  
**INSPIRE atributo functionalClass.**

- URI: FunctionalRoadClass::functionalClass (este atributo debería estar definido en <http://inspire.ec.europa.eu/ont/tn#> pero no se han encontrado referencias)
- Descripción: Functional rank of the road link in the road network.

**INSPIRE valor secondClass.**

- URI: <http://inspire.ec.europa.eu/enumeration/FunctionalRoadClassValue/secondClass>
- Descripción: Tercer nivel de importancia en una red dada.

**Alineamiento.**

```turtle
@prefix skos: <https://www.w3.org/2009/08/skos-reference/skos.html#> .
@prefix btn100: <https://datos.ign.es/def/btn100#> .
@prefix tn: <http://inspire.ec.europa.eu/ont/tn#> .
@prefix inspire_frcv: <http://inspire.ec.europa.eu/enumeration/FunctionalRoadClassValue/> .

btn100:carreteraAutonomica skos:exactMatch
( tn:Road and tn:functionalClass value inspire_frcv :secondClass )
```

#### Emparejamientos entre instancias (CL)

En la fase de recopilación de información no se ha podido seleccionar ningún CDE conforme a INSPIRE en RDF, por lo que no es posible generar ejemplos de emparejamientos entre instancias de BTN100 que sean conceptos equivalentes en el CDE conforme a INSPIRE.

### Representar el CDE en RDF utilizando el alineamiento anterior

A partir de las relaciones identificadas en el apartado anterior, se procede a representar las mismas en los CDE en RDF utilizando el alineamiento anterior.
Este proceso puede subdividirse en dos fases diferenciadas, las cuales se detallan a continuación.

#### Obtención del RDF mediante diferentes técnicas o herramientas

Para la obtención del RDF aplicando las relaciones entre CDE pueden utilizarse diferentes técnicas o herramientas.
Algunas de las más relevantes pueden ser las siguientes:

- SPARQL Construct: para más información puede consultarse la referencia <https://www.w3.org/TR/rdf-sparql-query/#construct>.
- Geokettle: herramienta especializada en diseño de procesos ETL con componente geográfica. Más información en <http://www.geokettle.org/>.
- TripleGeoKettle: librería para generar ficheros RDF a partir de información geométrica, usando un *plugin* de Geokettle. Más información en <https://github.com/oeg-upm/geo.linkeddata.es-TripleGeoKettle>.
- Lenguajes de programación de propósito general u otras herramientas para diseñar procesos ETL.

Así, por ejemplo, el código SPARQL Construct para realizar el ejemplo
CL-1 sobre los datos de BTN100 sería el siguiente:

```turtle
prefix skos: <http://www.w3.org/2004/02/skos/core#>
prefix btn100: <https://datos.ign.es/def/btn100#>
prefix inspire: <https://inspire.ec.europa.eu/featureconcept/>
CONSTRUCT {
  ?x skos:exactMatch inspire:AerodromeArea .
}
WHERE {
  ?x a btn100:ZonaAeroportuaria
}
```

#### Serialización del RDF

Para la serialización del RDF la propuesta es la publicación en alguno de los formatos Turtle o JSON-LD.

### Recomendaciones y buenas prácticas

A continuación, se recopila un conjunto de recomendaciones y buenas prácticas a considerar en el proceso de generación de datos enlazados geográficos:

- Uso de GeoSPARQL
- No uso de ontología propia, en lo posible, buscando reutilización de otras ontologías ya existentes.
- Búsqueda de uno o varios nodos centrales (similar a la idea propuesta de tener la BTN100 como nodo central del grafo)
- URI resolubles y persistentes.
- Documentación completa.

## Bibliografía

<a id="1"></a>\[1\] P. Espinoza-Arias, M. García-Delgado, O. Corcho, P. Vivas-White, y H. Potti-Manjavacas, «A sustainable process and toolbox for geographical linked data generation and publication: a case study with BTN100», *Open Geospatial Data, Softw. Stand.*, vol. 4, n. 1, p. 2, 2019 \[Online\]. Disponible en: <https://doi.org/10.1186/s40965-019-0060-4>

<a id="2"></a>\[2\] L. M. Vilches-Blázquez, B. Villazón-Terrazas, O. Corcho, y A. Gómez-Pérez, «Integrating geographical information in the Linked Digital Earth», *Int. J. Digit. Earth*, vol. 7, n. 7, pp. 554-575, ago. 2014 \[Online\]. Disponible en: <https://doi.org/10.1080/17538947.2013.783127>

<a id="3"></a>\[3\] A. de León, V. Saquicela, L. M. Vilches, B. Villazón-Terrazas, F. Priyatna, y O. Corcho, «Geographical linked data: a Spanish use case», en *Proceedings of the 6th International Conference on Semantic Systems - I-SEMANTICS ’10*, 2010, p. 1 \[Online\]. Disponible en: <https://doi.org/10.1145/1839707.1839753>

<a id="4"></a>\[4\] L. Vilches-Blázquez, B. Villazón-Terrazas, O. Corcho, y A. Gómez-Pérez, «GeoLinked Data. An application case/Un caso de aplicación», *I Jornadas Ibéricas Infraestructuras Datos Espac. (JIIDE 2010)*, pp. 1-9, 2010 \[Online\]. Disponible en: <http://oa.upm.es/6166/>

<a id="5"></a>\[5\] B. Villazón-Terrazas, L. M. Vilches-Blázquez, O. Corcho, y A. Gómez-Pérez, «Methodological Guidelines for Publishing Government Linked Data», en *Linking Government Data*, New York, NY: Springer New York, 2011, pp. 27-49 \[Online\]. Disponible en: <http://link.springer.com/10.1007/978-1-4614-1767-5_2>

<a id="6"></a>\[6\] M. de H. y A. P. España, «Norma Técnica de Interoperabilidad de Reutilización de recursos de la información». pp. 1-27, 01-mar-2013 \[Online\]. Disponible en: <http://www.boe.es/boe/dias/2013/03/04/pdfs/BOE-A-2013-2380.pdf>

<a id="7"></a>\[7\] H. Halpin, P. J. Hayes, J. P. McCusker, D. L. McGuinness, y H. S. Thompson, «When owl:sameAs Isn’t the Same: An Analysis of Identity in Linked Data», 2010, pp. 305-320 \[Online\]. Disponible en: <http://link.springer.com/10.1007/978-3-642-17746-0_20>
