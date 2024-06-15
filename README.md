# NxtTrendz-App
#Tested the login process of NxtTrendz App using Selenium Tool and also imported the necessary libraries from the Maven Repository.


import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.ui.ExpectedCondition;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

import java.time.Duration;

public class Logintest {
    public static void main(String[] args) {

        //Setting the path to browser
        System.setProperty("webdriver.chrome.driver","C:\\Users\\sksam\\Downloads\\chromedriver-win32 (1)\\chromedriver-win32\\chromedriver.exe");

        //Launch the chrome browser
        WebDriver driver=new ChromeDriver();

        //open the Nxttrendz app
        driver.get("https://rahulnxttrendz.ccbp.tech/login");

        WebElement usernameEl=driver.findElement(By.xpath("/html/body/div/div/form/div[1]/input"));
        usernameEl .sendKeys("rahul");

        WebElement passwordEl=driver.findElement(By.xpath("/html/body/div/div/form/div[2]/input"));
        passwordEl .sendKeys("rahul@2021");

        //submit the login details
        WebElement buttonEl=driver.findElement(By.xpath("/html/body/div/div/form/button"));
        buttonEl.submit();

        // Define the expected URL of the home page
        String expectedurl="https://rahulnxttrendz.ccbp.tech/";


        WebDriverWait wait=new WebDriverWait(driver, Duration.ofSeconds(10));
        wait.until(ExpectedConditions.urlToBe(expectedurl));

        String currentUrl=driver.getCurrentUrl();

        if(currentUrl.equals(expectedurl)) {

            System.out.println(("Succesful"));


        }

        driver.quit();




    }
}
