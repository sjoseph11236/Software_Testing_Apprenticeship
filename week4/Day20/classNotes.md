# RESTAssured: 
 
 __RESTAssured tests to show testing of basic API CRUD Operations__ 
  - [RestAssured Docs](https://rest-assured.io/)
  - [Reqres](https://reqres.in/)

**GET Tests**

```
package restAssuredTests;

/*

given()
    set params, set header etc..
when()
    get, post, put , delete etc...
then()
    validate status code, extract response
* */

import io.restassured.response.Response;
import org.junit.jupiter.api.Test;

import static io.restassured.RestAssured.get;
import static io.restassured.RestAssured.given;
import static org.hamcrest.CoreMatchers.equalTo;
import static org.hamcrest.CoreMatchers.hasItems;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class GetTests {

    @Test
    public void test() {
//        .then() has to be in the chain of methods.
        get("https://reqres.in/api/users?page=2").then().statusCode(200).log().all();
    }

    @Test
    public void testResponse() {
//        strore response as a response object and check different properties on the response object.
        Response response  = get("https://reqres.in/api/users?page=2");

        System.out.println(response.getBody());
        System.out.println(response.getStatusCode());

        assertEquals(200, response.getStatusCode());
    }

    @Test
    public void testParams() {
        given().pathParam("id", 2)
                .when().get("https://reqres.in/api/users/{id}")
                .then().statusCode(200)
                .body("data.id", equalTo(2));
    }

    @Test
    public void testDataArray(){
        given().when().get("https://reqres.in/api/users?page=2")
                .then().statusCode(200)
                .body("data[0].id", equalTo(7));
    }

    @Test
    public void testSeveralArrayElements() {
        given().when().get("https://reqres.in/api/users?page=2")
                .then().statusCode(200)
                .body("data.first_name", hasItems("Michael", "Lindsay"));
    }

}


```

**POST Tests**

```
package restAssuredTests;

import org.json.simple.JSONObject;
import org.junit.jupiter.api.Test;

import java.util.HashMap;
import java.util.Map;

import static io.restassured.RestAssured.given;

public class PostTests {


    @Test
    public void testMapObject() {
//        not json
        Map<String, Object> map = new HashMap<>();
        map.put("name", "Sayeed");
        map.put("job", "teacher");
//        System.out.println(map);
        JSONObject request = new JSONObject(map);
//        System.out.println(request);
        JSONObject anotherRequst = new JSONObject();
        anotherRequst.put("name", "Sayeed");
        anotherRequst.put("job", "teacher");
//        System.out.println(anotherRequst);

        given().body(request.toJSONString()).when().post("https://reqres.in/api/users")
                .then().statusCode(201);
    }


}


```
**PUT Tests**
```
package restAssuredTests;

import org.json.simple.JSONObject;
import org.junit.jupiter.api.Test;

import static io.restassured.RestAssured.given;

public class PutTests {

    @Test
    public void testUpdateUser() {
        JSONObject request = new JSONObject();
        request.put("name", "Sam");
        request.put("job", "editor");

        given().body(request.toJSONString()).when()
                .put("https://reqres.in/api/users/2")
                .then().statusCode(200).log().all();
    }

}



```

**DELETE Tests**

```
package restAssuredTests;

import org.junit.jupiter.api.Test;

import static io.restassured.RestAssured.given;

public class DeleteTests {

    @Test
    public void testDelete() {
//        204 = no content
        given().when().delete("https://reqres.in/api/users/2")
                .then().statusCode(204).log().all();
    }
}

```

**POM.xml**

```

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>restassuredDemo</artifactId>
    <version>1.0-SNAPSHOT</version>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>8</source>
                    <target>8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>

    <dependencies>
        <!-- https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter-api -->
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter-api</artifactId>
            <version>5.7.0</version>
            <scope>test</scope>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.junit.vintage/junit-vintage-engine -->
        <dependency>
            <groupId>org.junit.vintage</groupId>
            <artifactId>junit-vintage-engine</artifactId>
            <version>5.7.0</version>
            <scope>test</scope>
        </dependency>
        <!-- https://mvnrepository.com/artifact/io.cucumber/cucumber-java -->
        <dependency>
            <groupId>io.cucumber</groupId>
            <artifactId>cucumber-java</artifactId>
            <version>6.8.1</version>
        </dependency>
        <dependency>
            <groupId>io.cucumber</groupId>
            <artifactId>cucumber-junit</artifactId>
            <version>6.8.1</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.hamcrest</groupId>
            <artifactId>hamcrest-library</artifactId>
            <version>1.3</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>io.rest-assured</groupId>
            <artifactId>rest-assured</artifactId>
            <version>4.3.1</version>
            <scope>test</scope>
        </dependency>
        <!-- https://mvnrepository.com/artifact/com.googlecode.json-simple/json-simple -->
        <dependency>
            <groupId>com.googlecode.json-simple</groupId>
            <artifactId>json-simple</artifactId>
            <version>1.1.1</version>
        </dependency>
    </dependencies>
</project>



```