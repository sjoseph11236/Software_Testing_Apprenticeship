# SeleniumTest.java 

```

package SeleniumTests;

import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

import java.util.ArrayList;
import java.util.List;

import static org.hamcrest.CoreMatchers.hasItems;
import static org.hamcrest.MatcherAssert.assertThat;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class SeleniumTest {

    private WebDriver driver;

    @BeforeEach
    void setUp() {
        System.setProperty("webdriver.chrome.driver", "/Users/sayeedjoseph/selenium/chromedriver");
        driver = new ChromeDriver();
//        these two below do the same thing
//        driver.navigate().to("https://google.com");
        driver.get("https://google.com");
    }


    @AfterEach
    void tearDown() {
        driver.close();
//        driver.quit();
    }

    @Test
    void Test() {
        WebElement aboutAnchorTag = driver.findElement(By.tagName("a"));
        String expected = "About";
        String actual =  aboutAnchorTag.getText();
        assertEquals(expected, actual);
    }

    @Test
    void testBack() {
        driver.navigate().to("https://duckduckgo.com");
        driver.navigate().back();
        assertEquals("Google", driver.getTitle());
    }

    @Test
    void testForward() {
        driver.navigate().to("https://nba.com");
        driver.navigate().back();
        driver.navigate().forward();
        assertEquals("The official site of the NBA for the latest NBA Scores, Stats & News. | NBA.com", driver.getTitle());
    }

    @Test
    void testRefresh() {
        driver.navigate().refresh();
        assertEquals("Google", driver.getTitle());
    }

    @Test
    void testAllAnchors() {
        List<WebElement> anchors = driver.findElements(By.tagName("a"));
        assertEquals(22, anchors.size());
    }

    @Test
    void testPrintAllAnchors() {
        List<WebElement> anchors = driver.findElements(By.tagName("a"));
        for(WebElement anchor: anchors) {
            System.out.println(anchor.getText());
        }
    }

    @Test
    void testHasItemsAnchors() {
        List<WebElement> anchors = driver.findElements(By.tagName("a"));
        List<String> anchorContents = new ArrayList<String>();
        for(WebElement anchor: anchors) {
           anchorContents.add(anchor.getText());
        }

        assertThat(anchorContents, hasItems("About", "Privacy", "Terms"));
    }

    @Test
    void testAboutUrl() {
        WebElement anchor = driver.findElement(By.tagName("a"));
        anchor.click();
        assertEquals("https://about.google/?fg=1&utm_source=google-US&utm_medium=referral&utm_campaign=hp-header", driver.getCurrentUrl());
    }

    @Test
    void testWriteInSearchBar() {
//        driver.findElement(By.name("q")).sendKeys("Power Rangers" , Keys.ENTER);
//        driver.findElement(By.name("q")).sendKeys("Power Rangers" + Keys.ENTER);
        driver.findElement(By.name("q")).sendKeys("Power Rangers");
//        driver.findElement(By.name("btnK")).click();
//        driver.findElement(By.name("btnK")).sendKeys(Keys.ENTER);
          driver.findElement(By.xpath("//input[@name='btnK']")).click();

        assertEquals("Power Rangers - Google Search", driver.getTitle());
    }
}

```

# POM.xml

```

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>myFirstSeleniumProject</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>3.141.59</version>
        </dependency>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-chrome-driver</artifactId>
            <version>3.141.59</version>
        </dependency>
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter-engine</artifactId>
            <version>5.7.0</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.hamcrest</groupId>
            <artifactId>hamcrest-library</artifactId>
            <version>1.3</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>


```