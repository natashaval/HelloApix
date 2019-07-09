{
  "swagger" : "2.0",
  "info" : {
    "license" : null,
    "contact" : null,
    "description" : "Move your app forward with the Uber API",
    "termsOfService" : null,
    "title" : "Uber API",
    "version" : "1.0.0"
  },
  "host" : "api.uber.com",
  "basePath" : "/v1",
  "externalDocs" : null,
  "schema" : null,
  "tags" : [ { }, { }, { } ],
  "paths" : {
    "/products" : {
      "get" : {
        "summary" : "Product Types",
        "description" : "The Products endpoint returns information about the Uber products offered at a given location. The response includes the display name and other details about each product, and lists the products in the proper display order.",
        "produces" : null,
        "tags" : [ "Products" ],
        "parameters" : [ {
          "name" : "latitude",
          "in" : "query",
          "type" : "number",
          "description" : "Latitude component of location.",
          "format" : "double"
        }, {
          "name" : "longitude",
          "in" : "query",
          "type" : "number",
          "description" : "Longitude component of location.",
          "format" : "double"
        } ],
        "responses" : {
          "200" : {
            "description" : "An array of products",
            "required" : false,
            "schema" : {
              "type" : "array",
              "items" : {
                "type" : "object",
                "$ref" : "#/definitions/Product"
              }
            }
          },
          "default" : {
            "description" : "Unexpected error",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/Error"
            }
          }
        }
      }
    },
    "/history" : {
      "get" : {
        "summary" : "User Activity",
        "description" : "The User Activity endpoint returns data about a user's lifetime activity with Uber. The response will include pickup locations and times, dropoff locations and times, the distance of past requests, and information about which products were requested.<br><br>The history array in the response will have a maximum length based on the limit parameter. The response value count may exceed limit, therefore subsequent API requests may be necessary.",
        "produces" : null,
        "tags" : [ "User" ],
        "parameters" : [ {
          "name" : "offset",
          "in" : "query",
          "type" : "integer",
          "description" : "Offset the list of returned results by this amount. Default is zero.",
          "format" : "int32"
        }, {
          "name" : "limit",
          "in" : "query",
          "type" : "integer",
          "description" : "Number of items to retrieve. Default is 5, maximum is 100.",
          "format" : "int32"
        } ],
        "responses" : {
          "200" : {
            "description" : "History information for the given user",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/Activities"
            }
          },
          "default" : {
            "description" : "Unexpected error",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/Error"
            }
          }
        }
      }
    },
    "/me" : {
      "get" : {
        "summary" : "User Profile",
        "description" : "The User Profile endpoint returns information about the Uber user that has authorized with the application.",
        "produces" : null,
        "tags" : [ "User" ],
        "responses" : {
          "200" : {
            "description" : "Profile information for a user",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/Profile"
            }
          },
          "default" : {
            "description" : "Unexpected error",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/Error"
            }
          }
        }
      }
    },
    "/estimates/price" : {
      "get" : {
        "summary" : "Price Estimates",
        "description" : "The Price Estimates endpoint returns an estimated price range for each product offered at a given location. The price estimate is provided as a formatted string with the full price range and the localized currency symbol.<br><br>The response also includes low and high estimates, and the [ISO 4217](http://en.wikipedia.org/wiki/ISO_4217) currency code for situations requiring currency conversion. When surge is active for a particular product, its surge_multiplier will be greater than 1, but the price estimate already factors in this multiplier.",
        "produces" : null,
        "tags" : [ "Estimates" ],
        "parameters" : [ {
          "name" : "start_longitude",
          "in" : "query",
          "type" : "number",
          "description" : "Longitude component of start location.",
          "format" : "double"
        }, {
          "name" : "start_latitude",
          "in" : "query",
          "type" : "number",
          "description" : "Latitude component of start location.",
          "format" : "double"
        }, {
          "name" : "end_longitude",
          "in" : "query",
          "type" : "number",
          "description" : "Longitude component of end location.",
          "format" : "double"
        }, {
          "name" : "end_latitude",
          "in" : "query",
          "type" : "number",
          "description" : "Latitude component of end location.",
          "format" : "double"
        } ],
        "responses" : {
          "200" : {
            "description" : "An array of price estimates by product",
            "required" : false,
            "schema" : {
              "type" : "array",
              "items" : {
                "type" : "object",
                "$ref" : "#/definitions/PriceEstimate"
              }
            }
          },
          "default" : {
            "description" : "Unexpected error",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/Error"
            }
          }
        }
      }
    },
    "/estimates/time" : {
      "get" : {
        "summary" : "Time Estimates",
        "description" : "The Time Estimates endpoint returns ETAs for all products offered at a given location, with the responses expressed as integers in seconds. We recommend that this endpoint be called every minute to provide the most accurate, up-to-date ETAs.",
        "produces" : null,
        "tags" : [ "Estimates" ],
        "parameters" : [ {
          "name" : "start_longitude",
          "in" : "query",
          "type" : "number",
          "description" : "Longitude component of start location.",
          "format" : "double"
        }, {
          "name" : "start_latitude",
          "in" : "query",
          "type" : "number",
          "description" : "Latitude component of start location.",
          "format" : "double"
        }, {
          "name" : "customer_uuid",
          "in" : "query",
          "type" : "string",
          "description" : "Unique customer identifier to be used for experience customization.",
          "format" : "uuid"
        }, {
          "name" : "product_id",
          "in" : "query",
          "type" : "string",
          "description" : "Unique identifier representing a specific product for a given latitude & longitude."
        } ],
        "responses" : {
          "200" : {
            "description" : "An array of products",
            "required" : false,
            "schema" : {
              "type" : "array",
              "items" : {
                "type" : "object",
                "$ref" : "#/definitions/Product"
              }
            }
          },
          "default" : {
            "description" : "Unexpected error",
            "required" : false,
            "schema" : {
              "$ref" : "#/definitions/Error"
            }
          }
        }
      }
    }
  },
  "definitions" : {
    "Activities" : {
      "schema" : {
        "properties" : {
          "offset" : {
            "type" : "integer",
            "description" : "Position in pagination.",
            "format" : "int32"
          },
          "limit" : {
            "type" : "integer",
            "description" : "Number of items to retrieve (100 max).",
            "format" : "int32"
          },
          "count" : {
            "type" : "integer",
            "description" : "Total number of items available.",
            "format" : "int32"
          },
          "history" : {
            "type" : "array",
            "items" : {
              "type" : "object",
              "$ref" : "#/definitions/Activity"
            }
          }
        }
      },
      "_signature" : "7f1ecd4d-ea57-4edd-9637-f88322d95e05"
    },
    "Activity" : {
      "schema" : {
        "properties" : {
          "uuid" : {
            "type" : "string",
            "description" : "Unique identifier for the activity"
          }
        }
      },
      "_signature" : "164a5011-f392-4a5c-aaf2-4992a1afa276"
    },
    "Error" : {
      "schema" : {
        "properties" : {
          "code" : {
            "type" : "integer",
            "format" : "int32"
          },
          "message" : {
            "type" : "string"
          },
          "fields" : {
            "type" : "string"
          }
        }
      },
      "_signature" : "aba67b77-09e7-431c-8c5f-ab2099ad7fb3"
    },
    "Product" : {
      "schema" : {
        "properties" : {
          "image" : {
            "type" : "string",
            "description" : "Image URL representing the product."
          },
          "product_id" : {
            "type" : "string",
            "description" : "Unique identifier representing a specific product for a given latitude & longitude. For example, uberX in San Francisco will have a different product_id than uberX in Los Angeles."
          },
          "description" : {
            "type" : "string",
            "description" : "Description of product."
          },
          "display_name" : {
            "type" : "string",
            "description" : "Display name of product."
          },
          "capacity" : {
            "type" : "string",
            "description" : "Capacity of product. For example, 4 people."
          }
        }
      },
      "_signature" : "cce24540-9cd5-4cf9-a32d-f4e492ab5531"
    },
    "PriceEstimate" : {
      "schema" : {
        "properties" : {
          "high_estimate" : {
            "type" : "number",
            "description" : "Upper bound of the estimated price."
          },
          "product_id" : {
            "type" : "string",
            "description" : "Unique identifier representing a specific product for a given latitude & longitude. For example, uberX in San Francisco will have a different product_id than uberX in Los Angeles"
          },
          "low_estimate" : {
            "type" : "number",
            "description" : "Lower bound of the estimated price."
          },
          "surge_multiplier" : {
            "type" : "number",
            "description" : "Expected surge multiplier. Surge is active if surge_multiplier is greater than 1. Price estimate already factors in the surge multiplier."
          },
          "estimate" : {
            "type" : "string",
            "description" : "Formatted string of estimate in local currency of the start location. Estimate could be a range, a single number (flat rate) or \"Metered\" for TAXI."
          },
          "display_name" : {
            "type" : "string",
            "description" : "Display name of product."
          },
          "currency_code" : {
            "type" : "string",
            "description" : "[ISO 4217](http://en.wikipedia.org/wiki/ISO_4217) currency code."
          }
        }
      },
      "_signature" : "c7032cbd-8b41-4dd7-a277-b62b02b68bac"
    },
    "Profile" : {
      "schema" : {
        "properties" : {
          "last_name" : {
            "type" : "string",
            "description" : "Last name of the Uber user."
          },
          "promo_code" : {
            "type" : "string",
            "description" : "Promo code of the Uber user."
          },
          "first_name" : {
            "type" : "string",
            "description" : "First name of the Uber user."
          },
          "email" : {
            "type" : "string",
            "description" : "Email address of the Uber user"
          },
          "picture" : {
            "type" : "string",
            "description" : "Image URL of the Uber user."
          }
        }
      },
      "_signature" : "6e0ccd86-b31d-4731-ba21-e4723abcac57"
    }
  },
  "securityDefinitions" : { }
}
