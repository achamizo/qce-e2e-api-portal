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
      - "#/contract/texts/6cd150a4-8e35-4960-8dc9-00bb3a91a4d7"
      - "#/contract/texts/4294c385-55cf-4052-8051-5b4cc1fbf380"
      - "#/contract/types/7eed57d2-edda-43e8-9a2a-22505dcc5354"
    - name: "Contacts"
      elementOrder:
      - "#/contract/resources/d782566f-671c-4a92-a665-1e53df47fab7"
      - "#/contract/resources/57ab26b3-94ba-4913-8f04-84db19252dbc"
      - "#/contract/types/ac1a7210-54a2-4cd6-a145-c7eab03d17ee"
    - name: "Companies"
      elementOrder:
      - "#/contract/resources/15b37dbb-4362-4524-b289-cf81dda1f4b2"
      - "#/contract/resources/4ae39a86-cc0e-430c-830c-321edba15d8d"
      - "#/contract/types/0a66024f-3d93-4e75-b725-f07408e153a9"
    securitySchemes:
      c7f04e35-7859-41ba-a0a9-62da9afe97f7:
        name: "HTTP_BASIC"
        type: "basic"
        description: "All GET methods are public, meaning that *you can read all the data*. Write operations require authentication and therefore are forbidden to the general public."
        describedBy: {}
    resources:
      "15b37dbb-4362-4524-b289-cf81dda1f4b2":
        path: "/companies/"
        section: "#/contract/sections/17b3dda2-5958-4501-9ebe-7160c78fdd61"
        operations:
          "73ca5956-3fd5-4e0a-a992-4fc10e7cbad4":
            name: "Load the list of Companies"
            method: "GET"
            description: "Loads a list of Company."
            tags:
            - "Companies"
            queryParameters:
            - type: "#/components/queryParameters/3fde5f08-090d-4713-9c0a-e660434f3b0a"
            - type: "#/components/queryParameters/1918134b-dcd9-488c-9ca4-6ceae5078eb7"
            - type: "#/components/queryParameters/3f0dfc45-f829-47a7-9eb2-b8a0f7ad1b1f"
            - name: "name"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field `name`"
              examples:
              - value: "George Street Brewery"
            responses:
              e6c35ca6-06a5-48a6-be6d-31953fa361ad:
                status: "200"
                description: "Status 200"
                headers:
                - type: "#/components/headers/22e14f13-64ad-42e7-8820-f9db4df570c5"
                - type: "#/components/headers/4b3bc5dd-dc5e-4535-98e9-b129594610c5"
                - type: "#/components/headers/16689729-940c-4c1f-824b-1506aa200721"
                - type: "#/components/headers/e114a4f1-14e4-4dc7-b1f5-f2755f5d8288"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/0a66024f-3d93-4e75-b725-f07408e153a9"
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
              f83baf21-f433-4038-b93f-b3d22bb9903e:
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/2a105204-3a28-42f3-93aa-23cf23fc3eff"
          da0d4c7e-a2d1-428d-abe0-bc2e0f11e762:
            name: "Create a new Company"
            method: "POST"
            description: "Adds a Company."
            tags:
            - "Companies"
            securedBy:
            - scheme: "#/contract/securitySchemes/c7f04e35-7859-41ba-a0a9-62da9afe97f7"
              scopes: []
            bodies:
            - type: "#/contract/types/0a66024f-3d93-4e75-b725-f07408e153a9"
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
              "7477f981-ef43-49a9-9d7e-e97825b6cb89":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/0a66024f-3d93-4e75-b725-f07408e153a9"
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
      "4ae39a86-cc0e-430c-830c-321edba15d8d":
        path: "/companies/{companyid}"
        section: "#/contract/sections/17b3dda2-5958-4501-9ebe-7160c78fdd61"
        pathVariables:
        - type: "#/components/pathVariables/8437c6a6-b2dc-4c73-b4e9-60b32cc459e9"
        operations:
          "7e2db5bf-919f-436b-9661-a4f687ee5235":
            name: "Load a Company"
            method: "GET"
            description: "Loads a Company."
            tags:
            - "Companies"
            responses:
              c6a69b3f-9f58-47ea-a59d-02a0c7a93b2c:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/0a66024f-3d93-4e75-b725-f07408e153a9"
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
              ab316172-133b-4d7d-aeec-624c4251a3fd:
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/2a105204-3a28-42f3-93aa-23cf23fc3eff"
          a3fc4e9f-d448-4b7e-88a2-6389ccdf51d8:
            name: "Update a Company"
            method: "PUT"
            description: "Updates a Company."
            tags:
            - "Companies"
            securedBy:
            - scheme: "#/contract/securitySchemes/c7f04e35-7859-41ba-a0a9-62da9afe97f7"
              scopes: []
            bodies:
            - type: "#/contract/types/0a66024f-3d93-4e75-b725-f07408e153a9"
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
              "673fc7ff-4dee-47e9-b4ee-1950be427565":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/0a66024f-3d93-4e75-b725-f07408e153a9"
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
          eda9ec5b-a5c3-4e4c-b2ea-4a163e4e7919:
            name: "Delete a Company"
            method: "DELETE"
            description: "Deletes a Company."
            tags:
            - "Companies"
            securedBy:
            - scheme: "#/contract/securitySchemes/c7f04e35-7859-41ba-a0a9-62da9afe97f7"
              scopes: []
            responses:
              "96144d98-a5e9-42ac-a51c-dba3856096c4":
                status: "200"
                description: "Status 200"
      d782566f-671c-4a92-a665-1e53df47fab7:
        path: "/contacts/"
        section: "#/contract/sections/ab8caa3e-057d-48ed-8b4c-8ed92bfb8bdc"
        operations:
          "4e7e5331-2bb5-4e90-a3ad-33995e791b6c":
            name: "Get the list of Contacts"
            method: "GET"
            description: "Loads a list of Contacts."
            tags:
            - "Contacts"
            queryParameters:
            - type: "#/components/queryParameters/3fde5f08-090d-4713-9c0a-e660434f3b0a"
            - type: "#/components/queryParameters/1918134b-dcd9-488c-9ca4-6ceae5078eb7"
            - type: "#/components/queryParameters/3f0dfc45-f829-47a7-9eb2-b8a0f7ad1b1f"
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
              "154184d6-48f7-4437-a907-426f24e54898":
                status: "200"
                description: "Status 200"
                headers:
                - type: "#/components/headers/22e14f13-64ad-42e7-8820-f9db4df570c5"
                - type: "#/components/headers/4b3bc5dd-dc5e-4535-98e9-b129594610c5"
                - type: "#/components/headers/16689729-940c-4c1f-824b-1506aa200721"
                - type: "#/components/headers/e114a4f1-14e4-4dc7-b1f5-f2755f5d8288"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/ac1a7210-54a2-4cd6-a145-c7eab03d17ee"
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
              da46416d-6e28-4d2e-b57d-e92490f8f93d:
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/2a105204-3a28-42f3-93aa-23cf23fc3eff"
          e48f710a-2953-4888-b2e4-f80496f1e96e:
            name: "Create a Contact"
            method: "POST"
            description: "Adds a Contact."
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/c7f04e35-7859-41ba-a0a9-62da9afe97f7"
              scopes: []
            bodies:
            - type: "#/contract/types/ac1a7210-54a2-4cd6-a145-c7eab03d17ee"
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
              b3dc8fcc-b911-4057-9d49-ece4b75e013f:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/ac1a7210-54a2-4cd6-a145-c7eab03d17ee"
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
      "57ab26b3-94ba-4913-8f04-84db19252dbc":
        path: "/contacts/{contactid}"
        section: "#/contract/sections/ab8caa3e-057d-48ed-8b4c-8ed92bfb8bdc"
        pathVariables:
        - type: "#/components/pathVariables/637abb80-4bc2-471f-b659-7739ea7e16f2"
        operations:
          "1ceaf2f1-7885-43e8-ba9b-92f4141b094f":
            name: "Load a Contact"
            method: "GET"
            description: "Loads a Contact."
            tags:
            - "Contacts"
            responses:
              "1008277e-4483-43e4-b67e-aadd888f5428":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/ac1a7210-54a2-4cd6-a145-c7eab03d17ee"
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
              "917cede3-d317-4e43-a08c-550fceb96048":
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/2a105204-3a28-42f3-93aa-23cf23fc3eff"
          "36e01e38-d41b-446f-ac74-a632933f5baf":
            name: "Update a Contact"
            method: "PUT"
            description: "Updates a Contact."
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/c7f04e35-7859-41ba-a0a9-62da9afe97f7"
              scopes: []
            bodies:
            - type: "#/contract/types/ac1a7210-54a2-4cd6-a145-c7eab03d17ee"
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
              "560de1ad-727c-4cc1-b904-86e03a797fe3":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/ac1a7210-54a2-4cd6-a145-c7eab03d17ee"
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
          "4dd201bc-d297-4b98-adcd-0194da057b14":
            name: "Delete a Contact"
            method: "DELETE"
            description: "Deletes a Contact."
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/c7f04e35-7859-41ba-a0a9-62da9afe97f7"
              scopes: []
            responses:
              d5eea469-4f27-44d4-b6cb-f964522c976f:
                status: "200"
                description: "Status 200"
    types:
      "0a66024f-3d93-4e75-b725-f07408e153a9":
        name: "Company"
        type: "OBJECT"
        description: "The datatype of a Company"
        section: "#/contract/sections/17b3dda2-5958-4501-9ebe-7160c78fdd61"
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
      ac1a7210-54a2-4cd6-a145-c7eab03d17ee:
        name: "Contact"
        type: "OBJECT"
        description: "The datatype of a Contact"
        section: "#/contract/sections/ab8caa3e-057d-48ed-8b4c-8ed92bfb8bdc"
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
      "7eed57d2-edda-43e8-9a2a-22505dcc5354":
        name: "Error"
        type: "OBJECT"
        description: "This general error structure is used throughout this API."
        section: "#/contract/sections/aa24fde5-8794-4e64-9e99-78bc207acf91"
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
      "6cd150a4-8e35-4960-8dc9-00bb3a91a4d7":
        title: "Authentication"
        content: |-
          This API is secured using Basic Authentication.

          All **read operations are open** and don't require authentication. However, all **write operations require authentication**.
        section: "#/contract/sections/aa24fde5-8794-4e64-9e99-78bc207acf91"
      "4294c385-55cf-4052-8051-5b4cc1fbf380":
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
        section: "#/contract/sections/aa24fde5-8794-4e64-9e99-78bc207acf91"
  components:
    pathVariables:
      "637abb80-4bc2-471f-b659-7739ea7e16f2":
        name: "contactid"
        componentName: "contactid"
        type: "STRING"
        description: "Identifier of the Contact"
        required: true
        examples:
        - value: "0e8dd830-ad98-11e6-bf2e-47644ada7c0f"
      "8437c6a6-b2dc-4c73-b4e9-60b32cc459e9":
        name: "companyid"
        componentName: "companyid"
        type: "STRING"
        description: "Identifier of the Company"
        required: true
        examples:
        - value: "0e8c9fb0-ad98-11e6-bf2e-47644ada7c0f"
    queryParameters:
      "3fde5f08-090d-4713-9c0a-e660434f3b0a":
        name: "$size"
        componentName: "$size"
        type: "INTEGER"
        description: "Size of the page to retrieve."
        examples:
        - value: 10
      "1918134b-dcd9-488c-9ca4-6ceae5078eb7":
        name: "$page"
        componentName: "$page"
        type: "INTEGER"
        description: "Number of the page to retrieve."
        examples:
        - value: 1
        - value: 42
      "3f0dfc45-f829-47a7-9eb2-b8a0f7ad1b1f":
        name: "$sort"
        componentName: "$sort"
        type: "STRING"
        description: "Order in which to retrieve the results. Multiple sort criteria can be passed."
        examples:
        - value: "birthday DESC"
        - value: "birthday ASC,rank DESC"
    headers:
      "22e14f13-64ad-42e7-8820-f9db4df570c5":
        name: "X-Page-Count"
        componentName: "X-Page-Count"
        type: "INTEGER"
        examples:
        - value: 1
      "4b3bc5dd-dc5e-4535-98e9-b129594610c5":
        name: "X-Page-Number"
        componentName: "X-Page-Number"
        type: "INTEGER"
        examples:
        - value: 1
      "16689729-940c-4c1f-824b-1506aa200721":
        name: "X-Page-Size"
        componentName: "X-Page-Size"
        type: "INTEGER"
        examples:
        - value: 25
      e114a4f1-14e4-4dc7-b1f5-f2755f5d8288:
        name: "X-Total-Count"
        componentName: "X-Total-Count"
        type: "INTEGER"
        examples:
        - value: 2
    responses:
      "2a105204-3a28-42f3-93aa-23cf23fc3eff":
        status: "400"
        componentName: "Status 400"
        bodies:
        - type: "#/contract/types/7eed57d2-edda-43e8-9a2a-22505dcc5354"
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
        "importedFrom" : "a3e01871-7955-46ab-839f-97052a04c779"
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
            "id" : "4e7e5331-2bb5-4e90-a3ad-33995e791b6c",
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
            "id" : "e48f710a-2953-4888-b2e4-f80496f1e96e",
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
            "id" : "1ceaf2f1-7885-43e8-ba9b-92f4141b094f",
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
            "id" : "36e01e38-d41b-446f-ac74-a632933f5baf",
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
            "id" : "4dd201bc-d297-4b98-adcd-0194da057b14",
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
            "id" : "73ca5956-3fd5-4e0a-a992-4fc10e7cbad4",
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
            "id" : "da0d4c7e-a2d1-428d-abe0-bc2e0f11e762",
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
            "id" : "7e2db5bf-919f-436b-9661-a4f687ee5235",
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
            "id" : "a3fc4e9f-d448-4b7e-88a2-6389ccdf51d8",
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
            "id" : "eda9ec5b-a5c3-4e4c-b2ea-4a163e4e7919",
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
        "projectId" : "a3e01871-7955-46ab-839f-97052a04c779"
      },
      "variables" : {
        "a2dd73b6-abb5-4d84-9986-ccf8cf1a7ef2" : {
          "name" : "BaseUrl",
          "value" : "https://example.com",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
