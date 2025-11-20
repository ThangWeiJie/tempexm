
# MVC

- Stands for Model View Controller
- Model: Manages data and business logic, performing data operations; Example: Java Objects or Beans
- View: Renders the data and output to the user; Using JSP/Thymeleaf in HTML form
- Controller: Processes user input and business logic; Invokes model to process data; Choose view to render


# Servlet as Controller

- Java class that handles HTTP requests and forwards to model or view
- Lifecycle
	- init(): Initializes the servlet
	- service(): Routes the request to doGet() or doPost()
	- doGet(): Processes GET requests
	- doPost(): Processes POST requests
	- destroy(): Destroys and cleans up the servlet

- Forward requests from controller to view:
	- request.getRequestDispatcher("example.jsp").forward(request, response);


# POJO as Model

- POJO: Plain Old Java Object
- Like a regular Java Object with attributes, constructors, getter/setter methods and others

# JavaBeans

- Implement Serializable interface
- Public, no arg constructor
- set and get methods

- Using JavaBeans
	- <jsp:useBean id="bean name" scope = "bean scope" class = "bean class name"/>: Declare a bean
	- <jsp:setProperty name="bean name" property="property name" value="value/>
	- <jsp:getProperty name="bean name" property="property name"/>


# JSP for View

- Can include java code for dynamic rendering
- Scripting Elements
	- Scriptlet tag <% %>: used to write java code in JSP
	- Expression tag <%= %>: evaluates body and displays it 
	- Declaration tag <%! %>: used to declare variables/methods
	- JSP Comment tag: <%-- --%>; HTML Comment Tag: \<!-- -->
- Directive Elements
	- Page directive: \<%@ page attribute= "value"%>; Can be used to import classes/library into the JSP file
	- Include directive: \<%@ page include="filename" %> Used to include other pages directly into the page
	- Taglib directive: \<%@ taglib uri="uri" prefix="prefix" %>
		- Used to import JSTL
- Implicit objects:
	- out: JSPWriter
	- request: HTTPServletRequest
	- response: HTTPServletResponse
	- config: ServletConfig
	- application: ServletContext
	- session: HTTPSession
	- pageContext: PageContext
	- page: Object
	- exception: Throwable
- Action elements:
	- <jsp:include page="URL"/>: Include static or dynamic resources at request time
	- <jsp:forward page="URL"/>
	- <jsp:useBean id="name" path="fully_qualified_pathname" scope = "{page | request | session | application}" />



# Sessions

- How does Java keep track of session?
	- Uses an ID that is associated with a session object
	- Java checks if ID is included, if not, create a unique ID with the session object
## Cookies

- Types of cookies:
	- Persistent cookies: Cookies that last multiple sessions. Only removed if the user signs out
	- Per-session cookies: Cookies are removed after the user closes the browser
- Cookie class
	- `Cookie(String name, String value)`: Constructor
	- `addCookie(Cookie c)`: add cookie to response
	- `getCookies(): Cookie[]` : returns array of cookies from response
	- `setMaxAge(int seconds)`: persistent cookie: number > 0; per-session: -1
	- `setPath(String path)`: Set path to "/" to allow entire application to use the cookie
	-  `getName()`: Returns name of cookie
	-  `getValue()`: Returns value of cookie

## Hidden form field

- Uses `<input type="hidden">`

# URL Rewriting

- Uses `response.encodeURL(String url)`

## HttpSession

- `public HttpSession getSession(boolean create)`: Returns current session. If session doesnt exist and create is true, create new session, otherwise return null
- Implicit `session` object in JSP page
- `session.setAttribute(String name, Object o)`: Sets an object as a session attribute with a name.
- `session.getAttribute(String name)`: Returns value of attribute with the specified name, if does not exist return null. Type of value: Object
- `session.removeAttribute(String name):` Removes attribute
- `session.getAttributeNames()`: Return an Enumeration object with all attribute names.
- `session.getId()`: Returns unique id generated for the session
- `session.isNew()`
- `session.setMaxActiveInterval(int seconds)`: Default 1800 seconds
- `session.invalidate()`: Invalidates the session