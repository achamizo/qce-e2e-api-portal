---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "KJB - Customer API"
    version: "1.0.0"
    description: "This is the offical API for trusted Customer data at our organization."
    contact: {}
  contract:
    baseUrls:
    - url: "http://localhost:8042/services/customer-api"
      description: "Demo Environment"
      isPublished: true
    unsortedElementOrder:
    - "#/contract/resources/ffc44d13-4543-49a3-b718-fa22bbd16b25"
    - "#/contract/resources/cbc5ee2b-be81-429d-b996-5a627e1849e6"
    - "#/contract/types/22a052d0-5125-4a7f-a659-8106421aa7d2"
    - "#/contract/types/803569cb-e628-4c66-bcc7-db92cda749c0"
    resources:
      ffc44d13-4543-49a3-b718-fa22bbd16b25:
        path: "/customer/{id}/"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          "2bb10e27-b7fe-4fa3-b5e5-fdcb858f120f":
            name: "Get by Customer ID"
            method: "GET"
            description: "Get Customer using the Customer ID"
            responses:
              ddf4bfbf-3bb8-4e48-943d-b5d6fb0fc877:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/803569cb-e628-4c66-bcc7-db92cda749c0"
                  mediaTypes:
                  - "application/json"
          "04334aaf-7036-4dec-ae9f-1bc1a877e679":
            name: "Delete Customer"
            method: "DELETE"
            description: "Delete the Customer by ID"
            responses:
              "642353bf-0514-4b6c-bddf-47aaaf683040":
                status: "202"
                description: "Status 202"
      cbc5ee2b-be81-429d-b996-5a627e1849e6:
        path: "/customer/"
        operations:
          c6b6731f-a5e4-41af-9687-690affc946c7:
            name: "Get Customers"
            method: "GET"
            description: "Operacion que permite obtener la lista de clientes"
            tags:
            - "Qlik"
            - "Demo"
            queryParameters:
            - name: "lastName"
              type: "STRING"
              description: "Customer Last Name"
              maxLength: 50
              examples:
              - value: "Jones"
            - name: "entryTerm"
              type: "STRING"
              description: "Customer Entry Term"
              minLength: 6
              maxLength: 6
              examples:
              - value: "201801"
            - name: "applicantStatus"
              type: "STRING"
              description: "Customer Applicant Status"
              enum:
              - "accepted"
              - "denied"
              - "withdraw"
              - "enrolled"
            - name: "firstName"
              type: "STRING"
              description: "Customer First Name"
              maxLength: 50
              examples:
              - value: "John"
            responses:
              "1037b846-7a78-4b24-98a2-32e0320680a2":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/803569cb-e628-4c66-bcc7-db92cda749c0"
                  examples:
                  - value: "{  \n   \"customer\":[  \n      {  \n         \"customerId\":145003,\n         \"firstName\":\"Benjamin\",\n         \"middleName\":\"Woodrow\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"withdraw\",\n         \"entryTerm\":201702,\n         \"address\":\"539 Cleveland Ave.\",\n         \"city\":\"Helena\",\n         \"state\":\"Mississippi\",\n         \"zip\":3657\n      },\n      {  \n         \"customerId\":145013,\n         \"firstName\":\"Andrew\",\n         \"middleName\":\"Warren\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"accepted\",\n         \"entryTerm\":201701,\n         \"address\":\"1229 Bailard Avenue\",\n         \"city\":\"Trenton\",\n         \"state\":\"South Carolina\",\n         \"zip\":63959\n      },\n      {  \n         \"customerId\":145091,\n         \"firstName\":\"Millard\",\n         \"middleName\":\"Richard\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"enrolled\",\n         \"entryTerm\":201701,\n         \"address\":\"1090 Carpinteria North\",\n         \"city\":\"Providence\",\n         \"state\":\"Maine\",\n         \"zip\":57472\n      }\n   ]\n}"
                  mediaTypes:
                  - "application/json"
          "1a372998-63c7-4700-a580-56dc1b871453":
            name: "Add a new Customer"
            method: "POST"
            bodies:
            - type: "#/contract/types/803569cb-e628-4c66-bcc7-db92cda749c0"
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
              "2fb0b0f9-f9d6-453d-ab53-b2bc343b70ec":
                status: "200"
                description: "Status 200"
    types:
      "22a052d0-5125-4a7f-a659-8106421aa7d2":
        name: "applicantStatus"
        type: "STRING"
        description: "The Student Applicant Status"
        enum:
        - "accepted"
        - "denied"
        - "withdraw"
        - "enrolled"
      "803569cb-e628-4c66-bcc7-db92cda749c0":
        name: "Customer_JSON"
        type: "OBJECT"
        description: "Customer JSON Structure"
        properties:
        - name: "Customer"
          type: "OBJECT"
          properties:
          - name: "zip"
            type: "NUMBER"
            description: "Postal Code"
          - name: "city"
            type: "STRING"
            maxLength: 50
          - name: "state"
            type: "STRING"
            description: "State, Province, etc."
            minLength: 2
            maxLength: 2
          - name: "address"
            type: "STRING"
            description: "Street address"
          - name: "lastName"
            type: "STRING"
            maxLength: 50
          - name: "entryTerm"
            type: "NUMBER"
            examples:
            - value: 201701
          - name: "firstName"
            type: "STRING"
            maxLength: 50
          - name: "studentId"
            type: "NUMBER"
            examples:
            - value: 145001
          - name: "middleName"
            type: "STRING"
            maxLength: 50
          - name: "applicantStatus"
            type: "#/contract/types/22a052d0-5125-4a7f-a659-8106421aa7d2"
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
      "3bd6813f-3fae-4441-9eb4-a606a8f46fff":
        name: "studentId"
        componentName: "studentId"
        type: "INTEGER"
        format: "INT32"
        description: "The Student ID"
        required: true
        examples:
        - value: 44444
api-tryin: |-
  {
    "version" : 6,
    "entities" : [ {
      "entity" : {
        "type" : "Project",
        "name" : "KJB - Customer API 1.0.0",
        "description" : "This is the offical API for trusted Customer data at our organization.",
        "importedFrom" : "86dea3b0-33fb-44f5-9fb2-bb994ac0e7bb"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "2bb10e27-b7fe-4fa3-b5e5-fdcb858f120f",
          "name" : "Get by Customer ID",
          "description" : "Get Customer using the Customer ID",
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
          "id" : "04334aaf-7036-4dec-ae9f-1bc1a877e679",
          "name" : "Delete Customer",
          "description" : "Delete the Customer by ID",
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
          "id" : "c6b6731f-a5e4-41af-9687-690affc946c7",
          "name" : "Get Customers",
          "description" : "Operacion que permite obtener la lista de clientes",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/customer/",
            "query" : {
              "delimiter" : "&",
              "items" : [ {
                "name" : "lastName",
                "value" : "Jones",
                "enabled" : false
              }, {
                "name" : "entryTerm",
                "value" : "201801",
                "enabled" : false
              }, {
                "name" : "applicantStatus",
                "value" : "accepted",
                "enabled" : false
              }, {
                "name" : "firstName",
                "value" : "John",
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
          "id" : "1a372998-63c7-4700-a580-56dc1b871453",
          "name" : "Add a new Customer",
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
      "name" : "KJB - Customer API 1.0.0",
      "importedFrom" : {
        "projectId" : "86dea3b0-33fb-44f5-9fb2-bb994ac0e7bb"
      },
      "variables" : {
        "4ea2b84a-29c7-4121-84e8-dd8f076150ec" : {
          "name" : "BaseUrl",
          "value" : "http://localhost:8042/services/customer-api",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
