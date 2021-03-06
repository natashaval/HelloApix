{
  "swagger" : "2.0",
  "info" : {
    "description" : "<p>This is a sample server Petstore server.  You can find out more about Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).  For this sample, you can use the api key `special-key` to test the authorization filters.</p>",
    "version" : "1.0.0",
    "title" : "Swagger Petstore",
    "termsOfService" : "http://swagger.io/terms/",
    "contact" : {
      "email" : "apiteam@swagger.io"
    },
    "license" : {
      "name" : "Apache 2.0",
      "url" : "http://www.apache.org/licenses/LICENSE-2.0.html"
    }
  },
  "host" : "petstore.swagger.io",
  "basePath" : "/v2",
  "externalDocs" : {
    "description" : "Find out more about Swagger",
    "url" : "http://swagger.io"
  },
  "schema" : null,
  "tags" : [ {
    "name" : "store",
    "description" : "Access to Petstore orders"
  }, {
    "name" : "user",
    "description" : "Operations about user"
  }, {
    "name" : "pet",
    "description" : "Everything about your Pets"
  } ],
  "paths" : {
    "/store/inventory" : {
      "get" : {
        "summary" : "Returns pet inventories by status",
        "description" : "Returns a map of status codes to quantities",
        "operationId" : "getInventory",
        "produces" : [ "application/json" ],
        "tags" : [ "store" ],
        "responses" : {
          "200" : {
            "schema" : {
              "type" : "object"
            },
            "description" : "successful operation",
            "required" : false
          }
        }
      }
    },
    "/store/order" : {
      "post" : {
        "summary" : "Place an order for a pet",
        "description" : "",
        "operationId" : "placeOrder",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "store" ],
        "parameters" : [ {
          "in" : "body",
          "name" : "body",
          "required" : false,
          "schema" : {
            "$ref" : "#/definitions/Order"
          },
          "description" : "order placed for purchasing the pet"
        } ],
        "responses" : {
          "200" : {
            "schema" : {
              "$ref" : "#/definitions/Order"
            },
            "description" : "successful operation",
            "required" : false
          },
          "400" : {
            "description" : "Invalid Order",
            "required" : false
          }
        }
      }
    },
    "/store/order/{orderId}" : {
      "get" : {
        "summary" : "Find purchase order by ID",
        "description" : "For valid response try integer IDs with value >= 1 and <= 10. Other values will generated exceptions",
        "operationId" : "getOrderById",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "store" ],
        "responses" : {
          "200" : {
            "schema" : {
              "$ref" : "#/definitions/Order"
            },
            "description" : "successful operation",
            "required" : false
          },
          "400" : {
            "description" : "Invalid ID supplied",
            "required" : false
          },
          "404" : {
            "description" : "Order not found",
            "required" : false
          }
        }
      },
      "delete" : {
        "summary" : "Delete purchase order by ID",
        "description" : "For valid response try integer IDs with positive integer value. Negative or non-integer values will generate API errors",
        "operationId" : "deleteOrder",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "store" ],
        "responses" : {
          "400" : {
            "description" : "Invalid ID supplied",
            "required" : false
          },
          "404" : {
            "description" : "Order not found",
            "required" : false
          }
        }
      },
      "parameters" : [ {
        "type" : "integer",
        "description" : "ID of pet that needs to be fetched",
        "name" : "orderId",
        "in" : "path",
        "format" : "int64",
        "maximum" : 10,
        "minimum" : 1
      } ]
    },
    "/user/createWithList" : {
      "post" : {
        "summary" : "Creates list of users with given input array",
        "description" : "",
        "operationId" : "createUsersWithListInput",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "parameters" : [ {
          "in" : "body",
          "name" : "body",
          "required" : false,
          "schema" : {
            "type" : "array",
            "items" : {
              "$ref" : "#/definitions/User"
            }
          },
          "description" : "List of user object"
        } ],
        "responses" : {
          "default" : {
            "description" : "successful operation",
            "required" : false
          }
        }
      }
    },
    "/user/login" : {
      "get" : {
        "summary" : "Logs user into the system",
        "description" : "",
        "operationId" : "loginUser",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "parameters" : [ {
          "name" : "password",
          "in" : "query",
          "type" : "string",
          "description" : "The password for login in clear text"
        }, {
          "name" : "username",
          "in" : "query",
          "type" : "string",
          "description" : "The user name for login"
        } ],
        "responses" : {
          "200" : {
            "schema" : {
              "type" : "string"
            },
            "headers" : {
              "X-Rate-Limit" : {
                "type" : "integer",
                "description" : "calls per hour allowed by the user",
                "format" : "int32"
              },
              "X-Expires-After" : {
                "type" : "string",
                "description" : "date in UTC when token expires",
                "format" : "date-time"
              }
            },
            "description" : "successful operation",
            "required" : false
          },
          "400" : {
            "description" : "Invalid username/password supplied",
            "required" : false
          }
        }
      }
    },
    "/user" : {
      "post" : {
        "summary" : "Create user",
        "description" : "This can only be done by the logged in user.",
        "operationId" : "createUser",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "parameters" : [ {
          "in" : "body",
          "name" : "body",
          "required" : false,
          "schema" : {
            "$ref" : "#/definitions/User"
          },
          "description" : "Created user object"
        } ],
        "responses" : {
          "default" : {
            "description" : "successful operation",
            "required" : false
          }
        }
      }
    },
    "/user/createWithArray" : {
      "post" : {
        "summary" : "Creates list of users with given input array",
        "description" : "",
        "operationId" : "createUsersWithArrayInput",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "parameters" : [ {
          "in" : "body",
          "name" : "body",
          "required" : false,
          "schema" : {
            "type" : "array",
            "items" : {
              "$ref" : "#/definitions/User"
            }
          },
          "description" : "List of user object"
        } ],
        "responses" : {
          "default" : {
            "description" : "successful operation",
            "required" : false
          }
        }
      }
    },
    "/user/{username}" : {
      "get" : {
        "summary" : "Get user by user name",
        "description" : "",
        "operationId" : "getUserByName",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "responses" : {
          "200" : {
            "schema" : {
              "$ref" : "#/definitions/User"
            },
            "description" : "successful operation",
            "required" : false
          },
          "400" : {
            "description" : "Invalid username supplied",
            "required" : false
          },
          "404" : {
            "description" : "User not found",
            "required" : false
          }
        }
      },
      "delete" : {
        "summary" : "Delete user",
        "description" : "This can only be done by the logged in user.",
        "operationId" : "deleteUser",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "responses" : {
          "400" : {
            "description" : "Invalid username supplied",
            "required" : false
          },
          "404" : {
            "description" : "User not found",
            "required" : false
          }
        }
      },
      "put" : {
        "summary" : "Updated user",
        "description" : "This can only be done by the logged in user.",
        "operationId" : "updateUser",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "parameters" : [ {
          "in" : "body",
          "name" : "body",
          "required" : false,
          "schema" : {
            "$ref" : "#/definitions/User"
          },
          "description" : "Updated user object"
        } ],
        "responses" : {
          "400" : {
            "description" : "Invalid user supplied",
            "required" : false
          },
          "404" : {
            "description" : "User not found",
            "required" : false
          }
        }
      },
      "parameters" : [ {
        "type" : "string",
        "description" : "The name that needs to be fetched. Use user1 for testing. ",
        "name" : "username",
        "in" : "path"
      } ]
    },
    "/user/logout" : {
      "get" : {
        "summary" : "Logs out current logged in user session",
        "description" : "",
        "operationId" : "logoutUser",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "responses" : {
          "default" : {
            "description" : "successful operation",
            "required" : false
          }
        }
      }
    },
    "/pet/findByStatus" : {
      "get" : {
        "summary" : "Finds Pets by status",
        "description" : "Multiple status values can be provided with comma separated strings",
        "operationId" : "findPetsByStatus",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "pet" ],
        "parameters" : [ {
          "name" : "status",
          "in" : "query",
          "type" : "array",
          "description" : "Status values that need to be considered for filter",
          "collectionFormat" : "multi",
          "items" : {
            "type" : "string",
            "enum" : [ "available", "pending", "sold" ],
            "default" : "available"
          }
        } ],
        "responses" : {
          "200" : {
            "schema" : {
              "type" : "array",
              "items" : {
                "$ref" : "#/definitions/Pet"
              }
            },
            "description" : "successful operation",
            "required" : false
          },
          "400" : {
            "description" : "Invalid status value",
            "required" : false
          }
        }
      }
    },
    "/pet/{petId}/uploadImage" : {
      "post" : {
        "summary" : "uploads an image",
        "description" : "",
        "operationId" : "uploadFile",
        "consumes" : [ "multipart/form-data" ],
        "produces" : [ "application/json" ],
        "tags" : [ "pet" ],
        "parameters" : [ {
          "type" : "file",
          "description" : "file to upload",
          "name" : "file",
          "in" : "formData"
        }, {
          "type" : "string",
          "description" : "Additional data to pass to server",
          "name" : "additionalMetadata",
          "in" : "formData"
        } ],
        "responses" : {
          "200" : {
            "schema" : {
              "$ref" : "#/definitions/ApiResponse"
            },
            "description" : "successful operation",
            "required" : false
          }
        }
      },
      "parameters" : [ {
        "type" : "integer",
        "description" : "ID of pet to update",
        "name" : "petId",
        "in" : "path",
        "format" : "int64"
      } ]
    },
    "/pet/findByTags" : {
      "get" : {
        "summary" : "Finds Pets by tags",
        "description" : "Multiple tags can be provided with comma separated strings. Use tag1, tag2, tag3 for testing.",
        "operationId" : "findPetsByTags",
        "deprecated" : true,
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "pet" ],
        "parameters" : [ {
          "name" : "tags",
          "in" : "query",
          "type" : "array",
          "description" : "Tags to filter by",
          "collectionFormat" : "multi",
          "items" : {
            "type" : "string"
          }
        } ],
        "responses" : {
          "200" : {
            "schema" : {
              "type" : "array",
              "items" : {
                "$ref" : "#/definitions/Pet"
              }
            },
            "description" : "successful operation",
            "required" : false
          },
          "400" : {
            "description" : "Invalid tag value",
            "required" : false
          }
        }
      }
    },
    "/pet/{petId}" : {
      "post" : {
        "summary" : "Updates a pet in the store with form data",
        "description" : "",
        "operationId" : "updatePetWithForm",
        "consumes" : [ "application/x-www-form-urlencoded" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "pet" ],
        "parameters" : [ {
          "type" : "string",
          "description" : "Updated name of the pet",
          "name" : "name",
          "in" : "formData"
        }, {
          "type" : "string",
          "description" : "Updated status of the pet",
          "name" : "status",
          "in" : "formData"
        } ],
        "responses" : {
          "405" : {
            "description" : "Invalid input",
            "required" : false
          }
        }
      },
      "get" : {
        "summary" : "Find pet by ID",
        "description" : "Returns a single pet",
        "operationId" : "getPetById",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "pet" ],
        "responses" : {
          "200" : {
            "schema" : {
              "$ref" : "#/definitions/Pet"
            },
            "description" : "successful operation",
            "required" : false
          },
          "400" : {
            "description" : "Invalid ID supplied",
            "required" : false
          },
          "404" : {
            "description" : "Pet not found",
            "required" : false
          }
        }
      },
      "delete" : {
        "summary" : "Deletes a pet",
        "description" : "",
        "operationId" : "deletePet",
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "pet" ],
        "parameters" : [ {
          "name" : "api_key",
          "in" : "header",
          "type" : "string"
        } ],
        "responses" : {
          "400" : {
            "description" : "Invalid ID supplied",
            "required" : false
          },
          "404" : {
            "description" : "Pet not found",
            "required" : false
          }
        }
      },
      "parameters" : [ {
        "type" : "integer",
        "description" : "ID of pet to return",
        "name" : "petId",
        "in" : "path",
        "format" : "int64"
      } ]
    },
    "/pet/{petId2}/{petId3}" : {
      "patch" : {
        "summary" : "patch",
        "description" : "",
        "operationId" : "",
        "consumes" : [ ],
        "produces" : [ ],
        "tags" : [ "pet" ],
        "parameters" : [ {
          "name" : "petId",
          "in" : "query",
          "type" : "string",
          "description" : "",
          "example" : "",
          "enum" : [ ]
        }, {
          "name" : "session-id",
          "in" : "header",
          "type" : "string",
          "description" : "",
          "example" : "",
          "enum" : [ ]
        } ],
        "responses" : {
          "200" : {
            "schema" : {
              "type" : "string",
              "enum" : [ ]
            },
            "headers" : { },
            "description" : "",
            "required" : false
          },
          "202" : {
            "headers" : { },
            "description" : "",
            "required" : false
          }
        }
      },
      "post" : {
        "summary" : "Add a new pet to the store",
        "description" : "",
        "operationId" : "addPet",
        "consumes" : [ "application/json", "application/xml" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "pet" ],
        "parameters" : [ {
          "in" : "body",
          "name" : "body",
          "required" : false,
          "schema" : {
            "type" : "object",
            "properties" : {
              "qnumber" : {
                "type" : "number",
                "description" : "qnumber desc",
                "example" : "22",
                "format" : "double",
                "maximum" : 3,
                "minimum" : 2,
                "enum" : [ "1.0", "2.0", "3.0" ],
                "default" : 22.0
              },
              "qstring" : {
                "type" : "string",
                "description" : "qstring desc",
                "example" : "example1",
                "pattern" : "qweasd",
                "maxLength" : 3,
                "enum" : [ "string1", "string2" ],
                "default" : "eq"
              },
              "qinteger" : {
                "type" : "integer",
                "format" : "int32"
              },
              "qboolean" : {
                "type" : "boolean",
                "example" : "true",
                "default" : true
              },
              "qarray" : {
                "type" : "array",
                "description" : "desc1",
                "items" : {
                  "type" : "array",
                  "description" : "desc2",
                  "items" : {
                    "type" : "array",
                    "description" : "desc3",
                    "items" : {
                      "type" : "string",
                      "description" : "strdesc",
                      "example" : "exa1",
                      "pattern" : "daasdad",
                      "maxLength" : 6,
                      "minLength" : 5,
                      "enum" : [ "asd", "qwe" ],
                      "default" : "default"
                    },
                    "example" : "5",
                    "maxItems" : 5,
                    "minItems" : 4
                  },
                  "example" : "2",
                  "maxItems" : 4,
                  "minItems" : 3
                },
                "example" : "1",
                "maxItems" : 3,
                "minItems" : 1
              }
            }
          },
          "description" : "Pet object that needs to be added to the store"
        } ],
        "responses" : {
          "405" : {
            "description" : "Invalid input",
            "required" : false
          }
        }
      },
      "put" : {
        "summary" : "Update an existing pet",
        "description" : "",
        "operationId" : "updatePet",
        "consumes" : [ "application/json", "application/xml" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "pet" ],
        "parameters" : [ {
          "in" : "body",
          "name" : "body",
          "required" : false,
          "schema" : {
            "$ref" : "#/definitions/Pet"
          },
          "description" : "Pet object that needs to be added to the store"
        } ],
        "responses" : {
          "400" : {
            "description" : "Invalid ID supplied",
            "required" : false
          },
          "404" : {
            "description" : "Pet not found",
            "required" : false
          },
          "405" : {
            "description" : "Validation exception",
            "required" : false
          }
        }
      },
      "parameters" : [ {
        "type" : "integer",
        "name" : "petId2",
        "format" : "",
        "enum" : [ ]
      }, {
        "type" : "string",
        "name" : "petId3",
        "enum" : [ ]
      } ]
    }
  },
  "definitions" : {
    "Order" : {
      "schema" : {
        "type" : "object",
        "properties" : {
          "petId" : {
            "type" : "integer",
            "format" : "int64"
          },
          "quantity" : {
            "type" : "integer",
            "format" : "int32"
          },
          "id" : {
            "type" : "integer",
            "format" : "int64"
          },
          "shipDate" : {
            "type" : "string",
            "format" : "date-time"
          },
          "complete" : {
            "type" : "boolean",
            "default" : false
          },
          "status" : {
            "type" : "string",
            "description" : "Order Status",
            "enum" : [ "placed", "approved", "delivered" ]
          }
        },
        "xml" : {
          "name" : "Order"
        }
      }
    },
    "newModel" : {
      "schema" : {
        "type" : "object",
        "name" : "obj1",
        "properties" : {
          "obj-str" : {
            "type" : "string",
            "name" : "obj-str",
            "enum" : [ ],
            "default" : ""
          },
          "obj-num" : {
            "type" : "number",
            "name" : "obj-num",
            "enum" : [ ],
            "default" : "2"
          }
        }
      },
      "description" : ""
    },
    "User" : {
      "schema" : {
        "type" : "object",
        "properties" : {
          "firstName" : {
            "type" : "string"
          },
          "lastName" : {
            "type" : "string"
          },
          "password" : {
            "type" : "string"
          },
          "userStatus" : {
            "type" : "integer",
            "description" : "User Status",
            "format" : "int32"
          },
          "phone" : {
            "type" : "string"
          },
          "id" : {
            "type" : "integer",
            "format" : "int64"
          },
          "email" : {
            "type" : "string"
          },
          "username" : {
            "type" : "string"
          }
        },
        "xml" : {
          "name" : "User"
        }
      }
    },
    "Category" : {
      "schema" : {
        "type" : "object",
        "properties" : {
          "name" : {
            "type" : "string"
          },
          "id" : {
            "type" : "integer",
            "format" : "int64"
          }
        },
        "xml" : {
          "name" : "Category"
        }
      }
    },
    "Tag" : {
      "schema" : {
        "type" : "object",
        "properties" : {
          "name" : {
            "type" : "string"
          },
          "id" : {
            "type" : "integer",
            "format" : "int64"
          }
        },
        "xml" : {
          "name" : "Tag"
        }
      }
    },
    "Pet" : {
      "schema" : {
        "type" : "object",
        "properties" : {
          "photoUrls" : {
            "type" : "array",
            "items" : {
              "type" : "string"
            },
            "xml" : {
              "name" : "photoUrl",
              "wrapped" : true
            }
          },
          "name" : {
            "type" : "string",
            "example" : "doggie"
          },
          "id" : {
            "type" : "integer",
            "format" : "int64"
          },
          "category" : {
            "$ref" : "#/definitions/Category"
          },
          "tags" : {
            "type" : "array",
            "items" : {
              "$ref" : "#/definitions/Tag"
            },
            "xml" : {
              "name" : "tag",
              "wrapped" : true
            }
          },
          "status" : {
            "type" : "string",
            "description" : "pet status in the store",
            "enum" : [ "available", "pending", "sold" ]
          }
        },
        "xml" : {
          "name" : "Pet"
        }
      }
    },
    "ApiResponse" : {
      "schema" : {
        "type" : "object",
        "properties" : {
          "code" : {
            "type" : "integer",
            "format" : "int32"
          },
          "type" : {
            "type" : "string"
          },
          "message" : {
            "type" : "string"
          }
        }
      }
    }
  },
  "securityDefinitions" : {
    "petstore_auth" : {
      "type" : "oauth2",
      "flow" : "implicit",
      "authorizationUrl" : "https://petstore.swagger.io/oauth/authorize",
      "scopes" : {
        "write:pets" : "modify pets in your account",
        "read:pets" : "read your pets"
      }
    },
    "api_key" : {
      "type" : "apiKey",
      "name" : "api_key",
      "in" : "header"
    }
  }
}
