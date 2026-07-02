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
    - "#/contract/resources/4960e9cc-e5c3-47bd-9046-8d3e200a0242"
    - "#/contract/resources/bcea6923-9a8e-4bf5-85ab-03a3efb7e94c"
    - "#/contract/types/246be633-595b-4896-942f-ed1332fbd17a"
    - "#/contract/types/d24a7452-4fc9-47ce-b8df-47fed249ea82"
    resources:
      "4960e9cc-e5c3-47bd-9046-8d3e200a0242":
        path: "/customer/{id}/"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          b4c39269-4ad0-4b62-b367-b1b2b1042759:
            name: "Get by Customer ID"
            method: "GET"
            description: "Get Customer using the Customer ID"
            responses:
              "10d95a21-8844-430b-905d-7a7cd0c96e0c":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/d24a7452-4fc9-47ce-b8df-47fed249ea82"
                  mediaTypes:
                  - "application/json"
          "32cbae0c-5d0f-49d2-825c-c2d8c6134467":
            name: "Delete Customer"
            method: "DELETE"
            description: "Delete the Customer by ID"
            responses:
              b3b7420a-e476-4a33-8df5-25aaf38a1176:
                status: "202"
                description: "Status 202"
      bcea6923-9a8e-4bf5-85ab-03a3efb7e94c:
        path: "/customer/"
        operations:
          "08f93165-b0b9-4648-8e6c-aae1f991c181":
            name: "Get Customers"
            method: "GET"
            description: "Operacion que permite obtener la lista de clientes"
            tags:
            - "Qlik"
            - "Demo"
            queryParameters:
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
            - name: "lastName"
              type: "STRING"
              description: "Customer Last Name"
              maxLength: 50
              examples:
              - value: "Jones"
            - name: "firstName"
              type: "STRING"
              description: "Customer First Name"
              maxLength: 50
              examples:
              - value: "John"
            responses:
              b0771ae8-1186-4621-a6c4-93a5da765e52:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/d24a7452-4fc9-47ce-b8df-47fed249ea82"
                  examples:
                  - value: "{  \n   \"customer\":[  \n      {  \n         \"customerId\":145003,\n         \"firstName\":\"Benjamin\",\n         \"middleName\":\"Woodrow\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"withdraw\",\n         \"entryTerm\":201702,\n         \"address\":\"539 Cleveland Ave.\",\n         \"city\":\"Helena\",\n         \"state\":\"Mississippi\",\n         \"zip\":3657\n      },\n      {  \n         \"customerId\":145013,\n         \"firstName\":\"Andrew\",\n         \"middleName\":\"Warren\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"accepted\",\n         \"entryTerm\":201701,\n         \"address\":\"1229 Bailard Avenue\",\n         \"city\":\"Trenton\",\n         \"state\":\"South Carolina\",\n         \"zip\":63959\n      },\n      {  \n         \"customerId\":145091,\n         \"firstName\":\"Millard\",\n         \"middleName\":\"Richard\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"enrolled\",\n         \"entryTerm\":201701,\n         \"address\":\"1090 Carpinteria North\",\n         \"city\":\"Providence\",\n         \"state\":\"Maine\",\n         \"zip\":57472\n      }\n   ]\n}"
                  mediaTypes:
                  - "application/json"
          "5137ae77-df48-4060-8ba3-bfede7e25a2e":
            name: "Add a new Customer"
            method: "POST"
            bodies:
            - type: "#/contract/types/d24a7452-4fc9-47ce-b8df-47fed249ea82"
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
              "0ca2de95-2b0c-4b7e-9f8f-d54a212dbb2e":
                status: "200"
                description: "Status 200"
    types:
      "246be633-595b-4896-942f-ed1332fbd17a":
        name: "applicantStatus"
        type: "STRING"
        description: "The Student Applicant Status"
        enum:
        - "accepted"
        - "denied"
        - "withdraw"
        - "enrolled"
      d24a7452-4fc9-47ce-b8df-47fed249ea82:
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
            type: "#/contract/types/246be633-595b-4896-942f-ed1332fbd17a"
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
      "1720e8b8-4a09-45a6-88d9-1124bb007459":
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
        "importedFrom" : "d3a99601-64c6-4884-b03b-9df96c358a13"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "b4c39269-4ad0-4b62-b367-b1b2b1042759",
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
          "id" : "32cbae0c-5d0f-49d2-825c-c2d8c6134467",
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
          "id" : "08f93165-b0b9-4648-8e6c-aae1f991c181",
          "name" : "Get Customers",
          "description" : "Operacion que permite obtener la lista de clientes",
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
                "name" : "applicantStatus",
                "value" : "accepted",
                "enabled" : false
              }, {
                "name" : "lastName",
                "value" : "Jones",
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
          "id" : "5137ae77-df48-4060-8ba3-bfede7e25a2e",
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
        "projectId" : "d3a99601-64c6-4884-b03b-9df96c358a13"
      },
      "variables" : {
        "8c22dfd3-e84b-490e-9351-3b3a7ce732ca" : {
          "name" : "BaseUrl",
          "value" : "http://localhost:8042/services/customer-api",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
