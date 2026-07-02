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
    - "#/contract/resources/87e1c535-703c-468e-a65b-69066abb9d24"
    - "#/contract/resources/d1968305-8a7a-43d6-83fa-d85e914395a9"
    - "#/contract/types/a0027009-4b4d-4d16-b90e-d86637b02290"
    - "#/contract/types/03916ccb-20dd-42cc-b451-c1d1665fcbd1"
    securitySchemes:
      e7dc6078-715f-4426-bc82-8563f0183500:
        name: "HTTP_BASIC"
        type: "basic"
        description: "All GET methods are public, meaning that *you can read all the data*. Write operations require authentication and therefore are forbidden to the general public."
    resources:
      "87e1c535-703c-468e-a65b-69066abb9d24":
        path: "/tasks/"
        operations:
          "6f198966-efe4-4553-b203-583d404ce67c":
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
              "05b71a4d-a751-4289-8dd9-c7765c33d0f4":
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
                    type: "#/contract/types/a0027009-4b4d-4d16-b90e-d86637b02290"
                  examples:
                  - value: |-
                      [{
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }]
              "6afd9057-4577-4861-961a-c77aa44fab8f":
                status: "400"
                description: "Status 400"
                bodies:
                - type: "#/contract/types/03916ccb-20dd-42cc-b451-c1d1665fcbd1"
          "19ce2ca5-5aa0-482c-a5f9-945ca143b4ed":
            name: "Create a new task"
            method: "POST"
            securedBy:
            - scheme: "#/contract/securitySchemes/e7dc6078-715f-4426-bc82-8563f0183500"
              scopes: []
            bodies:
            - type: "#/contract/types/a0027009-4b4d-4d16-b90e-d86637b02290"
              examples:
              - value: |-
                  {
                    "name": "Feed the fish",
                    "completed": false,
                    "createdAt": "2016.07.03"
                  }
            responses:
              "3dbb1984-662e-4cb1-87b6-d8f73d99d2ff":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/a0027009-4b4d-4d16-b90e-d86637b02290"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
      d1968305-8a7a-43d6-83fa-d85e914395a9:
        path: "/tasks/{taskid}"
        pathVariables:
        - name: "taskid"
          type: "STRING"
          description: "Identifier of the Task"
          examples:
          - value: "47ee3550-b619-11e6-8408-0bdb025a7cfa"
        operations:
          "9bd2531c-a3f4-4ffd-b2f0-93bd1a367ae0":
            name: "Load a specific Task"
            method: "GET"
            responses:
              "061862c3-88a9-45a1-b253-ca568d645c4e":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/a0027009-4b4d-4d16-b90e-d86637b02290"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
              "5a8fbbf0-eb9d-4148-99de-f549a012ec63":
                status: "400"
                description: "Status 400"
                bodies:
                - type: "#/contract/types/03916ccb-20dd-42cc-b451-c1d1665fcbd1"
          "90603018-0372-4213-a6eb-8551a3f0a863":
            name: "Update a Task"
            method: "PUT"
            securedBy:
            - scheme: "#/contract/securitySchemes/e7dc6078-715f-4426-bc82-8563f0183500"
              scopes: []
            bodies:
            - type: "#/contract/types/a0027009-4b4d-4d16-b90e-d86637b02290"
              examples:
              - value: |-
                  {
                    "name": "Feed the fish",
                    "completed": false,
                    "createdAt": "2016.07.03"
                  }
            responses:
              acc32cac-68e1-402d-9c5b-7675668053c0:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/a0027009-4b4d-4d16-b90e-d86637b02290"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Feed the fish",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
          "63e912dd-a3cc-42b5-990d-4679e45c48f2":
            name: "Delete a Task"
            method: "DELETE"
            securedBy:
            - scheme: "#/contract/securitySchemes/e7dc6078-715f-4426-bc82-8563f0183500"
              scopes: []
            responses:
              "42ef28f9-62a3-4fd6-ad60-8eeb2ac46a86":
                status: "200"
                description: "Status 200"
    types:
      a0027009-4b4d-4d16-b90e-d86637b02290:
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
      "03916ccb-20dd-42cc-b451-c1d1665fcbd1":
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
        "importedFrom" : "3e57d43a-2b10-42c0-a163-9bf3a9e5d0dc"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "6f198966-efe4-4553-b203-583d404ce67c",
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
          "id" : "19ce2ca5-5aa0-482c-a5f9-945ca143b4ed",
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
          "id" : "9bd2531c-a3f4-4ffd-b2f0-93bd1a367ae0",
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
          "id" : "90603018-0372-4213-a6eb-8551a3f0a863",
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
          "id" : "63e912dd-a3cc-42b5-990d-4679e45c48f2",
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
        "projectId" : "3e57d43a-2b10-42c0-a163-9bf3a9e5d0dc"
      },
      "variables" : {
        "567fafd4-a492-4dc4-993a-ac4397989664" : {
          "name" : "BaseUrl",
          "value" : "https://example.com",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
