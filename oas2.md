{
  "schema" : [ "https", "http" ],
  "basePath" : "/v2",
  "paths" : {
    "/store/inventory" : {
      "get" : {
        "summary" : "Returns pet inventories by status",
        "description" : "Returns a map of status codes to quantities",
        "operationId" : "getInventory",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
        "produces" : [ "application/json" ],
        "tags" : [ "store" ],
        "parameters" : [ ],
        "responses" : {
          "200" : {
            "in" : "",
            "description" : "successful operation",
            "required" : false,
            "schema" : {
              "type" : "object",
              "additionalProperties" : {
                "type" : "integer",
                "format" : "int32"
              }
            }
          }
        }
      },
      "parameters" : [ ]
    },
    "/store/order" : {
      "post" : {
        "summary" : "Place an order for a pet",
        "description" : "",
        "operationId" : "placeOrder",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "store" ],
        "parameters" : [ {
          "in" : "body",
          "name" : "body",
          "required" : false,
          "schema" : {
            "$ref" : "#/definitions/Order"
          },
          "type" : null,
          "description" : null
        } ],
        "responses" : {
          "200" : {
            "in" : "",
            "description" : "successful operation",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/Order"
            }
          },
          "400" : {
            "in" : "",
            "description" : "Invalid Order",
            "required" : false
          }
        }
      },
      "parameters" : [ ]
    },
    "/store/order/{orderId}" : {
      "get" : {
        "summary" : "Find purchase order by ID",
        "description" : "For valid response try integer IDs with value >= 1 and <= 10. Other values will generated exceptions",
        "operationId" : "getOrderById",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "store" ],
        "parameters" : [ ],
        "responses" : {
          "200" : {
            "in" : "",
            "description" : "successful operation",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/Order"
            }
          },
          "400" : {
            "in" : "",
            "description" : "Invalid ID supplied",
            "required" : false
          },
          "404" : {
            "in" : "",
            "description" : "Order not found",
            "required" : false
          }
        }
      },
      "delete" : {
        "summary" : "Delete purchase order by ID",
        "description" : "For valid response try integer IDs with positive integer value. Negative or non-integer values will generate API errors",
        "operationId" : "deleteOrder",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "store" ],
        "parameters" : [ ],
        "responses" : {
          "400" : {
            "in" : "",
            "description" : "Invalid ID supplied",
            "required" : false
          },
          "404" : {
            "in" : "",
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
        "deprecated" : null,
        "consumes" : [ "application/json" ],
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
          "type" : null,
          "description" : null
        } ],
        "responses" : {
          "default" : {
            "in" : "",
            "description" : "successful operation",
            "required" : false
          }
        }
      },
      "parameters" : [ ]
    },
    "/user/login" : {
      "get" : {
        "summary" : "Logs user into the system",
        "description" : "",
        "operationId" : "loginUser",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
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
            "in" : "",
            "description" : "successful operation",
            "required" : false,
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
            "schema" : {
              "type" : "string"
            }
          },
          "400" : {
            "in" : "",
            "description" : "Invalid username/password supplied",
            "required" : false
          }
        }
      },
      "parameters" : [ ]
    },
    "/user" : {
      "post" : {
        "summary" : "Create user",
        "description" : "This can only be done by the logged in user.",
        "operationId" : "createUser",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "parameters" : [ {
          "in" : "body",
          "name" : "body",
          "required" : false,
          "schema" : {
            "$ref" : "#/definitions/User"
          },
          "type" : null,
          "description" : null
        } ],
        "responses" : {
          "default" : {
            "in" : "",
            "description" : "successful operation",
            "required" : false
          }
        }
      },
      "parameters" : [ ]
    },
    "/user/createWithArray" : {
      "post" : {
        "summary" : "Creates list of users with given input array",
        "description" : "",
        "operationId" : "createUsersWithArrayInput",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
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
          "type" : null,
          "description" : null
        } ],
        "responses" : {
          "default" : {
            "in" : "",
            "description" : "successful operation",
            "required" : false
          }
        }
      },
      "parameters" : [ ]
    },
    "/user/{username}" : {
      "get" : {
        "summary" : "Get user by user name",
        "description" : "",
        "operationId" : "getUserByName",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "parameters" : [ ],
        "responses" : {
          "200" : {
            "in" : "",
            "description" : "successful operation",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/User"
            }
          },
          "400" : {
            "in" : "",
            "description" : "Invalid username supplied",
            "required" : false
          },
          "404" : {
            "in" : "",
            "description" : "User not found",
            "required" : false
          }
        }
      },
      "delete" : {
        "summary" : "Delete user",
        "description" : "This can only be done by the logged in user.",
        "operationId" : "deleteUser",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "parameters" : [ ],
        "responses" : {
          "400" : {
            "in" : "",
            "description" : "Invalid username supplied",
            "required" : false
          },
          "404" : {
            "in" : "",
            "description" : "User not found",
            "required" : false
          }
        }
      },
      "put" : {
        "summary" : "Updated user",
        "description" : "This can only be done by the logged in user.",
        "operationId" : "updateUser",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "parameters" : [ {
          "in" : "body",
          "name" : "body",
          "required" : false,
          "schema" : {
            "$ref" : "#/definitions/User"
          },
          "type" : null,
          "description" : null
        } ],
        "responses" : {
          "400" : {
            "in" : "",
            "description" : "Invalid user supplied",
            "required" : false
          },
          "404" : {
            "in" : "",
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
        "deprecated" : null,
        "consumes" : [ "application/json" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "user" ],
        "parameters" : [ ],
        "responses" : {
          "default" : {
            "in" : "",
            "description" : "successful operation",
            "required" : false
          }
        }
      },
      "parameters" : [ ]
    },
    "/pet/findByStatus" : {
      "get" : {
        "summary" : "Finds Pets by status",
        "description" : "Multiple status values can be provided with comma separated strings",
        "operationId" : "findPetsByStatus",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
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
            "in" : "",
            "description" : "successful operation",
            "required" : false,
            "schema" : {
              "type" : "array",
              "items" : {
                "$ref" : "#/definitions/Pet"
              }
            }
          },
          "400" : {
            "in" : "",
            "description" : "Invalid status value",
            "required" : false
          }
        }
      },
      "parameters" : [ ]
    },
    "/pet/{petId}/uploadImage" : {
      "post" : {
        "summary" : "uploads an image",
        "description" : "",
        "operationId" : "uploadFile",
        "deprecated" : null,
        "consumes" : [ "multipart/form-data" ],
        "produces" : [ "application/json" ],
        "tags" : [ "pet" ],
        "parameters" : [ {
          "in" : "formData",
          "name" : "formData",
          "required" : false,
          "schema" : {
            "type" : "object",
            "properties" : {
              "file" : {
                "type" : "file",
                "description" : "file to upload",
                "name" : "file",
                "in" : "formData"
              },
              "additionalMetadata" : {
                "type" : "string",
                "description" : "Additional data to pass to server",
                "name" : "additionalMetadata",
                "in" : "formData"
              }
            }
          },
          "type" : null,
          "description" : null
        } ],
        "responses" : {
          "200" : {
            "in" : "",
            "description" : "successful operation",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/ApiResponse"
            }
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
    "/pet" : {
      "post" : {
        "summary" : "Add a new pet to the store",
        "description" : "",
        "operationId" : "addPet",
        "deprecated" : null,
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
          "type" : null,
          "description" : null
        } ],
        "responses" : {
          "405" : {
            "in" : "",
            "description" : "Invalid input",
            "required" : false
          }
        }
      },
      "put" : {
        "summary" : "Update an existing pet",
        "description" : "",
        "operationId" : "updatePet",
        "deprecated" : null,
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
          "type" : null,
          "description" : null
        } ],
        "responses" : {
          "400" : {
            "in" : "",
            "description" : "Invalid ID supplied",
            "required" : false
          },
          "404" : {
            "in" : "",
            "description" : "Pet not found",
            "required" : false
          },
          "405" : {
            "in" : "",
            "description" : "Validation exception",
            "required" : false
          }
        }
      },
      "parameters" : [ ]
    },
    "/pet/findByTags" : {
      "get" : {
        "summary" : "Finds Pets by tags",
        "description" : "Multiple tags can be provided with comma separated strings. Use tag1, tag2, tag3 for testing.",
        "operationId" : "findPetsByTags",
        "deprecated" : true,
        "consumes" : [ "application/json" ],
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
            "in" : "",
            "description" : "successful operation",
            "required" : false,
            "schema" : {
              "type" : "array",
              "items" : {
                "$ref" : "#/definitions/Pet"
              }
            }
          },
          "400" : {
            "in" : "",
            "description" : "Invalid tag value",
            "required" : false
          }
        }
      },
      "parameters" : [ ]
    },
    "/pet/{petId}" : {
      "post" : {
        "summary" : "Updates a pet in the store with form data",
        "description" : "",
        "operationId" : "updatePetWithForm",
        "deprecated" : null,
        "consumes" : [ "application/x-www-form-urlencoded" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "pet" ],
        "parameters" : [ {
          "in" : "formData",
          "name" : "formData",
          "required" : false,
          "schema" : {
            "type" : "object",
            "properties" : {
              "name" : {
                "type" : "string",
                "description" : "Updated name of the pet",
                "name" : "name",
                "in" : "formData"
              },
              "status" : {
                "type" : "string",
                "description" : "Updated status of the pet",
                "name" : "status",
                "in" : "formData"
              }
            }
          },
          "type" : null,
          "description" : null
        } ],
        "responses" : {
          "405" : {
            "in" : "",
            "description" : "Invalid input",
            "required" : false
          }
        }
      },
      "get" : {
        "summary" : "Find pet by ID",
        "description" : "Returns a single pet",
        "operationId" : "getPetById",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "pet" ],
        "parameters" : [ ],
        "responses" : {
          "200" : {
            "in" : "",
            "description" : "successful operation",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/Pet"
            }
          },
          "400" : {
            "in" : "",
            "description" : "Invalid ID supplied",
            "required" : false
          },
          "404" : {
            "in" : "",
            "description" : "Pet not found",
            "required" : false
          }
        }
      },
      "delete" : {
        "summary" : "Deletes a pet",
        "description" : "",
        "operationId" : "deletePet",
        "deprecated" : null,
        "consumes" : [ "application/json" ],
        "produces" : [ "application/xml", "application/json" ],
        "tags" : [ "pet" ],
        "parameters" : [ {
          "name" : "api_key",
          "in" : "header",
          "type" : "string"
        } ],
        "responses" : {
          "400" : {
            "in" : "",
            "description" : "Invalid ID supplied",
            "required" : false
          },
          "404" : {
            "in" : "",
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
    }
  },
  "host" : "petstore.swagger.io",
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
      "in" : "header",
      "scopes" : { }
    }
  },
  "swagger" : "2.0",
  "info" : {
    "license" : {
      "name" : "Apache 2.0",
      "description" : null,
      "email" : null,
      "url" : "http://www.apache.org/licenses/LICENSE-2.0.html"
    },
    "contact" : {
      "name" : null,
      "description" : null,
      "email" : "apiteam@swagger.io",
      "url" : null
    },
    "description" : "This is a sample server Petstore server.  You can find out more about Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).  For this sample, you can use the api key `special-key` to test the authorization filters.",
    "termsOfService" : "http://swagger.io/terms/",
    "title" : "Swagger Petstore",
    "version" : "1.0.0"
  }
}