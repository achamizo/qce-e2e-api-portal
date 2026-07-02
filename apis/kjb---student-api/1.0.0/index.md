---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "KJB - Student API"
    version: "1.0.0"
  contract:
    baseUrls:
    - url: "https://lp1uhp3.us.api-mocks.com"
      description: "This is your API mock endpoint. When called, it will simulate the behavior of your API."
      isPublished: true
    - url: "http://tal-bhough5520:8040/services/student-api"
      description: "Demo Environment"
      isPublished: true
    unsortedElementOrder:
    - "#/contract/resources/0e5bb39a-7c65-487c-bfd0-e511e1bf8772"
    - "#/contract/resources/00b5b8fa-8e29-41f4-bd91-df87670f0015"
    - "#/contract/types/acc15045-a9e9-413e-bff7-b2af4907883e"
    - "#/contract/types/da8b7cdd-a822-4dca-a725-4c3a10e7942b"
    resources:
      "0e5bb39a-7c65-487c-bfd0-e511e1bf8772":
        path: "/student/{id}/"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          "280e686b-5769-49b5-a9e3-2811c0ffce9c":
            name: "Get by Student ID"
            method: "GET"
            description: |-
              Get Students using the Student ID
              _IbR7VOeQ-WbSw4qwMTJVXiPDASdY29NthZRLcc8wsLz6QVdJbessomjA8yLLNZ3
            responses:
              e5c87048-6057-450c-9a00-41cf6d92e966:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/da8b7cdd-a822-4dca-a725-4c3a10e7942b"
                  mediaTypes:
                  - "application/json"
          a91e0b07-dc1e-43a4-847b-08733a8a7dd9:
            name: "Delete Student"
            method: "DELETE"
            description: "Delete the student by ID"
            responses:
              ead418bd-45aa-4568-8459-ac5bd029ba57:
                status: "202"
                description: "Status 202"
      "00b5b8fa-8e29-41f4-bd91-df87670f0015":
        path: "/student/"
        operations:
          ff7fe77c-9303-43fd-b26e-79c627ee5938:
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
              "53cb139c-164a-4f67-91c1-cf6e96f44202":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/da8b7cdd-a822-4dca-a725-4c3a10e7942b"
                  examples:
                  - value: "{  \n   \"student\":[  \n      {  \n         \"studentId\":145003,\n         \"firstName\":\"Benjamin\",\n         \"middleName\":\"Woodrow\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"withdraw\",\n         \"entryTerm\":201702,\n         \"address\":\"539 Cleveland Ave.\",\n         \"city\":\"Helena\",\n         \"state\":\"Mississippi\",\n         \"zip\":3657\n      },\n      {  \n         \"studentId\":145013,\n         \"firstName\":\"Andrew\",\n         \"middleName\":\"Warren\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"accepted\",\n         \"entryTerm\":201701,\n         \"address\":\"1229 Bailard Avenue\",\n         \"city\":\"Trenton\",\n         \"state\":\"South Carolina\",\n         \"zip\":63959\n      },\n      {  \n         \"studentId\":145091,\n         \"firstName\":\"Millard\",\n         \"middleName\":\"Richard\",\n         \"lastName\":\"Fillmore\",\n         \"applicantStatus\":\"enrolled\",\n         \"entryTerm\":201701,\n         \"address\":\"1090 Carpinteria North\",\n         \"city\":\"Providence\",\n         \"state\":\"Maine\",\n         \"zip\":57472\n      }\n   ]\n}"
                  mediaTypes:
                  - "application/json"
          "6a5b02a8-4b44-443e-bb48-ba0bb1c0c0cd":
            name: "Add a new Student"
            method: "POST"
            bodies:
            - type: "#/contract/types/da8b7cdd-a822-4dca-a725-4c3a10e7942b"
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
              ba49af60-3231-4e53-814a-e1bd7daab0de:
                status: "200"
                description: "Status 200"
    types:
      acc15045-a9e9-413e-bff7-b2af4907883e:
        name: "applicantStatus"
        type: "STRING"
        description: "The Student Applicant Status"
        enum:
        - "accepted"
        - "denied"
        - "withdraw"
        - "enrolled"
      da8b7cdd-a822-4dca-a725-4c3a10e7942b:
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
            type: "#/contract/types/acc15045-a9e9-413e-bff7-b2af4907883e"
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
      "99fe6688-8c25-495c-a1d7-1f60cefa64e2":
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
        "importedFrom" : "b423455e-3b1b-4268-ba20-2292565e2f45"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "280e686b-5769-49b5-a9e3-2811c0ffce9c",
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
          "id" : "a91e0b07-dc1e-43a4-847b-08733a8a7dd9",
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
          "id" : "ff7fe77c-9303-43fd-b26e-79c627ee5938",
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
          "id" : "6a5b02a8-4b44-443e-bb48-ba0bb1c0c0cd",
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
        "projectId" : "b423455e-3b1b-4268-ba20-2292565e2f45"
      },
      "variables" : {
        "ae292d52-8539-4dbf-861d-890eceb531af" : {
          "name" : "BaseUrl",
          "value" : "https://lp1uhp3.us.api-mocks.com",
          "enabled" : true,
          "private" : false
        }
      }
    }, {
      "name" : "KJB - Student API 1.0.0",
      "importedFrom" : {
        "projectId" : "b423455e-3b1b-4268-ba20-2292565e2f45"
      },
      "variables" : {
        "c525404c-f5ed-457f-8f91-72c0acb6b7cf" : {
          "name" : "BaseUrl",
          "value" : "http://tal-bhough5520:8040/services/student-api",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
