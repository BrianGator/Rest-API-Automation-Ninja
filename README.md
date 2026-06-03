# Rest API Automation Ninja Showcase

A comprehensive REST API automation showcase using **Java**, **REST Assured**, **TestNG**, **Maven**, **Postman**, **GitHub**, and **Jenkins**. This repository is designed as a practical learning path from REST API fundamentals through a maintainable end-to-end API automation framework.

REST Assured is a Java library for testing and validating RESTful APIs. It supports BDD-style request syntax, HTTP method execution, response validation, JSON/XML extraction, logging, reusable request/response specifications, TestNG execution, Maven builds, and CI integration.

**Written by Brian McCarthy**

---

## Table of Contents

| Module | Topic | Primary Coverage |
|---|---|---|
| 1 | [Introduction](#module-1-introduction) | Course structure, support, outcomes, API automation roadmap. |
| 2 | [Java Setup and Installation](#module-2-java-setup-and-installation) | JDK, Eclipse, Mac/Windows setup, Java version selection, environment validation. |
| 3 | [REST API Introduction](#module-3-rest-api-introduction) | REST architecture, endpoints, HTTP methods, headers, status codes, response validation, error behavior. |
| 4 | [REST Client Setup](#module-4-rest-client-setup) | Postman, Advanced REST Client, REST Easy Client, manual API exploration. |
| 5 | [REST API Testing Using Postman Client](#module-5-rest-api-testing-using-postman-client) | GET, POST, DELETE, API keys, request bodies, collections, WADL, manual validation. |
| 6 | [REST Assured Setup](#module-6-rest-assured-setup) | REST Assured dependency setup, IDE setup, Maven setup, build path cleanup. |
| 7 | [REST API Automation Overview](#module-7-rest-api-automation-overview) | GET/POST automation, response body extraction, JSON hierarchy, validation, POJO serialization, query/path parameters. |
| 8 | [OAuth Real World API Example](#module-8-oauth-real-world-api-example) | OAuth concepts, access tokens, secure credentials, authenticated GET/POST testing. |
| 9 | [Validating JSON Response](#module-9-validating-json-response) | JSON extraction, JSON Path, nested response validation, arrays, objects, dynamic values. |
| 10 | [End-To-End API Workflow](#module-10-end-to-end-api-workflow) | Create, read, validate, update, delete, path parameters, workflow chaining. |
| 11 | [Validating XML Response](#module-11-validating-xml-response) | XML extraction, XML Path, content type validation, XML response structure. |
| 12 | [Request and Response Logging](#module-12-request-and-response-logging) | Request logs, response logs, conditional logging, CI debugging. |
| 13 | [REST Assured Assertions](#module-13-rest-assured-assertions) | Hard assertions, soft assertions, Hamcrest matchers, TestNG validation strategy. |
| 14 | [Useful Tricks](#module-14-useful-tricks) | Root path, response time validation, reusable assertions, performance checks. |
| 15 | [REST Assured Specifications](#module-15-rest-assured-specifications) | Request specs, response specs, shared API configuration, DRY test design. |
| 16 | [Automation Framework - Part 1](#module-16-automation-framework---part-1) | Maven framework setup, constants, endpoints, configuration, dependencies. |
| 17 | [Automation Framework - Part 2](#module-17-automation-framework---part-2) | REST utility classes, reusable API methods, common request/response functions. |
| 18 | [Automation Framework - Part 3](#module-18-automation-framework---part-3) | Converting standalone tests into framework tests with shared specs/utilities. |
| 19 | [Practice Exercise](#module-19-practice-exercise) | Convert an end-to-end workflow into framework-compatible format. |
| 20 | [End-To-End Framework Execution](#module-20-end-to-end-framework-execution) | TestNG suite execution, Maven execution, command-line regression testing. |
| 21 | [Git and GitHub – Version Control System](#module-21-git-and-github--version-control-system) | Git setup, commits, remotes, branches, conflict resolution, GitHub clone/check-in. |
| 22 | [Continuous Integration with Jenkins](#module-22-continuous-integration-with-jenkins) | Jenkins setup, plugins, GitHub integration, freestyle jobs, CI execution. |
| 23 | [Build Management with Maven](#module-23-build-management-with-maven) | Maven features, repositories, POM, lifecycle, commands, dependency resolution. |
| 24 | [Conclusion](#module-24-conclusion) | Course wrap-up, next steps, framework improvement, portfolio-readiness. |

---

## Languages, Tools, and Methodologies Used

- **Java**: Main programming language for REST Assured automation.
- **REST Assured**: API automation, request execution, and response validation.
- **TestNG**: Test execution, assertions, suites, dependencies, and data providers.
- **Maven**: Dependency management and command-line test execution.
- **Postman**: Manual REST client validation before automation.
- **Git and GitHub**: Version control and portfolio hosting.
- **Jenkins**: Continuous integration for automated test execution.
- **BDD style**: `given()`, `when()`, `then()` test readability.
- **Data-driven testing**: Running the same API test against multiple inputs.
- **Framework design**: Specifications, utilities, constants, models, and reusable workflows.

---

## Recommended Project Structure

```text
Rest-API-Automation-Ninja-Showcase/
├── README.md
├── pom.xml
├── testng.xml
├── src/test/java/
│   ├── tests/
│   │   ├── GetRequestTest.java
│   │   ├── PostRequestTest.java
│   │   ├── PutPatchDeleteTest.java
│   │   ├── JsonValidationTest.java
│   │   ├── XmlValidationTest.java
│   │   └── EndToEndWorkflowTest.java
│   ├── framework/
│   │   ├── RestUtilities.java
│   │   ├── RequestSpecFactory.java
│   │   ├── ResponseSpecFactory.java
│   │   └── Endpoints.java
│   ├── model/
│   │   └── PlaceRequest.java
│   └── config/
│       └── TestConfig.java
└── reports/
```

---

## Core Maven Dependencies

```xml
<dependencies>
    <dependency>
        <groupId>io.rest-assured</groupId>
        <artifactId>rest-assured</artifactId>
        <version>5.4.0</version>
        <scope>test</scope>
    </dependency>

    <dependency>
        <groupId>org.testng</groupId>
        <artifactId>testng</artifactId>
        <version>7.10.2</version>
        <scope>test</scope>
    </dependency>

    <dependency>
        <groupId>org.hamcrest</groupId>
        <artifactId>hamcrest</artifactId>
        <version>2.2</version>
        <scope>test</scope>
    </dependency>

    <dependency>
        <groupId>io.rest-assured</groupId>
        <artifactId>json-path</artifactId>
        <version>5.4.0</version>
        <scope>test</scope>
    </dependency>

    <dependency>
        <groupId>io.rest-assured</groupId>
        <artifactId>xml-path</artifactId>
        <version>5.4.0</version>
        <scope>test</scope>
    </dependency>
</dependencies>
```

**Expected Result:** Maven downloads REST Assured, TestNG, Hamcrest, JSON Path, and XML Path dependencies so API tests can compile and run.

---

# Full REST API Automation Tutorial by Module

## Module 1: Introduction

This module introduces the course structure, support expectations, and learning outcomes. The technical tutorial starts with **Module 2: Java Setup and Installation**.

---

## Module 2: Java Setup and Installation

### Module Details

This module prepares the development environment required for REST Assured API automation. The learner installs a Java Development Kit, verifies Java compiler access, installs an IDE such as Eclipse, and confirms Maven availability for dependency management and test execution. The setup should work on both Windows and Mac, but environment variable configuration may differ by operating system.

### Programming Concept Area

REST Assured tests are Java-based automated tests. Before writing API automation, the machine must be able to compile Java code, run Java classes, resolve Maven dependencies, and execute TestNG tests from the IDE and command line.

### Code Sample

```bash
java -version
javac -version
mvn -version
```

```java
public class JavaSetupCheck {
    public static void main(String[] args) {
        System.out.println("Java setup is working");
    }
}
```

### Expected Output

```text
java version "17.x.x"
javac 17.x.x
Apache Maven 3.x.x
Java setup is working
```

### Expected Result

The terminal confirms the JDK, compiler, and Maven are available. The IDE can run a Java class without build path errors.

### Key Takeaways

- Install a JDK, not only a JRE.
- Configure `JAVA_HOME` and system `PATH` correctly.
- Verify Java and Maven before writing tests.
- Use Eclipse, IntelliJ IDEA, or VS Code for Java automation.
- Keep the Java version consistent between local development and CI.

---

## Module 3: REST API Introduction

### Module Details

This module explains the foundation of REST API testing. REST APIs expose resources through endpoint URLs. Each endpoint supports one or more HTTP methods that represent operations against those resources. API tests validate whether the server handles each operation correctly, returns the correct status code, sends the expected headers, provides the expected response body, responds within an acceptable time, and handles invalid input properly.

REST API testing is usually faster and more stable than UI testing because it validates service behavior directly. A strong API test should answer several questions: Did the request reach the correct endpoint? Did the server interpret the method correctly? Did the authentication and headers work? Did the response status match the operation? Did the returned data match the expected business rule? Did invalid input fail safely?

### Programming Concept Area

REST APIs expose resources through endpoints and HTTP methods. Common methods include `GET`, `POST`, `PUT`, `PATCH`, and `DELETE`. API tests verify status codes, headers, body content, response time, authentication behavior, authorization behavior, and error behavior.

### REST Resource Example

```text
Resource: users
Base URL: https://jsonplaceholder.typicode.com
Collection endpoint: /users
Single-resource endpoint: /users/{id}
```

### GET Method: Read a Resource

`GET` retrieves data. It should not create, update, or delete server-side data.

```java
@Test
public void shouldGetUserById() {
    given()
        .baseUri("https://jsonplaceholder.typicode.com")
        .pathParam("id", 1)
    .when()
        .get("/users/{id}")
    .then()
        .statusCode(200)
        .contentType(ContentType.JSON)
        .body("id", equalTo(1))
        .body("name", notNullValue());
}
```

**Expected Output**

```text
Status code: 200
Content-Type: application/json
id = 1
name is present
```

**Expected Result:** The API returns the requested user record and does not modify data.

### POST Method: Create a Resource

`POST` sends a request body to create a new resource or trigger a server-side action.

```java
@Test
public void shouldCreatePost() {
    String body = """
        {
          "title": "API automation",
          "body": "REST Assured create request",
          "userId": 1
        }
        """;

    given()
        .baseUri("https://jsonplaceholder.typicode.com")
        .contentType(ContentType.JSON)
        .body(body)
    .when()
        .post("/posts")
    .then()
        .statusCode(201)
        .body("title", equalTo("API automation"))
        .body("userId", equalTo(1));
}
```

**Expected Output**

```text
Status code: 201
Response body contains title = API automation
Response body contains userId = 1
```

**Expected Result:** The API accepts the JSON payload and returns a created-style response.

### PUT Method: Replace a Resource

`PUT` usually replaces an entire resource. Tests should send all required fields, not only the field being changed.

```java
@Test
public void shouldReplacePostWithPut() {
    String body = """
        {
          "id": 1,
          "title": "Updated title",
          "body": "Updated full body",
          "userId": 1
        }
        """;

    given()
        .baseUri("https://jsonplaceholder.typicode.com")
        .contentType(ContentType.JSON)
        .pathParam("id", 1)
        .body(body)
    .when()
        .put("/posts/{id}")
    .then()
        .statusCode(200)
        .body("title", equalTo("Updated title"))
        .body("body", equalTo("Updated full body"));
}
```

**Expected Output**

```text
Status code: 200
Updated title returned
Updated body returned
```

**Expected Result:** The API processes a full replacement update for the target resource.

### PATCH Method: Partially Update a Resource

`PATCH` updates only selected fields and leaves other fields unchanged.

```java
@Test
public void shouldPartiallyUpdatePostWithPatch() {
    String body = """
        {
          "title": "Patched title"
        }
        """;

    given()
        .baseUri("https://jsonplaceholder.typicode.com")
        .contentType(ContentType.JSON)
        .pathParam("id", 1)
        .body(body)
    .when()
        .patch("/posts/{id}")
    .then()
        .statusCode(200)
        .body("title", equalTo("Patched title"));
}
```

**Expected Output**

```text
Status code: 200
Patched title returned
```

**Expected Result:** The API updates only the submitted field.

### DELETE Method: Remove a Resource

`DELETE` removes a resource or marks it as deleted. Depending on the API, it may return `200 OK`, `202 Accepted`, or `204 No Content`.

```java
@Test
public void shouldDeletePost() {
    given()
        .baseUri("https://jsonplaceholder.typicode.com")
        .pathParam("id", 1)
    .when()
        .delete("/posts/{id}")
    .then()
        .statusCode(anyOf(equalTo(200), equalTo(204)));
}
```

**Expected Output**

```text
Status code: 200 or 204
Delete request completed successfully
```

**Expected Result:** The API accepts the delete operation for the target resource.

### HEAD Method: Validate Headers Without Body

`HEAD` retrieves response headers without downloading the response body. It is useful for checking availability, cache headers, and content type.

```java
@Test
public void shouldReturnHeadersForHeadRequest() {
    given()
        .baseUri("https://jsonplaceholder.typicode.com")
    .when()
        .head("/posts/1")
    .then()
        .statusCode(200)
        .header("Content-Type", notNullValue());
}
```

**Expected Result:** The API returns headers without a full response body.

### OPTIONS Method: Discover Supported Methods

`OPTIONS` can expose which HTTP methods an endpoint supports.

```java
@Test
public void shouldReturnAllowedMethods() {
    given()
        .baseUri("https://jsonplaceholder.typicode.com")
    .when()
        .options("/posts")
    .then()
        .statusCode(anyOf(equalTo(200), equalTo(204), equalTo(404), equalTo(405)));
}
```

**Expected Result:** The test documents whether the API supports method discovery. Some public demo APIs may not implement `OPTIONS` consistently.

### Request Headers to Validate

```java
given()
    .baseUri("https://jsonplaceholder.typicode.com")
    .header("Accept", "application/json")
.when()
    .get("/posts/1")
.then()
    .statusCode(200)
    .header("Content-Type", containsString("application/json"));
```

**Expected Result:** The API returns a JSON-compatible content type.

### Status Code Categories and Testing Meaning

| Range | Category | Meaning | What API Tests Should Verify |
|---|---|---|---|
| `1xx` | Informational | Request received, processing continues. | Rare in standard REST Assured tests; usually handled by HTTP client. |
| `2xx` | Success | Request succeeded. | Confirm correct success code for the method and business action. |
| `3xx` | Redirection | Client must follow another URL. | Validate redirect location when redirects are part of the API contract. |
| `4xx` | Client Error | Request is invalid, unauthorized, forbidden, or not found. | Confirm bad input fails safely with useful error messages. |
| `5xx` | Server Error | Server failed while processing a valid-looking request. | Treat as failure unless specifically testing fault scenarios. |

### Common Status Codes Explained

| Code | Meaning | Detailed API Testing Expectation |
|---|---|---|
| `200 OK` | Request succeeded. | Expected for successful `GET`, many `PUT`, many `PATCH`, and some `DELETE` responses. Validate body and headers. |
| `201 Created` | Resource created. | Expected for successful `POST` creation. Validate returned ID, location/header if available, and created body fields. |
| `202 Accepted` | Request accepted but not finished. | Used for async operations. Validate tracking ID, job status endpoint, or follow-up polling behavior. |
| `204 No Content` | Success with no body. | Common for successful `DELETE`. Validate empty body and correct status. |
| `301/302` | Redirect. | Validate `Location` header if redirects are expected. Disable auto-redirect when testing redirect behavior directly. |
| `304 Not Modified` | Cached resource unchanged. | Validate caching behavior with `ETag` or `If-None-Match` headers. |
| `400 Bad Request` | Invalid request syntax/data. | Send malformed body, missing fields, invalid types, or invalid query params and verify error message. |
| `401 Unauthorized` | Authentication missing or invalid. | Verify missing/expired token is rejected. Do not confuse with authorization. |
| `403 Forbidden` | Authenticated but not allowed. | Verify a valid user without permission cannot access protected data. |
| `404 Not Found` | Resource does not exist. | Verify invalid IDs return a clean not-found response. |
| `405 Method Not Allowed` | Method not supported for endpoint. | Send an unsupported method and validate the API rejects it properly. |
| `409 Conflict` | Request conflicts with current state. | Validate duplicate creation or version conflict behavior. |
| `415 Unsupported Media Type` | Wrong content type. | Send body with incorrect `Content-Type` and verify rejection. |
| `422 Unprocessable Entity` | Request syntax valid but business validation failed. | Validate business rule failures such as invalid email or invalid status transition. |
| `429 Too Many Requests` | Rate limit exceeded. | Validate rate limit handling, retry headers, and client backoff strategy when applicable. |
| `500 Internal Server Error` | Unexpected server failure. | Usually indicates a defect; API tests should capture request/response logs. |
| `502/503/504` | Gateway/service timeout/unavailable. | Validate resilience, retries, and environment stability if testing distributed systems. |

### Negative Test Example

```java
@Test
public void shouldRejectInvalidPostBody() {
    String invalidBody = "{ \"title\": \"\" }";

    given()
        .baseUri("https://api.example.com")
        .contentType(ContentType.JSON)
        .body(invalidBody)
    .when()
        .post("/posts")
    .then()
        .statusCode(anyOf(equalTo(400), equalTo(422)))
        .body("message", notNullValue());
}
```

**Expected Result:** The API rejects invalid input with a controlled client-error response and a useful error message.

### Key Takeaways

- Endpoints identify resources; methods define operations.
- `GET`, `POST`, `PUT`, `PATCH`, and `DELETE` should be tested separately.
- Status code validation must match the HTTP method and business rule.
- Headers verify content type, caching, auth, and metadata behavior.
- Negative tests are just as important as happy-path tests.
- A complete API test validates status, headers, body, schema, response time, and error handling.

---

## Module 4: REST Client Setup

### Module Details

This module covers manual API client setup. REST clients let testers send requests without writing code, inspect raw responses, compare headers, save examples, use environment variables, and confirm the API contract before automation begins. Postman is especially useful for creating repeatable collections that can later be translated into REST Assured tests.

### Programming Concept Area

Manual API exploration is the bridge between documentation and automation. Before automating, confirm the endpoint, method, parameters, request body, authentication, and expected response.

### Code Sample

```http
GET https://jsonplaceholder.typicode.com/users?page=1
Accept: application/json
```

### Expected Output

```json
[
  { "id": 1, "name": "Leanne Graham" },
  { "id": 2, "name": "Ervin Howell" }
]
```

### Expected Result

The REST client sends a request and displays response body, status, headers, cookies, and response time.

### Key Takeaways

- Use Postman to prototype before automation.
- Save base URLs and values as environment variables.
- Validate manual behavior before coding a test.
- REST clients help debug request setup problems quickly.

---

## Module 5: REST API Testing Using Postman Client

### Module Details

This module applies Postman to practical API testing workflows. It covers reading documentation, sending GET/POST/DELETE requests, using API keys or headers, validating responses with Postman test scripts, and organizing requests into collections. It also introduces how API documentation formats such as WADL describe available operations.

### Programming Concept Area

Postman validates API behavior before code automation. A well-built Postman collection documents request setup and expected API behavior, which makes conversion to REST Assured easier.

### Code Sample

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response has JSON content type", function () {
    pm.expect(pm.response.headers.get("Content-Type")).to.include("application/json");
});

pm.test("Response has an id field", function () {
    const json = pm.response.json();
    pm.expect(json.id).to.exist;
});
```

### Expected Output

```text
PASS Status code is 200
PASS Response has JSON content type
PASS Response has an id field
```

### Expected Result

Postman validates the response automatically after the request completes.

### Key Takeaways

- API documentation defines endpoints, parameters, and expected responses.
- API keys are commonly sent through headers or query parameters.
- Postman tests can validate status codes, headers, and body fields.
- Manual workflows can be converted into REST Assured tests.

---

## Module 6: REST Assured Setup

### Module Details

This module sets up the Java automation project. It includes adding REST Assured dependencies, adding TestNG, importing static methods, configuring Maven, confirming IDE build path correctness, and running a first test to prove the framework is ready.

### Programming Concept Area

REST Assured setup turns manual API calls into automated Java test cases that can be executed repeatedly from the IDE, command line, or CI server.

### Code Sample

```java
import org.testng.annotations.Test;
import static io.restassured.RestAssured.given;
import static org.hamcrest.Matchers.equalTo;

public class RestAssuredSetupTest {
    @Test
    public void shouldReturnUser() {
        given()
            .baseUri("https://jsonplaceholder.typicode.com")
        .when()
            .get("/users/1")
        .then()
            .statusCode(200)
            .body("id", equalTo(1));
    }
}
```

### Expected Output

```text
Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
```

### Expected Result

The first REST Assured test runs successfully and validates status code and response body.

### Key Takeaways

- REST Assured tests use `given()`, `when()`, and `then()`.
- Static imports make test syntax readable.
- TestNG can execute REST Assured tests.
- Build path cleanup prevents dependency conflicts.

---

## Module 7: REST API Automation Overview

### Module Details

This module introduces the core automation mechanics: sending GET and POST requests, extracting response data, understanding JSON hierarchy, validating nested fields, serializing Java objects into request bodies, and using query/path parameters correctly.

### Programming Concept Area

API automation is not only about sending requests. It also verifies response structure, validates business data, extracts values for later calls, and ensures that API behavior remains stable across builds.

### Code Sample

```java
@Test
public void validateJsonHierarchy() {
    given()
        .baseUri("https://jsonplaceholder.typicode.com")
    .when()
        .get("/users/1")
    .then()
        .statusCode(200)
        .body("address.city", equalTo("Gwenborough"))
        .body("company.name", notNullValue());
}
```

### Expected Output

```text
Status code: 200
address.city = Gwenborough
company.name is present
Test passed
```

### Expected Result

REST Assured navigates a nested JSON hierarchy and validates nested response fields.

### Key Takeaways

- JSON paths validate nested fields.
- Query parameters filter or configure requests.
- Path parameters identify specific resources.
- POJOs can serialize Java objects into JSON bodies.

---

## Module 8: OAuth Real World API Example

### Module Details

This module explains authenticated API testing. OAuth and bearer-token patterns allow test clients to access protected endpoints. The framework should load credentials securely from environment variables, Maven profiles, Jenkins credentials, or secret stores rather than hardcoding them.

### Programming Concept Area

Authenticated API testing verifies that protected endpoints allow valid clients and reject invalid, missing, expired, or unauthorized credentials.

### Code Sample

```java
String token = System.getenv("DEMO_API_TOKEN");

given()
    .baseUri("https://api.example.com")
    .header("Authorization", "Bearer " + token)
.when()
    .get("/account/profile")
.then()
    .statusCode(200);
```

### Expected Output

```text
Status code: 200
Authenticated request completed successfully.
```

### Expected Result

The API accepts the authenticated request when a valid token is supplied securely.

### Key Takeaways

- OAuth and bearer-token APIs require authenticated requests.
- Never commit real tokens or secrets to GitHub.
- Use environment variables, CI secrets, or secure config files.
- Test valid, missing, expired, and unauthorized credential scenarios.

---

## Module 9: Validating JSON Response

### Module Details

This module focuses on response extraction and JSON Path. API responses often contain nested objects, arrays, IDs, messages, flags, and business values. JSON Path lets tests extract and validate these values cleanly.

### Programming Concept Area

JSON validation confirms that API responses contain correct fields, values, arrays, objects, and nested structures.

### Code Sample

```java
Response response = given()
    .baseUri("https://jsonplaceholder.typicode.com")
.when()
    .get("/users");

String firstUserName = response.jsonPath().getString("[0].name");
List<String> emails = response.jsonPath().getList("email");

System.out.println(firstUserName);
System.out.println(emails.size());
```

### Expected Output

```text
Leanne Graham
10
```

### Expected Result

The test extracts the first user's name and the number of email values from a JSON array response.

### Key Takeaways

- JSON Path extracts values from nested responses.
- Array indexes can access specific response records.
- Extracted values can drive downstream API calls.
- Validate required fields and business rules.

---

## Module 10: End-To-End API Workflow

### Module Details

This module covers complete API workflow automation. End-to-end API workflows are useful when business behavior spans multiple endpoints, such as create, read, update, and delete. The workflow should capture dynamic IDs, reuse them safely, and clean up any test-created data.

### Programming Concept Area

End-to-end API workflows chain multiple requests: create data, read data, validate data, update data, and delete data. These tests confirm that multiple endpoints work together.

### Code Sample

```java
private String createdId;

@Test
public void createRecord() {
    createdId = given()
        .baseUri("https://jsonplaceholder.typicode.com")
        .contentType("application/json")
        .body("{\"title\":\"demo\",\"body\":\"workflow\",\"userId\":1}")
    .when()
        .post("/posts")
    .then()
        .statusCode(201)
        .extract()
        .path("id").toString();
}

@Test(dependsOnMethods = "createRecord")
public void readRecord() {
    given()
        .baseUri("https://jsonplaceholder.typicode.com")
        .pathParam("id", createdId)
    .when()
        .get("/posts/{id}")
    .then()
        .statusCode(anyOf(equalTo(200), equalTo(404)));
}
```

### Expected Output

```text
createRecord PASSED
readRecord PASSED
```

### Expected Result

The workflow creates a record, stores the generated ID, and uses it in a dependent request.

### Key Takeaways

- E2E API workflows depend on response data.
- Extract IDs and pass them into later requests.
- Use cleanup steps when APIs persist real data.
- Use TestNG dependencies carefully.

---

## Module 11: Validating XML Response

### Module Details

This module covers APIs that return XML. XML response testing is common in older enterprise systems, SOAP-adjacent services, configuration APIs, and systems that still expose XML contracts.

### Programming Concept Area

Some APIs return XML instead of JSON. XML Path allows tests to extract and validate XML elements and attributes.

### Code Sample

```java
Response response = given()
    .baseUri("https://www.w3schools.com")
.when()
    .get("/xml/note.xml");

String to = response.xmlPath().getString("note.to");
System.out.println(to);
```

### Expected Output

```text
Tove
```

### Expected Result

The test extracts an XML element value using XML Path.

### Key Takeaways

- XML APIs require XML Path validation.
- Validate content type before parsing XML.
- REST Assured supports both JSON and XML parsing.
- XML tests should validate elements, attributes, and structure.

---

## Module 12: Request and Response Logging

### Module Details

This module explains how to log request and response data. Logging is essential for diagnosing test failures, especially when a test passes locally but fails in CI. Good logging shows the request method, URL, headers, parameters, body, status code, and response body while avoiding secret exposure.

### Programming Concept Area

Logging helps troubleshoot request construction, parameters, headers, response bodies, status mismatches, and API failures.

### Code Sample

```java
given()
    .baseUri("https://jsonplaceholder.typicode.com")
    .log().all()
.when()
    .get("/posts/1")
.then()
    .log().body()
    .statusCode(200);
```

### Expected Output

```text
Request method: GET
Request URI: https://jsonplaceholder.typicode.com/posts/1
Response Body: { "userId": 1, "id": 1, "title": "..." }
```

### Expected Result

The test prints request details and response body, making failures easier to debug.

### Key Takeaways

- Request logs reveal outgoing configuration.
- Response logs reveal returned data.
- Logging is valuable in CI failures.
- Avoid logging secrets or tokens in shared logs.

---

## Module 13: REST Assured Assertions

### Module Details

This module covers validation strategy. API assertions should validate the response at several layers: status code, content type, required headers, required fields, field values, array sizes, schema expectations, and response timing. Hard assertions are useful when a failure should stop the test immediately. Soft assertions are useful when collecting several validation failures at once.

### Programming Concept Area

Assertions verify API behavior. Hard assertions stop immediately. Soft assertions collect multiple failures and report them together.

### Code Sample

```java
Response response = given()
    .baseUri("https://jsonplaceholder.typicode.com")
.when()
    .get("/posts/1");

SoftAssert softAssert = new SoftAssert();
softAssert.assertEquals(response.statusCode(), 200);
softAssert.assertTrue(response.asString().contains("userId"));
softAssert.assertAll();
```

### Expected Output

```text
All soft assertions passed.
```

### Expected Result

The test validates multiple response properties before reporting the final result.

### Key Takeaways

- Hard assertions stop on first failure.
- Soft assertions report multiple failures together.
- Validate status, headers, body, schema, and timing.
- Assertion strategy should match business risk.

---

## Module 14: Useful Tricks

### Module Details

This module introduces REST Assured features that reduce repetition and improve readability. Root paths simplify repeated nested JSON assertions. Response time checks add basic performance validation. These techniques are useful when tests become longer and need cleaner organization.

### Programming Concept Area

REST Assured root paths shorten repeated JSON path expressions. Response time checks validate performance expectations.

### Code Sample

```java
given()
    .baseUri("https://jsonplaceholder.typicode.com")
.when()
    .get("/users/1")
.then()
    .rootPath("address")
    .body("city", equalTo("Gwenborough"))
    .detachRootPath("address")
    .time(lessThan(3L), TimeUnit.SECONDS);
```

### Expected Output

```text
address.city validated
Response time less than 3 seconds
```

### Expected Result

The test validates a nested field using root path and confirms the response time is under the threshold.

### Key Takeaways

- Root paths shorten repeated assertions.
- Response time checks support performance validation.
- Thresholds should be realistic for CI.
- Tricks should improve readability, not hide intent.

---

## Module 15: REST Assured Specifications

### Module Details

This module explains request and response specifications. Specifications let the framework centralize repeated setup like base URI, base path, headers, authentication, content type, expected status code, expected content type, and response time limits. This prevents repeated configuration in every test.

### Programming Concept Area

Specifications centralize common request and response configuration, such as base URI, headers, authentication, content type, status code, and response timing.

### Code Sample

```java
RequestSpecification requestSpec = new RequestSpecBuilder()
    .setBaseUri("https://jsonplaceholder.typicode.com")
    .addHeader("Accept", "application/json")
    .build();

ResponseSpecification responseSpec = new ResponseSpecBuilder()
    .expectStatusCode(200)
    .expectContentType(ContentType.JSON)
    .build();

given()
    .spec(requestSpec)
.when()
    .get("/posts/1")
.then()
    .spec(responseSpec);
```

### Expected Output

```text
Request specification applied
Response specification validated
Test passed
```

### Expected Result

The test uses reusable request and response configuration instead of repeating setup in every test.

### Key Takeaways

- Specs enforce DRY test design.
- Request specs standardize setup.
- Response specs standardize expectations.
- Specs make framework tests easier to maintain.

---

## Module 16: Automation Framework - Part 1

### Module Details

This module begins framework design. The goal is to move from individual scripts into a maintainable test architecture. A framework should separate configuration, endpoints, reusable request setup, test data, model classes, utilities, and test classes.

### Programming Concept Area

Framework design organizes constants, endpoints, configuration, dependencies, test classes, and reusable components.

### Code Sample

```java
public class Endpoints {
    public static final String USERS = "/users";
    public static final String USER_BY_ID = "/users/{id}";
    public static final String POSTS = "/posts";
}

public class TestConfig {
    public static final String BASE_URI = "https://jsonplaceholder.typicode.com";
}
```

### Expected Output

```text
Constants are available to all framework test classes.
```

### Expected Result

Tests can reference endpoints and base paths from centralized classes instead of hardcoding strings repeatedly.

### Key Takeaways

- Frameworks reduce duplication.
- Constants prevent endpoint string drift.
- Maven standardizes project structure.
- Dependencies should be managed in `pom.xml`.

---

## Module 17: Automation Framework - Part 2

### Module Details

This module builds utility classes. Utilities reduce repeated REST Assured code, enforce common behavior, and make test classes easier to read. Utility methods can send common request types, apply specs, attach parameters, log failures, and return extracted responses.

### Programming Concept Area

Utility classes wrap common REST operations such as sending GET/POST requests, adding parameters, extracting responses, and applying shared specs.

### Code Sample

```java
public class RestUtilities {
    public static Response get(String endpoint) {
        return given()
            .baseUri(TestConfig.BASE_URI)
        .when()
            .get(endpoint)
        .then()
            .extract()
            .response();
    }

    public static Response post(String endpoint, Object body) {
        return given()
            .baseUri(TestConfig.BASE_URI)
            .contentType(ContentType.JSON)
            .body(body)
        .when()
            .post(endpoint)
        .then()
            .extract()
            .response();
    }
}
```

### Expected Output

```text
Reusable GET and POST helper methods are available.
```

### Expected Result

Test classes can call utility methods instead of rewriting REST Assured setup every time.

### Key Takeaways

- Utilities encapsulate repeated request logic.
- Helpers improve readability.
- Avoid hiding important test intent.
- Keep utilities small and focused.

---

## Module 18: Automation Framework - Part 3

### Module Details

This module converts raw test classes into framework-based tests. Instead of embedding URLs, credentials, parameters, and repeated setup in each class, tests use shared configuration and utilities. This makes the test suite easier to maintain as API coverage grows.

### Programming Concept Area

Standalone API tests become framework-compatible classes using shared specifications, constants, utility methods, and reusable validation.

### Code Sample

```java
public class UserApiTest {
    @Test
    public void shouldReturnUsers() {
        Response response = RestUtilities.get(Endpoints.USERS);

        Assert.assertEquals(response.statusCode(), 200);
        Assert.assertTrue(response.asString().contains("username"));
    }
}
```

### Expected Output

```text
shouldReturnUsers PASSED
```

### Expected Result

A standalone API test now uses the framework structure and reusable utilities.

### Key Takeaways

- Convert repeated scripts into framework tests.
- Use common utilities and endpoint constants.
- Keep assertions visible and meaningful.
- Framework tests should be easier to maintain.

---

## Module 19: Practice Exercise

### Module Details

This module applies the previous framework concepts through practice. The learner converts an end-to-end workflow into framework format, uses utilities, extracts IDs, creates dependent tests, and validates that the workflow still behaves correctly.

### Programming Concept Area

The practice exercise reinforces framework conversion by transforming an end-to-end workflow into reusable framework format.

### Code Sample

```java
public class WorkflowPracticeTest {
    private String recordId;

    @Test
    public void createRecord() {
        Response response = RestUtilities.post(Endpoints.POSTS, Map.of("title", "API Framework"));
        recordId = response.path("id").toString();
        Assert.assertNotNull(recordId);
    }

    @Test(dependsOnMethods = "createRecord")
    public void readRecord() {
        Response response = RestUtilities.get(Endpoints.POSTS + "/" + recordId);
        Assert.assertTrue(response.statusCode() == 200 || response.statusCode() == 404);
    }
}
```

### Expected Output

```text
createRecord PASSED
readRecord PASSED
```

### Expected Result

The workflow shares created response data across dependent test methods.

### Key Takeaways

- Practice converts knowledge into framework skill.
- E2E tests should create, validate, and clean up data.
- Test dependencies should be intentional.
- Reusable patterns reduce workflow complexity.

---

## Module 20: End-To-End Framework Execution

### Module Details

This module executes the complete framework using TestNG and Maven. The goal is to run tests consistently outside the IDE so the same suite can run locally, on a build agent, or in Jenkins.

### Programming Concept Area

Framework execution uses TestNG suites and Maven commands to run all tests from the command line, locally or in CI.

### Code Sample

```xml
<!DOCTYPE suite SYSTEM "https://testng.org/testng-1.0.dtd">
<suite name="REST API Automation Suite">
    <test name="Regression Tests">
        <classes>
            <class name="tests.UserApiTest"/>
            <class name="tests.WorkflowPracticeTest"/>
        </classes>
    </test>
</suite>
```

```bash
mvn clean test -DsuiteXmlFile=testng.xml
```

### Expected Output

```text
[INFO] BUILD SUCCESS
Tests run: 2, Failures: 0, Errors: 0, Skipped: 0
```

### Expected Result

Maven runs the TestNG suite and reports successful framework execution.

### Key Takeaways

- TestNG suites organize framework execution.
- Maven enables repeatable command-line runs.
- CI tools can run the same Maven command.
- Reports should be reviewed after each execution.

---

## Module 21: Git and GitHub – Version Control System

### Module Details

This module introduces version control for automation projects. Git allows the tester to track changes, create branches, commit framework updates, push to GitHub, clone repositories, and resolve merge conflicts.

### Programming Concept Area

Git tracks code changes. GitHub stores the repository remotely and supports collaboration, branching, conflict resolution, and project sharing.

### Code Sample

```bash
git init
git add .
git commit -m "Initial REST API automation framework"
git branch -M master
git remote add origin https://github.com/BrianGator/Rest-API-Automation-Ninja-Showcase.git
git push -u origin master
```

### Expected Output

```text
[master abc123] Initial REST API automation framework
Branch 'master' set up to track remote branch 'master'
```

### Expected Result

The local automation framework is committed and pushed to GitHub.

### Key Takeaways

- Commit frequently with meaningful messages.
- Use branches for feature work.
- Resolve merge conflicts carefully.
- GitHub makes automation work visible and reviewable.

---

## Module 22: Continuous Integration with Jenkins

### Module Details

This module connects the automation framework to Jenkins. Jenkins can pull the latest code from GitHub, run Maven commands, publish test results, and provide quick feedback when changes break the suite.

### Programming Concept Area

Jenkins automates framework execution after code changes. A Jenkins job can pull from GitHub, run Maven tests, and report results.

### Code Sample

```bash
mvn clean test -DsuiteXmlFile=testng.xml
```

### Expected Output

```text
Started by GitHub webhook or manual build
Checking out source code
Running Maven tests
BUILD SUCCESS
```

### Expected Result

Jenkins executes the REST API automation suite and reports build status.

### Key Takeaways

- CI gives fast feedback on API regression failures.
- Jenkins can integrate with GitHub repositories.
- Maven commands should work locally before CI setup.
- Jenkins logs help troubleshoot build and test failures.

---

## Module 23: Build Management with Maven

### Module Details

This module explains Maven as the build and dependency management tool. Maven standardizes project structure, downloads dependencies, runs plugins, manages the test lifecycle, and supports repeatable execution across local and CI machines.

### Programming Concept Area

Maven manages project structure, dependencies, plugins, repositories, and lifecycle commands. It makes test execution predictable across machines and CI systems.

### Code Sample

```bash
mvn clean
mvn test
mvn clean test
mvn dependency:tree
```

### Expected Output

```text
[INFO] BUILD SUCCESS
[INFO] Tests run: 10, Failures: 0, Errors: 0, Skipped: 0
```

### Expected Result

Maven cleans the project, resolves dependencies, compiles tests, and executes the suite.

### Key Takeaways

- `pom.xml` is the Maven project definition file.
- Maven downloads dependencies from repositories.
- Maven lifecycle phases standardize build behavior.
- `mvn clean test` is a core CI execution command.

---

## Module 24: Conclusion

### Module Details

This module wraps up the REST API automation learning path and identifies next steps. A strong portfolio-ready framework should include request and response specs, utility classes, clear endpoint constants, JSON/XML validation, negative tests, authentication tests, TestNG execution, Maven command-line support, source control, and CI execution.

### Programming Concept Area

The conclusion summarizes the complete REST API automation path and next steps: expanding coverage, strengthening framework structure, adding CI reporting, and applying patterns to real business APIs.

### Code Sample

```text
[ ] Java installed
[ ] Maven installed
[ ] REST Assured dependencies added
[ ] TestNG suite created
[ ] Request/response specs built
[ ] Utility classes created
[ ] JSON/XML validations implemented
[ ] E2E workflow tests added
[ ] GitHub repository updated
[ ] Jenkins CI job configured
```

### Expected Output

```text
REST API automation framework ready for portfolio demonstration.
```

### Expected Result

The learner has a complete foundation for REST API automation with Java, REST Assured, TestNG, Maven, GitHub, and Jenkins.

### Key Takeaways

- REST API automation is a high-value QA skill.
- Framework design matters as much as individual tests.
- CI execution turns tests into a repeatable quality gate.
- Continue improving with reporting, data-driven tests, schema validation, and security checks.

---

# Additional REST API Automation Examples

## GET Request Validation

```java
@Test
public void shouldGetPostById() {
    given()
        .baseUri("https://jsonplaceholder.typicode.com")
        .pathParam("id", 1)
    .when()
        .get("/posts/{id}")
    .then()
        .statusCode(200)
        .body("id", equalTo(1))
        .body("userId", equalTo(1));
}
```

**Expected Result:** The API returns post `1`, and the test validates the ID and owner user ID.

## POST Request with JSON Body

```java
@Test
public void shouldCreatePost() {
    String body = """
        {
          "title": "API automation",
          "body": "REST Assured test body",
          "userId": 1
        }
        """;

    given()
        .baseUri("https://jsonplaceholder.typicode.com")
        .contentType(ContentType.JSON)
        .body(body)
    .when()
        .post("/posts")
    .then()
        .statusCode(201)
        .body("title", equalTo("API automation"));
}
```

**Expected Result:** The API accepts the JSON payload and returns `201 Created`.

## Query Parameter vs Path Parameter

```java
// Query parameter example: /posts?userId=1
given()
    .queryParam("userId", 1)
.when()
    .get("/posts")
.then()
    .statusCode(200);

// Path parameter example: /posts/1
given()
    .pathParam("id", 1)
.when()
    .get("/posts/{id}")
.then()
    .statusCode(200);
```

**Expected Result:** Query parameters filter collections, while path parameters identify specific resources.

---

# Best Practices

1. Validate status codes first.
2. Validate content type and response schema.
3. Keep request and response specs reusable.
4. Do not hardcode secrets in test classes.
5. Use environment variables or secure configuration for tokens.
6. Keep test data isolated and clean up created records.
7. Use meaningful test method names.
8. Log request/response details only when useful.
9. Keep endpoint constants in one place.
10. Run the full suite through Maven before pushing.
11. Add CI execution through Jenkins or GitHub Actions.
12. Expand reporting with Surefire, Allure, or Extent Reports.

---

# Learning Path

## Beginner

1. Learn REST architecture.
2. Use Postman for GET/POST/DELETE requests.
3. Install Java, Eclipse, Maven, and REST Assured.
4. Write a first GET test.
5. Validate status code and response body.

## Intermediate

1. Add POST bodies and POJO serialization.
2. Extract JSON/XML response data.
3. Add authenticated request handling.
4. Validate response times.
5. Use TestNG assertions and dependencies.

## Advanced

1. Build request and response specifications.
2. Create reusable REST utility classes.
3. Convert standalone tests into framework tests.
4. Build end-to-end workflows.
5. Execute suites with Maven and TestNG.
6. Push to GitHub.
7. Run in Jenkins CI.

---

# Common HTTP Status Codes

| Code | Meaning | API Test Expectation |
|---|---|---|
| 200 | OK | Successful read/update operation. |
| 201 | Created | Successful create operation. |
| 202 | Accepted | Async request accepted but not completed yet. |
| 204 | No Content | Successful delete or update with no response body. |
| 301/302 | Redirect | Validate `Location` header when redirects are expected. |
| 304 | Not Modified | Validate cache behavior with ETag headers. |
| 400 | Bad Request | Invalid request payload or parameters. |
| 401 | Unauthorized | Missing or invalid authentication. |
| 403 | Forbidden | Authenticated but not allowed. |
| 404 | Not Found | Resource does not exist. |
| 405 | Method Not Allowed | HTTP method is not supported by the endpoint. |
| 409 | Conflict | Duplicate or conflicting resource state. |
| 415 | Unsupported Media Type | Wrong request content type. |
| 422 | Unprocessable Entity | Business validation failed. |
| 429 | Too Many Requests | Rate limit exceeded. |
| 500 | Internal Server Error | Server-side failure. |
| 502/503/504 | Gateway/Unavailable/Timeout | Infrastructure or upstream service failure. |

---

# Next Steps

1. Clone this repository.
2. Review examples in the sequential section folders.
3. Run individual REST Assured test classes with TestNG.
4. Add your own API endpoints and test data.
5. Refactor repeated request logic into utilities.
6. Add request and response specifications.
7. Execute the suite with Maven.
8. Push changes to GitHub.
9. Configure Jenkins CI execution.
10. Add reporting and logs for portfolio evidence.

---

**Happy API Testing!**

Written by Brian McCarthy
