# To Deploy Selenium Grid Enterprise with Docker

* Selenium HQ Docker Here: https://github.com/SeleniumHQ/docker-selenium
* Client : you/your code
* Hub : Selenium Server where Grid is hosted. Link: https://hub.docker.com/r/selenium/hub
* Nodes : where the test will be executed. Link: https://hub.docker.com/u/selenium?page=1&search=node
* Diagram here : <img width="455" alt="image" src="https://github.com/user-attachments/assets/e238db67-ba9c-4429-bbaa-d0b495877526" />
* From https://hub.docker.com/r/selenium/hub and https://github.com/SeleniumHQ/docker-selenium?tab=readme-ov-file#windows-powershell
*  In terminal(windows)
*  ``` $ docker network create grid  ``` => Creates a network 
*  ``` $ docker run -d -p 4442-4444:4442-4444 --net grid --name selenium-hub selenium/hub:4.30.0-20250323 ``` => Starts docker hub. Check http://localhost:4444
*  ``` $ docker run -d --net grid -e SE_EVENT_BUS_HOST=selenium-hub ` --shm-size="2g" ` selenium/node-chrome:4.30.0-20250323 ``` => Adds One Chrome Node To Grid Hub(Can run this again to add another chrome node)
*  ``` $ docker run -d --net grid -e SE_EVENT_BUS_HOST=selenium-hub ` --shm-size="2g" ` selenium/node-edge:4.30.0-20250323 ``` => Adds One edge Node To Grid Hub -- " ---
*  ``` $ docker run -d --net grid -e SE_EVENT_BUS_HOST=selenium-hub ` --shm-size="2g" ` selenium/node-firefox:4.30.0-20250323 ``` => Adds One firefix Node To Grid Hub -- " ---
 

## My Example 
* IMAGES  <img width="962" alt="image" src="https://github.com/user-attachments/assets/bdeaefc3-82d1-4a37-a778-2a9571f8d97b" />
* Terminal Command : <img width="620" alt="image" src="https://github.com/user-attachments/assets/b00018a0-df72-43cc-a997-554100ecd3f0" />
* Hub Started : <img width="956" alt="image" src="https://github.com/user-attachments/assets/f6b640d6-b27b-4c47-b225-c1eb75c34776" />
* Terminal Added Chrome Node : <img width="853" alt="image" src="https://github.com/user-attachments/assets/371c73dc-4f62-4c4f-beeb-b931ace3cd03" />
* Hub with Chrome : <img width="794" alt="image" src="https://github.com/user-attachments/assets/1c3f4e69-7c54-4e4f-8791-edc3d16484b8" />
* Terminal added Firefox: <img width="859" alt="image" src="https://github.com/user-attachments/assets/54657fb9-12bc-4c8a-bbbb-7a46ebe9582e" />
* Hub with chrome & firefox : <img width="899" alt="image" src="https://github.com/user-attachments/assets/c02bbc1d-3738-4ed6-a932-0bd5ef167c7f" />
* You can add multiple time to increase node strength.
* In your code
```
 WebDriver driver; <br>
 String baseUrl, nodeURL; 
 @BeforeTest 
 public void setUpWthrows MalformedURLException {
 baseUrl = "http://newtours.demoaut.com/";
 nodeURL = "http://localhost:4444/wd/hub"; 
 DesiredCapabilities capability = DesiredCapabilities.firefox();
 capability.setBrowserName("firefox");
 capability.setPlatform(Platform.XP);
 driver = new RemoteWebDriver(new URL(nodeURL), capability);
}
```
![image](https://github.com/user-attachments/assets/a690404c-e211-4d94-8944-1bac667acbcc)
#@ Alternatively In order to use Standalone
* Refer : https://hub.docker.com/u/selenium?page=1&search=standalone
* Note that hub and node are on the same localhost
* <img width="812" alt="image" src="https://github.com/user-attachments/assets/4b44af3d-db04-47cb-8589-27686de29939" />
* <img width="761" alt="image" src="https://github.com/user-attachments/assets/214822b4-7b31-4f81-a153-81abf02679de" />

## *************************************************************************************************************
You can also execute playwright https://playwright.dev/docs/next/selenium-grid
Start Standalone
``` docker run -d -p 4444:4444 --shm-size="2g" -e SE_NODE_GRID_URL="http://localhost:4444" selenium/standalone-chromium:latest ```
Then Execute like
``` SELENIUM_REMOTE_URL=http://localhost:4444 npx playwright test ```
``` SELENIUM_REMOTE_URL=http://localhost:4444 mvn clean test ```











