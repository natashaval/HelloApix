---
swagger: "2.0"
info:
  description: "APIX as Documentation Management System with OAS 2.0"
  version: "APIX TOS"
  title: "APIX"
  termsOfService: "Terms of Service"
  contact: {}
  license:
    name: "License of API"
    url: "API license URL"
host: "localhost:8080"
basePath: "/"
externalDocs: null
schema: null
tags:
- name: "github-api-controller"
  description: "Github Api Controller"
- name: "api-controller"
  description: "Api Controller"
- name: "basic-error-controller"
  description: "Basic Error Controller"
- name: "user-controller"
  description: "User Controller"
- name: "admin-controller"
  description: "Admin Controller"
- name: "team-controller"
  description: "Team Controller"
- name: "auth-controller"
  description: "Auth Controller"
paths:
  /github/api/user/repos:
    get:
      summary: "getMyselfRepositories"
      description: null
      operationId: "getMyselfRepositoriesUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "github-api-controller"
      responses:
        200:
          schema:
            type: "array"
            items:
              $ref: "#/definitions/GithubRepoResponse"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
  /github/api/repos/{owner}/{repo}/branches:
    get:
      summary: "getBranches"
      description: null
      operationId: "getBranchesUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "github-api-controller"
      responses:
        200:
          schema:
            type: "array"
            items:
              type: "string"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    parameters:
    - type: "string"
      description: "repo"
      name: "repo"
      in: "path"
    - type: "string"
      description: "owner"
      name: "owner"
      in: "path"
  /github/api/user:
    get:
      summary: "getMyself"
      description: null
      operationId: "getMyselfUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "github-api-controller"
      responses:
        200:
          schema:
            $ref: "#/definitions/GithubUserResponse"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
  /github/api/repos/{owner}/{repo}/contents/{path}:
    post:
      summary: "pullFileContent"
      description: null
      operationId: "pullFileContentUsingPOST"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "github-api-controller"
      parameters:
      - name: "ref"
        in: "query"
        type: "string"
        description: "ref"
      - name: "projectId"
        in: "query"
        type: "string"
        description: "projectId"
      responses:
        200:
          schema:
            $ref: "#/definitions/ProjectCreateResponse"
          description: "OK"
          required: false
        201:
          description: "Created"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    get:
      summary: "getFileContent"
      description: null
      operationId: "getFileContentUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "github-api-controller"
      parameters:
      - name: "ref"
        in: "query"
        type: "string"
        description: "ref"
      responses:
        200:
          schema:
            $ref: "#/definitions/GithubContentResponse"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    put:
      summary: "pushFileContent"
      description: null
      operationId: "pushFileContentUsingPUT"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "github-api-controller"
      parameters:
      - in: "body"
        name: "body"
        required: false
        schema:
          $ref: "#/definitions/GithubContentsRequest"
        description: "request"
      responses:
        200:
          schema:
            $ref: "#/definitions/GithubCommitResponse"
          description: "OK"
          required: false
        201:
          description: "Created"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    parameters:
    - type: "string"
      description: "repo"
      name: "repo"
      in: "path"
    - type: "string"
      description: "path"
      name: "path"
      in: "path"
    - type: "string"
      description: "owner"
      name: "owner"
      in: "path"
  /projects/{id}/export:
    get:
      summary: "exportToOas"
      description: null
      operationId: "exportToOasUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "api-controller"
      parameters:
      - name: "format"
        in: "query"
        type: "string"
        description: "format"
        enum:
        - "JSON"
        - "YAML"
      responses:
        200:
          schema:
            $ref: "#/definitions/RequestResponse"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    parameters:
    - type: "string"
      description: "id"
      name: "id"
      in: "path"
  /projects:
    post:
      summary: "createProject"
      description: null
      operationId: "createProjectUsingPOST"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "api-controller"
      parameters:
      - in: "body"
        name: "body"
        required: false
        schema:
          $ref: "#/definitions/ProjectCreateRequest"
        description: "request"
      responses:
        201:
          schema:
            $ref: "#/definitions/ProjectCreateResponse"
          description: "Created"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    get:
      summary: "findAll"
      description: null
      operationId: "findAllUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "api-controller"
      parameters:
      - name: "size"
        in: "query"
        type: "integer"
        description: "size"
        format: "int32"
        default: 10
      - name: "page"
        in: "query"
        type: "integer"
        description: "page"
        format: "int32"
        default: 0
      - name: "sort"
        in: "query"
        type: "string"
        description: "sort"
      - name: "direction"
        in: "query"
        type: "string"
        description: "direction"
      responses:
        200:
          schema:
            $ref: "#/definitions/Page«ApiProject»"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
  /projects/{id}:
    get:
      summary: "getById"
      description: null
      operationId: "getByIdUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "api-controller"
      responses:
        200:
          schema:
            $ref: "#/definitions/ApiProject"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    delete:
      summary: "deleteById"
      description: null
      operationId: "deleteByIdUsingDELETE"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "api-controller"
      responses:
        200:
          schema:
            $ref: "#/definitions/RequestResponse"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        204:
          description: "No Content"
          required: false
        403:
          description: "Forbidden"
          required: false
    put:
      summary: "doApiDataQuery"
      description: null
      operationId: "doApiDataQueryUsingPUT"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "api-controller"
      parameters:
      - in: "body"
        name: "body"
        required: false
        schema:
          type: "object"
        description: "query"
      responses:
        200:
          schema:
            $ref: "#/definitions/RequestResponse"
          description: "OK"
          required: false
        201:
          description: "Created"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    parameters:
    - type: "string"
      description: "id"
      name: "id"
      in: "path"
  /projects/import:
    post:
      summary: "importFromFile"
      description: null
      operationId: "importFromFileUsingPOST"
      deprecated: false
      consumes:
      - "multipart/form-data"
      produces:
      - "*/*"
      tags:
      - "api-controller"
      parameters:
      - type: "file"
        description: "file"
        name: "file"
        in: "formData"
      - name: "team"
        in: "query"
        type: "string"
        description: "team"
      - name: "type"
        in: "query"
        type: "string"
        description: "type"
      - name: "isNewTeam"
        in: "query"
        type: "boolean"
        description: "isNewTeam"
      responses:
        200:
          schema:
            $ref: "#/definitions/RequestResponse"
          description: "OK"
          required: false
        201:
          description: "Created"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
  /projects/all/info:
    get:
      summary: "findAllProjects"
      description: null
      operationId: "findAllProjectsUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "api-controller"
      responses:
        200:
          schema:
            type: "array"
            items:
              $ref: "#/definitions/ApiProject"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
  /projects/{id}/codegen:
    get:
      summary: "getCodegen"
      description: null
      operationId: "getCodegenUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "api-controller"
      responses:
        200:
          schema:
            $ref: "#/definitions/DownloadResponse"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    parameters:
    - type: "string"
      description: "id"
      name: "id"
      in: "path"
  /projects/{id}/assign:
    post:
      summary: "assignTeamToProject"
      description: null
      operationId: "assignTeamToProjectUsingPOST"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "api-controller"
      parameters:
      - in: "body"
        name: "body"
        required: false
        schema:
          $ref: "#/definitions/ProjectAssignTeamRequest"
        description: "request"
      responses:
        200:
          schema:
            $ref: "#/definitions/RequestResponse"
          description: "OK"
          required: false
        201:
          description: "Created"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    parameters:
    - type: "string"
      description: "id"
      name: "id"
      in: "path"
  /projects/search:
    get:
      summary: "findSearch"
      description: null
      operationId: "findSearchUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "api-controller"
      parameters:
      - name: "search"
        in: "query"
        type: "string"
        description: "search"
      - name: "size"
        in: "query"
        type: "integer"
        description: "size"
        format: "int32"
        default: 10
      - name: "page"
        in: "query"
        type: "integer"
        description: "page"
        format: "int32"
        default: 0
      responses:
        200:
          schema:
            $ref: "#/definitions/Page«ApiProject»"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
  /error:
    head:
      summary: "error"
      description: null
      operationId: "errorUsingHEAD"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "basic-error-controller"
      responses:
        200:
          schema:
            type: "object"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        204:
          description: "No Content"
          required: false
        403:
          description: "Forbidden"
          required: false
    patch:
      summary: "error"
      description: null
      operationId: "errorUsingPATCH"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "basic-error-controller"
      responses:
        200:
          schema:
            type: "object"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        204:
          description: "No Content"
          required: false
        403:
          description: "Forbidden"
          required: false
    post:
      summary: "error"
      description: null
      operationId: "errorUsingPOST"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "basic-error-controller"
      responses:
        200:
          schema:
            type: "object"
          description: "OK"
          required: false
        201:
          description: "Created"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    get:
      summary: "error"
      description: null
      operationId: "errorUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "basic-error-controller"
      responses:
        200:
          schema:
            type: "object"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    options:
      summary: "error"
      description: null
      operationId: "errorUsingOPTIONS"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "basic-error-controller"
      responses:
        200:
          schema:
            type: "object"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        204:
          description: "No Content"
          required: false
        403:
          description: "Forbidden"
          required: false
    delete:
      summary: "error"
      description: null
      operationId: "errorUsingDELETE"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "basic-error-controller"
      responses:
        200:
          schema:
            type: "object"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        204:
          description: "No Content"
          required: false
        403:
          description: "Forbidden"
          required: false
    put:
      summary: "error"
      description: null
      operationId: "errorUsingPUT"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "basic-error-controller"
      responses:
        200:
          schema:
            type: "object"
          description: "OK"
          required: false
        201:
          description: "Created"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
  /user/profile:
    get:
      summary: "getAuth"
      description: null
      operationId: "getAuthUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "user-controller"
      parameters:
      - name: "authorities[0].authority"
        in: "query"
        type: "string"
      - name: "principal"
        in: "query"
        type: "object"
      - name: "authenticated"
        in: "query"
        type: "boolean"
      - name: "credentials"
        in: "query"
        type: "object"
      - name: "details"
        in: "query"
        type: "object"
      responses:
        200:
          schema:
            $ref: "#/definitions/UserProfileResponse"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
  /admin/users:
    post:
      summary: "createUser"
      description: null
      operationId: "createUserUsingPOST"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "multipart/form-data"
      tags:
      - "admin-controller"
      parameters:
      - in: "body"
        name: "body"
        required: false
        schema:
          $ref: "#/definitions/UserCreateRequest"
        description: "request"
      responses:
        201:
          schema:
            $ref: "#/definitions/UserCreateResponse"
          headers: {}
          description: "Created"
          required: false
        401:
          headers: {}
          description: "Unauthorized"
          required: false
        403:
          headers: {}
          description: "Forbidden"
          required: false
        404:
          headers: {}
          description: "Not Found"
          required: false
    get:
      summary: "getUsers"
      description: null
      operationId: "getUsersUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "admin-controller"
      responses:
        200:
          schema:
            type: "array"
            items:
              $ref: "#/definitions/User"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
  /admin/users/{id}:
    delete:
      summary: "deleteUser"
      description: null
      operationId: "deleteUserUsingDELETE"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "admin-controller"
      responses:
        200:
          schema:
            $ref: "#/definitions/RequestResponse"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        204:
          description: "No Content"
          required: false
        403:
          description: "Forbidden"
          required: false
    parameters:
    - type: "string"
      description: "id"
      name: "id"
      in: "path"
  /teams:
    post:
      summary: "createTeam"
      description: null
      operationId: "createTeamUsingPOST"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "team-controller"
      parameters:
      - in: "body"
        name: "body"
        required: false
        schema:
          $ref: "#/definitions/CreateTeamRequest"
        description: "teamRequest"
      responses:
        201:
          schema:
            $ref: "#/definitions/RequestResponse"
          description: "Created"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    get:
      summary: "getTeams"
      description: null
      operationId: "getTeamsUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "team-controller"
      responses:
        200:
          schema:
            type: "array"
            items:
              $ref: "#/definitions/Team"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
  /teams/{name}:
    get:
      summary: "getTeamByName"
      description: null
      operationId: "getTeamByNameUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "team-controller"
      responses:
        200:
          schema:
            $ref: "#/definitions/Team"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    put:
      summary: "editTeam"
      description: null
      operationId: "editTeamUsingPUT"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "team-controller"
      parameters:
      - in: "body"
        name: "body"
        required: false
        schema:
          $ref: "#/definitions/Team"
        description: "team"
      responses:
        200:
          schema:
            $ref: "#/definitions/RequestResponse"
          description: "OK"
          required: false
        201:
          description: "Created"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
    parameters:
    - type: "string"
      description: "name"
      name: "name"
      in: "path"
  /teams/my-team:
    get:
      summary: "getMyTeams"
      description: null
      operationId: "getMyTeamsUsingGET"
      deprecated: false
      produces:
      - "*/*"
      tags:
      - "team-controller"
      parameters:
      - name: "authorities[0].authority"
        in: "query"
        type: "string"
      - name: "principal"
        in: "query"
        type: "object"
      - name: "authenticated"
        in: "query"
        type: "boolean"
      - name: "credentials"
        in: "query"
        type: "object"
      - name: "details"
        in: "query"
        type: "object"
      responses:
        200:
          schema:
            type: "array"
            items:
              $ref: "#/definitions/Team"
          description: "OK"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
  /auth/login:
    post:
      summary: "login"
      description: null
      operationId: "loginUsingPOST"
      deprecated: false
      consumes:
      - "application/json"
      produces:
      - "*/*"
      tags:
      - "auth-controller"
      parameters:
      - in: "body"
        name: "body"
        required: false
        schema:
          $ref: "#/definitions/AuthenticationRequest"
        description: "data"
      responses:
        200:
          schema:
            $ref: "#/definitions/AuthLoginResponse"
          description: "OK"
          required: false
        201:
          description: "Created"
          required: false
        401:
          description: "Unauthorized"
          required: false
        403:
          description: "Forbidden"
          required: false
        404:
          description: "Not Found"
          required: false
definitions:
  User:
    schema:
      type: "object"
      properties:
        password:
          type: "string"
        teams:
          type: "array"
          items:
            type: "string"
        credentialsNonExpired:
          type: "boolean"
        roles:
          type: "array"
          items:
            type: "string"
        accountNonExpired:
          type: "boolean"
        id:
          type: "string"
        authorities:
          type: "array"
          items:
            $ref: "#/definitions/GrantedAuthority"
        enabled:
          type: "boolean"
        accountNonLocked:
          type: "boolean"
        username:
          type: "string"
  UserProfileResponse:
    schema:
      type: "object"
      properties:
        teams:
          type: "array"
          items:
            type: "string"
        success:
          type: "boolean"
        roles:
          type: "array"
          items:
            type: "string"
        message:
          type: "string"
        username:
          type: "string"
  ApiProject:
    schema:
      type: "object"
      properties:
        schema:
          type: "array"
          items:
            type: "string"
        teams:
          type: "array"
          items:
            type: "string"
        .signature:
          type: "string"
        sections:
          type: "object"
        createdAt:
          type: "string"
          format: "date-time"
        basePath:
          type: "string"
        githubProject:
          $ref: "#/definitions/Github"
        host:
          type: "string"
        projectOwner:
          $ref: "#/definitions/Team"
        externalDocs:
          $ref: "#/definitions/Contact"
        id:
          type: "string"
        definitions:
          type: "object"
        securityDefinitions:
          type: "object"
        info:
          $ref: "#/definitions/ProjectInfo"
        updatedAt:
          type: "string"
          format: "date-time"
  Schema:
    schema:
      type: "object"
      properties:
        extension:
          type: "string"
        minLength:
          type: "integer"
          format: "int32"
        pattern:
          type: "string"
        description:
          type: "string"
        type:
          type: "string"
        example:
          type: "string"
        exclusiveMaximum:
          type: "boolean"
          default: false
        default:
          type: "object"
        ref:
          type: "string"
        xml:
          $ref: "#/definitions/Xml"
        exclusiveMinimum:
          type: "boolean"
          default: false
        multipleOf:
          type: "integer"
          format: "int32"
        maxItems:
          type: "integer"
          format: "int32"
        in:
          type: "string"
        format:
          type: "string"
        collectionFormat:
          type: "string"
        enum:
          type: "array"
          items:
            type: "string"
        minItems:
          type: "integer"
          format: "int32"
        uniqueItems:
          type: "boolean"
          default: false
        name:
          type: "string"
        maximum:
          type: "integer"
          format: "int32"
        items:
          $ref: "#/definitions/Schema"
        minimum:
          type: "integer"
          format: "int32"
        maxLength:
          type: "integer"
          format: "int32"
        properties:
          type: "object"
  ModelAndView:
    schema:
      type: "object"
      properties:
        reference:
          type: "boolean"
        view:
          $ref: "#/definitions/View"
        viewName:
          type: "string"
        model:
          type: "object"
        modelMap:
          type: "object"
        empty:
          type: "boolean"
        status:
          type: "string"
          enum:
          - "100 CONTINUE"
          - "101 SWITCHING_PROTOCOLS"
          - "102 PROCESSING"
          - "103 CHECKPOINT"
          - "200 OK"
          - "201 CREATED"
          - "202 ACCEPTED"
          - "203 NON_AUTHORITATIVE_INFORMATION"
          - "204 NO_CONTENT"
          - "205 RESET_CONTENT"
          - "206 PARTIAL_CONTENT"
          - "207 MULTI_STATUS"
          - "208 ALREADY_REPORTED"
          - "226 IM_USED"
          - "300 MULTIPLE_CHOICES"
          - "301 MOVED_PERMANENTLY"
          - "302 FOUND"
          - "302 MOVED_TEMPORARILY"
          - "303 SEE_OTHER"
          - "304 NOT_MODIFIED"
          - "305 USE_PROXY"
          - "307 TEMPORARY_REDIRECT"
          - "308 PERMANENT_REDIRECT"
          - "400 BAD_REQUEST"
          - "401 UNAUTHORIZED"
          - "402 PAYMENT_REQUIRED"
          - "403 FORBIDDEN"
          - "404 NOT_FOUND"
          - "405 METHOD_NOT_ALLOWED"
          - "406 NOT_ACCEPTABLE"
          - "407 PROXY_AUTHENTICATION_REQUIRED"
          - "408 REQUEST_TIMEOUT"
          - "409 CONFLICT"
          - "410 GONE"
          - "411 LENGTH_REQUIRED"
          - "412 PRECONDITION_FAILED"
          - "413 PAYLOAD_TOO_LARGE"
          - "413 REQUEST_ENTITY_TOO_LARGE"
          - "414 URI_TOO_LONG"
          - "414 REQUEST_URI_TOO_LONG"
          - "415 UNSUPPORTED_MEDIA_TYPE"
          - "416 REQUESTED_RANGE_NOT_SATISFIABLE"
          - "417 EXPECTATION_FAILED"
          - "418 I_AM_A_TEAPOT"
          - "419 INSUFFICIENT_SPACE_ON_RESOURCE"
          - "420 METHOD_FAILURE"
          - "421 DESTINATION_LOCKED"
          - "422 UNPROCESSABLE_ENTITY"
          - "423 LOCKED"
          - "424 FAILED_DEPENDENCY"
          - "426 UPGRADE_REQUIRED"
          - "428 PRECONDITION_REQUIRED"
          - "429 TOO_MANY_REQUESTS"
          - "431 REQUEST_HEADER_FIELDS_TOO_LARGE"
          - "451 UNAVAILABLE_FOR_LEGAL_REASONS"
          - "500 INTERNAL_SERVER_ERROR"
          - "501 NOT_IMPLEMENTED"
          - "502 BAD_GATEWAY"
          - "503 SERVICE_UNAVAILABLE"
          - "504 GATEWAY_TIMEOUT"
          - "505 HTTP_VERSION_NOT_SUPPORTED"
          - "506 VARIANT_ALSO_NEGOTIATES"
          - "507 INSUFFICIENT_STORAGE"
          - "508 LOOP_DETECTED"
          - "509 BANDWIDTH_LIMIT_EXCEEDED"
          - "510 NOT_EXTENDED"
          - "511 NETWORK_AUTHENTICATION_REQUIRED"
  GithubContentsRequest:
    schema:
      type: "object"
      properties:
        committer:
          $ref: "#/definitions/GithubCommitterRequest"
        author:
          $ref: "#/definitions/GithubCommitterRequest"
        message:
          type: "string"
        branch:
          type: "string"
        projectId:
          type: "string"
        sha:
          type: "string"
  DownloadResponse:
    schema:
      type: "object"
      properties:
        success:
          type: "boolean"
        file.url:
          type: "string"
        message:
          type: "string"
  RequestResponse:
    schema:
      type: "object"
      properties:
        success:
          type: "boolean"
        message:
          type: "string"
  ProjectCreateResponse:
    schema:
      type: "object"
      properties:
        success:
          type: "boolean"
        message:
          type: "string"
        new.project:
          type: "string"
  GithubUserResponse:
    schema:
      type: "object"
      properties:
        date:
          type: "string"
          format: "date-time"
        name:
          type: "string"
        id:
          type: "integer"
          format: "int64"
        login:
          type: "string"
        email:
          type: "string"
  OperationDetail:
    schema:
      type: "object"
      properties:
        schema:
          $ref: "#/definitions/Schema"
        headers:
          type: "object"
        in:
          type: "string"
        queryParams:
          type: "object"
        name:
          type: "string"
        description:
          type: "string"
        type:
          type: "string"
        required:
          type: "boolean"
  ApiSection:
    schema:
      type: "object"
      properties:
        .signature:
          type: "string"
        paths:
          type: "object"
        info:
          $ref: "#/definitions/Tag"
  UserCreateResponse:
    schema:
      type: "object"
      properties:
        success:
          type: "boolean"
        message:
          type: "string"
        new.user:
          type: "string"
  Pageable:
    schema:
      type: "object"
      properties:
        paged:
          type: "boolean"
        pageNumber:
          type: "integer"
          format: "int32"
        offset:
          type: "integer"
          format: "int64"
        pageSize:
          type: "integer"
          format: "int32"
        unpaged:
          type: "boolean"
        sort:
          $ref: "#/definitions/Sort"
  GithubRepoResponse:
    schema:
      type: "object"
      properties:
        ownerName:
          type: "string"
        name:
          type: "string"
        description:
          type: "string"
        fullName:
          type: "string"
        id:
          type: "integer"
          format: "int64"
  ProjectInfo:
    schema:
      type: "object"
      properties:
        license:
          $ref: "#/definitions/Contact"
        .signature:
          type: "string"
        contact:
          $ref: "#/definitions/Contact"
        description:
          type: "string"
        termsOfService:
          type: "string"
        title:
          type: "string"
        version:
          type: "string"
  Sort:
    schema:
      type: "object"
      properties:
        unsorted:
          type: "boolean"
        sorted:
          type: "boolean"
        empty:
          type: "boolean"
  ProjectAssignTeamRequest:
    schema:
      type: "object"
      properties:
        teamName:
          type: "string"
        assignType:
          type: "string"
  Team:
    schema:
      type: "object"
      properties:
        createdAt:
          type: "string"
          format: "date-time"
        creator:
          type: "string"
        access:
          type: "string"
          enum:
          - "PRIVATE"
          - "PUBLIC"
        members:
          type: "array"
          items:
            $ref: "#/definitions/Member"
        name:
          type: "string"
        id:
          type: "string"
        updatedAt:
          type: "string"
          format: "date-time"
  AuthenticationRequest:
    schema:
      type: "object"
      properties:
        password:
          type: "string"
        username:
          type: "string"
  SecurityScheme:
    schema:
      type: "object"
      properties:
        tokenUrl:
          type: "string"
        authorizationUrl:
          type: "string"
        in:
          type: "string"
        name:
          type: "string"
        description:
          type: "string"
        scopes:
          type: "object"
        type:
          type: "string"
        flow:
          type: "string"
  Member:
    schema:
      type: "object"
      properties:
        grant:
          type: "boolean"
        username:
          type: "string"
  UserCreateRequest:
    schema:
      type: "object"
      properties:
        password:
          type: "string"
        roles:
          type: "array"
          items:
            type: "string"
        confirmPassword:
          type: "string"
        username:
          type: "string"
  Path:
    schema:
      type: "object"
      properties:
        pathVariables:
          type: "object"
        .signature:
          type: "string"
        methods:
          type: "object"
        description:
          type: "string"
  CreateTeamRequest:
    schema:
      type: "object"
      properties:
        teamName:
          type: "string"
        creator:
          type: "string"
        access:
          type: "string"
          enum:
          - "PRIVATE"
          - "PUBLIC"
        members:
          type: "array"
          items:
            type: "string"
  Github:
    schema:
      type: "object"
      properties:
        owner:
          type: "string"
        path:
          type: "string"
        .signature:
          type: "string"
        repo:
          type: "string"
        branch:
          type: "string"
  GithubCommitterRequest:
    schema:
      type: "object"
      properties:
        name:
          type: "string"
        email:
          type: "string"
  GithubCommitResponse:
    schema:
      type: "object"
      properties:
        owner:
          $ref: "#/definitions/GithubRepoResponse"
        committer:
          $ref: "#/definitions/GithubUserResponse"
        message:
          type: "string"
        sha:
          type: "string"
        commitDate:
          type: "string"
          format: "date-time"
  Page«ApiProject»:
    schema:
      type: "object"
      properties:
        number:
          type: "integer"
          format: "int32"
        last:
          type: "boolean"
        numberOfElements:
          type: "integer"
          format: "int32"
        size:
          type: "integer"
          format: "int32"
        totalPages:
          type: "integer"
          format: "int32"
        pageable:
          $ref: "#/definitions/Pageable"
        sort:
          $ref: "#/definitions/Sort"
        content:
          type: "array"
          items:
            $ref: "#/definitions/ApiProject"
        first:
          type: "boolean"
        empty:
          type: "boolean"
        totalElements:
          type: "integer"
          format: "int64"
  GrantedAuthority:
    schema:
      type: "object"
      properties:
        authority:
          type: "string"
  Definition:
    schema:
      type: "object"
      properties:
        schema:
          $ref: "#/definitions/Schema"
        .signature:
          type: "string"
        name:
          type: "string"
        description:
          type: "string"
  GithubContentResponse:
    schema:
      type: "object"
      properties:
        path:
          type: "string"
        size:
          type: "integer"
          format: "int64"
        repoName:
          type: "string"
        htmlUrl:
          type: "string"
        name:
          type: "string"
        json:
          type: "object"
        encoding:
          type: "string"
        type:
          type: "string"
        sha:
          type: "string"
        content:
          type: "string"
        url:
          type: "string"
  View:
    schema:
      type: "object"
      properties:
        contentType:
          type: "string"
  Contact:
    schema:
      type: "object"
      properties:
        name:
          type: "string"
        description:
          type: "string"
        email:
          type: "string"
        url:
          type: "string"
  Xml:
    schema:
      type: "object"
      properties:
        prefix:
          type: "string"
        name:
          type: "string"
        namespace:
          type: "string"
        attribute:
          type: "boolean"
        wrapped:
          type: "boolean"
  AuthLoginResponse:
    schema:
      type: "object"
      properties:
        success:
          type: "boolean"
        message:
          type: "string"
        token:
          type: "string"
        username:
          type: "string"
  ApiMethodData:
    schema:
      type: "object"
      properties:
        summary:
          type: "string"
        request:
          $ref: "#/definitions/OperationDetail"
        .signature:
          type: "string"
        deprecated:
          type: "boolean"
        produces:
          type: "array"
          items:
            type: "string"
        description:
          type: "string"
        operationId:
          type: "string"
        responses:
          type: "object"
        consumes:
          type: "array"
          items:
            type: "string"
  Tag:
    schema:
      type: "object"
      properties:
        .signature:
          type: "string"
        name:
          type: "string"
        description:
          type: "string"
  ProjectCreateRequest:
    schema:
      type: "object"
      properties:
        basePath:
          type: "string"
        host:
          type: "string"
        team:
          type: "string"
        info:
          $ref: "#/definitions/ProjectInfo"
        isNewTeam:
          type: "boolean"
securityDefinitions:
  JWT:
    type: "apiKey"
    name: "Authorization"
    in: "header"
