
# JSTL tags

- <c:foreach>
	- Attributes:
		-  items: collection of items to loop over
		-  var: variable used for the loop
		-  begin: begin at value specified
		-  end: end at value specified
		-  step: increment/decrement

- <c:out>
	- Like <%= %> but for expressions
	- Attributes:
		-  value: expression to be evaluated
		-  default: evaluated if value is null

- <c:set>
	- Sets result of expression evaluation
	- Attributes:
		- var: variable for the value being set
		- value: evaluated value to be set

- <c:url>
	- Creates url with optional parameters
	- Attributes:
		- var: variable for the url
		- value: url to be processed

- <c:param>
	-  Adds parameter to url
	-  Attributes:
		- name: name of parameter
		- value: value of parameter

- <c:if>
	- Conditional tag, evaluates body if test condition is true
	- Attributes;
		- test: boolean expression to be tested
		- var: export boolean value of the test condition

- <c:choose>
	- Tag that contains mutually exclusive conditional operations, like if/else
	- if - <c:when>
	- else: <c:otherwise>

- <c:when>
	- Subtag of <c:choose>, executes body if test condition is true
	- Attributes:
		- test: boolean expression to be tested

- <c:otherwise>
	- Follows <c:when> tags and executes body when all other conditions are false

- pageScope.name
	- Comes from pageContext.setAttribute(name, value)
	- only lasts for a specific JSP page

- requestScope.name
	- Comes from request.setAttribute(name, value); request.getRequestDispatcher(jsp).forward(req, resp);
	- Available for a single HTTP request

- sessionScope.name
	- Comes from session.setAttribute(name, value)
	- Stored in users session, available until session expires
