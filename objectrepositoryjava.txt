package webdriver.pack;

import java.io.File;
import java.io.FileInputStream;

import org.dom4j.Document;
import org.dom4j.io.SAXReader;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.Test;



public class Objectrepository {
	 @Test
	  public void verifyEmail() throws Exception{
		  

		  //to access property file
		  File src = new File("./Configure/objectrepository.xml");
		  
		  
		  
		  //to read the property file create an obj of properties class
		  FileInputStream fis = new FileInputStream(src);
		  SAXReader sax=new SAXReader();
		  Document document = sax.read(fis);
		  
		  
			WebDriver driver = new FirefoxDriver();
			driver.get("http://ndafile:8081/OnlineBankingProjectSpring/");

		
			driver.findElement(By.xpath(document.selectSingleNode("//login_Detail/useradmin").getText())).click();
			Thread.sleep(1000);
			driver.findElement(By.name(document.selectSingleNode("//login_Detail/userid").getText())).sendKeys("Admin");
			Thread.sleep(1000);
			driver.findElement(By.name(document.selectSingleNode("//login_Detail/password").getText())).sendKeys("Admin123");
			Thread.sleep(1000);
			driver.findElement(By.xpath(document.selectSingleNode("//login_Detail/submit").getText())).click();
			Thread.sleep(1000);
			
	  }
}
