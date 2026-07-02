---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "KJB - Custom - CRV"
    version: "1.0.0"
    description: "No description"
    contact: {}
  contract:
    baseUrls:
    - url: "http://localhost:8042/services/crv_api"
      isPublished: true
    unsortedElementOrder:
    - "#/contract/resources/2f58fa59-2e39-440d-b794-5ccb42ff6999"
    - "#/contract/resources/668e3fe8-d63c-45e7-aacc-5676999bee13"
    - "#/contract/types/c61e2325-b38f-413e-bfc6-c6ce34b0ffec"
    resources:
      "2f58fa59-2e39-440d-b794-5ccb42ff6999":
        path: "/invoice/{id}"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          "4e867493-a140-4d0b-b7f2-d6164e3359f2":
            name: "GetInvoiceInfo"
            method: "GET"
            description: "Obtener información de una factura específica. Esta API recibe como parámetro el **id** de la factura y devuelve el detalle de la misma."
            tags:
            - "Invoice"
            - "API"
            - "REST"
            responses:
              "39f10ceb-c76e-4793-970b-d5d12a209aa3":
                status: "200"
                description: "Estatus 200 si la factura es encontrada"
                bodies:
                - type: "#/contract/types/c61e2325-b38f-413e-bfc6-c6ce34b0ffec"
                  mediaTypes:
                  - "application/json"
              e846fdd8-06a0-4eff-8f80-113dfcaa2994:
                status: "404"
                description: "Invoice Not Found"
                bodies:
                - type: "OBJECT"
                  examples:
                  - value: |-
                      {
                          "error": [
                              "mesage": "The invoice 1111111 was not found"
                        ]
                      }
                  mediaTypes:
                  - "application/json"
      "668e3fe8-d63c-45e7-aacc-5676999bee13":
        path: "/invoice"
        operations:
          dc22844c-9170-4de0-a0d8-728935bf5d32:
            name: "GetSupplierInvoices"
            method: "GET"
            tags:
            - "Invoice"
            - "API"
            - "REST"
            - "Supplier"
            queryParameters:
            - name: "supplierId"
              type: "STRING"
              description: "Supplier ID"
              examples:
              - value: "1111111"
            - name: "fromDate"
              type: "STRING"
              description: "From Date"
              examples:
              - value: "2025-01-01"
            - name: "toDate"
              type: "STRING"
              description: "To Date"
              examples:
              - value: "2025-01-31"
            responses:
              b025980c-77c1-4489-a0f7-94b681a13468:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/c61e2325-b38f-413e-bfc6-c6ce34b0ffec"
                  examples:
                  - value: |-
                      {
                        "Invoice": [
                              {
                                  "supplierId": 1111111,
                                  "supplierName": "Emisor Anonimo_1111111",
                                  "customerId": 19999999,
                                  "customerName": "Receptor Anonimo_29999999",
                                  "number": "FV6076230706",
                                  "date": "2024-02-10",
                                  "subTotal": "34,874.00",
                                  "total": "41,500.00"
                              },
                              {
                                  "supplierId": 2222222,
                                  "supplierName": "Emisor Anonimo_2222222",
                                  "customerId": 29999999,
                                  "customerName": "Receptor Anonimo_29999999",
                                  "number": "FV6076230706",
                                  "date": "2024-02-10",
                                  "subTotal": "34,874.00",
                                  "total": "41,500.00"
                              },
                              {
                                  "supplierId": 3333333,
                                  "supplierName": "Emisor Anonimo_3333333",
                                  "customerId": 39999999,
                                  "customerName": "Receptor Anonimo_29999999",
                                  "number": "FV6076230706",
                                  "date": "2024-02-10",
                                  "subTotal": "34,874.00",
                                  "total": "41,500.00"
                              }
                          ]
                      }
                  mediaTypes:
                  - "application/json"
    types:
      c61e2325-b38f-413e-bfc6-c6ce34b0ffec:
        name: "Invoice_JSON"
        type: "OBJECT"
        description: "Invoice JSON Structure"
        properties:
        - name: "Invoice"
          type: "OBJECT"
          description: "Invoice Information"
          properties:
          - name: "supplierId"
            type: "NUMBER"
            description: "Supplier ID"
            minimum: 1
            maximum: 15
            examples:
            - value: 1111111
          - name: "supplierName"
            type: "STRING"
            description: "Supplier Name"
            minLength: 1
            maxLength: 50
            examples:
            - value: "Emisor Anonimo_1111111"
          - name: "customerId"
            type: "NUMBER"
            description: "Customer ID"
            minimum: 1
            maximum: 15
            examples:
            - value: 29999999
          - name: "customerName"
            type: "STRING"
            description: "Customer Name"
            minLength: 1
            maxLength: 50
            examples:
            - value: "Receptor Anonimo_29999999"
          - name: "number"
            type: "STRING"
            description: "Invoice Number"
            minLength: 1
            maxLength: 15
            examples:
            - value: "FV6076230706"
          - name: "date"
            type: "STRING"
            description: "Invoice Date"
            minLength: 10
            maxLength: 10
            pattern: "YYYY-MM-DD"
            examples:
            - value: "2024-02-10"
          - name: "subTotal"
            type: "STRING"
            description: "Invoice Subtotal Amount"
            examples:
            - value: "34,874.00"
          - name: "total"
            type: "STRING"
            description: "Invoice Total Amount"
            examples:
            - value: "41,500.00"
        examples:
        - value: |-
            {
              "Invoice": {
                "supplierId": 1111111,
                "supplierName": "Emisor Anonimo_1111111",
                "customerId": 29999999,
                "customerName": "Receptor Anonimo_29999999",
                "number": "FV6076230706",
                "date": "2024-02-10",
                "subTotal": "34,874.00",
                "total": "41,500.00"
              }
            }
  components: {}
api-tryin: |-
  {
    "version" : 6,
    "entities" : [ {
      "entity" : {
        "type" : "Project",
        "name" : "KJB - Custom - CRV 1.0.0",
        "description" : "No description",
        "importedFrom" : "0a41c1b0-3fb1-47ee-9a7b-2cccb8d644dd"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "4e867493-a140-4d0b-b7f2-d6164e3359f2",
          "name" : "GetInvoiceInfo",
          "description" : "Obtener información de una factura específica. Esta API recibe como parámetro el **id** de la factura y devuelve el detalle de la misma.",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/invoice/{id}"
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
          "id" : "dc22844c-9170-4de0-a0d8-728935bf5d32",
          "name" : "GetSupplierInvoices",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/invoice",
            "query" : {
              "delimiter" : "&",
              "items" : [ {
                "name" : "supplierId",
                "value" : "1111111",
                "enabled" : false
              }, {
                "name" : "fromDate",
                "value" : "2025-01-01",
                "enabled" : false
              }, {
                "name" : "toDate",
                "value" : "2025-01-31",
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
      } ]
    } ],
    "environments" : [ {
      "name" : "KJB - Custom - CRV 1.0.0",
      "importedFrom" : {
        "projectId" : "0a41c1b0-3fb1-47ee-9a7b-2cccb8d644dd"
      },
      "variables" : {
        "80b8b60b-dc91-46b9-adb4-e56b242a9b51" : {
          "name" : "BaseUrl",
          "value" : "http://localhost:8042/services/crv_api",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
