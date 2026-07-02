---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "KJB - Customer API"
    version: "1.0.1"
    description: |-
      Esta **API** es la interfaz oficial de acceso a datos de **Clientes** de la organización. Su diseño busca combinar confiabilidad, consistencia y escalabilidad para integraciones seguras y de alto rendimiento. Está pensada para ser el punto único de verdad (single source of truth) de la información de clientes, permitiendo a sistemas internos, aplicaciones de terceros y plataformas de análisis consumir datos precisos en tiempo real.

      Esta guía no solo describe la estructura técnica de la API, sino que la enmarca en un contexto práctico, con ejemplos y recomendaciones para maximizar su aprovechamiento.

      **Base URL:** http://localhost:8090/services/customer-api

      **Formato de Intercambio: JSON** sobre HTTP/HTTPS, especificación OpenAPI 3.0.1

      > Esta guía no solo describe la estructura técnica de la API, sino que la enmarca en un contexto práctico, con ejemplos y recomendaciones para maximizar su aprovechamiento

      # Términos de Servicio de la API
      ## **1. Propósito y Alcance**

      La **API de Clientes** ha sido concebida para centralizar el acceso a datos de clientes, reduciendo duplicidades y evitando inconsistencias entre sistemas. Su uso está autorizado únicamente para aplicaciones, integraciones o procesos previamente validados por la organización. Esto incluye, pero no se limita a:

      - Portales y apps corporativas.
      - Herramientas de análisis de datos y *business intelligence*.
      - Flujos ETL y procesos batch.
      - Integraciones con partners aprobados.

      Queda expresamente prohibido:

      - Usar la API para recopilar datos con fines de venta o distribución no autorizada.
      - Inyectar datos maliciosos o manipular información con fines fraudulentos.
      - Realizar pruebas de carga o *stress testing* sin aprobación previa.

      ## **2. Acceso y Autenticación**
      En entornos productivos, todo acceso debe pasar por mecanismos robustos de autenticación y autorización, como OAuth2, JWT o certificados digitales. Las credenciales son personales e intransferibles, y su custodia es responsabilidad del titular. La pérdida o filtración de credenciales debe notificarse inmediatamente al equipo de soporte.

      ### **3. Privacidad y Protección de Datos**
      Todos los consumidores de esta API se comprometen a cumplir con las leyes de protección de datos aplicables en su jurisdicción, incluyendo GDPR, CCPA o equivalentes locales. Esto implica:

      - No almacenar datos personales más allá del tiempo estrictamente necesario.
      - Garantizar cifrado en tránsito (HTTPS) y en reposo si se persisten datos.
      - No compartir datos con terceros no autorizados.

      El incumplimiento de estas políticas podrá derivar en la revocación del acceso y acciones legales.

      ## **4. Límites de Uso (*Rate Limits*)**
      Para proteger la disponibilidad del servicio y garantizar equidad entre todos los consumidores, la API podrá imponer límites de peticiones por minuto, hora o día. Los límites se comunican a través de cabeceras HTTP como `X-RateLimit-Limit` y `X-RateLimit-Remaining`. Superar de forma reiterada estos límites puede resultar en la suspensión temporal o permanente del acceso.

      ## **5. Disponibilidad y Mantenimiento**
      La API está diseñada para alta disponibilidad, con redundancia y monitoreo continuo. No obstante, pueden producirse interrupciones programadas para mantenimiento o emergencias. Dichos mantenimientos serán anunciados con antelación razonable siempre que sea posible. La organización no se hace responsable por daños derivados de interrupciones temporales.

      ## **6. Responsabilidad del Consumidor**
      Cada integrador o desarrollador es responsable de:

      - Manejar adecuadamente los códigos de estado y mensajes de error.
      - Implementar reintentos y tolerancia a fallos.
      - Validar los datos recibidos antes de procesarlos.
      - Garantizar que el uso de la API no degrade su rendimiento ni el de otros consumidores.

      ## **7. Propiedad Intelectual**
      Todo el contenido, diseño, código fuente y documentación de la API son propiedad de la organización. Se prohíbe su reproducción, redistribución o modificación sin autorización expresa. El uso de esta API no concede derechos de propiedad sobre la misma ni sobre los datos que proporciona.

      ## **8. Modificaciones del Servicio**
      La organización se reserva el derecho de modificar el comportamiento, estructura o disponibilidad de la API. Esto incluye cambios en los endpoints, formatos de datos, parámetros y límites de uso. Cuando sea posible, se mantendrán versiones previas para facilitar la transición.

      ## **9. Soporte y Comunicación**
      El soporte técnico se ofrece a través de canales oficiales (correo, portal de soporte, chat corporativo). Para incidencias críticas, el tiempo de respuesta estará definido según los acuerdos de nivel de servicio (SLAs) vigentes.

      > **Aceptación:** El uso de la **KJB – Customer API** implica la aceptación plena y sin reservas de estos términos. Cualquier uso no conforme podrá ser sancionado conforme a las políticas internas y legislación vigente.
    license:
      name: "Uso Interno"
      url: "http://www.qlik.com"
    contact:
      name: "Alexander Chamizo"
      email: "alexander.chamizo@qlik.com"
      url: "http://www.qlik.com"
  contract:
    baseUrls:
    - url: "http://127.0.0.1:8090/services/customer-api"
      description: "Ambiente de Desarrollo"
      isPublished: true
    - url: "http://replicate.attunitydemo.com:5070/services/customer-api"
      description: "Ambiente de Pruebas"
      isPublished: true
    unsortedElementOrder:
    - "#/contract/resources/394bf4ff-d348-4793-8446-474198927166"
    - "#/contract/resources/b039c360-084f-4385-a386-65ce67f20dfc"
    - "#/contract/types/10523893-12a9-474f-9b43-bdbe48b64a3e"
    - "#/contract/types/ac6847b0-83bf-43eb-a4d5-68190603a845"
    securitySchemes:
      "98b60173-deb2-4f73-89f3-3d55c6566161":
        name: "Usuario_y_contrasena"
        type: "basic"
        description: "Utilice este método de autenticación cuando se trate de información interna."
      acc87249-c486-4d36-90dd-8f6af9b3c617:
        name: "Autenticacion_por_Token"
        type: "bearer"
        description: "Use este método de autenticación cuando se trate de información sensible."
    securedBy:
    - null
    resources:
      "394bf4ff-d348-4793-8446-474198927166":
        path: "/customer/{id}/"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          "47c75165-aa2a-43d0-a84e-198dcdd00524":
            name: "Get by Customer ID"
            method: "GET"
            description: |-
              # Consulta de cliente por identificador

              **Propósito:** Este endpoint es la herramienta principal para recuperar la información de un cliente específico. Va más allá de simplemente "traer datos"; es una pieza fundamental en la verificación de identidad, personalización de experiencias, auditorías internas y cualquier proceso que requiera información precisa y en tiempo real.

              **Casos de uso concretos:**

              - **Atención personalizada:** Un agente de soporte recupera los datos del cliente para ofrecer asistencia contextual.
              - **Validación de identidad:** Un proceso de pago revisa que el cliente y sus datos sean correctos antes de autorizar la operación.
              - **Historial de interacciones:** Un sistema CRM combina estos datos con el historial de llamadas y correos para una visión 360°.
              - **Control de accesos:** Una aplicación valida si un cliente cumple con ciertos criterios para acceder a un servicio premium.

              **Ejemplo adicional:** En una aplicación de banca digital, al iniciar sesión, la app llama a este endpoint para mostrar el nombre, dirección y estado de la cuenta del cliente en la pantalla principal.
            tags:
            - "Demo"
            - "Qlik"
            - "Customer"
            - "Query"
            responses:
              "2d92e864-c18b-49af-ba48-99451175dad7":
                status: "200"
                description: "Cliente encontrado"
                bodies:
                - type: "#/contract/types/ac6847b0-83bf-43eb-a4d5-68190603a845"
                  examples:
                  - value: |-
                      {
                        "customer": {
                          "customerId": 145025,
                          "firstName": "Andrew",
                          "middleName": "Franklin",
                          "lastName": "Quincy",
                          "applicantStatus": "accepted",
                          "entryTerm": 201702,
                          "address": "1793 East Main Street",
                          "city": "Columbia",
                          "state": "Hawaii",
                          "zip": 62433
                        }
                      }
                  mediaTypes:
                  - "application/json"
              b1b25b72-5363-4b3f-bd1c-811e719d8409:
                status: "404"
                description: "Cliente no encontrado"
                bodies:
                - type: "OBJECT"
                  examples:
                  - value: |-
                      {
                          "error": {
                              "message": "Could not find customer ID '444444'"
                          }
                      }
                  mediaTypes:
                  - "application/json"
          "08deb9b8-2de6-4dd3-96f6-a5ada3e198a7":
            name: "Delete Customer"
            method: "DELETE"
            description: |
              # Eliminación de cliente

              **Propósito:** Este endpoint garantiza que se pueda eliminar o desactivar un cliente de forma controlada, cumpliendo tanto con regulaciones de privacidad como con políticas internas de gestión de datos. Además, habilita flujos de negocio que requieren "limpieza" de información obsoleta o incorrecta.

              **Casos de uso concretos:**

              - **Derecho al olvido (GDPR/CCPA):** Eliminación definitiva de datos a solicitud del cliente.
              - **Depuración de base de datos:** Eliminación de registros obsoletos, duplicados o incorrectos.
              - **Baja de servicios:** Al cancelar una suscripción, se elimina la información asociada o se marca como inactiva.
              - **Migración de datos:** Antes de migrar, se eliminan registros no válidos para evitar errores.

              **Ejemplo adicional:** Un sistema de suscripciones online ejecuta este endpoint automáticamente cuando un cliente se da de baja y finaliza su último periodo de servicio.
            tags:
            - "Demo"
            - "Qlik"
            - "Customer"
            - "Delete"
            responses:
              c708c4c5-5bc4-4019-a0bf-dc8ef98cdfc2:
                status: "202"
                description: "Cliente eliminado"
      b039c360-084f-4385-a386-65ce67f20dfc:
        path: "/customer/"
        operations:
          "01979793-310b-4863-af3b-1842e2673dab":
            name: "Get Customers"
            method: "GET"
            description: |-
              # Listado y búsqueda avanzada de clientes

              **Propósito:** Este endpoint actúa como un motor de búsqueda y filtrado para recuperar conjuntos de clientes. Es esencial para análisis masivos, segmentaciones y generación de reportes. Permite combinar múltiples filtros para obtener datos muy específicos.

              **Casos de uso concretos:**

              - **Segmentación de campañas:** Obtener todos los clientes con `applicantStatus=accepted` en un `entryTerm`específico.
              - **Análisis estadístico:** Filtrar clientes por apellido, nombre o periodo de ingreso para detectar patrones.
              - **Preparación de datos para BI:** Exportar información filtrada para cargar en un dashboard.
              - **Procesos operativos:** Listar clientes que cumplan con criterios para asignaciones de recursos o auditorías.

              **Ejemplo adicional:** En una campaña de email marketing, el sistema usa este endpoint para obtener únicamente los clientes "enrolled" en el último trimestre y con direcciones en una región específica.

              **Opciones de filtrado:** Permite refinar la búsqueda mediante parámetros como `applicantStatus`, `lastName`, `entryTerm` y `firstName`, lo que brinda flexibilidad y precisión. Por ejemploi, un sistema de reportes necesita generar un listado de todos los clientes aceptados en el periodo `201801`. Se invoca este endpoint con `applicantStatus=accepted` y `entryTerm=201801` para obtener exactamente esa segmentación.
            tags:
            - "Qlik"
            - "Demo"
            - "Customer"
            - "Query"
            queryParameters:
            - name: "entryTerm"
              type: "STRING"
              description: "Customer Entry Term"
              minLength: 6
              maxLength: 6
              examples:
              - value: "201801"
            - name: "firstName"
              type: "STRING"
              description: "Customer First Name"
              maxLength: 50
              examples:
              - value: "John"
            - name: "applicantStatus"
              type: "STRING"
              description: "Customer Applicant Status"
              enum:
              - "accepted"
              - "denied"
              - "withdraw"
              - "enrolled"
            - name: "lastName"
              type: "STRING"
              description: "Customer Last Name"
              maxLength: 50
              examples:
              - value: "Jones"
            responses:
              bce80300-eabf-4fc9-b10f-52f2c5b22803:
                status: "200"
                description: "Clientes encontrados"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/ac6847b0-83bf-43eb-a4d5-68190603a845"
                  examples:
                  - value: "{  \n   \"customer\":[  \n      {  \n         \"customerId\":145003,\n         \"firstName\":\"Benjamin\",\n         \"middleName\":\"Woodrow\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"withdraw\",\n         \"entryTerm\":201702,\n         \"address\":\"539 Cleveland Ave.\",\n         \"city\":\"Helena\",\n         \"state\":\"Mississippi\",\n         \"zip\":3657\n      },\n      {  \n         \"customerId\":145013,\n         \"firstName\":\"Andrew\",\n         \"middleName\":\"Warren\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"accepted\",\n         \"entryTerm\":201701,\n         \"address\":\"1229 Bailard Avenue\",\n         \"city\":\"Trenton\",\n         \"state\":\"South Carolina\",\n         \"zip\":63959\n      },\n      {  \n         \"customerId\":145091,\n         \"firstName\":\"Millard\",\n         \"middleName\":\"Richard\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"enrolled\",\n         \"entryTerm\":201701,\n         \"address\":\"1090 Carpinteria North\",\n         \"city\":\"Providence\",\n         \"state\":\"Maine\",\n         \"zip\":57472\n      }\n   ]\n}"
                  mediaTypes:
                  - "application/json"
          e2452493-f419-46b8-ba0f-bb94e5ee5d33:
            name: "Add a new Customer"
            method: "POST"
            description: |
              # Creación de nuevos clientes

              **Propósito:** Permite registrar nuevos clientes en el sistema maestro, asegurando que toda la organización tenga acceso a la información más reciente desde el momento de la creación. Es la puerta de entrada para iniciar relaciones comerciales, registrar leads convertidos o realizar altas masivas durante migraciones.

              **Casos de uso concretos:**

              - **Registro web:** Un visitante completa un formulario en el portal y se crea el registro del cliente.
              - **Alta en punto de venta:** Un vendedor introduce los datos de un nuevo cliente directamente en el sistema.
              - **Captura móvil en campo:** Un agente comercial registra clientes durante un evento o visita.
              - **Carga masiva:** Durante una migración de sistema, se insertan miles de registros nuevos de una sola vez.

              **Ejemplo adicional:** En un evento corporativo, se capturan los datos de todos los asistentes y se cargan en la API mediante un script para iniciar campañas de seguimiento post-evento.
            tags:
            - "Demo"
            - "Qlik"
            - "Customer"
            - "Add"
            bodies:
            - type: "#/contract/types/ac6847b0-83bf-43eb-a4d5-68190603a845"
              examples:
              - value: |-
                  {
                    "customer": {
                      "customerId": 55555,
                      "firstName": "Andrew",
                      "middleName": "Franklin",
                      "lastName": "Quincy",
                      "applicantStatus": "accepted",
                      "entryTerm": 201702,
                      "address": "1793 East Main Street",
                      "city": "Columbia",
                      "state": "Hawaii",
                      "zip": 62433
                    }
                  }
              mediaTypes:
              - "application/json"
            responses:
              "5349bc1a-f015-44f4-9311-d3f411cb42e9":
                status: "200"
                description: "Cliente registrado"
    types:
      "10523893-12a9-474f-9b43-bdbe48b64a3e":
        name: "applicantStatus"
        type: "STRING"
        description: |-
          El estatus actual del registro del cliente:

          * **accepted** - Aceptado
          * **denied** - Solicitud denegada
          * **withdraw** - Dado de baja
          * **enrolled** - Registrado
          * **unknown** - Proceso incompleto
        default: "unknown"
        enum:
        - "accepted"
        - "denied"
        - "withdraw"
        - "enrolled"
        - "unknown"
        examples:
        - value: "accepted"
      ac6847b0-83bf-43eb-a4d5-68190603a845:
        name: "Customer_JSON"
        type: "OBJECT"
        description: |
          Define el formato estándar de intercambio de datos de cliente, asegurando integridad y compatibilidad entre sistemas. Incluye identificadores, datos personales, dirección y estado dentro de un proceso de admisión o gestión.

          **Campos clave:**

          - `customerId` – Identificador único.
          - `firstName`, `middleName`, `lastName` – Nombres y apellidos.
          - `applicantStatus` – Estado del cliente en el proceso.
          - `entryTerm` – Periodo de ingreso (AAAAMM).
          - `address`, `city`, `state`, `zip` – Datos de ubicación.

          **Ejemplo práctico:** En un flujo de Talend, este modelo puede mapearse directamente a un esquema relacional o enviarse a Qlik para generar visualizaciones en tiempo real.
        properties:
        - name: "Customer"
          type: "OBJECT"
          description: "Información del Cliente"
          properties:
          - name: "zip"
            type: "NUMBER"
            description: "Código Postal"
          - name: "city"
            type: "STRING"
            description: "Ciudad"
            maxLength: 50
          - name: "state"
            type: "STRING"
            description: "Estado o Provincia"
            minLength: 2
            maxLength: 2
          - name: "address"
            type: "STRING"
            description: "Dirección"
          - name: "lastName"
            type: "STRING"
            description: "Apellido"
            maxLength: 50
          - name: "entryTerm"
            type: "NUMBER"
            description: "Fecha de Registro"
            examples:
            - value: 201701
          - name: "firstName"
            type: "STRING"
            description: "Nombre"
            maxLength: 50
          - name: "customerId"
            type: "NUMBER"
            description: "Identificador del Cliente"
            examples:
            - value: 145001
          - name: "middleName"
            type: "STRING"
            description: "Segundo Nombre"
            maxLength: 50
          - name: "applicantStatus"
            type: "#/contract/types/10523893-12a9-474f-9b43-bdbe48b64a3e"
        examples:
        - value: |-
            {
              "customer": {
                "customerId": 145025,
                "firstName": "Andrew",
                "middleName": "Franklin",
                "lastName": "Quincy",
                "applicantStatus": "accepted",
                "entryTerm": 201702,
                "address": "1793 East Main Street",
                "city": "Columbia",
                "state": "Hawaii",
                "zip": 62433
              }
            }
  components:
    pathVariables:
      "40e542c7-0b7f-4552-8e12-0924412cbba0":
        name: "studentId"
        componentName: "studentId"
        type: "INTEGER"
        format: "INT32"
        description: "The Student ID"
        required: true
        examples:
        - value: 44444
    queryParameters:
      "2f4a7499-2937-47f5-bcce-03ce58743b49":
        name: "customerId"
        componentName: "customerId"
        type: "INTEGER"
        format: "INT32"
        description: "Identificador de Cliente"
        examples:
        - value: 44444
api-tryin: |-
  {
    "version" : 6,
    "entities" : [ {
      "entity" : {
        "type" : "Project",
        "name" : "KJB - Customer API 1.0.1",
        "description" : "Esta **API** es la interfaz oficial de acceso a datos de **Clientes** de la organización. Su diseño busca combinar confiabilidad, consistencia y escalabilidad para integraciones seguras y de alto rendimiento. Está pensada para ser el punto único de verdad (single source of truth) de la información de clientes, permitiendo a sistemas internos, aplicaciones de terceros y plataformas de análisis consumir datos precisos en tiempo real.\n\nEsta guía no solo describe la estructura técnica de la API, sino que la enmarca en un contexto práctico, con ejemplos y recomendaciones para maximizar su aprovechamiento.\n\n**Base URL:** http://localhost:8090/services/customer-api\n\n**Formato de Intercambio: JSON** sobre HTTP/HTTPS, especificación OpenAPI 3.0.1\n\n> Esta guía no solo describe la estructura técnica de la API, sino que la enmarca en un contexto práctico, con ejemplos y recomendaciones para maximizar su aprovechamiento\n\n# Términos de Servicio de la API\n## **1. Propósito y Alcance**\n\nLa **API de Clientes** ha sido concebida para centralizar el acceso a datos de clientes, reduciendo duplicidades y evitando inconsistencias entre sistemas. Su uso está autorizado únicamente para aplicaciones, integraciones o procesos previamente validados por la organización. Esto incluye, pero no se limita a:\n\n- Portales y apps corporativas.\n- Herramientas de análisis de datos y *business intelligence*.\n- Flujos ETL y procesos batch.\n- Integraciones con partners aprobados.\n\nQueda expresamente prohibido:\n\n- Usar la API para recopilar datos con fines de venta o distribución no autorizada.\n- Inyectar datos maliciosos o manipular información con fines fraudulentos.\n- Realizar pruebas de carga o *stress testing* sin aprobación previa.\n\n## **2. Acceso y Autenticación**\nEn entornos productivos, todo acceso debe pasar por mecanismos robustos de autenticación y autorización, como OAuth2, JWT o certificados digitales. Las credenciales son personales e intransferibles, y su custodia es responsabilidad del titular. La pérdida o filtración de credenciales debe notificarse inmediatamente al equipo de soporte.\n\n### **3. Privacidad y Protección de Datos**\nTodos los consumidores de esta API se comprometen a cumplir con las leyes de protección de datos aplicables en su jurisdicción, incluyendo GDPR, CCPA o equivalentes locales. Esto implica:\n\n- No almacenar datos personales más allá del tiempo estrictamente necesario.\n- Garantizar cifrado en tránsito (HTTPS) y en reposo si se persisten datos.\n- No compartir datos con terceros no autorizados.\n\nEl incumplimiento de estas políticas podrá derivar en la revocación del acceso y acciones legales.\n\n## **4. Límites de Uso (*Rate Limits*)**\nPara proteger la disponibilidad del servicio y garantizar equidad entre todos los consumidores, la API podrá imponer límites de peticiones por minuto, hora o día. Los límites se comunican a través de cabeceras HTTP como `X-RateLimit-Limit` y `X-RateLimit-Remaining`. Superar de forma reiterada estos límites puede resultar en la suspensión temporal o permanente del acceso.\n\n## **5. Disponibilidad y Mantenimiento**\nLa API está diseñada para alta disponibilidad, con redundancia y monitoreo continuo. No obstante, pueden producirse interrupciones programadas para mantenimiento o emergencias. Dichos mantenimientos serán anunciados con antelación razonable siempre que sea posible. La organización no se hace responsable por daños derivados de interrupciones temporales.\n\n## **6. Responsabilidad del Consumidor**\nCada integrador o desarrollador es responsable de:\n\n- Manejar adecuadamente los códigos de estado y mensajes de error.\n- Implementar reintentos y tolerancia a fallos.\n- Validar los datos recibidos antes de procesarlos.\n- Garantizar que el uso de la API no degrade su rendimiento ni el de otros consumidores.\n\n## **7. Propiedad Intelectual**\nTodo el contenido, diseño, código fuente y documentación de la API son propiedad de la organización. Se prohíbe su reproducción, redistribución o modificación sin autorización expresa. El uso de esta API no concede derechos de propiedad sobre la misma ni sobre los datos que proporciona.\n\n## **8. Modificaciones del Servicio**\nLa organización se reserva el derecho de modificar el comportamiento, estructura o disponibilidad de la API. Esto incluye cambios en los endpoints, formatos de datos, parámetros y límites de uso. Cuando sea posible, se mantendrán versiones previas para facilitar la transición.\n\n## **9. Soporte y Comunicación**\nEl soporte técnico se ofrece a través de canales oficiales (correo, portal de soporte, chat corporativo). Para incidencias críticas, el tiempo de respuesta estará definido según los acuerdos de nivel de servicio (SLAs) vigentes.\n\n> **Aceptación:** El uso de la **KJB – Customer API** implica la aceptación plena y sin reservas de estos términos. Cualquier uso no conforme podrá ser sancionado conforme a las políticas internas y legislación vigente.",
        "importedFrom" : "8d9eb274-ddb2-4aca-9c3d-0b6f8b518c5c"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "47c75165-aa2a-43d0-a84e-198dcdd00524",
          "name" : "Get by Customer ID",
          "description" : "# Consulta de cliente por identificador\n\n**Propósito:** Este endpoint es la herramienta principal para recuperar la información de un cliente específico. Va más allá de simplemente \"traer datos\"; es una pieza fundamental en la verificación de identidad, personalización de experiencias, auditorías internas y cualquier proceso que requiera información precisa y en tiempo real.\n\n**Casos de uso concretos:**\n\n- **Atención personalizada:** Un agente de soporte recupera los datos del cliente para ofrecer asistencia contextual.\n- **Validación de identidad:** Un proceso de pago revisa que el cliente y sus datos sean correctos antes de autorizar la operación.\n- **Historial de interacciones:** Un sistema CRM combina estos datos con el historial de llamadas y correos para una visión 360°.\n- **Control de accesos:** Una aplicación valida si un cliente cumple con ciertos criterios para acceder a un servicio premium.\n\n**Ejemplo adicional:** En una aplicación de banca digital, al iniciar sesión, la app llama a este endpoint para mostrar el nombre, dirección y estado de la cuenta del cliente en la pantalla principal.",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/customer/{id}/"
          },
          "method" : {
            "link" : "",
            "name" : "GET"
          },
          "headers" : [ {
            "enabled" : true,
            "name" : "Accept",
            "value" : "application/json"
          } ],
          "headersType" : "Form"
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "08deb9b8-2de6-4dd3-96f6-a5ada3e198a7",
          "name" : "Delete Customer",
          "description" : "# Eliminación de cliente\n\n**Propósito:** Este endpoint garantiza que se pueda eliminar o desactivar un cliente de forma controlada, cumpliendo tanto con regulaciones de privacidad como con políticas internas de gestión de datos. Además, habilita flujos de negocio que requieren \"limpieza\" de información obsoleta o incorrecta.\n\n**Casos de uso concretos:**\n\n- **Derecho al olvido (GDPR/CCPA):** Eliminación definitiva de datos a solicitud del cliente.\n- **Depuración de base de datos:** Eliminación de registros obsoletos, duplicados o incorrectos.\n- **Baja de servicios:** Al cancelar una suscripción, se elimina la información asociada o se marca como inactiva.\n- **Migración de datos:** Antes de migrar, se eliminan registros no válidos para evitar errores.\n\n**Ejemplo adicional:** Un sistema de suscripciones online ejecuta este endpoint automáticamente cuando un cliente se da de baja y finaliza su último periodo de servicio.\n",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/customer/{id}/"
          },
          "method" : {
            "link" : "",
            "name" : "DELETE"
          },
          "headers" : [ ],
          "headersType" : "Form"
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "01979793-310b-4863-af3b-1842e2673dab",
          "name" : "Get Customers",
          "description" : "# Listado y búsqueda avanzada de clientes\n\n**Propósito:** Este endpoint actúa como un motor de búsqueda y filtrado para recuperar conjuntos de clientes. Es esencial para análisis masivos, segmentaciones y generación de reportes. Permite combinar múltiples filtros para obtener datos muy específicos.\n\n**Casos de uso concretos:**\n\n- **Segmentación de campañas:** Obtener todos los clientes con `applicantStatus=accepted` en un `entryTerm`específico.\n- **Análisis estadístico:** Filtrar clientes por apellido, nombre o periodo de ingreso para detectar patrones.\n- **Preparación de datos para BI:** Exportar información filtrada para cargar en un dashboard.\n- **Procesos operativos:** Listar clientes que cumplan con criterios para asignaciones de recursos o auditorías.\n\n**Ejemplo adicional:** En una campaña de email marketing, el sistema usa este endpoint para obtener únicamente los clientes \"enrolled\" en el último trimestre y con direcciones en una región específica.\n\n**Opciones de filtrado:** Permite refinar la búsqueda mediante parámetros como `applicantStatus`, `lastName`, `entryTerm` y `firstName`, lo que brinda flexibilidad y precisión. Por ejemploi, un sistema de reportes necesita generar un listado de todos los clientes aceptados en el periodo `201801`. Se invoca este endpoint con `applicantStatus=accepted` y `entryTerm=201801` para obtener exactamente esa segmentación.",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/customer/",
            "query" : {
              "delimiter" : "&",
              "items" : [ {
                "name" : "entryTerm",
                "value" : "201801",
                "enabled" : false
              }, {
                "name" : "firstName",
                "value" : "John",
                "enabled" : false
              }, {
                "name" : "applicantStatus",
                "value" : "accepted",
                "enabled" : false
              }, {
                "name" : "lastName",
                "value" : "Jones",
                "enabled" : false
              } ]
            }
          },
          "method" : {
            "link" : "",
            "name" : "GET"
          },
          "headers" : [ {
            "enabled" : true,
            "name" : "Accept",
            "value" : "application/json"
          } ],
          "headersType" : "Form",
          "uriEditor" : true
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "e2452493-f419-46b8-ba0f-bb94e5ee5d33",
          "name" : "Add a new Customer",
          "description" : "# Creación de nuevos clientes\n\n**Propósito:** Permite registrar nuevos clientes en el sistema maestro, asegurando que toda la organización tenga acceso a la información más reciente desde el momento de la creación. Es la puerta de entrada para iniciar relaciones comerciales, registrar leads convertidos o realizar altas masivas durante migraciones.\n\n**Casos de uso concretos:**\n\n- **Registro web:** Un visitante completa un formulario en el portal y se crea el registro del cliente.\n- **Alta en punto de venta:** Un vendedor introduce los datos de un nuevo cliente directamente en el sistema.\n- **Captura móvil en campo:** Un agente comercial registra clientes durante un evento o visita.\n- **Carga masiva:** Durante una migración de sistema, se insertan miles de registros nuevos de una sola vez.\n\n**Ejemplo adicional:** En un evento corporativo, se capturan los datos de todos los asistentes y se cargan en la API mediante un script para iniciar campañas de seguimiento post-evento.\n",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/customer/"
          },
          "method" : {
            "link" : "",
            "name" : "POST",
            "requestBody" : true
          },
          "headers" : [ {
            "enabled" : true,
            "name" : "Content-Type",
            "value" : "application/json"
          } ],
          "headersType" : "Form",
          "body" : {
            "bodyType" : "Text",
            "textBody" : "{\n  \"customer\": {\n    \"customerId\": 55555,\n    \"firstName\": \"Andrew\",\n    \"middleName\": \"Franklin\",\n    \"lastName\": \"Quincy\",\n    \"applicantStatus\": \"accepted\",\n    \"entryTerm\": 201702,\n    \"address\": \"1793 East Main Street\",\n    \"city\": \"Columbia\",\n    \"state\": \"Hawaii\",\n    \"zip\": 62433\n  }\n}"
          }
        }
      } ]
    } ],
    "environments" : [ {
      "name" : "KJB - Customer API 1.0.1",
      "importedFrom" : {
        "projectId" : "8d9eb274-ddb2-4aca-9c3d-0b6f8b518c5c"
      },
      "variables" : {
        "fab77d4a-7194-404e-a92d-fabbcad44fd3" : {
          "name" : "BaseUrl",
          "value" : "http://127.0.0.1:8090/services/customer-api",
          "enabled" : true,
          "private" : false
        }
      }
    }, {
      "name" : "KJB - Customer API 1.0.1",
      "importedFrom" : {
        "projectId" : "8d9eb274-ddb2-4aca-9c3d-0b6f8b518c5c"
      },
      "variables" : {
        "36db1997-4f5c-434d-9d15-94abf8df1d1a" : {
          "name" : "BaseUrl",
          "value" : "http://replicate.attunitydemo.com:5070/services/customer-api",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
