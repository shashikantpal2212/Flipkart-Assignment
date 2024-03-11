# Flipkart-Assignment
I have done this Assignment upto login because in assingnment mention that login through username and password but in real scenario it required login 
with Email or Phone No. and validate through OTP. So , i don't have permission to validate OTP.
------------------------------------------------------------------------------------------------------------------------------------------------------

package demo_Project;

import java.util.Iterator;
import java.util.Set;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.decorators.WebDriverDecorator;
import org.openqa.selenium.support.ui.WebDriverWait;

import io.github.bonigarcia.wdm.WebDriverManager;

public class flipcarte2e {

	public static void main(String[] args) throws InterruptedException {
		// TODO Auto-generated method stub

		WebDriverManager.chromedriver().setup();

		// Create an instance of ChromeDriver
		WebDriver driver = new ChromeDriver();

		// Maximize the browser page
		driver.manage().window().maximize();

		//
		driver.manage().timeouts().implicitlyWait(2, TimeUnit.SECONDS);

		// Invoking the Flipkart webapplication URL
		driver.get("https://www.flipkart.com");

		// Creating Action class
		Actions a = new Actions(driver);

		// Searching Laptop products in search bar
		WebElement searchBox = driver.findElement(By.cssSelector("input[class='Pke_EE']"));

		a.moveToElement(searchBox).click().sendKeys("laptop").sendKeys(Keys.ENTER).build().perform();

		// Creating JavaScriptExecutor method to scroll the page
		JavascriptExecutor js = (JavascriptExecutor) driver;
		js.executeScript("window.scrollBy(0,400)");

		// Selecting a laptop
		driver.findElement(By.xpath("//div[contains(text(),'HP 15s Intel Core i3 12th Gen 1215U - (8 GB/512 GB')]")).click();

		// Window handling method to handling different pages of a Browser
		Set<String> windows = driver.getWindowHandles();
		Iterator<String> it = windows.iterator();
		String pid = it.next();
		String cid = it.next();
		driver.switchTo().window(cid);

		js.executeScript("window.scrollBy(0,50)");

		WebElement deliverypin = driver.findElement(By.cssSelector("input[placeholder='Enter Delivery Pincode']"));

		// Entering Delivery pin code
		a.moveToElement(deliverypin).click().sendKeys("110074").sendKeys(Keys.ENTER).build().perform();

		Thread.sleep(2000);

		// click on Go TO CART option
		driver.findElement(By.xpath("//button[@class='_2KpZ6l _2U9uOA _3v1-ww']")).click();

		// Click on Place Order Option
		driver.findElement(By.xpath("//button[@class='_2KpZ6l _2ObVJD _3AWRsL']")).click();

		// Enter valid phone number
		driver.findElement(By.cssSelector("input[maxlength='auto']")).sendKeys("8737056139");

		// Click on Continue option
		driver.findElement(By.cssSelector("button[class='_2KpZ6l _20xBvF _3AWRsL']")).click();

	}
}
