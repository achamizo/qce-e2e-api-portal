---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "KJB - Custom - CRV"
    version: "1.0.0"
    description: "No description"
  contract:
    baseUrls:
    - url: "http://localhost:8042/services/crv_api"
      isPublished: true
    unsortedElementOrder:
    - "#/contract/resources/e30341d1-7176-4460-97dc-1627c1dacbe0"
    - "#/contract/resources/942ffa1c-9488-40de-8577-51136bba753a"
    - "#/contract/types/30be5cdd-1650-451d-830b-c4692db488fa"
    resources:
      e30341d1-7176-4460-97dc-1627c1dacbe0:
        path: "/invoice/{id}"
        pathVariables:
        - name: "id"
          type: "STRING"
          required: true
        operations:
          "9b136af2-e41b-42f7-a28f-b726255ca496":
            name: "GetInvoiceInfo"
            method: "GET"
            description: "Obtener información de una factura específica. Esta API recibe como parámetro el **id** de la factura y devuelve el detalle de la misma."
            tags:
            - "Invoice"
            - "API"
            - "REST"
            responses:
              "4b166397-c0c8-4ef4-a205-f59c0556b9d8":
                status: "200"
                description: "Estatus 200 si la factura es encontrada"
                bodies:
                - type: "#/contract/types/30be5cdd-1650-451d-830b-c4692db488fa"
                  mediaTypes:
                  - "application/json"
              "186e6214-78d2-4a20-b78b-bf9e9196c1ab":
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
      "942ffa1c-9488-40de-8577-51136bba753a":
        path: "/invoice"
        operations:
          "324c4bb6-6f11-419a-a1b7-0b6c1e2066ab":
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
              ba8a33a2-7185-43a1-a7da-b2b0aab11114:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/30be5cdd-1650-451d-830b-c4692db488fa"
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
      "30be5cdd-1650-451d-830b-c4692db488fa":
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
        "importedFrom" : "9fe81817-863e-46b0-a32f-19875b10f407"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "9b136af2-e41b-42f7-a28f-b726255ca496",
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
          "id" : "324c4bb6-6f11-419a-a1b7-0b6c1e2066ab",
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
        "projectId" : "9fe81817-863e-46b0-a32f-19875b10f407"
      },
      "variables" : {
        "74177fe5-81f5-4ecb-a46e-7d86ab3e7de8" : {
          "name" : "BaseUrl",
          "value" : "http://localhost:8042/services/crv_api",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
