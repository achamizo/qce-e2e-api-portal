---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "KJB - Student API"
    version: "1.0.1"
    description: "This is the offical API for trusted Student data at our institution."
    contact: {}
  contract:
    baseUrls:
    - url: "http://localhost:8042/services/student-api"
      description: "Demo Environment"
      isPublished: true
    unsortedElementOrder:
    - "#/contract/resources/6e567151-42ab-41bb-b3a6-f215bf08a8bc"
    - "#/contract/resources/6ffc4436-0d8a-40e9-825d-2d4821896677"
    - "#/contract/types/5de4428f-266d-4642-b7a0-6f9daafa1db9"
    - "#/contract/types/77fbc285-2e5d-4def-844a-3ef73bf00eaa"
    resources:
      "6e567151-42ab-41bb-b3a6-f215bf08a8bc":
        path: "/student/{id}/"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          "5d39eb40-7132-4241-9b95-c43c57cffa11":
            name: "Get by Student ID"
            method: "GET"
            description: "Get Students using the Student ID"
            responses:
              "43521c65-6e2b-439f-8d46-61391589c01a":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/77fbc285-2e5d-4def-844a-3ef73bf00eaa"
                  mediaTypes:
                  - "application/json"
          "8724a222-80fb-4b5e-8f11-7e84f20f95c0":
            name: "Delete Student"
            method: "DELETE"
            description: "Delete the student by ID"
            responses:
              "391dfc31-8d63-413f-912d-c2a808c8dbad":
                status: "202"
                description: "Status 202"
      "6ffc4436-0d8a-40e9-825d-2d4821896677":
        path: "/student/"
        operations:
          a7324c71-4671-4006-a138-9e2c39c54178:
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
              "7f6cc3e0-562f-4795-9157-219200664ab9":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/77fbc285-2e5d-4def-844a-3ef73bf00eaa"
                  examples:
                  - value: "{  \n   \"student\":[  \n      {  \n         \"studentId\":145003,\n         \"firstName\":\"Benjamin\",\n         \"middleName\":\"Woodrow\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"withdraw\",\n         \"entryTerm\":201702,\n         \"address\":\"539 Cleveland Ave.\",\n         \"city\":\"Helena\",\n         \"state\":\"Mississippi\",\n         \"zip\":3657\n      },\n      {  \n         \"studentId\":145013,\n         \"firstName\":\"Andrew\",\n         \"middleName\":\"Warren\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"accepted\",\n         \"entryTerm\":201701,\n         \"address\":\"1229 Bailard Avenue\",\n         \"city\":\"Trenton\",\n         \"state\":\"South Carolina\",\n         \"zip\":63959\n      },\n      {  \n         \"studentId\":145091,\n         \"firstName\":\"Millard\",\n         \"middleName\":\"Richard\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"enrolled\",\n         \"entryTerm\":201701,\n         \"address\":\"1090 Carpinteria North\",\n         \"city\":\"Providence\",\n         \"state\":\"Maine\",\n         \"zip\":57472\n      }\n   ]\n}"
                  mediaTypes:
                  - "application/json"
          "6739b153-a9ee-4391-bbe6-dcf5e861708b":
            name: "Add a new Student"
            method: "POST"
            bodies:
            - type: "#/contract/types/77fbc285-2e5d-4def-844a-3ef73bf00eaa"
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
              f127f803-8d01-4de2-9187-3bc3943e7509:
                status: "200"
                description: "Status 200"
    types:
      "5de4428f-266d-4642-b7a0-6f9daafa1db9":
        name: "applicantStatus"
        type: "STRING"
        description: "The Student Applicant Status"
        enum:
        - "accepted"
        - "denied"
        - "withdraw"
        - "enrolled"
      "77fbc285-2e5d-4def-844a-3ef73bf00eaa":
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
            type: "#/contract/types/5de4428f-266d-4642-b7a0-6f9daafa1db9"
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
      "60162efb-36f4-4045-b31e-ab49fdf9a1ba":
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
        "name" : "KJB - Student API 1.0.1",
        "description" : "This is the offical API for trusted Student data at our institution.",
        "importedFrom" : "2db27baa-6635-4cc1-961c-5421d8de0a1e"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "5d39eb40-7132-4241-9b95-c43c57cffa11",
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
          "id" : "8724a222-80fb-4b5e-8f11-7e84f20f95c0",
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
          "id" : "a7324c71-4671-4006-a138-9e2c39c54178",
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
          "id" : "6739b153-a9ee-4391-bbe6-dcf5e861708b",
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
      "name" : "KJB - Student API 1.0.1",
      "importedFrom" : {
        "projectId" : "2db27baa-6635-4cc1-961c-5421d8de0a1e"
      },
      "variables" : {
        "8e8fee86-9765-4db2-865a-97fbbc8719c7" : {
          "name" : "BaseUrl",
          "value" : "http://localhost:8042/services/student-api",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
