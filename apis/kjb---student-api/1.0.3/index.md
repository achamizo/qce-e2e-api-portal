---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "KJB - Student API"
    version: "1.0.3"
    description: "This is the offical API for trusted Student data at our institution."
    contact: {}
  contract:
    baseUrls:
    - url: "http://localhost:8042/services/student-api"
      description: "Demo Environment"
      isPublished: true
    unsortedElementOrder:
    - "#/contract/resources/d97cec1b-5ce7-4382-a1be-7b9746745fd9"
    - "#/contract/resources/8c3139db-9a29-48e2-b0a3-8ac2bb986f12"
    - "#/contract/types/fad433ae-3436-4b06-8725-5b2d468c298b"
    - "#/contract/types/ccb18737-2654-41d4-b152-8e0c1e47e138"
    resources:
      d97cec1b-5ce7-4382-a1be-7b9746745fd9:
        path: "/student/{id}/"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          "0b083980-1e99-422e-a9f6-310c9047ed7b":
            name: "Get by Student ID"
            method: "GET"
            description: "Get Students using the Student ID"
            responses:
              "692cde52-bd7c-4b06-9e4d-7aecca5012d5":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/ccb18737-2654-41d4-b152-8e0c1e47e138"
                  mediaTypes:
                  - "application/json"
          "4af9ead5-fa5b-458d-87bd-434b3d191dc0":
            name: "Delete Student"
            method: "DELETE"
            description: "Delete the student by ID"
            responses:
              "3a9ebce0-6c92-4edf-b280-023f7c78a19a":
                status: "202"
                description: "Status 202"
      "8c3139db-9a29-48e2-b0a3-8ac2bb986f12":
        path: "/student/"
        operations:
          "309843e0-329c-4ddd-9f36-349e21bc88e8":
            name: "Get Students"
            method: "GET"
            queryParameters:
            - name: "lastName"
              type: "STRING"
              description: "Student Last Name"
              maxLength: 50
              examples:
              - value: "Jones"
            - name: "entryTerm"
              type: "STRING"
              description: "Student Entry Term"
              minLength: 6
              maxLength: 6
              examples:
              - value: "201801"
            - name: "applicantStatus"
              type: "STRING"
              description: "Student Applicant Status"
              enum:
              - "accepted"
              - "denied"
              - "withdraw"
              - "enrolled"
            - name: "firstName"
              type: "STRING"
              description: "Student First Name"
              maxLength: 50
              examples:
              - value: "John"
            responses:
              dfda261a-bf9f-45c2-8959-ce90b4408b17:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/ccb18737-2654-41d4-b152-8e0c1e47e138"
                  examples:
                  - value: "{  \n   \"student\":[  \n      {  \n         \"studentId\":145003,\n         \"firstName\":\"Benjamin\",\n         \"middleName\":\"Woodrow\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"withdraw\",\n         \"entryTerm\":201702,\n         \"address\":\"539 Cleveland Ave.\",\n         \"city\":\"Helena\",\n         \"state\":\"Mississippi\",\n         \"zip\":3657\n      },\n      {  \n         \"studentId\":145013,\n         \"firstName\":\"Andrew\",\n         \"middleName\":\"Warren\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"accepted\",\n         \"entryTerm\":201701,\n         \"address\":\"1229 Bailard Avenue\",\n         \"city\":\"Trenton\",\n         \"state\":\"South Carolina\",\n         \"zip\":63959\n      },\n      {  \n         \"studentId\":145091,\n         \"firstName\":\"Millard\",\n         \"middleName\":\"Richard\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"enrolled\",\n         \"entryTerm\":201701,\n         \"address\":\"1090 Carpinteria North\",\n         \"city\":\"Providence\",\n         \"state\":\"Maine\",\n         \"zip\":57472\n      }\n   ]\n}"
                  mediaTypes:
                  - "application/json"
          "67d64f2f-ca95-41f4-9723-dd14d8d1d0bb":
            name: "Add a new Student"
            method: "POST"
            bodies:
            - type: "#/contract/types/ccb18737-2654-41d4-b152-8e0c1e47e138"
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
              cbf0b644-98d0-4692-92f9-7a7e3db000fa:
                status: "200"
                description: "Status 200"
    types:
      fad433ae-3436-4b06-8725-5b2d468c298b:
        name: "applicantStatus"
        type: "STRING"
        description: "The Student Applicant Status"
        enum:
        - "accepted"
        - "denied"
        - "withdraw"
        - "enrolled"
      ccb18737-2654-41d4-b152-8e0c1e47e138:
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
            type: "#/contract/types/fad433ae-3436-4b06-8725-5b2d468c298b"
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
      e3e6e62e-94c8-48e6-adaf-0431117eb2bd:
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
        "name" : "KJB - Student API 1.0.3",
        "description" : "This is the offical API for trusted Student data at our institution.",
        "importedFrom" : "638cf589-437f-4b1e-ad7b-9477ba69e335"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "0b083980-1e99-422e-a9f6-310c9047ed7b",
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
          "id" : "4af9ead5-fa5b-458d-87bd-434b3d191dc0",
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
          "id" : "309843e0-329c-4ddd-9f36-349e21bc88e8",
          "name" : "Get Students",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/student/",
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
          "id" : "67d64f2f-ca95-41f4-9723-dd14d8d1d0bb",
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
      "name" : "KJB - Student API 1.0.3",
      "importedFrom" : {
        "projectId" : "638cf589-437f-4b1e-ad7b-9477ba69e335"
      },
      "variables" : {
        "ec92c164-32ad-48a1-8706-e5bf7ecaf9bc" : {
          "name" : "BaseUrl",
          "value" : "http://localhost:8042/services/student-api",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
