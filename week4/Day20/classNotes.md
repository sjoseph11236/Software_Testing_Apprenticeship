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