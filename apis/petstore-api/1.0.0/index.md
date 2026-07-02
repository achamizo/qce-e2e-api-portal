---
# NOTICE: Copyright 2026 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "Petstore API"
    version: "1.0.0"
    description: "This is a sample server Petstore server. You can find out more about Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/). For this sample, you can use the api key `special-key` to test the authorization filters."
    license:
      name: "Apache 2.0"
      url: "http://www.apache.org/licenses/LICENSE-2.0.html"
    contact:
      email: "apiteam@swagger.io"
    termsOfService: "http://swagger.io/terms/"
  contract:
    baseUrls:
    - url: "http://petstore.swagger.io/v2"
      isPublished: true
    mediaTypes:
    - "application/json"
    sections:
    - name: "Pet"
      elementOrder:
      - "#/contract/resources/60a51c5c-c7c7-4247-9dc9-5d0f1806e69c"
      - "#/contract/resources/25aac257-c3a6-49da-b047-3b99d909aca1"
      - "#/contract/resources/0c0064a8-4356-4350-b71e-333de24d5b59"
      - "#/contract/resources/283e6e9d-50cd-4da6-b86f-863f3ce2f809"
      - "#/contract/resources/afc52f6f-2be1-493d-a690-5462bae4d169"
      - "#/contract/types/352e5ce2-6e61-4ac3-aaf5-830a9e8d566d"
      - "#/contract/types/3eed7867-b86a-462a-b608-44f1a4ba89b8"
      - "#/contract/types/4b442975-ed0b-4f9f-b6c1-2ec3e65c5d25"
      - "#/contract/types/fb300b48-c9fc-47e0-8299-afaaad7f17d2"
    - name: "Store"
      elementOrder:
      - "#/contract/resources/f831c268-714d-49e6-af40-d079fb3e860d"
      - "#/contract/resources/e74fa543-9c64-421d-8a5a-6f2b56acbf37"
      - "#/contract/resources/601e4329-c397-4f42-aa67-31061ddf003d"
      - "#/contract/types/066f4082-a7bf-42a8-9ec4-933bc93ce5d0"
    - name: "User"
      elementOrder:
      - "#/contract/resources/2123bb52-b7f3-4b35-8a3d-24762bd8ab8b"
      - "#/contract/resources/5c4edad4-1860-49ee-af81-352ef1e9a594"
      - "#/contract/resources/a548909d-000e-4cad-a7d5-8ae3b4d9b3eb"
      - "#/contract/resources/e41682d9-5e3c-43d8-bc50-83f90a43f01c"
      - "#/contract/resources/66c035b8-dd40-45f5-81e5-a5976544202a"
      - "#/contract/resources/5b8dc004-1484-425d-9738-b723ce883d91"
      - "#/contract/types/4395b394-1185-4d76-973b-1fa930587cfc"
    securitySchemes:
      "3a2c0161-e07e-41b2-a4b6-25f25cf43d28":
        name: "petstore_auth"
        type: "oauth2"
        settings:
          authorizationUri: "http://petstore.swagger.io/oauth/dialog"
          authorizationGrants:
          - "implicit"
          scopes:
            e941e063-674d-46f2-9403-6a668b8ed605:
              name: "write:pets"
              description: "modify pets in your account"
            "0a03227d-a96a-4f8a-9e80-6c8857ef375f":
              name: "read:pets"
              description: "read your pets"
      f6e37a05-0ceb-4b57-bf09-faa0da50e302:
        name: "api_key"
        type: "custom"
        describedBy:
          headers:
          - name: "api_key"
            type: "STRING"
    resources:
      "0c0064a8-4356-4350-b71e-333de24d5b59":
        path: "/pet"
        section: "#/contract/sections/2de475d2-7c3a-4889-9e09-b9f14805e863"
        operations:
          "69b6b23d-066e-4c0f-8d6f-d8e60ea4c564":
            name: "Update an existing pet"
            method: "PUT"
            description: ""
            operationId: "updatePet"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28"
              scopes:
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/e941e063-674d-46f2-9403-6a668b8ed605"
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/0a03227d-a96a-4f8a-9e80-6c8857ef375f"
            bodies:
            - type: "#/contract/types/352e5ce2-6e61-4ac3-aaf5-830a9e8d566d"
              mediaTypes:
              - "application/json"
              - "application/xml"
            responses:
              "23c31f4f-74d6-4b38-ae17-c9a655fd7aee":
                status: "400"
                description: "Invalid ID supplied"
              "44a4d07d-e0d4-473e-a837-9fedb0c65e2b":
                status: "404"
                description: "Pet not found"
              de18f805-83f4-40d1-8ec6-08be1c92531e:
                status: "405"
                description: "Validation exception"
          b672559d-a54f-42ef-bcef-d654af651197:
            name: "Add a new pet to the store"
            method: "POST"
            description: ""
            operationId: "addPet"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28"
              scopes:
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/e941e063-674d-46f2-9403-6a668b8ed605"
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/0a03227d-a96a-4f8a-9e80-6c8857ef375f"
            bodies:
            - type: "#/contract/types/352e5ce2-6e61-4ac3-aaf5-830a9e8d566d"
              mediaTypes:
              - "application/json"
              - "application/xml"
            responses:
              d07957b8-4bc7-4525-a36f-c47269a06e23:
                status: "405"
                description: "Invalid input"
      "25aac257-c3a6-49da-b047-3b99d909aca1":
        path: "/pet/findByStatus"
        section: "#/contract/sections/2de475d2-7c3a-4889-9e09-b9f14805e863"
        operations:
          dcd1a2c0-a515-4df3-a686-10a4e8a9ab6c:
            name: "Finds Pets by status"
            method: "GET"
            description: "Multiple status values can be provided with comma separated strings"
            operationId: "findPetsByStatus"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28"
              scopes:
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/e941e063-674d-46f2-9403-6a668b8ed605"
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/0a03227d-a96a-4f8a-9e80-6c8857ef375f"
            queryParameters:
            - name: "status"
              type: "ARRAY"
              description: "Status values that need to be considered for filter"
              required: true
              items:
                type: "STRING"
                default: "available"
                enum:
                - "available"
                - "pending"
                - "sold"
            responses:
              "9a2af392-72ad-46ae-b3e0-b1542714b905":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/352e5ce2-6e61-4ac3-aaf5-830a9e8d566d"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              "1e303c44-9abb-4645-9556-88a0f67d54b9":
                status: "400"
                description: "Invalid status value"
      "60a51c5c-c7c7-4247-9dc9-5d0f1806e69c":
        path: "/pet/findByTags"
        section: "#/contract/sections/2de475d2-7c3a-4889-9e09-b9f14805e863"
        operations:
          "275340bb-945f-4484-9741-603257d4aec9":
            name: "Finds Pets by tags"
            method: "GET"
            description: "Muliple tags can be provided with comma separated strings. Use tag1, tag2, tag3 for testing."
            operationId: "findPetsByTags"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28"
              scopes:
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/e941e063-674d-46f2-9403-6a668b8ed605"
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/0a03227d-a96a-4f8a-9e80-6c8857ef375f"
            queryParameters:
            - name: "tags"
              type: "ARRAY"
              description: "Tags to filter by"
              required: true
              items:
                type: "STRING"
            responses:
              fd2b5d98-cdeb-4d9b-a441-8b56db73f689:
                status: "200"
                description: "successful operation"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/352e5ce2-6e61-4ac3-aaf5-830a9e8d566d"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              "30c04bf0-b076-49fe-ba82-f9ee61ce220d":
                status: "400"
                description: "Invalid tag value"
      "283e6e9d-50cd-4da6-b86f-863f3ce2f809":
        path: "/pet/{petId}"
        section: "#/contract/sections/2de475d2-7c3a-4889-9e09-b9f14805e863"
        pathVariables:
        - name: "petId"
          type: "INTEGER"
          description: "ID of pet to return"
          required: true
        operations:
          bac36bee-1b5a-491c-bfd3-8ef3359b44d8:
            name: "Find pet by ID"
            method: "GET"
            description: "Returns a single pet"
            operationId: "getPetById"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/f6e37a05-0ceb-4b57-bf09-faa0da50e302"
              scopes: []
            responses:
              "3ccc3abb-7b23-4182-a14b-ebaacc32bc15":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "#/contract/types/352e5ce2-6e61-4ac3-aaf5-830a9e8d566d"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              "3ae05e64-3fdb-4f88-99ec-71c135b9895d":
                status: "400"
                description: "Invalid ID supplied"
              "6f5adaa2-c09e-44f9-beeb-e760f8adef7c":
                status: "404"
                description: "Pet not found"
          "733738ea-f949-4366-82da-306487bb27aa":
            name: "Updates a pet in the store with form data"
            method: "POST"
            description: ""
            operationId: "updatePetWithForm"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28"
              scopes:
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/e941e063-674d-46f2-9403-6a668b8ed605"
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/0a03227d-a96a-4f8a-9e80-6c8857ef375f"
            bodies:
            - type: "OBJECT"
              properties:
              - name: "name"
                type: "STRING"
                description: "Updated name of the pet"
              - name: "status"
                type: "STRING"
                description: "Updated status of the pet"
              mediaTypes:
              - "application/x-www-form-urlencoded"
            responses:
              c0d18b13-ef5e-4300-81dd-ca3d4f76619f:
                status: "405"
                description: "Invalid input"
          "89e554a3-b4dc-41bc-a104-ace747bf0f76":
            name: "Deletes a pet"
            method: "DELETE"
            description: ""
            operationId: "deletePet"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28"
              scopes:
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/e941e063-674d-46f2-9403-6a668b8ed605"
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/0a03227d-a96a-4f8a-9e80-6c8857ef375f"
            headers:
            - name: "api_key"
              type: "STRING"
            responses:
              ae64be17-3894-4e8b-a1be-691d22eaaa68:
                status: "400"
                description: "Invalid ID supplied"
              "4e1904fb-20ef-4c17-91ad-8aef83c9c404":
                status: "404"
                description: "Pet not found"
      afc52f6f-2be1-493d-a690-5462bae4d169:
        path: "/pet/{petId}/uploadImage"
        section: "#/contract/sections/2de475d2-7c3a-4889-9e09-b9f14805e863"
        pathVariables:
        - name: "petId"
          type: "INTEGER"
          format: "INT64"
          description: "ID of pet to return"
          required: true
        operations:
          bf662c94-3a82-4fc7-bca4-ab1699e87c67:
            name: "uploads an image"
            method: "POST"
            description: ""
            operationId: "uploadFile"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28"
              scopes:
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/e941e063-674d-46f2-9403-6a668b8ed605"
              - "#/contract/securitySchemes/3a2c0161-e07e-41b2-a4b6-25f25cf43d28/settings/scopes/0a03227d-a96a-4f8a-9e80-6c8857ef375f"
            bodies:
            - type: "OBJECT"
              properties:
              - name: "additionalMetadata"
                type: "STRING"
                description: "Additional data to pass to server"
              - name: "file"
                type: "FILE"
                description: "file to upload"
              mediaTypes:
              - "multipart/form-data"
            responses:
              "417f773c-f941-4fc0-a261-77ca0da0bbc8":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "#/contract/types/fb300b48-c9fc-47e0-8299-afaaad7f17d2"
                  mediaTypes:
                  - "application/json"
      "601e4329-c397-4f42-aa67-31061ddf003d":
        path: "/store/inventory"
        section: "#/contract/sections/8f81c891-0871-4861-abb9-bd8401e83496"
        operations:
          fdff8be1-4dca-4305-9140-6d16c486128b:
            name: "Returns pet inventories by status"
            method: "GET"
            description: "Returns a map of status codes to quantities"
            operationId: "getInventory"
            tags:
            - "store"
            securedBy:
            - scheme: "#/contract/securitySchemes/f6e37a05-0ceb-4b57-bf09-faa0da50e302"
              scopes: []
            responses:
              e85b3bad-3b0f-46d4-bfae-8bd30affbfc9:
                status: "200"
                description: "successful operation"
                bodies:
                - type: "OBJECT"
                  mediaTypes:
                  - "application/json"
      f831c268-714d-49e6-af40-d079fb3e860d:
        path: "/store/order"
        section: "#/contract/sections/8f81c891-0871-4861-abb9-bd8401e83496"
        operations:
          e8123d55-b7a7-449c-a69b-15b577cb6efe:
            name: "Place an order for a pet"
            method: "POST"
            description: ""
            operationId: "placeOrder"
            tags:
            - "store"
            bodies:
            - type: "#/contract/types/066f4082-a7bf-42a8-9ec4-933bc93ce5d0"
            responses:
              "42c368ac-1f87-4a88-b956-9d758034784e":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "#/contract/types/066f4082-a7bf-42a8-9ec4-933bc93ce5d0"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              d2c8d1b8-b52b-4fbb-89ac-abea3ac23026:
                status: "400"
                description: "Invalid Order"
      e74fa543-9c64-421d-8a5a-6f2b56acbf37:
        path: "/store/order/{orderId}"
        section: "#/contract/sections/8f81c891-0871-4861-abb9-bd8401e83496"
        pathVariables:
        - name: "orderId"
          type: "INTEGER"
          format: "INT64"
          required: true
          minimum: 1
          maximum: 10
        operations:
          "27ccc911-b8b3-4a6b-920b-d9229353318d":
            name: "Find purchase order by ID"
            method: "GET"
            description: "For valid response try integer IDs with value >= 1 and <= 10. Other values will generated exceptions"
            operationId: "getOrderById"
            tags:
            - "store"
            responses:
              "63f49864-1d7f-4745-9330-dec0f582ead2":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "#/contract/types/066f4082-a7bf-42a8-9ec4-933bc93ce5d0"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              "5bac8c9b-1c7d-4899-ba8d-e0a1469af63e":
                status: "400"
                description: "Invalid ID supplied"
              fdbd5045-186b-48e8-a698-dc601b7843df:
                status: "404"
                description: "Order not found"
          "91a52bfe-4fd2-48de-80ca-e09b8688ba70":
            name: "Delete purchase order by ID"
            method: "DELETE"
            description: "For valid response try integer IDs with positive integer value. Negative or non-integer values will generate API errors"
            operationId: "deleteOrder"
            tags:
            - "store"
            responses:
              "849965c0-bdbd-413c-9c8d-322f96386c9f":
                status: "400"
                description: "Invalid ID supplied"
              b3c8833b-26a1-4cdc-ae5d-4a45525564fb:
                status: "404"
                description: "Order not found"
      "2123bb52-b7f3-4b35-8a3d-24762bd8ab8b":
        path: "/user"
        section: "#/contract/sections/32c17ac4-ed40-47ed-8829-4307162bab01"
        operations:
          facf4547-d186-468c-a87d-d984a2940fa6:
            name: "Create user"
            method: "POST"
            description: "This can only be done by the logged in user."
            operationId: "createUser"
            tags:
            - "user"
            bodies:
            - type: "#/contract/types/4395b394-1185-4d76-973b-1fa930587cfc"
      "5c4edad4-1860-49ee-af81-352ef1e9a594":
        path: "/user/createWithArray"
        section: "#/contract/sections/32c17ac4-ed40-47ed-8829-4307162bab01"
        operations:
          "9a39c0d0-13af-4ccf-9ee4-754590b8c709":
            name: "Creates list of users with given input array"
            method: "POST"
            description: ""
            operationId: "createUsersWithArrayInput"
            tags:
            - "user"
            bodies:
            - type: "ARRAY"
              items:
                type: "#/contract/types/4395b394-1185-4d76-973b-1fa930587cfc"
      a548909d-000e-4cad-a7d5-8ae3b4d9b3eb:
        path: "/user/createWithList"
        section: "#/contract/sections/32c17ac4-ed40-47ed-8829-4307162bab01"
        operations:
          a4a1f200-ccc1-4838-80c8-16f987e68293:
            name: "Creates list of users with given input array"
            method: "POST"
            description: ""
            operationId: "createUsersWithListInput"
            tags:
            - "user"
            bodies:
            - type: "ARRAY"
              items:
                type: "#/contract/types/4395b394-1185-4d76-973b-1fa930587cfc"
      "66c035b8-dd40-45f5-81e5-a5976544202a":
        path: "/user/login"
        section: "#/contract/sections/32c17ac4-ed40-47ed-8829-4307162bab01"
        operations:
          "9ed026b9-6cde-4afd-96f3-ca80a7daea0a":
            name: "Logs user into the system"
            method: "GET"
            description: ""
            operationId: "loginUser"
            tags:
            - "user"
            queryParameters:
            - name: "username"
              type: "STRING"
              description: "The user name for login"
              required: true
            - name: "password"
              type: "STRING"
              description: "The password for login in clear text"
              required: true
            responses:
              "6348cd40-a8ec-4d14-80b4-299fe46823e0":
                status: "200"
                description: "successful operation"
                headers:
                - name: "X-Rate-Limit"
                  type: "INTEGER"
                  format: "INT32"
                  description: "calls per hour allowed by the user"
                - name: "X-Expires-After"
                  type: "DATETIME"
                  description: "date in UTC when token expires"
                bodies:
                - type: "STRING"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              fd878a47-5797-49a5-aa36-82728bba671f:
                status: "400"
                description: "Invalid username/password supplied"
      "5b8dc004-1484-425d-9738-b723ce883d91":
        path: "/user/logout"
        section: "#/contract/sections/32c17ac4-ed40-47ed-8829-4307162bab01"
        operations:
          "30224fd0-b80d-4474-85ed-cb912ce98532":
            name: "Logs out current logged in user session"
            method: "GET"
            operationId: "logoutUser"
            tags:
            - "user"
            responses:
              "44e0ffe0-188c-4f66-9c2f-a1fa34290627":
                status: "200"
      e41682d9-5e3c-43d8-bc50-83f90a43f01c:
        path: "/user/{username}"
        section: "#/contract/sections/32c17ac4-ed40-47ed-8829-4307162bab01"
        pathVariables:
        - name: "username"
          type: "STRING"
          description: "The name that needs to be fetched. Use user1 for testing."
          required: true
        operations:
          "6b9d8417-33b3-4cca-aed1-3fe1be402118":
            name: "Get user by user name"
            method: "GET"
            description: ""
            operationId: "getUserByName"
            tags:
            - "user"
            responses:
              "5ebb556b-ac5e-4478-a9d9-737dc57d3027":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "#/contract/types/4395b394-1185-4d76-973b-1fa930587cfc"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              fa87ed9f-b293-4898-8baf-be96db4a0c42:
                status: "400"
                description: "Invalid username supplied"
              "72fe45cf-62be-436b-bb72-ff58fc0cb1d3":
                status: "404"
                description: "User not found"
          ca69f0db-b9c2-4e4b-b462-899e5261ddc1:
            name: "Updated user"
            method: "PUT"
            description: "This can only be done by the logged in user."
            operationId: "updateUser"
            tags:
            - "user"
            bodies:
            - type: "#/contract/types/4395b394-1185-4d76-973b-1fa930587cfc"
            responses:
              aa49a940-c332-47b1-bc9c-ed8031186641:
                status: "400"
                description: "Invalid user supplied"
              "7d01f3ac-8fb0-4db2-9897-4ae23f02bf5a":
                status: "404"
                description: "User not found"
          "407019fb-4669-4193-876f-7dd411e1a242":
            name: "Delete user"
            method: "DELETE"
            description: "This can only be done by the logged in user."
            operationId: "deleteUser"
            tags:
            - "user"
            responses:
              "6dec5a65-bc1c-4a1a-a207-02b392c20ac2":
                status: "400"
                description: "Invalid username supplied"
              bf6d86e8-4ef1-403c-9ae5-8a73c5e2cde7:
                status: "404"
                description: "User not found"
    types:
      "066f4082-a7bf-42a8-9ec4-933bc93ce5d0":
        name: "Order"
        type: "OBJECT"
        section: "#/contract/sections/8f81c891-0871-4861-abb9-bd8401e83496"
        properties:
        - name: "id"
          type: "INTEGER"
          format: "INT64"
        - name: "petId"
          type: "INTEGER"
          format: "INT64"
        - name: "quantity"
          type: "INTEGER"
          format: "INT32"
        - name: "shipDate"
          type: "DATETIME"
        - name: "status"
          type: "STRING"
          description: "Order Status"
          enum:
          - "placed"
          - "approved"
          - "delivered"
        - name: "complete"
          type: "BOOLEAN"
          default: false
      "4b442975-ed0b-4f9f-b6c1-2ec3e65c5d25":
        name: "Category"
        type: "OBJECT"
        section: "#/contract/sections/2de475d2-7c3a-4889-9e09-b9f14805e863"
        properties:
        - name: "id"
          type: "INTEGER"
          format: "INT64"
        - name: "name"
          type: "STRING"
      "4395b394-1185-4d76-973b-1fa930587cfc":
        name: "User"
        type: "OBJECT"
        section: "#/contract/sections/32c17ac4-ed40-47ed-8829-4307162bab01"
        properties:
        - name: "id"
          type: "INTEGER"
          format: "INT64"
        - name: "username"
          type: "STRING"
        - name: "firstName"
          type: "STRING"
        - name: "lastName"
          type: "STRING"
        - name: "email"
          type: "STRING"
        - name: "password"
          type: "STRING"
        - name: "phone"
          type: "STRING"
        - name: "userStatus"
          type: "INTEGER"
          format: "INT32"
          description: "User Status"
      "3eed7867-b86a-462a-b608-44f1a4ba89b8":
        name: "Tag"
        type: "OBJECT"
        section: "#/contract/sections/2de475d2-7c3a-4889-9e09-b9f14805e863"
        properties:
        - name: "id"
          type: "INTEGER"
          format: "INT64"
        - name: "name"
          type: "STRING"
      "352e5ce2-6e61-4ac3-aaf5-830a9e8d566d":
        name: "Pet"
        type: "OBJECT"
        section: "#/contract/sections/2de475d2-7c3a-4889-9e09-b9f14805e863"
        properties:
        - name: "id"
          type: "INTEGER"
          format: "INT64"
        - name: "category"
          type: "#/contract/types/4b442975-ed0b-4f9f-b6c1-2ec3e65c5d25"
        - name: "name"
          type: "STRING"
          required: true
          examples:
          - value: "doggie"
        - name: "photoUrls"
          type: "ARRAY"
          required: true
          items:
            type: "STRING"
        - name: "tags"
          type: "ARRAY"
          items:
            type: "#/contract/types/3eed7867-b86a-462a-b608-44f1a4ba89b8"
        - name: "status"
          type: "STRING"
          description: "pet status in the store"
          enum:
          - "available"
          - "pending"
          - "sold"
      fb300b48-c9fc-47e0-8299-afaaad7f17d2:
        name: "ApiResponse"
        type: "OBJECT"
        section: "#/contract/sections/2de475d2-7c3a-4889-9e09-b9f14805e863"
        properties:
        - name: "code"
          type: "INTEGER"
          format: "INT32"
        - name: "type"
          type: "STRING"
        - name: "message"
          type: "STRING"
  components: {}
api-tryin: |-
  {
    "version" : 6,
    "entities" : [ {
      "entity" : {
        "type" : "Project",
        "name" : "Petstore API 1.0.0",
        "description" : "This is a sample server Petstore server. You can find out more about Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/). For this sample, you can use the api key `special-key` to test the authorization filters.",
        "importedFrom" : "2e06d1d2-1efa-4969-9077-869b5c42f9b2"
      },
      "children" : [ {
        "entity" : {
          "type" : "Service",
          "name" : "Pet"
        },
        "children" : [ {
          "entity" : {
            "type" : "Request",
            "id" : "275340bb-945f-4484-9741-603257d4aec9",
            "name" : "Finds Pets by tags",
            "description" : "Muliple tags can be provided with comma separated strings. Use tag1, tag2, tag3 for testing.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/pet/findByTags",
              "query" : {
                "delimiter" : "&",
                "items" : [ {
                  "name" : "tags",
                  "value" : "",
                  "enabled" : true
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
              "value" : "application/xml, application/json"
            } ],
            "headersType" : "Form",
            "uriEditor" : true
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "dcd1a2c0-a515-4df3-a686-10a4e8a9ab6c",
            "name" : "Finds Pets by status",
            "description" : "Multiple status values can be provided with comma separated strings",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/pet/findByStatus",
              "query" : {
                "delimiter" : "&",
                "items" : [ {
                  "name" : "status",
                  "value" : "",
                  "enabled" : true
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
              "value" : "application/xml, application/json"
            } ],
            "headersType" : "Form",
            "uriEditor" : true
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "69b6b23d-066e-4c0f-8d6f-d8e60ea4c564",
            "name" : "Update an existing pet",
            "description" : "",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/pet"
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
              "enabled" : false,
              "name" : "Content-Type",
              "value" : "application/xml"
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Text",
              "textBody" : ""
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "b672559d-a54f-42ef-bcef-d654af651197",
            "name" : "Add a new pet to the store",
            "description" : "",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/pet"
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
              "enabled" : false,
              "name" : "Content-Type",
              "value" : "application/xml"
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Text",
              "textBody" : ""
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "bac36bee-1b5a-491c-bfd3-8ef3359b44d8",
            "name" : "Find pet by ID",
            "description" : "Returns a single pet",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/pet/{petId}"
            },
            "method" : {
              "link" : "",
              "name" : "GET"
            },
            "headers" : [ {
              "enabled" : false,
              "name" : "api_key",
              "value" : "${\"Api_keyHeaderApi_key\"}"
            }, {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/xml, application/json"
            } ],
            "headersType" : "Form"
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "733738ea-f949-4366-82da-306487bb27aa",
            "name" : "Updates a pet in the store with form data",
            "description" : "",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/pet/{petId}"
            },
            "method" : {
              "link" : "",
              "name" : "POST",
              "requestBody" : true
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Content-Type",
              "value" : "application/x-www-form-urlencoded"
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Form",
              "formBody" : {
                "items" : [ {
                  "enabled" : false,
                  "name" : "name",
                  "value" : "",
                  "type" : "Text"
                }, {
                  "enabled" : false,
                  "name" : "status",
                  "value" : "",
                  "type" : "Text"
                } ],
                "encoding" : "application/x-www-form-urlencoded"
              }
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "89e554a3-b4dc-41bc-a104-ace747bf0f76",
            "name" : "Deletes a pet",
            "description" : "",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/pet/{petId}"
            },
            "method" : {
              "link" : "",
              "name" : "DELETE"
            },
            "headers" : [ {
              "enabled" : false,
              "name" : "api_key",
              "value" : ""
            } ],
            "headersType" : "Form"
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "bf662c94-3a82-4fc7-bca4-ab1699e87c67",
            "name" : "uploads an image",
            "description" : "",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/pet/{petId}/uploadImage"
            },
            "method" : {
              "link" : "",
              "name" : "POST",
              "requestBody" : true
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Content-Type",
              "value" : "multipart/form-data"
            }, {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Form",
              "formBody" : {
                "items" : [ {
                  "enabled" : false,
                  "name" : "additionalMetadata",
                  "value" : "",
                  "type" : "Text"
                }, {
                  "enabled" : false,
                  "name" : "file",
                  "type" : "File"
                } ],
                "encoding" : "multipart/form-data"
              }
            }
          }
        } ]
      }, {
        "entity" : {
          "type" : "Service",
          "name" : "Store"
        },
        "children" : [ {
          "entity" : {
            "type" : "Request",
            "id" : "e8123d55-b7a7-449c-a69b-15b577cb6efe",
            "name" : "Place an order for a pet",
            "description" : "",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/store/order"
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
              "value" : "application/xml, application/json"
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Text",
              "textBody" : ""
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "27ccc911-b8b3-4a6b-920b-d9229353318d",
            "name" : "Find purchase order by ID",
            "description" : "For valid response try integer IDs with value >= 1 and <= 10. Other values will generated exceptions",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/store/order/{orderId}"
            },
            "method" : {
              "link" : "",
              "name" : "GET"
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/xml, application/json"
            } ],
            "headersType" : "Form"
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "91a52bfe-4fd2-48de-80ca-e09b8688ba70",
            "name" : "Delete purchase order by ID",
            "description" : "For valid response try integer IDs with positive integer value. Negative or non-integer values will generate API errors",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/store/order/{orderId}"
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
            "id" : "fdff8be1-4dca-4305-9140-6d16c486128b",
            "name" : "Returns pet inventories by status",
            "description" : "Returns a map of status codes to quantities",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/store/inventory"
            },
            "method" : {
              "link" : "",
              "name" : "GET"
            },
            "headers" : [ {
              "enabled" : false,
              "name" : "api_key",
              "value" : "${\"Api_keyHeaderApi_key\"}"
            }, {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form"
          }
        } ]
      }, {
        "entity" : {
          "type" : "Service",
          "name" : "User"
        },
        "children" : [ {
          "entity" : {
            "type" : "Request",
            "id" : "facf4547-d186-468c-a87d-d984a2940fa6",
            "name" : "Create user",
            "description" : "This can only be done by the logged in user.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/user"
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
              "textBody" : ""
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "9a39c0d0-13af-4ccf-9ee4-754590b8c709",
            "name" : "Creates list of users with given input array",
            "description" : "",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/user/createWithArray"
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
              "textBody" : ""
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "a4a1f200-ccc1-4838-80c8-16f987e68293",
            "name" : "Creates list of users with given input array",
            "description" : "",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/user/createWithList"
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
              "textBody" : ""
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "6b9d8417-33b3-4cca-aed1-3fe1be402118",
            "name" : "Get user by user name",
            "description" : "",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/user/{username}"
            },
            "method" : {
              "link" : "",
              "name" : "GET"
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/xml, application/json"
            } ],
            "headersType" : "Form"
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "ca69f0db-b9c2-4e4b-b462-899e5261ddc1",
            "name" : "Updated user",
            "description" : "This can only be done by the logged in user.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/user/{username}"
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
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Text",
              "textBody" : ""
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "407019fb-4669-4193-876f-7dd411e1a242",
            "name" : "Delete user",
            "description" : "This can only be done by the logged in user.",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/user/{username}"
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
            "id" : "9ed026b9-6cde-4afd-96f3-ca80a7daea0a",
            "name" : "Logs user into the system",
            "description" : "",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/user/login",
              "query" : {
                "delimiter" : "&",
                "items" : [ {
                  "name" : "username",
                  "value" : "",
                  "enabled" : true
                }, {
                  "name" : "password",
                  "value" : "",
                  "enabled" : true
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
              "value" : "application/xml, application/json"
            } ],
            "headersType" : "Form",
            "uriEditor" : true
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "30224fd0-b80d-4474-85ed-cb912ce98532",
            "name" : "Logs out current logged in user session",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/user/logout"
            },
            "method" : {
              "link" : "",
              "name" : "GET"
            },
            "headers" : [ ],
            "headersType" : "Form"
          }
        } ]
      } ]
    } ],
    "environments" : [ {
      "name" : "Petstore API 1.0.0",
      "importedFrom" : {
        "projectId" : "2e06d1d2-1efa-4969-9077-869b5c42f9b2"
      },
      "variables" : {
        "463d5a62-1d5b-4311-a5c0-6332c89e919e" : {
          "name" : "BaseUrl",
          "value" : "http://petstore.swagger.io/v2",
          "enabled" : true,
          "private" : false
        },
        "00b30349-b7bd-4cc4-87ee-11038d4a6c45" : {
          "name" : "Api_keyHeaderApi_key",
          "value" : "",
          "enabled" : true,
          "private" : true
        }
      }
    } ]
  }
---
