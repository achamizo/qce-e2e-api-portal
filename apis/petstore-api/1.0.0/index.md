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
      - "#/contract/resources/ac778a00-b7a2-4396-aa54-5c7fd36cb6c0"
      - "#/contract/resources/76a92369-fc6f-45a4-bebc-41fb5009ca32"
      - "#/contract/resources/6063470f-e146-4787-a394-abaa1b59ebd2"
      - "#/contract/resources/618920c9-6a45-4de1-bcfd-2561a23427b2"
      - "#/contract/resources/2a4d8cbe-010d-47b5-89ab-ba6a8b6dee03"
      - "#/contract/types/a7733b29-643e-4b27-8dc7-4f5749ed3183"
      - "#/contract/types/f3312185-1a64-4918-94c0-c277d60c72d3"
      - "#/contract/types/edd4cbff-f01c-48e7-abc8-8cdb655cb780"
      - "#/contract/types/acebf174-02bf-4e32-8df9-b79a4bc88568"
    - name: "Store"
      elementOrder:
      - "#/contract/resources/8b72badb-367d-4a75-a201-dfdeb9c2aa8b"
      - "#/contract/resources/c433a93e-c0e4-462e-9124-b0ee35dc8dba"
      - "#/contract/resources/b1bb8191-f54d-4315-adaa-0211cc2cb736"
      - "#/contract/types/f4b0175b-e2ae-4061-b315-ca9c9960cf79"
    - name: "User"
      elementOrder:
      - "#/contract/resources/6a702a3a-0810-432b-844a-1fd5a0df860a"
      - "#/contract/resources/b5877e24-cb00-421c-b45b-cecb68b0709f"
      - "#/contract/resources/c9675c4b-7887-44da-86b0-ee02b2a5e094"
      - "#/contract/resources/8aa18a44-3b9c-4a1e-a6ac-51233bc56b65"
      - "#/contract/resources/4d0d3262-b0f3-4d36-8f0f-1ae1c963da70"
      - "#/contract/resources/9fe737e4-dba4-4577-87fb-41c1bd5cc781"
      - "#/contract/types/4e76a117-5de3-42bc-a08d-673397dd637f"
    securitySchemes:
      ed76b159-1024-4f12-8041-91d7c4a26926:
        name: "petstore_auth"
        type: "oauth2"
        settings:
          authorizationUri: "http://petstore.swagger.io/oauth/dialog"
          authorizationGrants:
          - "implicit"
          scopes:
            "26c6a882-731b-4822-a61f-cfe2eeab12c3":
              name: "write:pets"
              description: "modify pets in your account"
            "8415346a-9a39-4143-a941-0341bc0d5760":
              name: "read:pets"
              description: "read your pets"
      ff948d40-283f-4e4c-a0c2-9425a1836496:
        name: "api_key"
        type: "custom"
        describedBy:
          headers:
          - name: "api_key"
            type: "STRING"
    resources:
      "6063470f-e146-4787-a394-abaa1b59ebd2":
        path: "/pet"
        section: "#/contract/sections/6d8d0dd2-ad9e-4308-ad5c-3c37d77b445b"
        operations:
          "9104e62f-3b71-47f1-80c7-598e2a5d0e2c":
            name: "Update an existing pet"
            method: "PUT"
            description: ""
            operationId: "updatePet"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926"
              scopes:
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/26c6a882-731b-4822-a61f-cfe2eeab12c3"
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/8415346a-9a39-4143-a941-0341bc0d5760"
            bodies:
            - type: "#/contract/types/a7733b29-643e-4b27-8dc7-4f5749ed3183"
              mediaTypes:
              - "application/json"
              - "application/xml"
            responses:
              "9abbcbaa-3866-48d4-b154-5a3cbfe83280":
                status: "400"
                description: "Invalid ID supplied"
              "31f31c59-a1ee-498f-86f7-aee69d96b90f":
                status: "404"
                description: "Pet not found"
              "428bb538-930c-48a8-b543-f80b72edc87c":
                status: "405"
                description: "Validation exception"
          "69322742-4b8d-4ba2-a9a8-70aef0d0177f":
            name: "Add a new pet to the store"
            method: "POST"
            description: ""
            operationId: "addPet"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926"
              scopes:
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/26c6a882-731b-4822-a61f-cfe2eeab12c3"
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/8415346a-9a39-4143-a941-0341bc0d5760"
            bodies:
            - type: "#/contract/types/a7733b29-643e-4b27-8dc7-4f5749ed3183"
              mediaTypes:
              - "application/json"
              - "application/xml"
            responses:
              fb2bd268-fbfc-4515-8958-9f8971592a84:
                status: "405"
                description: "Invalid input"
      "76a92369-fc6f-45a4-bebc-41fb5009ca32":
        path: "/pet/findByStatus"
        section: "#/contract/sections/6d8d0dd2-ad9e-4308-ad5c-3c37d77b445b"
        operations:
          "6a83ef85-34c5-444f-b102-39336c8e2732":
            name: "Finds Pets by status"
            method: "GET"
            description: "Multiple status values can be provided with comma separated strings"
            operationId: "findPetsByStatus"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926"
              scopes:
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/26c6a882-731b-4822-a61f-cfe2eeab12c3"
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/8415346a-9a39-4143-a941-0341bc0d5760"
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
              "542a174c-6ec1-470d-899c-ee48d01bce7e":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/a7733b29-643e-4b27-8dc7-4f5749ed3183"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              "075acd9d-bbbf-4b58-b542-19baf12845f3":
                status: "400"
                description: "Invalid status value"
      ac778a00-b7a2-4396-aa54-5c7fd36cb6c0:
        path: "/pet/findByTags"
        section: "#/contract/sections/6d8d0dd2-ad9e-4308-ad5c-3c37d77b445b"
        operations:
          "2909fd5c-d988-4f17-a8e3-14671615384b":
            name: "Finds Pets by tags"
            method: "GET"
            description: "Muliple tags can be provided with comma separated strings. Use tag1, tag2, tag3 for testing."
            operationId: "findPetsByTags"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926"
              scopes:
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/26c6a882-731b-4822-a61f-cfe2eeab12c3"
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/8415346a-9a39-4143-a941-0341bc0d5760"
            queryParameters:
            - name: "tags"
              type: "ARRAY"
              description: "Tags to filter by"
              required: true
              items:
                type: "STRING"
            responses:
              "1a9cc4e2-cfc1-49da-b223-948e7b9e3fe0":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/a7733b29-643e-4b27-8dc7-4f5749ed3183"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              c3e756cf-c7a9-464d-bd6a-75810bcae371:
                status: "400"
                description: "Invalid tag value"
      "618920c9-6a45-4de1-bcfd-2561a23427b2":
        path: "/pet/{petId}"
        section: "#/contract/sections/6d8d0dd2-ad9e-4308-ad5c-3c37d77b445b"
        pathVariables:
        - name: "petId"
          type: "INTEGER"
          description: "ID of pet to return"
          required: true
        operations:
          "10b0c930-cd8a-4d78-9d19-68e11bfeef0f":
            name: "Find pet by ID"
            method: "GET"
            description: "Returns a single pet"
            operationId: "getPetById"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/ff948d40-283f-4e4c-a0c2-9425a1836496"
              scopes: []
            responses:
              deb1e61a-89c7-4acc-9e15-510b3311f514:
                status: "200"
                description: "successful operation"
                bodies:
                - type: "#/contract/types/a7733b29-643e-4b27-8dc7-4f5749ed3183"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              "03d5e01f-f2a7-4200-b8c3-7efe03e6ab23":
                status: "400"
                description: "Invalid ID supplied"
              dcb202a7-0802-48ad-8b01-5d2f224cad47:
                status: "404"
                description: "Pet not found"
          "1452b1e1-9cf1-4f3b-a203-d44b762d1db8":
            name: "Updates a pet in the store with form data"
            method: "POST"
            description: ""
            operationId: "updatePetWithForm"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926"
              scopes:
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/26c6a882-731b-4822-a61f-cfe2eeab12c3"
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/8415346a-9a39-4143-a941-0341bc0d5760"
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
              "315c4b3c-4072-4026-9e17-116894407d4c":
                status: "405"
                description: "Invalid input"
          "1d508a0b-10cd-4a2a-85af-d2623cd3c03d":
            name: "Deletes a pet"
            method: "DELETE"
            description: ""
            operationId: "deletePet"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926"
              scopes:
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/26c6a882-731b-4822-a61f-cfe2eeab12c3"
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/8415346a-9a39-4143-a941-0341bc0d5760"
            headers:
            - name: "api_key"
              type: "STRING"
            responses:
              "97951b6c-f74b-4038-aa4d-3688950cf3b5":
                status: "400"
                description: "Invalid ID supplied"
              "55b30570-9c28-4217-bfd2-77b5245e6016":
                status: "404"
                description: "Pet not found"
      "2a4d8cbe-010d-47b5-89ab-ba6a8b6dee03":
        path: "/pet/{petId}/uploadImage"
        section: "#/contract/sections/6d8d0dd2-ad9e-4308-ad5c-3c37d77b445b"
        pathVariables:
        - name: "petId"
          type: "INTEGER"
          format: "INT64"
          description: "ID of pet to return"
          required: true
        operations:
          f23bcf53-9695-4452-8ec1-82efd938effe:
            name: "uploads an image"
            method: "POST"
            description: ""
            operationId: "uploadFile"
            tags:
            - "pet"
            securedBy:
            - scheme: "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926"
              scopes:
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/26c6a882-731b-4822-a61f-cfe2eeab12c3"
              - "#/contract/securitySchemes/ed76b159-1024-4f12-8041-91d7c4a26926/settings/scopes/8415346a-9a39-4143-a941-0341bc0d5760"
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
              "38ef30f2-658c-4566-a17b-8f691c8a47c9":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "#/contract/types/acebf174-02bf-4e32-8df9-b79a4bc88568"
                  mediaTypes:
                  - "application/json"
      b1bb8191-f54d-4315-adaa-0211cc2cb736:
        path: "/store/inventory"
        section: "#/contract/sections/577c3166-1f33-456e-927d-6ef35363725c"
        operations:
          "2901c684-c8c0-4eea-a8c6-1347135e82a0":
            name: "Returns pet inventories by status"
            method: "GET"
            description: "Returns a map of status codes to quantities"
            operationId: "getInventory"
            tags:
            - "store"
            securedBy:
            - scheme: "#/contract/securitySchemes/ff948d40-283f-4e4c-a0c2-9425a1836496"
              scopes: []
            responses:
              "190f46e4-c4ec-432e-8099-13d24d49efa1":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "OBJECT"
                  mediaTypes:
                  - "application/json"
      "8b72badb-367d-4a75-a201-dfdeb9c2aa8b":
        path: "/store/order"
        section: "#/contract/sections/577c3166-1f33-456e-927d-6ef35363725c"
        operations:
          "4cda63b9-09e1-498f-9ad7-28f6e6e924cd":
            name: "Place an order for a pet"
            method: "POST"
            description: ""
            operationId: "placeOrder"
            tags:
            - "store"
            bodies:
            - type: "#/contract/types/f4b0175b-e2ae-4061-b315-ca9c9960cf79"
            responses:
              f2c438d0-9f84-4e59-9c09-e61e8f70c2bb:
                status: "200"
                description: "successful operation"
                bodies:
                - type: "#/contract/types/f4b0175b-e2ae-4061-b315-ca9c9960cf79"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              "9989e869-6bc7-488d-a0e4-a61dcdf8e15a":
                status: "400"
                description: "Invalid Order"
      c433a93e-c0e4-462e-9124-b0ee35dc8dba:
        path: "/store/order/{orderId}"
        section: "#/contract/sections/577c3166-1f33-456e-927d-6ef35363725c"
        pathVariables:
        - name: "orderId"
          type: "INTEGER"
          format: "INT64"
          required: true
          minimum: 1
          maximum: 10
        operations:
          e42bfc18-a06a-46d4-ab3e-26651fc5f28a:
            name: "Find purchase order by ID"
            method: "GET"
            description: "For valid response try integer IDs with value >= 1 and <= 10. Other values will generated exceptions"
            operationId: "getOrderById"
            tags:
            - "store"
            responses:
              "548c15f5-bbdc-4a29-a8c1-3c594851a444":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "#/contract/types/f4b0175b-e2ae-4061-b315-ca9c9960cf79"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              c708c3d2-f726-47b2-8af5-a5fd973886c5:
                status: "400"
                description: "Invalid ID supplied"
              a15c7b36-de14-4e4b-a621-342d52cf702a:
                status: "404"
                description: "Order not found"
          ee31d233-c809-4d4d-b3e4-eb5b725d2355:
            name: "Delete purchase order by ID"
            method: "DELETE"
            description: "For valid response try integer IDs with positive integer value. Negative or non-integer values will generate API errors"
            operationId: "deleteOrder"
            tags:
            - "store"
            responses:
              faba2fe5-3529-4abc-82e8-99d3fe3836c6:
                status: "400"
                description: "Invalid ID supplied"
              daf92006-fec1-4b75-b2c2-90de8c0b2a50:
                status: "404"
                description: "Order not found"
      "6a702a3a-0810-432b-844a-1fd5a0df860a":
        path: "/user"
        section: "#/contract/sections/8f7f95e5-428c-450d-a269-5f2896643e37"
        operations:
          deda1f86-1223-4304-b295-534d5657817e:
            name: "Create user"
            method: "POST"
            description: "This can only be done by the logged in user."
            operationId: "createUser"
            tags:
            - "user"
            bodies:
            - type: "#/contract/types/4e76a117-5de3-42bc-a08d-673397dd637f"
      b5877e24-cb00-421c-b45b-cecb68b0709f:
        path: "/user/createWithArray"
        section: "#/contract/sections/8f7f95e5-428c-450d-a269-5f2896643e37"
        operations:
          "4abe9635-0f9f-4d9a-8e15-626f4823986b":
            name: "Creates list of users with given input array"
            method: "POST"
            description: ""
            operationId: "createUsersWithArrayInput"
            tags:
            - "user"
            bodies:
            - type: "ARRAY"
              items:
                type: "#/contract/types/4e76a117-5de3-42bc-a08d-673397dd637f"
      c9675c4b-7887-44da-86b0-ee02b2a5e094:
        path: "/user/createWithList"
        section: "#/contract/sections/8f7f95e5-428c-450d-a269-5f2896643e37"
        operations:
          "499d5f79-23d1-4037-bae7-b8991685ec55":
            name: "Creates list of users with given input array"
            method: "POST"
            description: ""
            operationId: "createUsersWithListInput"
            tags:
            - "user"
            bodies:
            - type: "ARRAY"
              items:
                type: "#/contract/types/4e76a117-5de3-42bc-a08d-673397dd637f"
      "4d0d3262-b0f3-4d36-8f0f-1ae1c963da70":
        path: "/user/login"
        section: "#/contract/sections/8f7f95e5-428c-450d-a269-5f2896643e37"
        operations:
          dfc15418-2195-42a9-8865-012817531588:
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
              d33b2e36-51cd-4d89-a6f3-a5b3b822c9b7:
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
              "791d2489-a7a6-42ac-aa38-f92f2932f26f":
                status: "400"
                description: "Invalid username/password supplied"
      "9fe737e4-dba4-4577-87fb-41c1bd5cc781":
        path: "/user/logout"
        section: "#/contract/sections/8f7f95e5-428c-450d-a269-5f2896643e37"
        operations:
          a3ca8055-2d46-4dc8-8d38-c730abdb31d5:
            name: "Logs out current logged in user session"
            method: "GET"
            operationId: "logoutUser"
            tags:
            - "user"
            responses:
              d6d40d2b-ea1d-4cbc-b058-6228d7292b24:
                status: "200"
      "8aa18a44-3b9c-4a1e-a6ac-51233bc56b65":
        path: "/user/{username}"
        section: "#/contract/sections/8f7f95e5-428c-450d-a269-5f2896643e37"
        pathVariables:
        - name: "username"
          type: "STRING"
          description: "The name that needs to be fetched. Use user1 for testing."
          required: true
        operations:
          "1f027a20-4654-483e-b896-7955bffa462d":
            name: "Get user by user name"
            method: "GET"
            description: ""
            operationId: "getUserByName"
            tags:
            - "user"
            responses:
              "9c8ce66f-5c77-4a9c-8f36-8031786bd69a":
                status: "200"
                description: "successful operation"
                bodies:
                - type: "#/contract/types/4e76a117-5de3-42bc-a08d-673397dd637f"
                  mediaTypes:
                  - "application/xml"
                  - "application/json"
              "72b45910-6439-4c7a-9b9c-6a84936d5677":
                status: "400"
                description: "Invalid username supplied"
              "6da8c36a-e1bf-4286-8936-b8301c29dc02":
                status: "404"
                description: "User not found"
          "80ffd03d-de40-426c-8a82-03535e5eb724":
            name: "Updated user"
            method: "PUT"
            description: "This can only be done by the logged in user."
            operationId: "updateUser"
            tags:
            - "user"
            bodies:
            - type: "#/contract/types/4e76a117-5de3-42bc-a08d-673397dd637f"
            responses:
              "49e3cd8f-5230-478a-9e4f-ddc346125ab8":
                status: "400"
                description: "Invalid user supplied"
              cde62671-6108-4288-aa79-209cff3406ae:
                status: "404"
                description: "User not found"
          fdacc882-6a81-4af1-85d0-76f65479a6e7:
            name: "Delete user"
            method: "DELETE"
            description: "This can only be done by the logged in user."
            operationId: "deleteUser"
            tags:
            - "user"
            responses:
              d5efc1d5-a664-4265-9692-7e3d4767ab27:
                status: "400"
                description: "Invalid username supplied"
              "5b31930d-1ab7-4f33-9e30-be9e0939a14b":
                status: "404"
                description: "User not found"
    types:
      f4b0175b-e2ae-4061-b315-ca9c9960cf79:
        name: "Order"
        type: "OBJECT"
        section: "#/contract/sections/577c3166-1f33-456e-927d-6ef35363725c"
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
      edd4cbff-f01c-48e7-abc8-8cdb655cb780:
        name: "Category"
        type: "OBJECT"
        section: "#/contract/sections/6d8d0dd2-ad9e-4308-ad5c-3c37d77b445b"
        properties:
        - name: "id"
          type: "INTEGER"
          format: "INT64"
        - name: "name"
          type: "STRING"
      "4e76a117-5de3-42bc-a08d-673397dd637f":
        name: "User"
        type: "OBJECT"
        section: "#/contract/sections/8f7f95e5-428c-450d-a269-5f2896643e37"
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
      f3312185-1a64-4918-94c0-c277d60c72d3:
        name: "Tag"
        type: "OBJECT"
        section: "#/contract/sections/6d8d0dd2-ad9e-4308-ad5c-3c37d77b445b"
        properties:
        - name: "id"
          type: "INTEGER"
          format: "INT64"
        - name: "name"
          type: "STRING"
      a7733b29-643e-4b27-8dc7-4f5749ed3183:
        name: "Pet"
        type: "OBJECT"
        section: "#/contract/sections/6d8d0dd2-ad9e-4308-ad5c-3c37d77b445b"
        properties:
        - name: "id"
          type: "INTEGER"
          format: "INT64"
        - name: "category"
          type: "#/contract/types/edd4cbff-f01c-48e7-abc8-8cdb655cb780"
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
            type: "#/contract/types/f3312185-1a64-4918-94c0-c277d60c72d3"
        - name: "status"
          type: "STRING"
          description: "pet status in the store"
          enum:
          - "available"
          - "pending"
          - "sold"
      acebf174-02bf-4e32-8df9-b79a4bc88568:
        name: "ApiResponse"
        type: "OBJECT"
        section: "#/contract/sections/6d8d0dd2-ad9e-4308-ad5c-3c37d77b445b"
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
        "importedFrom" : "9bf4b2f2-94ae-4617-a611-9ef34e33282a"
      },
      "children" : [ {
        "entity" : {
          "type" : "Service",
          "name" : "Pet"
        },
        "children" : [ {
          "entity" : {
            "type" : "Request",
            "id" : "2909fd5c-d988-4f17-a8e3-14671615384b",
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
            "id" : "6a83ef85-34c5-444f-b102-39336c8e2732",
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
            "id" : "9104e62f-3b71-47f1-80c7-598e2a5d0e2c",
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
            "id" : "69322742-4b8d-4ba2-a9a8-70aef0d0177f",
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
            "id" : "10b0c930-cd8a-4d78-9d19-68e11bfeef0f",
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
            "id" : "1452b1e1-9cf1-4f3b-a203-d44b762d1db8",
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
            "id" : "1d508a0b-10cd-4a2a-85af-d2623cd3c03d",
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
            "id" : "f23bcf53-9695-4452-8ec1-82efd938effe",
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
            "id" : "4cda63b9-09e1-498f-9ad7-28f6e6e924cd",
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
            "id" : "e42bfc18-a06a-46d4-ab3e-26651fc5f28a",
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
            "id" : "ee31d233-c809-4d4d-b3e4-eb5b725d2355",
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
            "id" : "2901c684-c8c0-4eea-a8c6-1347135e82a0",
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
            "id" : "deda1f86-1223-4304-b295-534d5657817e",
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
            "id" : "4abe9635-0f9f-4d9a-8e15-626f4823986b",
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
            "id" : "499d5f79-23d1-4037-bae7-b8991685ec55",
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
            "id" : "1f027a20-4654-483e-b896-7955bffa462d",
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
            "id" : "80ffd03d-de40-426c-8a82-03535e5eb724",
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
            "id" : "fdacc882-6a81-4af1-85d0-76f65479a6e7",
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
            "id" : "dfc15418-2195-42a9-8865-012817531588",
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
            "id" : "a3ca8055-2d46-4dc8-8d38-c730abdb31d5",
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
        "projectId" : "9bf4b2f2-94ae-4617-a611-9ef34e33282a"
      },
      "variables" : {
        "9d7cfe98-2bae-4650-897f-5193bd272a0c" : {
          "name" : "BaseUrl",
          "value" : "http://petstore.swagger.io/v2",
          "enabled" : true,
          "private" : false
        },
        "66056732-3d78-4515-808e-6880f03f3b5a" : {
          "name" : "Api_keyHeaderApi_key",
          "value" : "",
          "enabled" : true,
          "private" : true
        }
      }
    } ]
  }
---
