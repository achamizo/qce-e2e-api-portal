---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "KJB - Student API"
    version: "1.0.0"
    description: "This is the offical API for trusted Student data at our institution."
    contact: {}
  contract:
    baseUrls:
    - url: "https://lp1uhp3.us.api-mocks.com"
      description: "This is your API mock endpoint. When called, it will simulate the behavior of your API."
      isPublished: true
    - url: "http://tal-bhough5520:8040/services/student-api"
      description: "Demo Environment"
      isPublished: true
    unsortedElementOrder:
    - "#/contract/resources/f055f7dd-f057-4889-b2d6-56edbe75010b"
    - "#/contract/resources/d5581043-6fcb-4dd3-a16d-43f7b4a68013"
    - "#/contract/types/f235080a-ad54-4462-a4e6-46cfe755c50d"
    - "#/contract/types/c7d2d295-77cd-40a0-8040-b9c4884b0232"
    resources:
      f055f7dd-f057-4889-b2d6-56edbe75010b:
        path: "/student/{id}/"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          "1aad8d54-ffdb-4184-baf0-8c8f806077f5":
            name: "Get by Student ID"
            method: "GET"
            description: |-
              Get Students using the Student ID
              _IbR7VOeQ-WbSw4qwMTJVXiPDASdY29NthZRLcc8wsLz6QVdJbessomjA8yLLNZ3
            responses:
              "9b8f8340-2d3b-4ea3-bff5-9def370afabd":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/c7d2d295-77cd-40a0-8040-b9c4884b0232"
                  mediaTypes:
                  - "application/json"
          bcba21bc-5c5a-4167-a32d-c0648d47e266:
            name: "Delete Student"
            method: "DELETE"
            description: "Delete the student by ID"
            responses:
              f9ae43a1-f6b4-491f-92eb-5f17e1525150:
                status: "202"
                description: "Status 202"
      d5581043-6fcb-4dd3-a16d-43f7b4a68013:
        path: "/student/"
        operations:
          "5fe40feb-6b5f-49b3-97c9-43d31a0f391a":
            name: "Get Students"
            method: "GET"
            description: "Operation to get a list of students which can be filtered by: \n* First Name\n* Last Name\n* Status,\n* Entry Term"
            tags:
            - "Students"
            - "List"
            - "API"
            - "Talend"
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
              "7aaeffcb-db5e-4051-b3c2-c55aea9949a7":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/c7d2d295-77cd-40a0-8040-b9c4884b0232"
                  examples:
                  - value: "{  \n   \"student\":[  \n      {  \n         \"studentId\":145003,\n         \"firstName\":\"Benjamin\",\n         \"middleName\":\"Woodrow\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"withdraw\",\n         \"entryTerm\":201702,\n         \"address\":\"539 Cleveland Ave.\",\n         \"city\":\"Helena\",\n         \"state\":\"Mississippi\",\n         \"zip\":3657\n      },\n      {  \n         \"studentId\":145013,\n         \"firstName\":\"Andrew\",\n         \"middleName\":\"Warren\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"accepted\",\n         \"entryTerm\":201701,\n         \"address\":\"1229 Bailard Avenue\",\n         \"city\":\"Trenton\",\n         \"state\":\"South Carolina\",\n         \"zip\":63959\n      },\n      {  \n         \"studentId\":145091,\n         \"firstName\":\"Millard\",\n         \"middleName\":\"Richard\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"enrolled\",\n         \"entryTerm\":201701,\n         \"address\":\"1090 Carpinteria North\",\n         \"city\":\"Providence\",\n         \"state\":\"Maine\",\n         \"zip\":57472\n      }\n   ]\n}"
                  mediaTypes:
                  - "application/json"
          bade2b95-96c3-4026-98cb-8ea415d3bef9:
            name: "Add a new Student"
            method: "POST"
            bodies:
            - type: "#/contract/types/c7d2d295-77cd-40a0-8040-b9c4884b0232"
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
              fbf549c2-0aac-4a4c-95dd-7d8bdd732174:
                status: "200"
                description: "Status 200"
    types:
      f235080a-ad54-4462-a4e6-46cfe755c50d:
        name: "applicantStatus"
        type: "STRING"
        description: "The Student Applicant Status"
        enum:
        - "accepted"
        - "denied"
        - "withdraw"
        - "enrolled"
      c7d2d295-77cd-40a0-8040-b9c4884b0232:
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
            type: "#/contract/types/f235080a-ad54-4462-a4e6-46cfe755c50d"
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
      fee3970b-fdfe-44a1-8e33-e025e2aac5ae:
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
        "name" : "KJB - Student API 1.0.0",
        "description" : "This is the offical API for trusted Student data at our institution.",
        "importedFrom" : "d7d4897b-ca68-453f-8cae-bc73d3587426"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "1aad8d54-ffdb-4184-baf0-8c8f806077f5",
          "name" : "Get by Student ID",
          "description" : "Get Students using the Student ID\n_IbR7VOeQ-WbSw4qwMTJVXiPDASdY29NthZRLcc8wsLz6QVdJbessomjA8yLLNZ3",
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
          "id" : "bcba21bc-5c5a-4167-a32d-c0648d47e266",
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
          "id" : "5fe40feb-6b5f-49b3-97c9-43d31a0f391a",
          "name" : "Get Students",
          "description" : "Operation to get a list of students which can be filtered by: \n* First Name\n* Last Name\n* Status,\n* Entry Term",
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
          "id" : "bade2b95-96c3-4026-98cb-8ea415d3bef9",
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
      "name" : "KJB - Student API 1.0.0",
      "importedFrom" : {
        "projectId" : "d7d4897b-ca68-453f-8cae-bc73d3587426"
      },
      "variables" : {
        "5c612f53-6d21-4e7d-aeda-e9b5475685d4" : {
          "name" : "BaseUrl",
          "value" : "https://lp1uhp3.us.api-mocks.com",
          "enabled" : true,
          "private" : false
        }
      }
    }, {
      "name" : "KJB - Student API 1.0.0",
      "importedFrom" : {
        "projectId" : "d7d4897b-ca68-453f-8cae-bc73d3587426"
      },
      "variables" : {
        "d0e84211-3f32-4928-af0a-99e88678cf7a" : {
          "name" : "BaseUrl",
          "value" : "http://tal-bhough5520:8040/services/student-api",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
