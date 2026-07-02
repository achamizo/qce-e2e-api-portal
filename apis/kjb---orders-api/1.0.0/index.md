---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "KJB - Orders API"
    version: "1.0.0"
    description: "No description"
    contact: {}
  contract:
    unsortedElementOrder:
    - "#/contract/resources/b2c981f9-53d8-4d8f-86bb-2b3d715d4444"
    - "#/contract/resources/b2bce5fb-305d-4866-8601-b211f5d9a585"
    - "#/contract/resources/748cb95f-787e-48b3-bab7-cbb6e3388a03"
    - "#/contract/types/a5974626-f775-402c-8250-edabd435d26a"
    - "#/contract/types/61a7308b-a488-49a3-a348-505c7bd9bc3f"
    resources:
      b2c981f9-53d8-4d8f-86bb-2b3d715d4444:
        path: "/northwind/orders/{id}/"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          "1a2692c9-698b-4e83-9fbf-fc9fbedac52a":
            name: "Get Order by ID"
            method: "GET"
            responses:
              "42e43dd0-6154-41f9-b091-0bfd2ed211fe":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/61a7308b-a488-49a3-a348-505c7bd9bc3f"
                  mediaTypes:
                  - "application/json"
              "0c6b1427-f77d-431d-8e1c-045dd1a3eb6a":
                status: "404"
                description: "Status 404"
                bodies:
                - type: "#/contract/types/a5974626-f775-402c-8250-edabd435d26a"
                  mediaTypes:
                  - "application/json"
          "3278a54d-99c5-4fff-b225-e0555d6ba0cb":
            name: "Delete Order"
            method: "DELETE"
            responses:
              e64f6847-47b0-4799-9f0a-56f535974926:
                status: "202"
                description: "Status 202"
      b2bce5fb-305d-4866-8601-b211f5d9a585:
        path: "/northwind/orders/"
        operations:
          "6bcf1902-0aa0-4e1b-bf8f-d372db08cb1f":
            name: "Put Order"
            method: "PUT"
            bodies:
            - type: "#/contract/types/61a7308b-a488-49a3-a348-505c7bd9bc3f"
              mediaTypes:
              - "application/json"
            responses:
              ec8dee00-0bc5-44ba-b686-74eba00ea084:
                status: "500"
                description: "Status 500"
                bodies:
                - type: "OBJECT"
                  examples:
                  - value: |-
                      {
                        "fault": {
                          "orderId": "10247",
                          "errorCode": "500",
                          "errorMessage": "Exception: ..."
                          }
                      }
                  mediaTypes:
                  - "application/json"
      "748cb95f-787e-48b3-bab7-cbb6e3388a03":
        path: "/northwind/orders/bulk/"
        operations:
          "330c9686-5682-4603-9edf-c175d0f5515b":
            name: "Put Orders BULK"
            method: "PUT"
            bodies:
            - type: "ARRAY"
              items:
                type: "#/contract/types/61a7308b-a488-49a3-a348-505c7bd9bc3f"
              mediaTypes:
              - "application/json"
            responses:
              ae1d214e-db35-48f3-b051-65d4b7b50af6:
                status: "500"
                description: "Status 500"
                bodies:
                - type: "OBJECT"
                  examples:
                  - value: |-
                      {
                        "faults": {
                          "rejectedCount": "8",
                          "fault": {
                            "errorCode": "500",
                            "errorMessage": "Exception: ..."
                          }
                        }
                      }
                  mediaTypes:
                  - "application/json"
    types:
      a5974626-f775-402c-8250-edabd435d26a:
        name: "Fault"
        type: "OBJECT"
        properties:
        - name: "fault"
          type: "OBJECT"
          properties:
          - name: "message"
            type: "STRING"
        examples:
        - value: |-
            {
                "fault": {
                    "message": "Could not find order ID: '10242'"
                }
            }
      "61a7308b-a488-49a3-a348-505c7bd9bc3f":
        name: "Orders_JSON"
        type: "OBJECT"
        properties:
        - name: "order"
          type: "OBJECT"
          properties:
          - name: "id"
            type: "NUMBER"
          - name: "cust_id"
            type: "STRING"
          - name: "emp_id"
            type: "NUMBER"
          - name: "order_dt"
            type: "STRING"
          - name: "required_dt"
            type: "STRING"
          - name: "shipping"
            type: "OBJECT"
            properties:
            - name: "ship_dt"
              type: "STRING"
            - name: "ship_via"
              type: "NUMBER"
            - name: "freight"
              type: "NUMBER"
            - name: "ship_name"
              type: "STRING"
            - name: "address"
              type: "OBJECT"
              properties:
              - name: "line_1"
                type: "STRING"
              - name: "line_2"
                type: "STRING"
              - name: "city"
                type: "STRING"
              - name: "postal_code"
                type: "NUMBER"
              - name: "region"
                type: "STRING"
              - name: "country"
                type: "STRING"
        examples:
        - value: "{\r\n    \"order\": {\r\n        \"id\": 10249,\r\n        \"cust_id\": \"TOMSP\",\r\n        \"emp_id\": 6,\r\n        \"order_dt\": \"05-07-2021\",\r\n        \"required_dt\": \"16-08-2021\",\r\n        \"shipping\": {\r\n            \"ship_dt\": \"10-07-2021\",\r\n            \"ship_via\": 1,\r\n            \"freight\": 11.61,\r\n            \"ship_name\": \"Toms Spezialit-ten\",\r\n            \"address\": {\r\n                \"line_1\": \"Luisenstr. 48\",\r\n                \"line_2\": \"\",\r\n                \"city\": \"M-nster\",\r\n                \"postal_code\": 44087,\r\n                \"region\": \"\",\r\n                \"country\": \"Germany\"\r\n            }\r\n        }\r\n    }\r\n}\r\n"
  components: {}
api-tryin: |-
  {
    "version" : 6,
    "entities" : [ {
      "entity" : {
        "type" : "Project",
        "name" : "KJB - Orders API 1.0.0",
        "description" : "No description",
        "importedFrom" : "c8bce67f-2c70-40df-a7f4-df2cfedf527d"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "1a2692c9-698b-4e83-9fbf-fc9fbedac52a",
          "name" : "Get Order by ID",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/northwind/orders/{id}/"
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
          "id" : "3278a54d-99c5-4fff-b225-e0555d6ba0cb",
          "name" : "Delete Order",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/northwind/orders/{id}/"
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
          "id" : "6bcf1902-0aa0-4e1b-bf8f-d372db08cb1f",
          "name" : "Put Order",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/northwind/orders/"
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
            "textBody" : "{\r\n    \"order\": {\r\n        \"id\": 10249,\r\n        \"cust_id\": \"TOMSP\",\r\n        \"emp_id\": 6,\r\n        \"order_dt\": \"05-07-2021\",\r\n        \"required_dt\": \"16-08-2021\",\r\n        \"shipping\": {\r\n            \"ship_dt\": \"10-07-2021\",\r\n            \"ship_via\": 1,\r\n            \"freight\": 11.61,\r\n            \"ship_name\": \"Toms Spezialit-ten\",\r\n            \"address\": {\r\n                \"line_1\": \"Luisenstr. 48\",\r\n                \"line_2\": \"\",\r\n                \"city\": \"M-nster\",\r\n                \"postal_code\": 44087,\r\n                \"region\": \"\",\r\n                \"country\": \"Germany\"\r\n            }\r\n        }\r\n    }\r\n}\r\n"
          }
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "330c9686-5682-4603-9edf-c175d0f5515b",
          "name" : "Put Orders BULK",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/northwind/orders/bulk/"
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
            "textBody" : ""
          }
        }
      } ]
    } ],
    "environments" : [ {
      "name" : "KJB - Orders API 1.0.0",
      "importedFrom" : {
        "projectId" : "c8bce67f-2c70-40df-a7f4-df2cfedf527d"
      },
      "variables" : {
        "f5a8e1b8-0618-4de9-9922-206662f7f803" : {
          "name" : "BaseUrl",
          "value" : "https://example.com",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
