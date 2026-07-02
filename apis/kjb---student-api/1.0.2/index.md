---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "KJB - Student API"
    version: "1.0.2"
    description: "This is the offical API for trusted Student data at our institution."
    contact: {}
  contract:
    baseUrls:
    - url: "http://localhost:8042/services/student-api"
      description: "Demo Environment"
      isPublished: true
    unsortedElementOrder:
    - "#/contract/resources/7e59d5eb-820e-4977-aed5-211cdded6eda"
    - "#/contract/resources/c0d77b1e-2665-44f7-82d4-935ea993b025"
    - "#/contract/types/f90739ea-3949-44b4-9540-a61bd8721398"
    - "#/contract/types/68769775-0c5b-4883-b3f8-8318d9150cbc"
    resources:
      "7e59d5eb-820e-4977-aed5-211cdded6eda":
        path: "/student/{id}/"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          "70b7dd1b-41af-4a2a-aafe-f92a4f271922":
            name: "Get by Student ID"
            method: "GET"
            description: "Get Students using the Student ID"
            responses:
              e033ec21-f5d5-4fdb-8c0c-e527886c46bd:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/68769775-0c5b-4883-b3f8-8318d9150cbc"
                  mediaTypes:
                  - "application/json"
          "47eb44dc-a0e2-4dcd-9e22-65181459d0b1":
            name: "Delete Student"
            method: "DELETE"
            description: "Delete the student by ID"
            responses:
              "2ce18cff-ffbb-495d-909d-8e1a7947fa87":
                status: "202"
                description: "Status 202"
      c0d77b1e-2665-44f7-82d4-935ea993b025:
        path: "/student/"
        operations:
          cf2d7139-4123-4882-ba22-16cabfb92f85:
            name: "Get Students"
            method: "GET"
            queryParameters:
            - name: "entryTerm"
              type: "STRING"
              description: "Student Entry Term"
              minLength: 6
              maxLength: 6
              examples:
              - value: "201801"
            - name: "firstName"
              type: "STRING"
              description: "Student First Name"
              maxLength: 50
              examples:
              - value: "John"
            - name: "applicantStatus"
              type: "STRING"
              description: "Student Applicant Status"
              enum:
              - "accepted"
              - "denied"
              - "withdraw"
              - "enrolled"
            - name: "lastName"
              type: "STRING"
              description: "Student Last Name"
              maxLength: 50
              examples:
              - value: "Jones"
            responses:
              dd0181b8-639e-469d-8c8e-0a0c755138bf:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/68769775-0c5b-4883-b3f8-8318d9150cbc"
                  examples:
                  - value: "{  \n   \"student\":[  \n      {  \n         \"studentId\":145003,\n         \"firstName\":\"Benjamin\",\n         \"middleName\":\"Woodrow\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"withdraw\",\n         \"entryTerm\":201702,\n         \"address\":\"539 Cleveland Ave.\",\n         \"city\":\"Helena\",\n         \"state\":\"Mississippi\",\n         \"zip\":3657\n      },\n      {  \n         \"studentId\":145013,\n         \"firstName\":\"Andrew\",\n         \"middleName\":\"Warren\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"accepted\",\n         \"entryTerm\":201701,\n         \"address\":\"1229 Bailard Avenue\",\n         \"city\":\"Trenton\",\n         \"state\":\"South Carolina\",\n         \"zip\":63959\n      },\n      {  \n         \"studentId\":145091,\n         \"firstName\":\"Millard\",\n         \"middleName\":\"Richard\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"enrolled\",\n         \"entryTerm\":201701,\n         \"address\":\"1090 Carpinteria North\",\n         \"city\":\"Providence\",\n         \"state\":\"Maine\",\n         \"zip\":57472\n      }\n   ]\n}"
                  mediaTypes:
                  - "application/json"
          "2d8d83e4-f8e3-4b01-bcbf-211c2e794e71":
            name: "Add a new Student"
            method: "POST"
            bodies:
            - type: "#/contract/types/68769775-0c5b-4883-b3f8-8318d9150cbc"
              examples:
              - value: |-
                  {
                    "student": {
                      "studentId": 55555,
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
              "73a22b34-792a-479e-8f42-37ab01d7c473":
                status: "200"
                description: "Status 200"
    types:
      f90739ea-3949-44b4-9540-a61bd8721398:
        name: "applicantStatus"
        type: "STRING"
        description: "The Student Applicant Status"
        enum:
        - "accepted"
        - "denied"
        - "withdraw"
        - "enrolled"
      "68769775-0c5b-4883-b3f8-8318d9150cbc":
        name: "Student_JSON"
        type: "OBJECT"
        description: "Student JSON Structure"
        properties:
        - name: "Student"
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
            type: "#/contract/types/f90739ea-3949-44b4-9540-a61bd8721398"
        examples:
        - value: |-
            {
              "student": {
                "studentId": 145025,
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
      e695a6cf-e188-4588-87bc-652f8a0b9917:
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
        "name" : "KJB - Student API 1.0.2",
        "description" : "This is the offical API for trusted Student data at our institution.",
        "importedFrom" : "08099417-82f5-4acf-9ff8-db1aaa40eba9"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "70b7dd1b-41af-4a2a-aafe-f92a4f271922",
          "name" : "Get by Student ID",
          "description" : "Get Students using the Student ID",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/student/{id}/"
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
          "id" : "47eb44dc-a0e2-4dcd-9e22-65181459d0b1",
          "name" : "Delete Student",
          "description" : "Delete the student by ID",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/student/{id}/"
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
          "id" : "cf2d7139-4123-4882-ba22-16cabfb92f85",
          "name" : "Get Students",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/student/",
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
          "id" : "2d8d83e4-f8e3-4b01-bcbf-211c2e794e71",
          "name" : "Add a new Student",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/student/"
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
            "textBody" : "{\n  \"student\": {\n    \"studentId\": 55555,\n    \"firstName\": \"Andrew\",\n    \"middleName\": \"Franklin\",\n    \"lastName\": \"Quincy\",\n    \"applicantStatus\": \"accepted\",\n    \"entryTerm\": 201702,\n    \"address\": \"1793 East Main Street\",\n    \"city\": \"Columbia\",\n    \"state\": \"Hawaii\",\n    \"zip\": 62433\n  }\n}"
          }
        }
      } ]
    } ],
    "environments" : [ {
      "name" : "KJB - Student API 1.0.2",
      "importedFrom" : {
        "projectId" : "08099417-82f5-4acf-9ff8-db1aaa40eba9"
      },
      "variables" : {
        "ca9e3a74-fda7-4363-90ed-ff7c59968001" : {
          "name" : "BaseUrl",
          "value" : "http://localhost:8042/services/student-api",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
