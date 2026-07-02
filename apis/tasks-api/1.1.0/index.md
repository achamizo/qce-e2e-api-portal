---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "Tasks API"
    version: "1.1.0"
    description: "An API for managing a list of tasks that need to be done"
    license: {}
    contact: {}
    termsOfService: ""
  contract:
    mediaTypes:
    - "application/json"
    unsortedElementOrder:
    - "#/contract/resources/eabe39f1-69b8-4ce6-9bcf-1c384a1457d6"
    - "#/contract/resources/04d37c91-fa6d-4da4-bdc3-cce7c7d5b5f4"
    - "#/contract/types/0ec25e72-fbbb-4576-86bc-59233922fa33"
    - "#/contract/types/f6c21f7a-8995-4a62-a6b6-41cd010e8543"
    securitySchemes:
      dad6bf9f-a1a3-4abf-8eac-314ae8aa432f:
        name: "HTTP_BASIC"
        type: "basic"
        description: "All GET methods are public, meaning that *you can read all the data*. Write operations require authentication and therefore are forbidden to the general public."
    resources:
      eabe39f1-69b8-4ce6-9bcf-1c384a1457d6:
        path: "/tasks/"
        operations:
          "8365a7bb-f2aa-46c1-85f7-522aea67beaf":
            name: "Load the list of Tasks"
            method: "GET"
            queryParameters:
            - name: "$size"
              type: "INTEGER"
              description: "Size of the page to retrieve."
              examples:
              - value: 10
            - name: "$page"
              type: "INTEGER"
              description: "Number of the page to retrieve."
              examples:
              - value: 1
            - name: "$sort"
              type: "STRING"
              description: "Order in which to retrieve the results. Multiple sort criteria can be passed."
              examples:
              - value: "createdAt DESC"
              - value: "name ASC"
            - name: "id"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field id"
              examples:
              - value: "47ee3550-b619-11e6-8408-0bdb025a7cfa"
            - name: "name"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field `name`"
              examples:
              - value: "Learn about hypermedia APIs"
            - name: "createdAt"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field `createdAt`"
              examples:
              - value: "2016.07.03"
            - name: "completed"
              type: "BOOLEAN"
              description: "Allows to filter the collection of results by the value of field `completed`"
              examples:
              - value: true
              - value: false
            responses:
              "470d2000-8f85-405b-a90f-99636d2dd193":
                status: "200"
                description: "Status 200"
                headers:
                - name: "X-Page-Count"
                  type: "INTEGER"
                  examples:
                  - value: 1
                - name: "X-Page-Number"
                  type: "INTEGER"
                  examples:
                  - value: 1
                - name: "X-Page-Size"
                  type: "INTEGER"
                  examples:
                  - value: 25
                - name: "X-Total-Count"
                  type: "INTEGER"
                  examples:
                  - value: 2
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/0ec25e72-fbbb-4576-86bc-59233922fa33"
                  examples:
                  - value: |-
                      [{
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }]
              "9fef6bc0-e0af-48be-8dda-1648f6183c07":
                status: "400"
                description: "Status 400"
                bodies:
                - type: "#/contract/types/f6c21f7a-8995-4a62-a6b6-41cd010e8543"
          "8cddfa1e-5eb6-463f-9c0b-9436a062e0bf":
            name: "Create a new task"
            method: "POST"
            securedBy:
            - scheme: "#/contract/securitySchemes/dad6bf9f-a1a3-4abf-8eac-314ae8aa432f"
              scopes: []
            bodies:
            - type: "#/contract/types/0ec25e72-fbbb-4576-86bc-59233922fa33"
              examples:
              - value: |-
                  {
                    "name": "Feed the fish",
                    "completed": false,
                    "createdAt": "2016.07.03"
                  }
            responses:
              ef2fa886-9270-4284-9515-6bc943a2ca43:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/0ec25e72-fbbb-4576-86bc-59233922fa33"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
      "04d37c91-fa6d-4da4-bdc3-cce7c7d5b5f4":
        path: "/tasks/{taskid}"
        pathVariables:
        - name: "taskid"
          type: "STRING"
          description: "Identifier of the Task"
          examples:
          - value: "47ee3550-b619-11e6-8408-0bdb025a7cfa"
        operations:
          "05a69c5e-c708-45f1-81cd-26776068fd50":
            name: "Load a specific Task"
            method: "GET"
            responses:
              "36ffc478-a4de-458d-9a0f-386c01a06af2":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/0ec25e72-fbbb-4576-86bc-59233922fa33"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
              "6d827983-e44e-422c-b9fb-be17e318347e":
                status: "400"
                description: "Status 400"
                bodies:
                - type: "#/contract/types/f6c21f7a-8995-4a62-a6b6-41cd010e8543"
          "985470ba-f305-449f-81da-22e6d385eac2":
            name: "Update a Task"
            method: "PUT"
            securedBy:
            - scheme: "#/contract/securitySchemes/dad6bf9f-a1a3-4abf-8eac-314ae8aa432f"
              scopes: []
            bodies:
            - type: "#/contract/types/0ec25e72-fbbb-4576-86bc-59233922fa33"
              examples:
              - value: |-
                  {
                    "name": "Feed the fish",
                    "completed": false,
                    "createdAt": "2016.07.03"
                  }
            responses:
              fb8a8934-620a-47cd-9d7f-2f2698ab8d9a:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/0ec25e72-fbbb-4576-86bc-59233922fa33"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
          d6c5c21a-25b7-415d-a00d-d912888f8c0c:
            name: "Delete a Task"
            method: "DELETE"
            securedBy:
            - scheme: "#/contract/securitySchemes/dad6bf9f-a1a3-4abf-8eac-314ae8aa432f"
              scopes: []
            responses:
              "7840b827-04cf-4c0a-b08c-0fc4d031b17a":
                status: "200"
                description: "Status 200"
    types:
      "0ec25e72-fbbb-4576-86bc-59233922fa33":
        name: "Task"
        type: "OBJECT"
        description: "An object that represents a task"
        properties:
        - name: "id"
          type: "STRING"
          description: "Auto-generated primary key field"
          required: true
          examples:
          - value: "3fa2eb40-b61c-11e6-9de0-fdbe71bceebb"
        - name: "name"
          type: "STRING"
          required: true
          examples:
          - value: "Figure out how to colonize Mars"
        - name: "completed"
          type: "BOOLEAN"
          required: true
        - name: "createdAt"
          type: "STRING"
          examples:
          - value: "2016.10.06"
        examples:
        - value: |-
            {
              "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
              "name": "Feed the fish",
              "completed": false,
              "createdAt": "2016.07.03"
            }
      f6c21f7a-8995-4a62-a6b6-41cd010e8543:
        name: "Error"
        type: "OBJECT"
        description: "This general error structure is used throughout this API."
        properties:
        - name: "code"
          type: "INTEGER"
          required: true
          minimum: 400
          maximum: 599
        - name: "description"
          type: "STRING"
          examples:
          - value: "Bad query parameter [$size]: Invalid integer value [abc]"
          - value: "The server understood the request, but is refusing to fulfill it"
        - name: "reasonPhrase"
          type: "STRING"
          examples:
          - value: "Bad Request"
          - value: "Forbidden"
        examples:
        - value: |-
            {
              "code": 400,
              "description": "Bad query parameter [$size]: Invalid integer value [abc]",
              "reasonPhrase": "Bad Request"
            }
  components: {}
api-tryin: |-
  {
    "version" : 6,
    "entities" : [ {
      "entity" : {
        "type" : "Project",
        "name" : "Tasks API 1.1.0",
        "description" : "An API for managing a list of tasks that need to be done",
        "importedFrom" : "1af3ca97-9559-470d-80cc-64aed4483a3a"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "8365a7bb-f2aa-46c1-85f7-522aea67beaf",
          "name" : "Load the list of Tasks",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/",
            "query" : {
              "delimiter" : "&",
              "items" : [ {
                "name" : "$size",
                "value" : "10",
                "enabled" : false
              }, {
                "name" : "$page",
                "value" : "1",
                "enabled" : false
              }, {
                "name" : "$sort",
                "value" : "createdAt DESC",
                "enabled" : false
              }, {
                "name" : "id",
                "value" : "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                "enabled" : false
              }, {
                "name" : "name",
                "value" : "Learn about hypermedia APIs",
                "enabled" : false
              }, {
                "name" : "createdAt",
                "value" : "2016.07.03",
                "enabled" : false
              }, {
                "name" : "completed",
                "value" : "true",
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
          "id" : "8cddfa1e-5eb6-463f-9c0b-9436a062e0bf",
          "name" : "Create a new task",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/"
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
          }, {
            "enabled" : true,
            "name" : "Accept",
            "value" : "application/json"
          } ],
          "headersType" : "Form",
          "body" : {
            "bodyType" : "Text",
            "textBody" : "{\n  \"name\": \"Feed the fish\",\n  \"completed\": false,\n  \"createdAt\": \"2016.07.03\"\n}"
          }
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "05a69c5e-c708-45f1-81cd-26776068fd50",
          "name" : "Load a specific Task",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/{taskid}"
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
          "id" : "985470ba-f305-449f-81da-22e6d385eac2",
          "name" : "Update a Task",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/{taskid}"
          },
          "method" : {
            "link" : "",
            "name" : "PUT",
            "requestBody" : true
          },
          "headers" : [ {
            "enabled" : true,
            "name" : "Content-Type",
            "value" : "application/json"
          }, {
            "enabled" : true,
            "name" : "Accept",
            "value" : "application/json"
          } ],
          "headersType" : "Form",
          "body" : {
            "bodyType" : "Text",
            "textBody" : "{\n  \"name\": \"Feed the fish\",\n  \"completed\": false,\n  \"createdAt\": \"2016.07.03\"\n}"
          }
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "d6c5c21a-25b7-415d-a00d-d912888f8c0c",
          "name" : "Delete a Task",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/{taskid}"
          },
          "method" : {
            "link" : "",
            "name" : "DELETE"
          },
          "headers" : [ ],
          "headersType" : "Form"
        }
      } ]
    } ],
    "environments" : [ {
      "name" : "Tasks API 1.1.0",
      "importedFrom" : {
        "projectId" : "1af3ca97-9559-470d-80cc-64aed4483a3a"
      },
      "variables" : {
        "eb3b88e6-770e-47ad-b0f9-03b0865c866c" : {
          "name" : "BaseUrl",
          "value" : "https://example.com",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
