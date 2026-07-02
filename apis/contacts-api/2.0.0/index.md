---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "Contacts API"
    version: "2.0.0"
    description: "An API for keeping track of your contacts and the companies they work for."
    license: {}
    contact: {}
    termsOfService: ""
  contract:
    mediaTypes:
    - "application/json"
    sections:
    - name: "General"
      elementOrder:
      - "#/contract/texts/364c2342-b829-485b-a5bd-1ee9e8b17d03"
      - "#/contract/texts/f95e20a7-cc50-4785-ae80-165ca0d56b3a"
      - "#/contract/types/44d46f38-664d-476a-8ea1-ea8d83cfab2c"
    - name: "Contacts"
      elementOrder:
      - "#/contract/resources/be7aa06e-5e22-48b0-9048-7aac22ff377e"
      - "#/contract/resources/ee3ccc0f-3cda-4754-ac58-73163a8bf532"
      - "#/contract/types/1a064cf2-7e06-4318-896b-6f19aff83e2c"
    - name: "Companies"
      elementOrder:
      - "#/contract/resources/3a84910a-ca78-428d-b7ff-25fcffc75b49"
      - "#/contract/resources/19b5343d-d3a2-4e4b-86e4-391f2966b948"
      - "#/contract/types/61c439e2-e0b4-4236-99f5-fcd62c915107"
    securitySchemes:
      "8948e1b0-de19-487e-bd1e-c272a236b267":
        name: "HTTP_BASIC"
        type: "basic"
        description: "All GET methods are public, meaning that *you can read all the data*. Write operations require authentication and therefore are forbidden to the general public."
        describedBy: {}
    resources:
      "3a84910a-ca78-428d-b7ff-25fcffc75b49":
        path: "/companies/"
        section: "#/contract/sections/d99ce30d-197b-4b4e-99fb-6fa803d78c21"
        operations:
          "35002bf8-b8f8-4b2d-b08c-32416ed7a739":
            name: "Load the list of Companies"
            method: "GET"
            description: "Loads a list of Company."
            tags:
            - "Companies"
            queryParameters:
            - type: "#/components/queryParameters/343a97d5-3870-46d0-b5f6-f647907cf10d"
            - type: "#/components/queryParameters/acb5ba96-9238-4c9b-807d-f5661deb4baf"
            - type: "#/components/queryParameters/8ef04c15-4c18-4f78-aac0-75ce81b87f8a"
            - name: "name"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field `name`"
              examples:
              - value: "George Street Brewery"
            responses:
              dad4029f-988f-4e6e-a98f-8fafec7c04fb:
                status: "200"
                description: "Status 200"
                headers:
                - type: "#/components/headers/66399869-353d-4f16-9190-c2dd504996f5"
                - type: "#/components/headers/a3e96163-5f99-4492-9f11-f6d021815504"
                - type: "#/components/headers/ec640144-11a2-4fe8-9077-abd1bc7d34ef"
                - type: "#/components/headers/88115c97-1951-4f16-9a40-6564b6ba571d"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/61c439e2-e0b4-4236-99f5-fcd62c915107"
                  examples:
                  - value: |-
                      [{
                        "id": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f",
                        "name": "George Street Brewery",
                        "address":{
                          "street": "2 place de la Defense",
                          "zipcode": "92053",
                          "city": "Paris"
                        },
                        "tags":[
                          "brewery",
                          "beer",
                          "ale"
                        ]
                      }]
              "37236c73-a5c4-4cf5-acde-b1fc82cbd5cc":
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/c02c78ae-759c-450c-8da0-0f5abe356970"
          c4c264f7-a7fa-4a56-b6b5-0a0d7895fbdc:
            name: "Create a new Company"
            method: "POST"
            description: "Adds a Company."
            tags:
            - "Companies"
            securedBy:
            - scheme: "#/contract/securitySchemes/8948e1b0-de19-487e-bd1e-c272a236b267"
              scopes: []
            bodies:
            - type: "#/contract/types/61c439e2-e0b4-4236-99f5-fcd62c915107"
              examples:
              - value: |-
                  {
                    "name": "George Street Brewery",
                    "address":{
                      "street": "2 place de la Defense",
                      "zipcode": "92053",
                      "city": "Paris"
                    },
                    "tags":[
                      "brewery",
                      "beer",
                      "ale"
                    ]
                  }
            responses:
              "70a99330-0a76-416e-af26-864570652d30":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/61c439e2-e0b4-4236-99f5-fcd62c915107"
                  examples:
                  - value: |-
                      {
                        "id": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f",
                        "name": "George Street Brewery",
                        "address":{
                          "street": "2 place de la Defense",
                          "zipcode": "92053",
                          "city": "Paris"
                        },
                        "tags":[
                          "brewery",
                          "beer",
                          "ale"
                        ]
                      }
      "19b5343d-d3a2-4e4b-86e4-391f2966b948":
        path: "/companies/{companyid}"
        section: "#/contract/sections/d99ce30d-197b-4b4e-99fb-6fa803d78c21"
        pathVariables:
        - type: "#/components/pathVariables/93d46685-af4a-492c-87c6-a5b155f97c7a"
        operations:
          af53c32e-218d-4d7d-b29a-6d29ebd3669d:
            name: "Load a Company"
            method: "GET"
            description: "Loads a Company."
            tags:
            - "Companies"
            responses:
              eb9557ca-3896-4677-80d5-d19fa0615d44:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/61c439e2-e0b4-4236-99f5-fcd62c915107"
                  examples:
                  - value: |-
                      {
                        "id": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f",
                        "name": "George Street Brewery",
                        "address":{
                          "street": "2 place de la Defense",
                          "zipcode": "92053",
                          "city": "Paris"
                        },
                        "tags":[
                          "brewery",
                          "beer",
                          "ale"
                        ]
                      }
              "64f04647-d611-443a-8800-50677baebcb6":
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/c02c78ae-759c-450c-8da0-0f5abe356970"
          "6675ed5a-57f0-463a-8b03-cae807aedd81":
            name: "Update a Company"
            method: "PUT"
            description: "Updates a Company."
            tags:
            - "Companies"
            securedBy:
            - scheme: "#/contract/securitySchemes/8948e1b0-de19-487e-bd1e-c272a236b267"
              scopes: []
            bodies:
            - type: "#/contract/types/61c439e2-e0b4-4236-99f5-fcd62c915107"
              examples:
              - value: |-
                  {
                    "name": "George Street Brewery",
                    "address":{
                      "street": "2 place de la Defense",
                      "zipcode": "92053",
                      "city": "Paris"
                    },
                    "tags":[
                      "brewery",
                      "beer",
                      "ale"
                    ]
                  }
            responses:
              "64a8326e-dba8-4a14-bae7-a70d55cbf7aa":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/61c439e2-e0b4-4236-99f5-fcd62c915107"
                  examples:
                  - value: |-
                      {
                        "id": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f",
                        "name": "George Street Brewery",
                        "address":{
                          "street": "2 place de la Defense",
                          "zipcode": "92053",
                          "city": "Paris"
                        },
                        "tags":[
                          "brewery",
                          "beer",
                          "ale"
                        ]
                      }
          d879d187-48c8-4286-b11c-968eb381659f:
            name: "Delete a Company"
            method: "DELETE"
            description: "Deletes a Company."
            tags:
            - "Companies"
            securedBy:
            - scheme: "#/contract/securitySchemes/8948e1b0-de19-487e-bd1e-c272a236b267"
              scopes: []
            responses:
              e1f19250-7114-4abd-9ca9-0a8833bf2566:
                status: "200"
                description: "Status 200"
      be7aa06e-5e22-48b0-9048-7aac22ff377e:
        path: "/contacts/"
        section: "#/contract/sections/7126834d-18cc-40bc-87c8-fe12a240213e"
        operations:
          cc629628-40d4-4bfb-9a66-ff6b48b45e7e:
            name: "Get the list of Contacts"
            method: "GET"
            description: "Loads a list of Contacts."
            tags:
            - "Contacts"
            queryParameters:
            - type: "#/components/queryParameters/343a97d5-3870-46d0-b5f6-f647907cf10d"
            - type: "#/components/queryParameters/acb5ba96-9238-4c9b-807d-f5661deb4baf"
            - type: "#/components/queryParameters/8ef04c15-4c18-4f78-aac0-75ce81b87f8a"
            - name: "firstName"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field `firstName`"
              examples:
              - value: "John"
            - name: "lastName"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field `lastName`"
              examples:
              - value: "Doe"
            - name: "active"
              type: "BOOLEAN"
              description: "Allows to filter the collection of results by the value of field `active`"
              examples:
              - value: true
              - value: false
            - name: "company"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field `company`"
              examples:
              - value: "0e8c9fb0-ad98-11e6-bf2e-47644ada7c0f"
            responses:
              "96d67be5-646f-45a4-a508-9d59c608e3b2":
                status: "200"
                description: "Status 200"
                headers:
                - type: "#/components/headers/66399869-353d-4f16-9190-c2dd504996f5"
                - type: "#/components/headers/a3e96163-5f99-4492-9f11-f6d021815504"
                - type: "#/components/headers/ec640144-11a2-4fe8-9077-abd1bc7d34ef"
                - type: "#/components/headers/88115c97-1951-4f16-9a40-6564b6ba571d"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/1a064cf2-7e06-4318-896b-6f19aff83e2c"
                  examples:
                  - value: |-
                      [{
                        "id": "0e8dd830-ad98-11e6-bf2e-47644ada7c0f",
                        "firstName": "John",
                        "lastName": "Smith",
                        "birthday": 152755200000,
                        "active": true,
                        "rank": 1,
                        "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                      }]
              "3480ee1a-d7f8-48cd-91a3-fe4581df15a8":
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/c02c78ae-759c-450c-8da0-0f5abe356970"
          "81279661-0296-403b-9d85-90dde28dde89":
            name: "Create a Contact"
            method: "POST"
            description: "Adds a Contact."
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/8948e1b0-de19-487e-bd1e-c272a236b267"
              scopes: []
            bodies:
            - type: "#/contract/types/1a064cf2-7e06-4318-896b-6f19aff83e2c"
              examples:
              - value: |-
                  {
                    "firstName": "John",
                    "lastName": "Smith",
                    "birthday": 152755200000,
                    "active": true,
                    "rank": 1,
                    "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                  }
            responses:
              "6323d199-1b67-46a0-825c-a6c2f638d1de":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/1a064cf2-7e06-4318-896b-6f19aff83e2c"
                  examples:
                  - value: |-
                      {
                        "id": "0e8dd830-ad98-11e6-bf2e-47644ada7c0f",
                        "firstName": "John",
                        "lastName": "Smith",
                        "birthday": 152755200000,
                        "active": true,
                        "rank": 1,
                        "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                      }
      ee3ccc0f-3cda-4754-ac58-73163a8bf532:
        path: "/contacts/{contactid}"
        section: "#/contract/sections/7126834d-18cc-40bc-87c8-fe12a240213e"
        pathVariables:
        - type: "#/components/pathVariables/0d094acb-f51d-44ff-8062-077d2678a342"
        operations:
          aa4296c1-9992-4ade-a8a2-9b19ff94c2a9:
            name: "Load a Contact"
            method: "GET"
            description: "Loads a Contact."
            tags:
            - "Contacts"
            responses:
              "81f5cf74-1842-4977-adac-76c10c39f6a4":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/1a064cf2-7e06-4318-896b-6f19aff83e2c"
                  examples:
                  - value: |-
                      {
                        "id": "0e8dd830-ad98-11e6-bf2e-47644ada7c0f",
                        "firstName": "John",
                        "lastName": "Smith",
                        "birthday": 152755200000,
                        "active": true,
                        "rank": 1,
                        "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                      }
              "5b0ac473-d06c-4141-8f36-caefb441ec08":
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/c02c78ae-759c-450c-8da0-0f5abe356970"
          b0d32bd1-880c-4425-965d-5b741428175b:
            name: "Update a Contact"
            method: "PUT"
            description: "Updates a Contact."
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/8948e1b0-de19-487e-bd1e-c272a236b267"
              scopes: []
            bodies:
            - type: "#/contract/types/1a064cf2-7e06-4318-896b-6f19aff83e2c"
              examples:
              - value: |-
                  {
                    "firstName": "John",
                    "lastName": "Smith",
                    "birthday": 152755200000,
                    "active": true,
                    "rank": 1,
                    "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                  }
            responses:
              f0b633a0-700a-4c25-9cce-b8114ec659e3:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/1a064cf2-7e06-4318-896b-6f19aff83e2c"
                  examples:
                  - value: |-
                      {
                        "id": "0e8dd830-ad98-11e6-bf2e-47644ada7c0f",
                        "firstName": "John",
                        "lastName": "Smith",
                        "birthday": 152755200000,
                        "active": true,
                        "rank": 1,
                        "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                      }
          b4b24e5e-1eda-409e-896c-fd9a44430075:
            name: "Delete a Contact"
            method: "DELETE"
            description: "Deletes a Contact."
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/8948e1b0-de19-487e-bd1e-c272a236b267"
              scopes: []
            responses:
              "7b21f073-49c1-483a-99e0-5e5011ec89ba":
                status: "200"
                description: "Status 200"
    types:
      "61c439e2-e0b4-4236-99f5-fcd62c915107":
        name: "Company"
        type: "OBJECT"
        description: "The datatype of a Company"
        section: "#/contract/sections/d99ce30d-197b-4b4e-99fb-6fa803d78c21"
        properties:
        - name: "id"
          type: "STRING"
          description: "Auto-generated primary key field"
          required: true
        - name: "name"
          type: "STRING"
          required: true
        - name: "tags"
          type: "ARRAY"
          items:
            type: "STRING"
            pattern: "[a-zA-Z]+"
          examples:
          - value: "[\"brewery\", \"beer\", \"ale\"]"
        - name: "address"
          type: "OBJECT"
          required: true
          properties:
          - name: "street"
            type: "STRING"
            required: true
          - name: "city"
            type: "STRING"
            required: true
          - name: "zipcode"
            type: "STRING"
            required: true
            pattern: "[0-9]*"
        examples:
        - value: |-
            {
              "id": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f",
              "name": "George Street Brewery",
              "address":{
                "street": "2 place de la Defense",
                "zipcode": "92053",
                "city": "Paris"
              },
              "tags":[
                "brewery",
                "beer",
                "ale"
              ]
            }
      "1a064cf2-7e06-4318-896b-6f19aff83e2c":
        name: "Contact"
        type: "OBJECT"
        description: "The datatype of a Contact"
        section: "#/contract/sections/7126834d-18cc-40bc-87c8-fe12a240213e"
        properties:
        - name: "id"
          type: "STRING"
          description: "Auto-generated primary key field"
          required: true
          examples:
          - value: "0e8ffb10-ad98-11e6-bf2e-47644ada7c0f"
        - name: "firstName"
          type: "STRING"
          required: true
          examples:
          - value: "Kurt"
        - name: "lastName"
          type: "STRING"
          required: true
          examples:
          - value: "Williams"
        - name: "birthday"
          type: "INTEGER"
          format: "INT64"
          description: "Birthday as unix timestamp (in ms)"
          examples:
          - value: 173664000000
          - value: 383270400000
        - name: "active"
          type: "BOOLEAN"
          default: true
        - name: "rank"
          type: "INTEGER"
          format: "INT32"
          minimum: 1
          examples:
          - value: 1
          - value: 2
          - value: 3
        - name: "company"
          type: "STRING"
          description: "This property is a reference to a Company."
          examples:
          - value: "0e8c9fb0-ad98-11e6-bf2e-47644ada7c0f"
        examples:
        - value: |-
            {
              "id": "0e8dd830-ad98-11e6-bf2e-47644ada7c0f",
              "firstName": "John",
              "lastName": "Smith",
              "birthday": 152755200000,
              "active": true,
              "rank": 1,
              "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
            }
      "44d46f38-664d-476a-8ea1-ea8d83cfab2c":
        name: "Error"
        type: "OBJECT"
        description: "This general error structure is used throughout this API."
        section: "#/contract/sections/1a36893d-2974-4bf6-a346-be9e7d238ef1"
        properties:
        - name: "code"
          type: "INTEGER"
          required: true
          minimum: 400
          maximum: 599
        - name: "description"
          type: "STRING"
          examples:
          - value: "Bad query parameter [$size]: Invalid integer value [abc]"
          - value: "The server understood the request, but is refusing to fulfill it"
        - name: "reasonPhrase"
          type: "STRING"
          examples:
          - value: "Bad Request"
          - value: "Forbidden"
        examples:
        - value: "{\"code\": 400, \"description\": \"Bad query parameter [$size]: Invalid integer value [abc]\", \"reasonPhrase\": \"Bad Request\"}"
    texts:
      "364c2342-b829-485b-a5bd-1ee9e8b17d03":
        title: "Authentication"
        content: |-
          This API is secured using Basic Authentication.

          All **read operations are open** and don't require authentication. However, all **write operations require authentication**.
        section: "#/contract/sections/1a36893d-2974-4bf6-a346-be9e7d238ef1"
      f95e20a7-cc50-4785-ae80-165ca0d56b3a:
        title: "Error handling"
        content: |-
          This API uses standard HTTP status codes to indicate the status of a response.

          There are two main categories of error responses. Each have a different response payload structure.

          * Simple errors
          * Detailed errors


          # Simple errors

          | Name | Code | Description |
          | -------- | -------- | -------- |
          | Bad request     | 400     | The request was unacceptable.     |
          | Unauthorized     | 401     | The request has not been applied because it lacks valid authentication credentials for the target resource.     |
          | Forbidden     | 403     | The server understood the request, but is refusing to fulfill it.     |
          | Not Found     | 404     | The server has not found anything matching the request URI.     |
          | Not acceptable     | 406     | The server cannot return a response in the format that was requested by the client.     |
          | Unsupported Media Type     | 415     | The server refuses to process the request because the entity of the request is in a format not supported by the requested resource for the requested method.     |
          Too many requests     | 429     | Too many requests hit the API too quickly     |
          | Server error     | 500     | A technical error occurred.  |






          # Detailed errors
          | Name | Code | Description |
          | -------- | -------- | -------- |
          | Unprocessable entity     | 422     | The server understands the content type of the request entity, which has a correct syntax, but failed to process the contained instructions.     |
        section: "#/contract/sections/1a36893d-2974-4bf6-a346-be9e7d238ef1"
  components:
    pathVariables:
      "0d094acb-f51d-44ff-8062-077d2678a342":
        name: "contactid"
        componentName: "contactid"
        type: "STRING"
        description: "Identifier of the Contact"
        required: true
        examples:
        - value: "0e8dd830-ad98-11e6-bf2e-47644ada7c0f"
      "93d46685-af4a-492c-87c6-a5b155f97c7a":
        name: "companyid"
        componentName: "companyid"
        type: "STRING"
        description: "Identifier of the Company"
        required: true
        examples:
        - value: "0e8c9fb0-ad98-11e6-bf2e-47644ada7c0f"
    queryParameters:
      "343a97d5-3870-46d0-b5f6-f647907cf10d":
        name: "$size"
        componentName: "$size"
        type: "INTEGER"
        description: "Size of the page to retrieve."
        examples:
        - value: 10
      acb5ba96-9238-4c9b-807d-f5661deb4baf:
        name: "$page"
        componentName: "$page"
        type: "INTEGER"
        description: "Number of the page to retrieve."
        examples:
        - value: 1
        - value: 42
      "8ef04c15-4c18-4f78-aac0-75ce81b87f8a":
        name: "$sort"
        componentName: "$sort"
        type: "STRING"
        description: "Order in which to retrieve the results. Multiple sort criteria can be passed."
        examples:
        - value: "birthday DESC"
        - value: "birthday ASC,rank DESC"
    headers:
      "66399869-353d-4f16-9190-c2dd504996f5":
        name: "X-Page-Count"
        componentName: "X-Page-Count"
        type: "INTEGER"
        examples:
        - value: 1
      a3e96163-5f99-4492-9f11-f6d021815504:
        name: "X-Page-Number"
        componentName: "X-Page-Number"
        type: "INTEGER"
        examples:
        - value: 1
      ec640144-11a2-4fe8-9077-abd1bc7d34ef:
        name: "X-Page-Size"
        componentName: "X-Page-Size"
        type: "INTEGER"
        examples:
        - value: 25
      "88115c97-1951-4f16-9a40-6564b6ba571d":
        name: "X-Total-Count"
        componentName: "X-Total-Count"
        type: "INTEGER"
        examples:
        - value: 2
    responses:
      c02c78ae-759c-450c-8da0-0f5abe356970:
        status: "400"
        componentName: "Status 400"
        bodies:
        - type: "#/contract/types/44d46f38-664d-476a-8ea1-ea8d83cfab2c"
          mediaTypes:
          - "application/json"
api-tryin: |-
  {
    "version" : 6,
    "entities" : [ {
      "entity" : {
        "type" : "Project",
        "name" : "Contacts API 2.0.0",
        "description" : "An API for keeping track of your contacts and the companies they work for.",
        "importedFrom" : "76702a41-e6dc-4a4e-9382-51bcbac3a4dc"
      },
      "children" : [ {
        "entity" : {
          "type" : "Service",
          "name" : "General"
        }
      }, {
        "entity" : {
          "type" : "Service",
          "name" : "Contacts"
        },
        "children" : [ {
          "entity" : {
            "type" : "Request",
            "id" : "cc629628-40d4-4bfb-9a66-ff6b48b45e7e",
            "name" : "Get the list of Contacts",
            "description" : "Loads a list of Contacts.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/contacts/",
              "query" : {
                "delimiter" : "&",
                "items" : [ {
                  "name" : "$size",
                  "value" : "10",
                  "enabled" : false
                }, {
                  "name" : "$page",
                  "value" : "1",
                  "enabled" : false
                }, {
                  "name" : "$sort",
                  "value" : "birthday DESC",
                  "enabled" : false
                }, {
                  "name" : "firstName",
                  "value" : "John",
                  "enabled" : false
                }, {
                  "name" : "lastName",
                  "value" : "Doe",
                  "enabled" : false
                }, {
                  "name" : "active",
                  "value" : "true",
                  "enabled" : false
                }, {
                  "name" : "company",
                  "value" : "0e8c9fb0-ad98-11e6-bf2e-47644ada7c0f",
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
            "id" : "81279661-0296-403b-9d85-90dde28dde89",
            "name" : "Create a Contact",
            "description" : "Adds a Contact.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/contacts/"
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
            }, {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Text",
              "textBody" : "{\n  \"firstName\": \"John\",\n  \"lastName\": \"Smith\",\n  \"birthday\": 152755200000,\n  \"active\": true,\n  \"rank\": 1,\n  \"company\": \"0e8cedd0-ad98-11e6-bf2e-47644ada7c0f\"\n}"
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "aa4296c1-9992-4ade-a8a2-9b19ff94c2a9",
            "name" : "Load a Contact",
            "description" : "Loads a Contact.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/contacts/{contactid}"
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
            "id" : "b0d32bd1-880c-4425-965d-5b741428175b",
            "name" : "Update a Contact",
            "description" : "Updates a Contact.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/contacts/{contactid}"
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
              "textBody" : "{\n  \"firstName\": \"John\",\n  \"lastName\": \"Smith\",\n  \"birthday\": 152755200000,\n  \"active\": true,\n  \"rank\": 1,\n  \"company\": \"0e8cedd0-ad98-11e6-bf2e-47644ada7c0f\"\n}"
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "b4b24e5e-1eda-409e-896c-fd9a44430075",
            "name" : "Delete a Contact",
            "description" : "Deletes a Contact.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/contacts/{contactid}"
            },
            "method" : {
              "link" : "",
              "name" : "DELETE"
            },
            "headers" : [ ],
            "headersType" : "Form"
          }
        } ]
      }, {
        "entity" : {
          "type" : "Service",
          "name" : "Companies"
        },
        "children" : [ {
          "entity" : {
            "type" : "Request",
            "id" : "35002bf8-b8f8-4b2d-b08c-32416ed7a739",
            "name" : "Load the list of Companies",
            "description" : "Loads a list of Company.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/companies/",
              "query" : {
                "delimiter" : "&",
                "items" : [ {
                  "name" : "$size",
                  "value" : "10",
                  "enabled" : false
                }, {
                  "name" : "$page",
                  "value" : "1",
                  "enabled" : false
                }, {
                  "name" : "$sort",
                  "value" : "birthday DESC",
                  "enabled" : false
                }, {
                  "name" : "name",
                  "value" : "George Street Brewery",
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
            "id" : "c4c264f7-a7fa-4a56-b6b5-0a0d7895fbdc",
            "name" : "Create a new Company",
            "description" : "Adds a Company.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/companies/"
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
            }, {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Text",
              "textBody" : "{\n  \"name\": \"George Street Brewery\",\n  \"address\":{\n    \"street\": \"2 place de la Defense\",\n    \"zipcode\": \"92053\",\n    \"city\": \"Paris\"\n  },\n  \"tags\":[\n    \"brewery\",\n    \"beer\",\n    \"ale\"\n  ]\n}"
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "af53c32e-218d-4d7d-b29a-6d29ebd3669d",
            "name" : "Load a Company",
            "description" : "Loads a Company.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/companies/{companyid}"
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
            "id" : "6675ed5a-57f0-463a-8b03-cae807aedd81",
            "name" : "Update a Company",
            "description" : "Updates a Company.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/companies/{companyid}"
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
              "textBody" : "{\n  \"name\": \"George Street Brewery\",\n  \"address\":{\n    \"street\": \"2 place de la Defense\",\n    \"zipcode\": \"92053\",\n    \"city\": \"Paris\"\n  },\n  \"tags\":[\n    \"brewery\",\n    \"beer\",\n    \"ale\"\n  ]\n}"
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "d879d187-48c8-4286-b11c-968eb381659f",
            "name" : "Delete a Company",
            "description" : "Deletes a Company.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/companies/{companyid}"
            },
            "method" : {
              "link" : "",
              "name" : "DELETE"
            },
            "headers" : [ ],
            "headersType" : "Form"
          }
        } ]
      } ]
    } ],
    "environments" : [ {
      "name" : "Contacts API 2.0.0",
      "importedFrom" : {
        "projectId" : "76702a41-e6dc-4a4e-9382-51bcbac3a4dc"
      },
      "variables" : {
        "1b11ae17-3e65-4cf4-b2a4-2624a8eeeac2" : {
          "name" : "BaseUrl",
          "value" : "https://example.com",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
