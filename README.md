# Rest API Automation Ninja Showcase

A comprehensive REST API automation showcase using **Java**, **REST Assured**, **TestNG**, **Maven**, **Postman**, **GitHub**, and **Jenkins**. This repository is designed as a practical learning path from REST API fundamentals through a maintainable end-to-end API automation framework.

REST Assured is a Java library for testing and validating RESTful APIs. It supports BDD-style request syntax, HTTP method execution, response validation, JSON/XML extraction, logging, reusable request/response specifications, TestNG execution, Maven builds, and CI integration.

**Written by Brian McCarthy**

---

## Table of Contents

| Module | Topic | Time | Primary Coverage |
|---|---|---:|---|
| 1 | [Introduction](#module-1-introduction) | 22 min | Course structure, support, outcomes, API automation roadmap. |
| 2 | [Java Setup and Installation](#module-2-java-setup-and-installation) | 1 hr | JDK, Eclipse, Mac/Windows setup, Java version selection. |
| 3 | [REST API Introduction](#module-3-rest-api-introduction) | 1 hr | REST architecture, endpoints, methods, headers, response validation. |
| 4 | [REST Client Setup](#module-4-rest-client-setup) | 27 min | Postman, Advanced REST Client, REST Easy Client. |
| 5 | [REST API Testing Using Postman Client](#module-5-rest-api-testing-using-postman-client) | 1 hr | GET, POST, DELETE, API keys, WADL, manual validation. |
| 6 | [REST Assured Setup](#module-6-rest-assured-setup) | 1 hr | REST Assured dependency setup and build path cleanup. |
| 7 | [REST API Automation Overview](#module-7-rest-api-automation-overview) | 2 hr | GET/POST automation, JSON hierarchy, response validation, POJO serialization. |
| 8 | [OAuth Real World API Example](#module-8-oauth-real-world-api-example) | 1 hr | OAuth concepts, access tokens, authenticated GET/POST testing. |
| 9 | [Validating JSON Response](#module-9-validating-json-response) | 30 min | JSON extraction, JSON Path, field validation. |
| 10 | [End-To-End API Workflow](#module-10-end-to-end-api-workflow) | 1 hr | Create, read, validate, delete workflow chaining. |
| 11 | [Validating XML Response](#module-11-validating-xml-response) | 1 hr | XML extraction, XML Path, XML response validation. |
| 12 | [Request and Response Logging](#module-12-request-and-response-logging) | 1 hr | Request logs, response logs, debugging API failures. |
| 13 | [REST Assured Assertions](#module-13-rest-assured-assertions) | 1 hr | Hard assertions, soft assertions, validation strategy. |
| 14 | [Useful Tricks](#module-14-useful-tricks) | 1 hr | Root path, response time validation, performance checks. |
| 15 | [REST Assured Specifications](#module-15-rest-assured-specifications) | 1 hr | Request specs, response specs, shared API configuration. |
| 16 | [Automation Framework - Part 1](#module-16-automation-framework---part-1) | 1 hr | Maven framework setup, constants, dependencies. |
| 17 | [Automation Framework - Part 2](#module-17-automation-framework---part-2) | 1 hr | REST utility classes and reusable API operations. |
| 18 | [Automation Framework - Part 3](#module-18-automation-framework---part-3) | 1 hr | Converting standalone tests into framework tests. |
| 19 | [Practice Exercise](#module-19-practice-exercise) | 1 hr | Convert an end-to-end workflow into framework format. |
| 20 | [End-To-End Framework Execution](#module-20-end-to-end-framework-execution) | 1 hr | TestNG and Maven suite execution. |
| 21 | [Git and GitHub – Version Control System](#module-21-git-and-github--version-control-system) | 2 hr | Git setup, commits, remotes, branches, conflicts, clone. |
| 22 | [Continuous Integration with Jenkins](#module-22-continuous-integration-with-jenkins) | 1 hr | Jenkins setup, plugins, GitHub integration, CI execution. |
| 23 | [Build Management with Maven](#module-23-build-management-with-maven) | 2 hr | Maven features, repositories, POM, lifecycle commands. |
| 24 | [Conclusion](#module-24-conclusion) | 1 hr | Course wrap-up, next steps, continued API automation growth. |

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

### Programming Concept Area

This module introduces the course structure and final outcome: building practical REST API automation skills from manual REST client testing to a reusable Java REST Assured automation framework.

### Code Sample

```java
public class CourseGoal {
    public static void main(String[] args) {
        System.out.println("Goal: Build a REST Assured API automation framework.");
    }
}
```

### Expected Output

```text
Goal: Build a REST Assured API automation framework.
```

### Expected Result

The learner understands the course roadmap and the final framework objective.

### Key Takeaways

- API testing validates service behavior without relying on the UI.
- REST Assured enables readable code-based API tests.
- The course moves from basic requests to reusable framework design.

---

## Module 2: Java Setup and Installation

### Programming Concept Area

REST Assured automation requires a working Java environment. This module covers JDK installation, Eclipse installation, Mac/Windows setup, and environment verification.

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

The terminal confirms the JDK, compiler, and Maven are available.

### Key Takeaways

- Install a JDK, not only a JRE.
- Configure `JAVA_HOME` correctly.
- Verify Java and Maven before writing tests.
- Use Eclipse, IntelliJ IDEA, or VS Code for Java automation.

---

## Module 3: REST API Introduction

### Programming Concept Area

REST APIs expose resources through endpoints and HTTP methods. Common methods include `GET`, `POST`, `PUT`, and `DELETE`. API tests verify status codes, headers, body content, response time, and error behavior.

### Code Sample

```http
GET /api/users/123 HTTP/1.1
Host: api.example.com
Accept: application/json
```

```json
{
  "id": 123,
  "name": "Brian",
  "role": "QA Automation Engineer"
}
```

### Expected Output

```text
Status: 200 OK
Content-Type: application/json
Response body contains user id, name, and role.
```

### Expected Result

The API returns a successful response and a JSON body representing the requested resource.

### Key Takeaways

- Endpoints identify resources.
- HTTP methods describe operations.
- Headers provide metadata.
- API tests should validate status, body, headers, and timing.

---

## Module 4: REST Client Setup

### Programming Concept Area

REST clients such as Postman, Advanced REST Client, and REST Easy help testers manually explore APIs before automation.

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

The REST client sends a request and displays response body, status, headers, and response time.

### Key Takeaways

- Use Postman to prototype before automation.
- Save base URLs and values as environment variables.
- Validate manual behavior before coding a test.
- REST clients help debug request setup problems quickly.

---

## Module 5: REST API Testing Using Postman Client

### Programming Concept Area

Postman can send GET, POST, PUT, and DELETE requests, validate responses, work with API keys, and document request workflows before those workflows are automated.

### Code Sample

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response is JSON", function () {
    pm.response.to.have.header("Content-Type");
});
```

### Expected Output

```text
PASS Status code is 200
PASS Response is JSON
```

### Expected Result

Postman validates response expectations automatically after the request completes.

### Key Takeaways

- API documentation defines endpoints, parameters, and expected responses.
- API keys are commonly sent through headers or query parameters.
- Postman tests can validate status codes and body fields.
- Manual workflows can be converted into REST Assured tests.

---

## Module 6: REST Assured Setup

### Programming Concept Area

REST Assured setup includes adding Maven dependencies, importing static methods, cleaning build path conflicts, and writing the first automated API test.

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

### Programming Concept Area

This module covers GET/POST automation, response extraction, JSON hierarchy, response validation, Java object serialization, query parameters, and path parameters.

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
        .body("address.city", equalTo("Gwenborough"));
}
```

### Expected Output

```text
Status code: 200
address.city = Gwenborough
Test passed
```

### Expected Result

REST Assured navigates a nested JSON hierarchy and validates a nested field.

### Key Takeaways

- JSON paths validate nested fields.
- Query parameters filter or configure requests.
- Path parameters identify specific resources.
- POJOs can serialize Java objects into JSON bodies.

---

## Module 8: OAuth Real World API Example

### Programming Concept Area

OAuth allows authorized access to protected APIs. In a safe demo framework, credentials should be loaded from environment variables or secure CI secrets, not hardcoded in source code.

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

### Programming Concept Area

JSON validation confirms that API responses contain correct fields, values, arrays, objects, and nested structures.

### Code Sample

```java
Response response = given()
    .baseUri("https://jsonplaceholder.typicode.com")
.when()
    .get("/users");

String firstUserName = response.jsonPath().getString("[0].name");
System.out.println(firstUserName);
```

### Expected Output

```text
Leanne Graham
```

### Expected Result

The test extracts the first user's name from a JSON array response.

### Key Takeaways

- JSON Path extracts values from nested responses.
- Array indexes can access specific response records.
- Extracted values can drive downstream API calls.
- Validate required fields and business rules.

---

## Module 10: End-To-End API Workflow

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

### Programming Concept Area

This module converts standalone API tests into framework-compatible classes using shared specifications, constants, utility methods, and reusable validation.

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
| 204 | No Content | Successful delete or update with no response body. |
| 400 | Bad Request | Invalid request payload or parameters. |
| 401 | Unauthorized | Missing or invalid authentication. |
| 403 | Forbidden | Authenticated but not allowed. |
| 404 | Not Found | Resource does not exist. |
| 409 | Conflict | Duplicate or conflicting resource state. |
| 500 | Internal Server Error | Server-side failure. |

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
