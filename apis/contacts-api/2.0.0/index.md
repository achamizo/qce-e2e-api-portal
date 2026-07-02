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
      - "#/contract/texts/2739d471-ac9c-4d7d-8dc9-8e83c6642ef8"
      - "#/contract/texts/689c9d6f-6b08-43c5-aa5c-eefc6bdcc73c"
      - "#/contract/types/13c3033c-c151-461b-9336-b1b909f9466e"
    - name: "Contacts"
      elementOrder:
      - "#/contract/resources/bfea18b6-e697-4817-8309-b8ddbb407d25"
      - "#/contract/resources/f32f1556-a51c-4da2-93af-cceb70aac37a"
      - "#/contract/types/c4830643-01e0-4ff8-9ef8-a406b8684f99"
    - name: "Companies"
      elementOrder:
      - "#/contract/resources/1b6d441c-a543-4b69-9841-62df65868f5c"
      - "#/contract/resources/5e175883-32f8-475f-b362-f43f60a7e220"
      - "#/contract/types/4fd1989a-91a8-4ebb-b179-0490b2567228"
    securitySchemes:
      "82f5cc2c-aa44-4736-b9f2-a966ebed24db":
        name: "HTTP_BASIC"
        type: "basic"
        description: "All GET methods are public, meaning that *you can read all the data*. Write operations require authentication and therefore are forbidden to the general public."
        describedBy: {}
    resources:
      "1b6d441c-a543-4b69-9841-62df65868f5c":
        path: "/companies/"
        section: "#/contract/sections/6de5fdef-a4af-4095-b7db-566612a920cf"
        operations:
          c4c0204e-f141-45d3-a85e-07b2987769a1:
            name: "Load the list of Companies"
            method: "GET"
            description: "Loads a list of Company."
            tags:
            - "Companies"
            queryParameters:
            - type: "#/components/queryParameters/861a8c2d-0bcc-4dc5-8077-5679afc315f2"
            - type: "#/components/queryParameters/6c4262cb-f308-4155-a006-02685af30a7b"
            - type: "#/components/queryParameters/70b967df-b22c-47f7-956d-2a20cb0091f6"
            - name: "name"
              type: "STRING"
              description: "Allows to filter the collection of results by the value of field `name`"
              examples:
              - value: "George Street Brewery"
            responses:
              "54fd93f3-c364-4643-bdb4-47d26c692995":
                status: "200"
                description: "Status 200"
                headers:
                - type: "#/components/headers/217a0526-d611-4580-9dfc-5263635bfdc4"
                - type: "#/components/headers/ba95c11c-d9e1-4769-a87b-d126363a2fa6"
                - type: "#/components/headers/1c9270f0-60b0-44da-98d1-a9b1dd7682bb"
                - type: "#/components/headers/ea4f7e11-0ab9-408e-b5e6-7a7c654d790c"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/4fd1989a-91a8-4ebb-b179-0490b2567228"
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
              d952ca5e-962d-4422-aefa-f44ed12a8064:
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/1fc7d06a-5499-42bc-8d7e-76cb49401661"
          ca3f4993-a9be-404e-9e96-efc12456b645:
            name: "Create a new Company"
            method: "POST"
            description: "Adds a Company."
            tags:
            - "Companies"
            securedBy:
            - scheme: "#/contract/securitySchemes/82f5cc2c-aa44-4736-b9f2-a966ebed24db"
              scopes: []
            bodies:
            - type: "#/contract/types/4fd1989a-91a8-4ebb-b179-0490b2567228"
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
              f4ebed3a-f3aa-432e-b8ea-bcba6088dd61:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/4fd1989a-91a8-4ebb-b179-0490b2567228"
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
      "5e175883-32f8-475f-b362-f43f60a7e220":
        path: "/companies/{companyid}"
        section: "#/contract/sections/6de5fdef-a4af-4095-b7db-566612a920cf"
        pathVariables:
        - type: "#/components/pathVariables/7c48e52f-0fff-462e-8b03-4bef379f9646"
        operations:
          fa2fe36a-ca93-4614-94b8-4454fcb98449:
            name: "Load a Company"
            method: "GET"
            description: "Loads a Company."
            tags:
            - "Companies"
            responses:
              "7facf2ab-d84f-43de-8e57-a58445305b4a":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/4fd1989a-91a8-4ebb-b179-0490b2567228"
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
              bc584320-c4dd-4123-906a-4ce56106cd20:
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/1fc7d06a-5499-42bc-8d7e-76cb49401661"
          "007ddd8f-be8f-4b20-a934-9bc06a61935c":
            name: "Update a Company"
            method: "PUT"
            description: "Updates a Company."
            tags:
            - "Companies"
            securedBy:
            - scheme: "#/contract/securitySchemes/82f5cc2c-aa44-4736-b9f2-a966ebed24db"
              scopes: []
            bodies:
            - type: "#/contract/types/4fd1989a-91a8-4ebb-b179-0490b2567228"
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
              "0315c373-1d4c-48a7-a132-2ebe89f76b3c":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/4fd1989a-91a8-4ebb-b179-0490b2567228"
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
          "028b414f-a0b1-4636-b931-349fdc749010":
            name: "Delete a Company"
            method: "DELETE"
            description: "Deletes a Company."
            tags:
            - "Companies"
            securedBy:
            - scheme: "#/contract/securitySchemes/82f5cc2c-aa44-4736-b9f2-a966ebed24db"
              scopes: []
            responses:
              "584e91ca-9cc0-41dd-8860-11f8dadd8b71":
                status: "200"
                description: "Status 200"
      bfea18b6-e697-4817-8309-b8ddbb407d25:
        path: "/contacts/"
        section: "#/contract/sections/2f9e309d-4f9f-40ad-99a8-7aa43bd79b99"
        operations:
          "86677e26-d774-477a-a7ac-3dbf9237e2aa":
            name: "Get the list of Contacts"
            method: "GET"
            description: "Loads a list of Contacts."
            tags:
            - "Contacts"
            queryParameters:
            - type: "#/components/queryParameters/861a8c2d-0bcc-4dc5-8077-5679afc315f2"
            - type: "#/components/queryParameters/6c4262cb-f308-4155-a006-02685af30a7b"
            - type: "#/components/queryParameters/70b967df-b22c-47f7-956d-2a20cb0091f6"
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
              f6f00fd5-77c1-490a-a408-f1c2f333d409:
                status: "200"
                description: "Status 200"
                headers:
                - type: "#/components/headers/217a0526-d611-4580-9dfc-5263635bfdc4"
                - type: "#/components/headers/ba95c11c-d9e1-4769-a87b-d126363a2fa6"
                - type: "#/components/headers/1c9270f0-60b0-44da-98d1-a9b1dd7682bb"
                - type: "#/components/headers/ea4f7e11-0ab9-408e-b5e6-7a7c654d790c"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/c4830643-01e0-4ff8-9ef8-a406b8684f99"
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
              "7df7e193-4b8d-41bb-abcc-f303c4972602":
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/1fc7d06a-5499-42bc-8d7e-76cb49401661"
          f99949c2-4106-4f71-b659-84ad581cb5cc:
            name: "Create a Contact"
            method: "POST"
            description: "Adds a Contact."
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/82f5cc2c-aa44-4736-b9f2-a966ebed24db"
              scopes: []
            bodies:
            - type: "#/contract/types/c4830643-01e0-4ff8-9ef8-a406b8684f99"
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
              "583fd4f3-6584-4854-b624-9353c44a428c":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/c4830643-01e0-4ff8-9ef8-a406b8684f99"
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
      f32f1556-a51c-4da2-93af-cceb70aac37a:
        path: "/contacts/{contactid}"
        section: "#/contract/sections/2f9e309d-4f9f-40ad-99a8-7aa43bd79b99"
        pathVariables:
        - type: "#/components/pathVariables/ca2b378c-f0b6-4962-9f20-7594fecf7506"
        operations:
          bd46abc2-5031-48d5-b48e-fec10e83b0f8:
            name: "Load a Contact"
            method: "GET"
            description: "Loads a Contact."
            tags:
            - "Contacts"
            responses:
              "59117308-9604-4a5e-9dc0-ecb4d54d6fa5":
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/c4830643-01e0-4ff8-9ef8-a406b8684f99"
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
              a799c5c7-e270-454d-9368-81d3a60127ac:
                status: "400"
                componentName: "Status 400"
                reference: "#/components/responses/1fc7d06a-5499-42bc-8d7e-76cb49401661"
          "1db01d70-278d-4595-ae49-5697ca3c443d":
            name: "Update a Contact"
            method: "PUT"
            description: "Updates a Contact."
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/82f5cc2c-aa44-4736-b9f2-a966ebed24db"
              scopes: []
            bodies:
            - type: "#/contract/types/c4830643-01e0-4ff8-9ef8-a406b8684f99"
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
              f9b7fdf7-2176-4c3e-93fa-f45d1951c418:
                status: "200"
                description: "Status 200"
                bodies:
                - type: "#/contract/types/c4830643-01e0-4ff8-9ef8-a406b8684f99"
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
          d4f98c0e-e259-43e0-ad05-f40da9e8476e:
            name: "Delete a Contact"
            method: "DELETE"
            description: "Deletes a Contact."
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/82f5cc2c-aa44-4736-b9f2-a966ebed24db"
              scopes: []
            responses:
              "690915fb-cbb8-43b9-ae54-8c2621adddcb":
                status: "200"
                description: "Status 200"
    types:
      "4fd1989a-91a8-4ebb-b179-0490b2567228":
        name: "Company"
        type: "OBJECT"
        description: "The datatype of a Company"
        section: "#/contract/sections/6de5fdef-a4af-4095-b7db-566612a920cf"
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
      c4830643-01e0-4ff8-9ef8-a406b8684f99:
        name: "Contact"
        type: "OBJECT"
        description: "The datatype of a Contact"
        section: "#/contract/sections/2f9e309d-4f9f-40ad-99a8-7aa43bd79b99"
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
      "13c3033c-c151-461b-9336-b1b909f9466e":
        name: "Error"
        type: "OBJECT"
        description: "This general error structure is used throughout this API."
        section: "#/contract/sections/c62597e4-1637-4990-ab01-4e10b7f803ce"
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
      "2739d471-ac9c-4d7d-8dc9-8e83c6642ef8":
        title: "Authentication"
        content: |-
          This API is secured using Basic Authentication.

          All **read operations are open** and don't require authentication. However, all **write operations require authentication**.
        section: "#/contract/sections/c62597e4-1637-4990-ab01-4e10b7f803ce"
      "689c9d6f-6b08-43c5-aa5c-eefc6bdcc73c":
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
        section: "#/contract/sections/c62597e4-1637-4990-ab01-4e10b7f803ce"
  components:
    pathVariables:
      ca2b378c-f0b6-4962-9f20-7594fecf7506:
        name: "contactid"
        componentName: "contactid"
        type: "STRING"
        description: "Identifier of the Contact"
        required: true
        examples:
        - value: "0e8dd830-ad98-11e6-bf2e-47644ada7c0f"
      "7c48e52f-0fff-462e-8b03-4bef379f9646":
        name: "companyid"
        componentName: "companyid"
        type: "STRING"
        description: "Identifier of the Company"
        required: true
        examples:
        - value: "0e8c9fb0-ad98-11e6-bf2e-47644ada7c0f"
    queryParameters:
      "861a8c2d-0bcc-4dc5-8077-5679afc315f2":
        name: "$size"
        componentName: "$size"
        type: "INTEGER"
        description: "Size of the page to retrieve."
        examples:
        - value: 10
      "6c4262cb-f308-4155-a006-02685af30a7b":
        name: "$page"
        componentName: "$page"
        type: "INTEGER"
        description: "Number of the page to retrieve."
        examples:
        - value: 1
        - value: 42
      "70b967df-b22c-47f7-956d-2a20cb0091f6":
        name: "$sort"
        componentName: "$sort"
        type: "STRING"
        description: "Order in which to retrieve the results. Multiple sort criteria can be passed."
        examples:
        - value: "birthday DESC"
        - value: "birthday ASC,rank DESC"
    headers:
      "217a0526-d611-4580-9dfc-5263635bfdc4":
        name: "X-Page-Count"
        componentName: "X-Page-Count"
        type: "INTEGER"
        examples:
        - value: 1
      ba95c11c-d9e1-4769-a87b-d126363a2fa6:
        name: "X-Page-Number"
        componentName: "X-Page-Number"
        type: "INTEGER"
        examples:
        - value: 1
      "1c9270f0-60b0-44da-98d1-a9b1dd7682bb":
        name: "X-Page-Size"
        componentName: "X-Page-Size"
        type: "INTEGER"
        examples:
        - value: 25
      ea4f7e11-0ab9-408e-b5e6-7a7c654d790c:
        name: "X-Total-Count"
        componentName: "X-Total-Count"
        type: "INTEGER"
        examples:
        - value: 2
    responses:
      "1fc7d06a-5499-42bc-8d7e-76cb49401661":
        status: "400"
        componentName: "Status 400"
        bodies:
        - type: "#/contract/types/13c3033c-c151-461b-9336-b1b909f9466e"
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
        "importedFrom" : "f4795885-eb56-4edb-9e1a-c3219e0e883a"
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
            "id" : "86677e26-d774-477a-a7ac-3dbf9237e2aa",
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
            "id" : "f99949c2-4106-4f71-b659-84ad581cb5cc",
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
            "id" : "bd46abc2-5031-48d5-b48e-fec10e83b0f8",
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
            "id" : "1db01d70-278d-4595-ae49-5697ca3c443d",
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
            "id" : "d4f98c0e-e259-43e0-ad05-f40da9e8476e",
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
            "id" : "c4c0204e-f141-45d3-a85e-07b2987769a1",
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
            "id" : "ca3f4993-a9be-404e-9e96-efc12456b645",
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
            "id" : "fa2fe36a-ca93-4614-94b8-4454fcb98449",
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
            "id" : "007ddd8f-be8f-4b20-a934-9bc06a61935c",
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
            "id" : "028b414f-a0b1-4636-b931-349fdc749010",
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
        "projectId" : "f4795885-eb56-4edb-9e1a-c3219e0e883a"
      },
      "variables" : {
        "83eff6e2-a182-4b26-a039-80f86d5ec243" : {
          "name" : "BaseUrl",
          "value" : "https://example.com",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
