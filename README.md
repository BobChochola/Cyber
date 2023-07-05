# Cyber

## 1-Domain questions.txt

#### 1. Please explain the difference between patch and post in HTTP methods.

POST is used for creating new resources or submitting data,
PATCH is used for making partial updates to existing resources.
POST sends the entire representation of the resource, whereas PATCH sends only the changes to be applied.

#### 2. Please describe the steps involved when opening https://mammothcyber.com in a web browser.

I think it can be answered according to the OSI 7 layer.

1. DNS Lookup: The browser initiates a DNS lookup to translate the domain name "mammothcyber.com" into an IP address.

2. Establishing a TCP Connection: Once the IP address is obtained, the browser establishes a TCP connection with the server hosting the website. This involves a three-way handshake process.

3. SSL/TLS Handshake : If the website uses HTTPS, which is indicated by "https://" in the URL, an SSL/TLS handshake takes place.

4. Sending the HTTP Request: After the connection is established, the browser sends an HTTP request to the server. The request contains information such as the HTTP method (usually GET), the specific path or URL ("/" in this case), headers, and any additional data.

5. Processing the Request: in this case, the content of the "https://mammothcyber.com" homepage and prepares a response to send back to the browser.

6. Receiving and Rendering the Response: The browser receives the server's response, which includes an HTTP status code and the requested content (the HTML, CSS, JavaScript, and other resources that make up the website). The browser starts rendering the HTML and executing.

7. Fetching Additional Resources: As the browser processes the received HTML, it may encounter references to additional resources such as images, stylesheets, or scripts. It then sends subsequent requests to the server to fetch those resources.

8. Rendering and Displaying the Website: The browser continues to render and display the website, incorporating all the retrieved resources. It interprets the HTML structure, applies CSS styles, executes JavaScript code, and renders the visual elements accordingly.

#### 3. What is the flow of DNS and please describe it as much as possible.

1.  When you enter a domain name in your web browser (e.g., "example.com"), the browser checks with your local DNS resolver for the corresponding IP address.

2.  If the local DNS resolver doesn't have the IP address, it contacts a recursive DNS server.

3.  The recursive DNS server sends a request to the root DNS server to find the DNS server for the top-level domain (TLD).

4.  The root DNS server responds with the IP address of the TLD DNS server.

5.  The recursive DNS server then sends a request to the TLD DNS server to find the authoritative DNS server for the domain.

6.  The TLD DNS server provides the IP address of the authoritative DNS server.

7.  The recursive DNS server retrieves the IP address from the authoritative DNS server.

8.  The IP address is sent back to the local DNS resolver.

9.  The local DNS resolver returns the IP address to the browser, allowing it to establish a connection with the web server associated with the domain.

#### 4. What is Network Address Translation (NAT)? Why do we need it?

1.  With the limited availability of public IPv4 addresses, NAT helps conserve the use of public IP addresses.
    Instead of assigning a unique public IP address to each device in a private network, NAT allows multiple devices to use a single public IP address.

2.  It acts as a gateway, translating the private IP addresses of devices into the public IP address assigned to the network's router or firewall.

3.  Security and Privacy.

4.  NAT simplifies network management by allowing an organization to use private IP address ranges within their internal network without worrying about conflicts with globally unique public IP addresses.

5.  As the internet moves towards IPv6, which has a larger address space, NAT is still necessary for the transition period. Many networks still rely on IPv4, and NAT helps bridge the gap by allowing IPv4 devices to communicate with IPv6 devices and vice versa.

#### 5. What are the roles of manual testing, automated testing, and CI/CD? Which one is more important?

I believe all three are important and have different levels of importance at different stages. For example, in the early stages of development, when there is no well-defined process and there is a pressing need for release, manual testing is the most important. It allows for direct and effective communication with developers and helps identify and fix errors.

In situations where there is ample time and numerous features, automated testing becomes necessary. It can effectively check past features and save a significant amount of manpower costs.

As automation is established, CI/CD can be implemented alongside it. This allows us to further reduce manpower costs by focusing on the execution and deployment of automation.

## 2-Test Case Design questions.txt

1. Given a website to upload apps, and its UI has a mechanism to avoid submitting duplicated apps.
   Using GET method to a REST API (https://mammothcyber.com/apps) will get a JSON representing the apps, like below
   { ‘apps’: [
   {‘id’: ‘app_id_1’,
   ‘name’: ‘app_name_1’
   },
   {‘id’: ‘app_id_2'
   ‘name’: ‘app_name_2'
   }]
   }

a. Assume UI working correctly to forbid duplicated apps being uploaded.
But, we still get duplicated app entities from the REST API. Please list as many possible root causes as you can.
b. Please write API test cases for the REST API.

2. Given a function that takes a string as input and returns the first character that appears twice in the string.
   If no such character is found, it should return null. Please design test cases for this function called 'getFirstDoubleChar'

#### 2-1-a.

1. Backend synchronization
2. Caching
3. Network delay
4. Error handling or exception handling
5. Inconsistent data validation (schema)
6. The frontend might only check if the names are the same without considering if the IDs are also the same.

#### 2-1-b.

- testing GET method response data 200, verify that the API returns a JSON response.
- testing list of ids in app object do not duplicate
- testing the structure and fields of the JSON response.
- testing the uniqueness of app IDs in the response.
- testing the response when no apps are available.
- testing UI and API releted
-

#### 2-2

- Define a set variable of type set() to store the first character that appears twice in the string.
- Define a string variable first_character with the default value set to None for storing the first character.
- Run a for loop on the string to find the first character that appears twice. If no such character is found, assign the character to the first_character variable.
- Compare the return value of the function with the first character found.
  and
- Input: "hello", expected : 'l'
- Input: "programming", expected : 'r'
- Input: "abcdefg", expected : null
- Input: "a", expected : null
- INput: "", expected: error message
- Input: "a b c c d e", expected : 'c'
- Input: "!@#$%^&\*()", expected : null

## 3-Git questions.txt

#### 1. Please explain the commands needed to submit your modified code to the remote GitHub repository.

1. git status
2. git add .
3. git commit -m "modify where"
4. git pull origin branch_name
5. fix conflict
6. git push origin branch_name

#### 2. Assuming you are creating a Git branch for an automation test case and have started developing and committing changes.

You realize that you have made 5 commits, making it difficult to perform code reviews on the branch or merge it into
the main branch. Please describe briefly what you would do and provide the corresponding git commands.

1. git branch
2. git checkout branch_name
3. git status
4. git rebase -i HEAD~5
5. git pull origin branch_name
6. fix conflict
7. git push origin branch_name

## 4-Coding questions.txt

Please design a function that takes an integer array and returns the indices of two numbers whose sum equals a target number.
For example, if the array is [2, 7, 11, 15] and the target number is 9, the function should return [0, 1], because 2 + 7 = 9.
Consider the following scenarios:

1. If no two numbers whose sum equals the target number are found, return null.
2. Numbers may appear multiple times in the array, but there is only one combination that meets the target sum.
3. The numbers in the array may have a large range, so please consider performance issues if you have time.

```js
var twoSum = function (nums, target) {
  var map = {};
  for (let i = 0; i < nums.length; i++) {
    let v = nums[i];

    if (map[target - v] >= 0) {
      return [map[target - v], i];
    } else {
      map[v] = i;
    }
  }
};
```
