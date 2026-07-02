---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "KJB - Store"
    version: "1.0.0"
    description: "No description"
  contract:
    baseUrls:
    - url: "https://jsonplaceholder.typicode.com/todos/1"
      description: "Test"
      isPublished: true
    unsortedElementOrder:
    - "#/contract/resources/adc89bc7-a39d-4b1e-a4c3-ec8100c53e68"
    - "#/contract/resources/81590c77-b8fd-4501-a35b-388a091f40a2"
    resources:
      adc89bc7-a39d-4b1e-a4c3-ec8100c53e68:
        path: "/books"
        operations:
          "7b56aa8f-09ee-4756-b2c4-2a5f040f904e":
            name: "Get Books"
            method: "GET"
            description: "Get books list"
            responses:
              "849e3cad-8d2f-4d90-aa3a-2362a58f0bb2":
                status: "200"
                description: "Status 200"
      "81590c77-b8fd-4501-a35b-388a091f40a2":
        path: "/movies"
        operations:
          f2d776c2-3eaf-4ec0-a3a8-4eaa3a8d7692:
            name: "Get Movies"
            method: "GET"
            responses:
              e7caae67-86d0-449e-896b-9fb525da655c:
                status: "200"
                description: "Status 200"
          bc949ffd-1d04-48ce-81c5-4d501853ddc3:
            name: "New Movie"
            method: "POST"
            responses:
              "00232d2f-435e-4018-b28a-7f91a2885142":
                status: "200"
                description: "Status 200"
          "240a7767-e377-440f-96dc-10d455621fa1":
            name: "Update Movie"
            method: "PUT"
            responses:
              f906a938-55c7-48a5-93bf-59a2a6f0d83c:
                status: "200"
                description: "Status 200"
          "1ada0b85-21df-49a8-a45e-2d4e3d6edba8":
            name: "Delete Movie"
            method: "DELETE"
            responses:
              b010fe47-2ed2-4895-9ca4-6afef2c51535:
                status: "200"
                description: "Status 200"
          "3389a84e-0161-4fc4-b551-a618999946f0":
            name: "Update Movie Name"
            method: "PATCH"
            responses:
              "7184556a-c9d2-44d8-bce1-04b2aa499beb":
                status: "200"
                description: "Status 200"
  components: {}
api-tryin: |-
  {
    "version" : 6,
    "entities" : [ {
      "entity" : {
        "type" : "Project",
        "name" : "KJB - Store 1.0.0",
        "description" : "No description",
        "importedFrom" : "239f6bf8-ca7a-42f8-aa34-07c6bff0fb2e"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "7b56aa8f-09ee-4756-b2c4-2a5f040f904e",
          "name" : "Get Books",
          "description" : "Get books list",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/books"
          },
          "method" : {
            "link" : "",
            "name" : "GET"
          },
          "headers" : [ ],
          "headersType" : "Form"
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "f2d776c2-3eaf-4ec0-a3a8-4eaa3a8d7692",
          "name" : "Get Movies",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/movies"
          },
          "method" : {
            "link" : "",
            "name" : "GET"
          },
          "headers" : [ ],
          "headersType" : "Form"
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "bc949ffd-1d04-48ce-81c5-4d501853ddc3",
          "name" : "New Movie",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/movies"
          },
          "method" : {
            "link" : "",
            "name" : "POST"
          },
          "headers" : [ ],
          "headersType" : "Form"
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "240a7767-e377-440f-96dc-10d455621fa1",
          "name" : "Update Movie",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/movies"
          },
          "method" : {
            "link" : "",
            "name" : "PUT"
          },
          "headers" : [ ],
          "headersType" : "Form"
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "1ada0b85-21df-49a8-a45e-2d4e3d6edba8",
          "name" : "Delete Movie",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/movies"
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
          "id" : "3389a84e-0161-4fc4-b551-a618999946f0",
          "name" : "Update Movie Name",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/movies"
          },
          "method" : {
            "link" : "",
            "name" : "PATCH"
          },
          "headers" : [ ],
          "headersType" : "Form"
        }
      } ]
    } ],
    "environments" : [ {
      "name" : "KJB - Store 1.0.0",
      "importedFrom" : {
        "projectId" : "239f6bf8-ca7a-42f8-aa34-07c6bff0fb2e"
      },
      "variables" : {
        "ae9e6568-3518-42b9-bf76-e3e70e6a9bb2" : {
          "name" : "BaseUrl",
          "value" : "https://jsonplaceholder.typicode.com/todos/1",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
