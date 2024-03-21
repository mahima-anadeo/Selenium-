# Selenium-
This repository contains Selenium code for CURA Healthcare Services

package webdriverExamples;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.Select;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.openqa.selenium.chrome.ChromeDriver;

import java.time.Duration;

import org.openqa.selenium.By;



public class TS001 {
	public static void main(String args[]) throws InterruptedException{
		
	 WebDriver driver=new ChromeDriver();
	 driver.navigate().to("https://katalon-demo-cura.herokuapp.com/");
	 driver.manage().window().maximize();
	 System.out.println("URL "+driver.getCurrentUrl());
	 System.out.println("Title "+driver.getTitle());
	 driver.findElement(By.xpath("//*[@id=\"btn-make-appointment\"]")).click();
	 Thread.sleep(1000);
	 driver.findElement(By.xpath("//*[@id=\"txt-username\"]")).click();
	 driver.findElement(By.xpath("//*[@id=\"txt-username\"]")).sendKeys("John Doe");
	 Thread.sleep(2000);
	 driver.findElement(By.xpath("//*[@id=\"txt-password\"]")).click();
	 driver.findElement(By.xpath("//*[@id=\"txt-password\"]")).sendKeys("ThisIsNotAPassword");
	 Thread.sleep(2000);
	 driver.findElement(By.xpath("//*[@id=\"btn-login\"]")).click();
	 Thread.sleep(1000);
	 
	WebElement ddown = driver.findElement(By.name("facility"));
	Select select=new Select(ddown);
	select.selectByValue("Seoul CURA Healthcare Center");
	Thread.sleep(2000);
	driver.findElement(By.id("chk_hospotal_readmission")).click();
	driver.findElement(By.id("chk_hospotal_readmission")).isSelected();
	Thread.sleep(1000);
	
	WebElement radio1=driver.findElement(By.id("radio_program_medicaid"));
	radio1.click();
	
	System.out.println(radio1.isSelected());
	Thread.sleep(2000);
	driver.findElement(By.id("txt_visit_date")).click();
	
	WebDriverWait wait= new WebDriverWait(driver,Duration.ofSeconds(10));
	wait.until(ExpectedConditions.visibilityOfAllElementsLocatedBy(By.className("datepicker-days")));
	
	String month=driver.findElement(By.className("datepicker-switch")).getText();
	driver.findElement(By.xpath("/html/body/div/div[1]/table/tbody/tr[6]/td[1]")).click();
	Thread.sleep(2000);
	
     driver.findElement(By.id("txt_comment")).click();
     driver.findElement(By.id("txt_comment")).sendKeys("Plz book my appointment on the selected above date");
     Thread.sleep(2000);
	 driver.findElement(By.id("btn-book-appointment")).click();
	 Thread.sleep(3000);
	 driver.close();
	
	}
	}
	
