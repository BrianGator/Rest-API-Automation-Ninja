# Rest API Automation With Rest Assured - Novice To Ninja

A comprehensive guide and practical examples for automating REST APIs using REST Assured library with Java. This repository contains step-by-step tutorials, real-world examples, and best practices for API test automation from beginner to advanced levels.

REST Assured is a powerful Java library that simplifies testing and validating RESTful APIs/RESTful Web services (similar to Selenium WebDriver for web applications). Almost all modern web applications use REST APIs to communicate, making API testing a critical part of QA.

**Written by Brian McCarthy**

---

## 📚 Table of Contents

- [Languages Used](#languages-used)
- [Methodologies Used](#methodologies-used)
- [File Structure](#file-structure)
- [Project Overview](#project-overview)
- [Code Methodologies & Patterns](#code-methodologies--patterns)
- [Getting Started](#getting-started)
- [REST API Automation Examples](#rest-api-automation-examples)
- [Tutorial & Guide](#tutorial--guide)
- [Tips & Best Practices](#tips--best-practices)
- [Learning Path](#learning-path)

---

## Languages Used

- **Java** (100%) - Core programming language for all test automation code
  - Version: Java 8 or higher recommended
  - Uses OOP principles, annotations, and lambda expressions

---

## Methodologies Used

### 1. **Behavior-Driven Development (BDD)**
```
Given I have this information
When I perform this action
Then this should be the output
```

### 2. **Test-Driven Development (TDD)**
- Write test cases first
- Design APIs based on test requirements
- Ensure code quality and maintainability

### 3. **Keyword-Driven Testing**
- Reusable test utilities
- Common keywords for API testing
- Modular and maintainable test code

### 4. **Data-Driven Testing**
- Parameterized tests
- Multiple test data scenarios
- XML/JSON response parsing

### 5. **API Testing Best Practices**
- Request/Response validation
- Status code verification
- Response time monitoring
- Authentication and authorization testing

---

## File Structure

```
Rest-API-Automation-Ninja/
│
├── README.md (this file)
│
├── S1 - S3/          # Foundational concepts and setup
│
├── S7/               # Basic API Automation Examples
│   ├── 1-GetRequestDemo.java
│   ├── 2-GetRequestDemo.java
│   ├── 4-ValidateResponse.java
│   ├── 5-POSTRequestDemo.java
│   ├── 6-POSTRequestWithPOJO.java
│   └── 6-PlacesAddModel.java (POJO Model)
│
├── S8/               # Twitter API Examples
│   └── 5-TwitterPOSTRequest.java
│
├── S11/              # Response Extraction
│   └── 1-GoogleExtractResponse.java
│
├── S12/              # Logging Examples
│   └── 2-RequestLoggingExample.java
│
├── S14/              # Useful Tricks & Techniques
│   ├── 1-TwitterRootPathExample.java
│   └── 2-TwitterCheckResponseTime.java
│
├── S15/              # Specifications
│   └── 2-RequestSpecificationDemo.java
│
├── S17/              # Utility Classes & Reusable Components
│   ├── 3-RestUtilities.java
│   └── 4-RestUtilities.java
│
├── S18-S21, S23/     # Advanced Workflows & Integration Tests
│   ├── UserTimelineTest.java
│   └── TwitterWorkflowTest.java
│
└── S19/              # End-to-End Workflows
    ├── 1-TwitterEndToEndWorkflow.java
    └── 2-TwitterWorkflowTest.java
```

---

## Project Overview

### What You Will Learn

- ✅ Design and structure API test automation frameworks
- ✅ Write GET, POST, PUT, and DELETE requests
- ✅ Validate response status codes, headers, and body content
- ✅ Extract and parse JSON/XML responses
- ✅ Implement request/response specifications
- ✅ Handle authentication (OAuth, Basic Auth)
- ✅ Create POJO (Plain Old Java Object) models for request/response mapping
- ✅ Build reusable utility classes
- ✅ Implement end-to-end API workflows
- ✅ Perform data-driven testing
- ✅ Monitor response times and performance

### Target Audience

- QA professionals and manual testers starting API automation
- QA automation professionals expanding their test automation skills
- Developers needing API testing knowledge
- Anyone interested in REST API testing with Java

---

## Code Methodologies & Patterns

### 1. **BDD/Given-When-Then Pattern**

Rest Assured uses a fluent API that naturally reads like BDD scenarios:

```java
@Test
public void testGetRequest() {
    given()                                    // Given - Setup preconditions
        .param("units", "imperial")
        .param("origins", "Washington,DC")
        .param("destinations", "New+York+City,NY")
        .param("key", "YOUR_API_KEY")
    .when()                                    // When - Perform action
        .get("/distancematrix/json")
    .then()                                    // Then - Verify results
        .statusCode(200)
        .body("rows[0].elements[0].distance.text", equalTo("225 mi"));
}
```

### 2. **POJO (Plain Old Java Object) Pattern**

Models for automatic request/response serialization/deserialization:

```java
public class PlacesAddModel {
    private Map<String, Double> location;
    private int accuracy;
    private String name;
    private String phone_number;
    private String address;
    private List<String> types;
    private String website;
    private String language;

    // Getters and setters...
}

// Usage in test:
PlacesAddModel places = new PlacesAddModel();
places.setLocation(locationMap);
places.setAccuracy(50);
places.setName("Google Shoes!");

given()
    .queryParam("key", "YOUR_API_KEY")
    .body(places)  // Automatically serialized to JSON
.when()
    .post("/place/add/json")
.then()
    .statusCode(200)
    .body("scope", equalTo("APP"));
```

### 3. **Request/Response Specifications Pattern**

Reusable specifications for common request/response patterns:

```java
public static RequestSpecification getRequestSpecification() {
    AuthenticationScheme authScheme = RestAssured.oauth(
        Auth.CONSUMER_KEY,
        Auth.CONSUMER_SECRET,
        Auth.ACCESS_TOKEN,
        Auth.ACCESS_SECRET
    );
    
    REQUEST_BUILDER = new RequestSpecBuilder();
    REQUEST_BUILDER.setBaseUri(Path.BASE_URI);
    REQUEST_BUILDER.setAuth(authScheme);
    REQUEST_SPEC = REQUEST_BUILDER.build();
    
    return REQUEST_SPEC;
}

public static ResponseSpecification getResponseSpecification() {
    RESPONSE_BUILDER = new ResponseSpecBuilder();
    RESPONSE_BUILDER.expectStatusCode(200);
    RESPONSE_BUILDER.expectResponseTime(lessThan(3L), TimeUnit.SECONDS);
    RESPONSE_SPEC = RESPONSE_BUILDER.build();
    
    return RESPONSE_SPEC;
}

// Usage in tests:
given()
    .spec(requestSpec)
.when()
    .get("/endpoint")
.then()
    .spec(responseSpec);
```

### 4. **Utility Class Pattern**

Centralized reusable methods for common API operations:

```java
public class RestUtilities {
    public static String ENDPOINT;
    public static RequestSpecification REQUEST_SPEC;
    
    public static RequestSpecification createQueryParam(
        RequestSpecification rspec,
        String param,
        String value) {
        return rspec.queryParam(param, value);
    }
    
    public static Response getResponse(
        RequestSpecification reqSpec,
        String type) {
        Response response = null;
        if (type.equalsIgnoreCase("get")) {
            response = given().spec(REQUEST_SPEC).get(ENDPOINT);
        } else if (type.equalsIgnoreCase("post")) {
            response = given().spec(REQUEST_SPEC).post(ENDPOINT);
        }
        response.then().log().all();
        return response;
    }
}
```

### 5. **End-to-End Workflow Pattern**

Chaining multiple API calls with data dependencies:

```java
@Test
public void postTweet() {
    Response response = given()
        .auth().oauth(consumerKey, consumerSecret, accessToken, accessSecret)
        .queryParam("status", "My First Tweet")
    .when()
        .post(EndPoints.STATUSES_TWEET_POST)
    .then()
        .statusCode(200)
        .extract()
        .response();
    
    tweetId = response.path("id_str");
}

@Test(dependsOnMethods = {"postTweet"})
public void readTweet() {
    Response res = given()
        .spec(requestSpec)
        .queryParam("id", tweetId)
    .when()
        .get(EndPoints.STATUSES_TWEET_READ)
    .then()
        .statusCode(200)
        .extract()
        .response();
}

@Test(dependsOnMethods = {"readTweet"})
public void deleteTweet() {
    given()
        .spec(requestSpec)
        .pathParam("id", tweetId)
    .when()
        .post(EndPoints.STATUSES_TWEET_DESTROY)
    .then()
        .statusCode(200);
}
```

---

## Getting Started

### Prerequisites

- Java 8 or higher installed
- Maven or Gradle for dependency management
- IDE (Eclipse, IntelliJ IDEA, or Visual Studio Code)
- TestNG framework for test execution

### Maven Dependencies

Add to your `pom.xml`:

```xml
<!-- REST Assured -->
<dependency>
    <groupId>io.rest-assured</groupId>
    <artifactId>rest-assured</artifactId>
    <version>4.5.1</version>
    <scope>test</scope>
</dependency>

<!-- TestNG -->
<dependency>
    <groupId>org.testng</groupId>
    <artifactId>testng</artifactId>
    <version>7.4.0</version>
    <scope>test</scope>
</dependency>

<!-- Hamcrest for assertions -->
<dependency>
    <groupId>org.hamcrest</groupId>
    <artifactId>hamcrest</artifactId>
    <version>2.2</version>
    <scope>test</scope>
</dependency>

<!-- JSON Path -->
<dependency>
    <groupId>io.rest-assured</groupId>
    <artifactId>json-path</artifactId>
    <version>4.5.1</version>
    <scope>test</scope>
</dependency>

<!-- Gson for JSON serialization -->
<dependency>
    <groupId>com.google.code.gson</groupId>
    <artifactId>gson</artifactId>
    <version>2.8.8</version>
</dependency>
```

---

## REST API Automation Examples

### Example 1: Simple GET Request

```java
@BeforeClass
public void setup() {
    RestAssured.baseURI = "https://maps.googleapis.com";
    RestAssured.basePath = "/maps/api";
}

@Test
public void getDistanceMatrix() {
    given()
        .param("units", "imperial")
        .param("origins", "Washington,DC")
        .param("destinations", "New+York+City,NY")
        .param("key", "YOUR_API_KEY")
    .when()
        .get("/distancematrix/json")
    .then()
        .statusCode(200);
}
```

### Example 2: POST Request with Body

```java
@Test
public void postWithJsonBody() {
    Response res = given()
        .queryParam("key", "YOUR_API_KEY")
        .body("{"
            + "\"location\": {"
            + "\"lat\": -33.8669710,"
            + "\"lng\": 151.1958750"
            + "},"
            + "\"accuracy\": 50,"
            + "\"name\": \"Google Shoes!\""
            + "}")
    .when()
        .post("/place/add/json");
    
    System.out.println(res.body().asString());
}
```

### Example 3: Response Validation

```java
@Test
public void validateResponse() {
    given()
        .param("units", "imperial")
        .param("origins", "Washington,DC")
        .param("destinations", "New+York+City,NY")
        .param("key", "YOUR_API_KEY")
    .when()
        .get("/distancematrix/json")
    .then()
        .statusCode(200)
        .and()
        .body("rows[0].elements[0].distance.text", equalTo("225 mi"))
        .contentType(ContentType.JSON);
}
```

### Example 4: Extract Response Data

```java
@Test
public void extractResponseData() {
    Response response = given()
        .queryParam("units", "imperial")
        .queryParam("origins", "Washington,DC")
        .queryParam("destinations", "New+York+City,NY")
        .queryParam("key", "YOUR_API_KEY")
    .when()
        .get("/distancematrix/xml")
    .then()
        .statusCode(200)
        .extract()
        .response();
    
    String responseString = response.asString();
    System.out.println(responseString);
    
    // Extract specific value using path
    String value = response.path("distancematrixresponse.row.element.duration.value");
    System.out.println("The duration value is: " + value);
}
```

### Example 5: POST with POJO

```java
@Test
public void postWithPOJO() {
    Map<String, Double> locationMap = new HashMap<>();
    locationMap.put("lat", -33.8669710);
    locationMap.put("lng", 151.1958750);
    
    ArrayList<String> types = new ArrayList<>();
    types.add("shoe_store");
    
    PlacesAddModel places = new PlacesAddModel();
    places.setLocation(locationMap);
    places.setAccuracy(50);
    places.setName("Google Shoes!");
    places.setPhone_number("(02) 9374 4000");
    places.setAddress("48 Pirrama Road, Pyrmont, NSW 2009, Australia");
    places.setTypes(types);
    places.setWebsite("http://www.google.com.au/");
    places.setLanguage("en-AU");
    
    given()
        .queryParam("key", "YOUR_API_KEY")
        .body(places)  // Automatically serialized to JSON
    .when()
        .post("/place/add/json")
    .then()
        .statusCode(200)
        .contentType(ContentType.JSON)
        .body("scope", equalTo("APP"))
        .body("status", equalTo("OK"));
}
```

### Example 6: Authentication (OAuth)

```java
@Test
public void oAuthRequest() {
    given()
        .auth()
        .oauth(consumerKey, consumerSecret, accessToken, accessSecret)
        .queryParam("user_id", "apiautomation")
    .when()
        .get("/user_timeline.json")
    .then()
        .statusCode(200);
}
```

### Example 7: Response Time Validation

```java
@Test
public void validateResponseTime() {
    given()
        .auth()
        .oauth(consumerKey, consumerSecret, accessToken, accessSecret)
        .queryParam("user_id", "apiautomation")
    .when()
        .get("/user_timeline.json")
    .then()
        .statusCode(200)
        .time(lessThan(1L), TimeUnit.SECONDS);
}
```

### Example 8: Request Specifications

```java
@BeforeClass
public void setup() {
    AuthenticationScheme authScheme = RestAssured.oauth(
        consumerKey,
        consumerSecret,
        accessToken,
        accessSecret
    );
    
    RequestSpecBuilder requestBuilder = new RequestSpecBuilder();
    requestBuilder.setBaseUri("https://api.twitter.com");
    requestBuilder.setBasePath("/1.1/statuses");
    requestBuilder.addQueryParam("user_id", "apiautomation");
    requestBuilder.setAuth(authScheme);
    requestSpec = requestBuilder.build();
}

@Test
public void testWithRequestSpec() {
    given()
        .spec(requestSpec)
    .when()
        .get("/user_timeline.json")
    .then()
        .statusCode(200);
}
```

### Example 9: Root Path for JSON Navigation

```java
@BeforeClass
public void setup() {
    RestAssured.baseURI = "https://api.twitter.com";
    RestAssured.basePath = "/1.1/statuses";
    RestAssured.rootPath = "entities.hashtags[0]";  // Set root path
}

@Test
public void testWithRootPath() {
    given()
        .auth()
        .oauth(consumerKey, consumerSecret, accessToken, accessSecret)
        .queryParam("user_id", "apiautomation")
    .when()
        .get("/user_timeline.json")
    .then()
        .statusCode(200)
        .body("text", hasItem("multiple"))
        .body("size()", equalTo(2));
}
```

### Example 10: End-to-End Workflow

```java
@Test
public void postTweet() {
    Response response = given()
        .auth()
        .oauth(consumerKey, consumerSecret, accessToken, accessSecret)
        .queryParam("status", "My First Tweet")
    .when()
        .post("/update.json")
    .then()
        .statusCode(200)
        .extract()
        .response();
    
    tweetId = response.path("id_str");
}

@Test(dependsOnMethods = {"postTweet"})
public void readTweet() {
    Response response = given()
        .auth()
        .oauth(consumerKey, consumerSecret, accessToken, accessSecret)
        .queryParam("id", tweetId)
    .when()
        .get("/show.json")
    .then()
        .extract()
        .response();
    
    String text = response.path("text");
    System.out.println("The tweet text is: " + text);
}

@Test(dependsOnMethods = {"readTweet"})
public void deleteTweet() {
    given()
        .auth()
        .oauth(consumerKey, consumerSecret, accessToken, accessSecret)
        .pathParam("id", tweetId)
    .when()
        .post("/destroy/{id}.json")
    .then()
        .statusCode(200);
}
```

---

## Tutorial & Guide

### Step 1: Setting Up Your First Test

1. Create a new Java class with @BeforeClass and @Test annotations
2. Initialize baseURI and basePath in @BeforeClass
3. Write your test using given-when-then syntax

```java
import io.restassured.RestAssured;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.Test;
import static io.restassured.RestAssured.given;

public class FirstAPITest {
    @BeforeClass
    public void setup() {
        RestAssured.baseURI = "https://api.example.com";
    }
    
    @Test
    public void testGetEndpoint() {
        given()
            .param("id", "123")
        .when()
            .get("/users")
        .then()
            .statusCode(200);
    }
}
```

### Step 2: Understanding Request Parameters

```java
// Query Parameters (in URL)
given()
    .queryParam("key", "value")
    .queryParam("search", "test")
    
// Path Parameters (replacing {variable} in path)
given()
    .pathParam("userId", "123")
.when()
    .get("/users/{userId}")
    
// Form Parameters (for form data)
given()
    .formParam("username", "john")
    .formParam("password", "secret")
    
// Header Parameters
given()
    .header("Authorization", "Bearer token")
    .header("Content-Type", "application/json")
```

### Step 3: Validating Responses

```java
// Status Code
.then()
    .statusCode(200)
    
// Content Type
.then()
    .contentType(ContentType.JSON)
    
// Body Content
.then()
    .body("status", equalTo("success"))
    .body("data.name", equalTo("John"))
    .body("data.age", greaterThan(18))
    .body("items", hasSize(5))
    
// Headers
.then()
    .header("Content-Type", containsString("application/json"))
```

### Step 4: Extracting Response Data

```java
// Extract entire response
Response response = given()
    .queryParam("id", "123")
.when()
    .get("/users")
.then()
    .extract()
    .response();

// Extract specific path
String name = response.path("data.name");
int age = response.path("data.age");

// Using JsonPath for complex parsing
JsonPath jsonPath = new JsonPath(response.asString());
List<String> names = jsonPath.getList("items.name");
```

### Step 5: Working with Authentication

```java
// Basic Authentication
given()
    .auth()
    .basic("username", "password")
    
// OAuth Authentication
given()
    .auth()
    .oauth(consumerKey, consumerSecret, accessToken, accessSecret)
    
// Bearer Token
given()
    .auth()
    .oauth2("access_token")
    .header("Authorization", "Bearer access_token")
```

### Step 6: Creating Reusable Request Specifications

```java
RequestSpecBuilder builder = new RequestSpecBuilder();
builder.setBaseUri("https://api.example.com");
builder.setBasePath("/api/v1");
builder.addHeader("Accept", "application/json");
builder.setAuth(AuthenticationScheme authScheme);

RequestSpecification requestSpec = builder.build();

// Use in multiple tests
given()
    .spec(requestSpec)
    .queryParam("page", "1")
.when()
    .get("/users")
.then()
    .statusCode(200);
```

### Step 7: Data-Driven Testing

```java
@DataProvider(name = "userIds")
public Object[][] getUserIds() {
    return new Object[][] {
        { "1" },
        { "2" },
        { "3" }
    };
}

@Test(dataProvider = "userIds")
public void testMultipleUsers(String userId) {
    given()
        .pathParam("id", userId)
    .when()
        .get("/users/{id}")
    .then()
        .statusCode(200);
}
```

---

## Tips & Best Practices

### 1. **Always Validate Status Codes First**
```java
.then()
    .statusCode(200)  // Validate response code before assertions
    .body("status", equalTo("success"));
```

### 2. **Use Meaningful Test Names**
```java
@Test
public void shouldReturnUserDataWhenValidUserIdProvided() {
    // Test code
}
```

### 3. **Leverage Request/Response Specifications**
```java
// Don't repeat base URI and auth in every test
// Use specifications for DRY (Don't Repeat Yourself) principle
given()
    .spec(requestSpec)
    .queryParam("specific", "value")
```

### 4. **Extract and Reuse Response Data**
```java
// Use extracted data for dependent API calls
Response response = given()...extract().response();
String id = response.path("id");

// Use in next request
given()
    .pathParam("id", id)
.when()
    .get("/users/{id}");
```

### 5. **Implement Proper Logging**
```java
given()
    .log()
    .all()  // Log all request details if validation fails
.when()
    .get("/endpoint")
.then()
    .log()
    .body()  // Always log response body on failure
    .statusCode(200);
```

### 6. **Use TestNG Dependencies for Workflows**
```java
@Test
public void createUser() {
    // Create user
}

@Test(dependsOnMethods = {"createUser"})
public void updateUser() {
    // Uses user created in previous test
}

@Test(dependsOnMethods = {"updateUser"})
public void deleteUser() {
    // Cleans up after workflow
}
```

### 7. **Create Utility Classes for Common Operations**
```java
public class ApiUtils {
    public static Response makeGetRequest(String endpoint, Map<String, String> params) {
        return given()
            .queryParams(params)
        .when()
            .get(endpoint)
        .then()
            .statusCode(200)
            .extract()
            .response();
    }
}
```

### 8. **Validate Response Times for Performance**
```java
.then()
    .statusCode(200)
    .time(lessThan(5L), TimeUnit.SECONDS)
    .body("status", equalTo("success"));
```

### 9. **Handle Dynamic Response Data**
```java
// Use anyOf for multiple valid responses
.body("status", anyOf(equalTo("success"), equalTo("pending")))

// Use hasItems for array validation
.body("items", hasItems("item1", "item2"))
```

### 10. **Organize Tests by Feature/Module**
```
tests/
├── users/
│   ├── CreateUserTest.java
│   ├── UpdateUserTest.java
│   └── DeleteUserTest.java
├── products/
│   ├── GetProductTest.java
│   └── SearchProductTest.java
└── utils/
    ├── RestUtilities.java
    └── TestDataBuilder.java
```

### 11. **Use Constants for URLs and Endpoints**
```java
public class Endpoints {
    public static final String GET_USERS = "/users";
    public static final String CREATE_USER = "/users";
    public static final String UPDATE_USER = "/users/{id}";
    public static final String DELETE_USER = "/users/{id}";
}

// Usage
.when()
    .get(Endpoints.GET_USERS)
```

### 12. **Implement Proper Error Handling**
```java
Response response = given()
    .queryParam("id", "invalid")
.when()
    .get("/users/{id}")
.then()
    .extract()
    .response();

if (response.statusCode() == 404) {
    System.out.println("User not found");
} else if (response.statusCode() == 200) {
    System.out.println("User found");
}
```

### 13. **Use Builders for Complex Request Bodies**
```java
PlacesAddModel places = new PlacesAddModel();
places.setName("Test Place");
places.setLocation(locationMap);
// ... set other properties

given()
    .body(places)
.when()
    .post("/places")
.then()
    .statusCode(201);
```

### 14. **Test Edge Cases**
```java
// Test with null values
// Test with empty strings
// Test with maximum length values
// Test with special characters
// Test with different data types
```

### 15. **Maintain Test Data Isolation**
```java
@BeforeMethod
public void setup() {
    // Fresh setup before each test
}

@AfterMethod
public void cleanup() {
    // Clean up test data after each test
}
```

---

## Learning Path

### Beginner Level
1. Basic GET requests
2. Query parameters
3. Status code validation
4. Response body validation
5. Understand BDD syntax

### Intermediate Level
6. POST requests with JSON body
7. PUT and DELETE operations
8. Response extraction
9. POJO models
10. Authentication (Basic, OAuth)

### Advanced Level
11. Request/Response specifications
12. Reusable utility classes
13. End-to-end workflows
14. Complex JSON parsing
15. Data-driven testing
16. Test framework organization
17. Performance testing
18. Multi-threaded testing

---

## Additional Resources

### REST Assured Documentation
- [REST Assured Official Documentation](https://rest-assured.io/)
- [GitHub Repository](https://github.com/rest-assured/rest-assured)

### Key Matchers for Assertions
```java
// Comparison
equalTo(value)
greaterThan(value)
lessThan(value)
greaterThanOrEqualTo(value)

// Collection
hasItems(item1, item2)
hasSize(size)
contains(items)
empty()

// String
containsString(substring)
startsWith(prefix)
endsWith(suffix)

// Logical
anyOf(matcher1, matcher2)
allOf(matcher1, matcher2)
not(matcher)
```

### Common HTTP Status Codes
- 200 OK - Request successful
- 201 Created - Resource created
- 204 No Content - Successful but no content
- 400 Bad Request - Invalid request
- 401 Unauthorized - Authentication required
- 403 Forbidden - Access denied
- 404 Not Found - Resource not found
- 500 Internal Server Error - Server error

---

## Next Steps

1. Clone the repository
2. Review examples in sequential folders (S1 through S23)
3. Run individual test classes with TestNG
4. Modify examples to test your own APIs
5. Build your own test framework using patterns demonstrated
6. Integrate with CI/CD pipeline

---

**Happy API Testing! 🚀**

Written by Brian McCarthy
