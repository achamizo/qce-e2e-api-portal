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
    - "#/contract/resources/ca312cd6-a8f3-449f-a0ea-b6a9d873f889"
    - "#/contract/resources/78d950f6-4e0e-4f39-b2fc-84df789627de"
    - "#/contract/types/27b082f3-baf6-4e86-b43f-8e69bea4d82a"
    - "#/contract/types/8020fae0-2336-4528-aa87-97141dea9cc8"
    resources:
      ca312cd6-a8f3-449f-a0ea-b6a9d873f889:
        path: "/student/{id}/"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          a61858e2-496c-42ed-a840-1a71c72a3fe9:
            name: "Get by Student ID"
            method: "GET"
            description: "Get Students using the Student ID"
            responses:
              b53553b6-29e4-4901-a1aa-bc7af56a8f3b:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/8020fae0-2336-4528-aa87-97141dea9cc8"
                  mediaTypes:
                  - "application/json"
          b601c9d6-ee9b-4138-8345-6b970c04942b:
            name: "Delete Student"
            method: "DELETE"
            description: "Delete the student by ID"
            responses:
              "3c08952d-f051-4193-9a08-6996ed797383":
                status: "202"
                description: "Status 202"
      "78d950f6-4e0e-4f39-b2fc-84df789627de":
        path: "/student/"
        operations:
          "8d2a3df8-24b5-47ef-9517-13dcdec74898":
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
              a7392b74-b5fa-41ab-b6da-a8087d4bedbc:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/8020fae0-2336-4528-aa87-97141dea9cc8"
                  examples:
                  - value: "{  \n   \"student\":[  \n      {  \n         \"studentId\":145003,\n         \"firstName\":\"Benjamin\",\n         \"middleName\":\"Woodrow\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"withdraw\",\n         \"entryTerm\":201702,\n         \"address\":\"539 Cleveland Ave.\",\n         \"city\":\"Helena\",\n         \"state\":\"Mississippi\",\n         \"zip\":3657\n      },\n      {  \n         \"studentId\":145013,\n         \"firstName\":\"Andrew\",\n         \"middleName\":\"Warren\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"accepted\",\n         \"entryTerm\":201701,\n         \"address\":\"1229 Bailard Avenue\",\n         \"city\":\"Trenton\",\n         \"state\":\"South Carolina\",\n         \"zip\":63959\n      },\n      {  \n         \"studentId\":145091,\n         \"firstName\":\"Millard\",\n         \"middleName\":\"Richard\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"enrolled\",\n         \"entryTerm\":201701,\n         \"address\":\"1090 Carpinteria North\",\n         \"city\":\"Providence\",\n         \"state\":\"Maine\",\n         \"zip\":57472\n      }\n   ]\n}"
                  mediaTypes:
                  - "application/json"
          f90d1909-60c1-4c84-9650-3a60a954c1f1:
            name: "Add a new Student"
            method: "POST"
            bodies:
            - type: "#/contract/types/8020fae0-2336-4528-aa87-97141dea9cc8"
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
              "4b1b64d3-26d9-4a52-93fe-456f51da1999":
                status: "200"
                description: "Status 200"
    types:
      "27b082f3-baf6-4e86-b43f-8e69bea4d82a":
        name: "applicantStatus"
        type: "STRING"
        description: "The Student Applicant Status"
        enum:
        - "accepted"
        - "denied"
        - "withdraw"
        - "enrolled"
      "8020fae0-2336-4528-aa87-97141dea9cc8":
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
            type: "#/contract/types/27b082f3-baf6-4e86-b43f-8e69bea4d82a"
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
      ef2f3200-9615-48f1-a412-5b6968ac0ed4:
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
        "importedFrom" : "3f97940a-01b8-42d4-8d42-54f4c95cb68e"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "a61858e2-496c-42ed-a840-1a71c72a3fe9",
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
          "id" : "b601c9d6-ee9b-4138-8345-6b970c04942b",
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
          "id" : "8d2a3df8-24b5-47ef-9517-13dcdec74898",
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
          "id" : "f90d1909-60c1-4c84-9650-3a60a954c1f1",
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
        "projectId" : "3f97940a-01b8-42d4-8d42-54f4c95cb68e"
      },
      "variables" : {
        "b4a595b2-548b-4b5f-a5eb-97da4288d22f" : {
          "name" : "BaseUrl",
          "value" : "http://localhost:8042/services/student-api",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
