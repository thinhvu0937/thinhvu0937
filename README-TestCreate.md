- 👋 Hi, I’m @thinhvu0937
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
thinhvu0937/thinhvu0937 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
package java4;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.util.Date;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Set;
import java.util.concurrent.TimeUnit;

import org.apache.poi.hssf.usermodel.HSSFSheet;
import org.apache.poi.hssf.usermodel.HSSFWorkbook;
import org.apache.poi.ss.usermodel.Cell;
import org.apache.poi.ss.usermodel.Row;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.AfterClass;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.Test;

import io.github.bonigarcia.wdm.WebDriverManager;

public class TestCreate {
	WebDriver driver;
	String url1 = "http://localhost:8080/Poly.AsgJv4/Login";
	String url2 = "http://localhost:8080/Poly.AsgJv4/Admin/VideosManagement";
	String USER_NAME = "admin";
	String PASS_WORD = "admin";
	String YOUTUBE_ID = "YB12";
	String YOUTUBE_ID2 = "YB13";
	String YOUTUBE_ID5 = "YB14";
	String VIEW_TITLE = "Huong dan uong nuoc bang mom";
	String VIEW_COUNT = "6";
	String DESCRIPTION = "nhu tieu de";
	String page_true = "alert alert-danger";
	String page ="";
	String YOUTUBE_ID_NULL = "";
	String VIEW_TITLE_NULL = "";
	String VIEW_COUNT_NULL = "";
	String DESCRIPTION_NULL = "";
	
	
	
	
	LocalDateTime localDateTime = LocalDateTime.now();
	LocalDate localDate = localDateTime.toLocalDate();
	String date = " " + localDate;
	Map<String, Object[]> testNGResult;
	HSSFWorkbook workbook;
	HSSFSheet sheet;
	
  @Test(priority = 1)
  public void form_qlVideoo_Them_01() {
		try {
			driver.get(url1);
			driver.manage().window().maximize();
			WebElement usernamelogin = driver.findElement(By.id("username"));
			usernamelogin.sendKeys(USER_NAME);
			WebElement passwordlogin = driver.findElement(By.id("password"));
			passwordlogin.sendKeys(PASS_WORD);
			WebElement login = driver.findElement(By.className("btn-login"));
			login.click();
			Thread.sleep(1000);
			WebElement admin = driver.findElement(By.id("admin"));
			admin.click();
			Thread.sleep(1000);
			WebElement videos = driver.findElement(By.id("videos"));
			videos.click();
			Thread.sleep(1000);
			WebElement videoId = driver.findElement(By.id("youtubeId"));
			videoId.sendKeys(YOUTUBE_ID);
			WebElement videoTile = driver.findElement(By.id("videoTitle"));
			videoTile.sendKeys(VIEW_TITLE);			
			WebElement viewCount = driver.findElement(By.id("viewCount"));
			viewCount.sendKeys(VIEW_COUNT);
			WebElement active = driver.findElement(By.name("active"));
			active.click();
			WebElement description =driver.findElement(By.id("description"));
			description.sendKeys(DESCRIPTION);
			WebElement create = driver.findElement(By.id("create"));
			create.click();
			Thread.sleep(1000);
			testNGResult.put("1",new Object[] { "form_qlVideoo_Them_01", "Kiểm Tra chức năng Create video"
					,"username: " + USER_NAME +"\n"+ " password: " + PASS_WORD + "\n"+" videoId_input: "+ YOUTUBE_ID +"\n"+ " videoTitle_input: " + VIEW_TITLE + "\n"+
					" viewCount: " + VIEW_COUNT +"\n"+ " descripsion: " + DESCRIPTION,
					"Them video thanh cong", "Them video thanh cong", "Pass", date  });
			Thread.sleep(1000);
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
			testNGResult.put("1",new Object[] { "form_qlVideoo_Them_01", "Kiểm Tra chức năng Create video"
					,"username: " + USER_NAME + " password: " + PASS_WORD + " videoId_input: "+ YOUTUBE_ID +"\n"+ " videoTitle_input: " + VIEW_TITLE + 
					" viewCount: " + VIEW_COUNT + "descripsion: " + DESCRIPTION ,
					"Them video that bai", "Them video thanh cong", "Fail", date  });
			Assert.assertTrue(false);
		}
	}
  
  
  	@Test(priority = 2)
  	public void form_qlVideoo_Them_02() {
  		try {
			driver.get(url2);
			driver.manage().window().maximize();
			WebElement videoId = driver.findElement(By.id("youtubeId"));
			videoId.sendKeys(YOUTUBE_ID2);
			WebElement videoTile = driver.findElement(By.id("videoTitle"));
			videoTile.sendKeys(VIEW_TITLE);			
			WebElement viewCount = driver.findElement(By.id("viewCount"));
			viewCount.sendKeys(VIEW_COUNT);
			
			WebElement description =driver.findElement(By.id("description"));
			description.sendKeys(DESCRIPTION);
			WebElement create = driver.findElement(By.id("create"));
			create.click();
			Thread.sleep(1000);
			page = driver.getPageSource();
			testNGResult.put("2",new Object[] { "form_qlVideoo_Them_02", "Kiểm Tra chức năng Create video"
					,"username: " + USER_NAME +"\n"+ " password: " + PASS_WORD + "\n"+" videoId_input: "+ YOUTUBE_ID2 +"\n"+ " videoTitle_input: " + VIEW_TITLE + "\n"+
					" viewCount: " + VIEW_COUNT +"\n"+ " descripsion: " + DESCRIPTION,
					"Them video thanh cong", "Them video that bai", "fail", date  });
			Thread.sleep(1000);
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
			testNGResult.put("2",new Object[] { "form_qlVideoo_Them_02", "Kiểm Tra chức năng Create video"
					,"username: " + USER_NAME + " password: " + PASS_WORD + " videoId_input: "+ YOUTUBE_ID2 +"\n"+ " videoTitle_input: " + VIEW_TITLE + 
					" viewCount: " + VIEW_COUNT + "descripsion: " + DESCRIPTION ,
					"Them video that bai", "Them video thanh cong", "pass", date  });
			Assert.assertTrue(false);
		}
	}
  	
  	
  	
  	@Test(priority = 3)
  	public void form_qlVideoo_Them_03() {
  		try {
			driver.get(url2);
			driver.manage().window().maximize();
			WebElement videoId = driver.findElement(By.id("youtubeId"));
			videoId.sendKeys(YOUTUBE_ID_NULL);
			WebElement videoTile = driver.findElement(By.id("videoTitle"));
			videoTile.sendKeys(VIEW_TITLE);			
			WebElement viewCount = driver.findElement(By.id("viewCount"));
			viewCount.sendKeys(VIEW_COUNT);
			
			WebElement description =driver.findElement(By.id("description"));
			description.sendKeys(DESCRIPTION);
			WebElement create = driver.findElement(By.id("create"));
			create.click();
			Thread.sleep(1000);
			page = driver.getPageSource();
			if (page.contentEquals(page_true)) {
			testNGResult.put("3",new Object[] { "form_qlVideoo_Them_03", "Kiểm Tra chức năng Create video"
					,"username: " + USER_NAME +"\n"+ " password: " + PASS_WORD + "\n"+" videoId_input: "+ YOUTUBE_ID_NULL +"\n"+ " videoTitle_input: " + VIEW_TITLE + "\n"+
					" viewCount: " + VIEW_COUNT +"\n"+ " descripsion: " + DESCRIPTION,
					"Them video thanh cong", "Them video thanh cong", "Pass", date  });
			}else {
				testNGResult.put("3",new Object[] { "form_qlVideoo_Them_03", "Kiểm Tra chức năng Create video"
						,"username: " + USER_NAME + " password: " + PASS_WORD + " videoId_input: "+ YOUTUBE_ID_NULL +"\n"+ " videoTitle_input: " + VIEW_TITLE + 
						" viewCount: " + VIEW_COUNT + "descripsion: " + DESCRIPTION ,
						"Them video that bai", "Them video thanh cong", "Fail", date  });
			}
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
			testNGResult.put("4",new Object[] { "form_qlVideoo_Them_03", "Kiểm Tra chức năng Create video"
					, " videoId_input: "+ YOUTUBE_ID +"\n"+ " videoTitle_input: " + VIEW_TITLE + 
					" viewCount: " + VIEW_COUNT + "descripsion: " + DESCRIPTION ,
					"Them video that bai", "Them video thanh cong", "Fail", date  });
			Assert.assertTrue(false);
		}
  	}
  	
  	@Test(priority = 4)
  	public void form_qlVideoo_Them_04() {
  		try {
			driver.get(url2);
			driver.manage().window().maximize();
			WebElement videoId = driver.findElement(By.id("youtubeId"));
			videoId.sendKeys(YOUTUBE_ID_NULL);
			WebElement videoTile = driver.findElement(By.id("videoTitle"));
			videoTile.sendKeys(VIEW_TITLE_NULL);			
			WebElement viewCount = driver.findElement(By.id("viewCount"));
			viewCount.sendKeys(VIEW_COUNT_NULL);
			
			WebElement description =driver.findElement(By.id("description"));
			description.sendKeys(DESCRIPTION_NULL);
			WebElement create = driver.findElement(By.id("create"));
			create.click();
			Thread.sleep(1000);
			page = driver.getPageSource();
			if (page.contentEquals(page_true)) {
			testNGResult.put("4",new Object[] { "form_qlVideoo_Them_04", "Kiểm Tra chức năng Create video"
					,"username: " + USER_NAME +"\n"+ " password: " + PASS_WORD + "\n"+" videoId_input: "+ YOUTUBE_ID_NULL +"\n"+ " videoTitle_input: " + VIEW_COUNT_NULL + "\n"+
					" viewCount: " + VIEW_COUNT_NULL +"\n"+ " descripsion: " + DESCRIPTION_NULL,
					"Them video thanh cong", "Them video thanh cong", "Pass", date  });
			}else {
				testNGResult.put("5",new Object[] { "form_qlVideoo_Them_04", "Kiểm Tra chức năng Create video"
						,"username: " + USER_NAME + " password: " + PASS_WORD + " videoId_input: "+ YOUTUBE_ID_NULL +"\n"+ " videoTitle_input: " + VIEW_COUNT_NULL + 
						" viewCount: " + VIEW_COUNT_NULL + "descripsion: " + DESCRIPTION_NULL ,
						"Them video that bai", "Them video thanh cong", "Fail", date  });
			}
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
			testNGResult.put("5",new Object[] { "form_qlVideoo_Them_04", "Kiểm Tra chức năng Create video"
					, " videoId_input: "+ YOUTUBE_ID_NULL +"\n"+ " videoTitle_input: " + VIEW_TITLE_NULL + 
					" viewCount: " + VIEW_COUNT_NULL + "descripsion: " + DESCRIPTION_NULL ,
					"Them video that bai", "Them video thanh cong", "Fail", date  });
			Assert.assertTrue(false);
		}
  	}
  	
  	@Test(priority = 5)
  	public void form_qlVideoo_Them_05() {
  		try {
			driver.get(url2);
			driver.manage().window().maximize();
			WebElement videoId = driver.findElement(By.id("youtubeId"));
			videoId.sendKeys(YOUTUBE_ID5);
			WebElement videoTile = driver.findElement(By.id("videoTitle"));
			videoTile.sendKeys(VIEW_TITLE);			
			WebElement viewCount = driver.findElement(By.id("viewCount"));
			viewCount.sendKeys(VIEW_COUNT);
			WebElement active = driver.findElement(By.name("active"));
			active.click();
			WebElement description =driver.findElement(By.id("description"));
			description.sendKeys(DESCRIPTION_NULL);
			WebElement create = driver.findElement(By.id("create"));
			create.click();
			Thread.sleep(1000);
			
			testNGResult.put("6",new Object[] { "form_qlVideoo_Them_05", "Kiểm Tra chức năng Create video"
					,"username: " + USER_NAME +"\n"+ " password: " + PASS_WORD + "\n"+" videoId_input: "+ YOUTUBE_ID5 +"\n"+ " videoTitle_input: " + VIEW_TITLE + "\n"+
					" viewCount: " + VIEW_COUNT +"\n"+ " descripsion: " + DESCRIPTION_NULL,
					"Them video thanh cong", "Them video thanh cong", "Pass", date  });
			Thread.sleep(1000);
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
			testNGResult.put("6",new Object[] { "form_qlVideoo_Them_05", "Kiểm Tra chức năng Create video"
					,"username: " + USER_NAME + " password: " + PASS_WORD + " videoId_input: "+ YOUTUBE_ID5 +"\n"+ " videoTitle_input: " + VIEW_TITLE + 
					" viewCount: " + VIEW_COUNT + "descripsion: " + DESCRIPTION_NULL ,
					"Them video that bai", "Them video thanh cong", "Fail", date  });
			Assert.assertTrue(false);
		}
  	}
  	
  	
  	@Test(priority = 6)
  	public void form_qlVideoo_Them_06() {
  		try {
			driver.get(url2);
			driver.manage().window().maximize();
			WebElement videoId = driver.findElement(By.id("youtubeId"));
			videoId.sendKeys(YOUTUBE_ID);
			WebElement videoTile = driver.findElement(By.id("videoTitle"));
			videoTile.sendKeys(VIEW_TITLE);			
			WebElement viewCount = driver.findElement(By.id("viewCount"));
			viewCount.sendKeys(VIEW_COUNT);
			
			WebElement description =driver.findElement(By.id("description"));
			description.sendKeys(DESCRIPTION);
			WebElement create = driver.findElement(By.id("create"));
			create.click();
			Thread.sleep(1000);
			page = driver.getPageSource();
			if (page.contentEquals(page_true)) {
			testNGResult.put("7",new Object[] { "form_qlVideoo_Them_06", "Kiểm Tra chức năng Create video"
					,"username: " + USER_NAME +"\n"+ " password: " + PASS_WORD + "\n"+" videoId_input: "+ YOUTUBE_ID +"\n"+ " videoTitle_input: " + VIEW_TITLE + "\n"+
					" viewCount: " + VIEW_COUNT +"\n"+ " descripsion: " + DESCRIPTION,
					"Them video thanh cong", "Them video thanh cong", "Pass", date  });
			}else {
				testNGResult.put("8",new Object[] { "form_qlVideoo_Them_06", "Kiểm Tra chức năng Create video"
						,"username: " + USER_NAME + " password: " + PASS_WORD + " videoId_input: "+ YOUTUBE_ID +"\n"+ " videoTitle_input: " + VIEW_TITLE + 
						" viewCount: " + VIEW_COUNT + "descripsion: " + DESCRIPTION ,
						"Them video that bai", "Them video thanh cong", "Fail", date  });
			}
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
			testNGResult.put("8",new Object[] { "form_qlVideoo_Them_06", "Kiểm Tra chức năng Create video"
					, " videoId_input: "+ YOUTUBE_ID +"\n"+ " videoTitle_input: " + VIEW_TITLE + 
					" viewCount: " + VIEW_COUNT + "descripsion: " + DESCRIPTION ,
					"Them video that bai", "Them video thanh cong", "Fail", date  });
			Assert.assertTrue(false);
		}
  	}
  
	@BeforeClass
	public void suiteSetUp() {
		WebDriverManager.chromedriver().setup();
		workbook = new HSSFWorkbook();
		sheet = workbook.createSheet("Test Create User Result");
		testNGResult = new LinkedHashMap<String, Object[]>();
		testNGResult.put("0", new Object[] { "Test ID", "Mô Tả", "Test Data", "Kết quả Thực Tế", "Kết quả mong đợi", "Trạng Thái", "Ngày Test" });
		try {
			driver = new ChromeDriver();
			driver.manage().timeouts().implicitlyWait(5, TimeUnit.SECONDS);
		} catch (Exception e) {
			throw new IllegalStateException("can't start web driver");
		}
	}

	@AfterClass
	public void afterClass() {
		Set<String> keyset = testNGResult.keySet();
		int rownum = 0;
		for (String key : keyset) {
			Row row = sheet.createRow(rownum++);
			Object[] objArr = testNGResult.get(key);
			int cellnum = 0;
			for (Object obj : objArr) {
				Cell cell = row.createCell(cellnum++);
				if (obj instanceof Date)
					cell.setCellValue((Date) obj);
				else if (obj instanceof Boolean)
					cell.setCellValue((Boolean) obj);
				else if (obj instanceof String)
					cell.setCellValue((String) obj);
				else if (obj instanceof Double)
					cell.setCellValue((Double) obj);
			}
		}
		try {
			FileOutputStream out = new FileOutputStream(new File("TestCreateUserResultExcel.xls"));
			workbook.write(out);
			out.close();
			System.out.println("Success");
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}
		driver.close();
		driver.quit();
	}
}
