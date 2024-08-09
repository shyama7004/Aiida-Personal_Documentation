# AiiDA GSoC Contribution Preparation

## AiiDA-Specific Knowledge

### AiiDA Framework (7 days)
- **[AiiDA Official Documentation](https://aiida.readthedocs.io/)**: The most comprehensive and authoritative guide for learning and using the AiiDA framework.
 
### AiiDA Framework (7 days)

**AiiDA Official Documentation:**  
This is the primary resource for understanding and mastering the AiiDA framework. It includes comprehensive guides, tutorials, and API references.

1. **Installation and Setup**
   - **Setting up an AiiDA Environment:**  
     - Learn how to install AiiDA on your local machine or a server.
     - Understand the necessary dependencies (like PostgreSQL, RabbitMQ) and how to configure them.
     - Explore virtual environments and package management with `pip` for AiiDA.
   - **Configuration:**  
     - Set up the `aiida` command-line interface (CLI).
     - Configure AiiDA to connect with external databases and message brokers.
     - Understand the purpose and setup of profiles in AiiDA.

2. **Managing Workflows**
   - **Creating Workflows:**  
     - Understand the basics of creating workflows using AiiDA’s `WorkChain` and `CalcJob` classes.
     - Learn how to define input parameters, manage computational tasks, and handle outputs.
   - **Submitting Workflows:**  
     - Explore the process of submitting workflows to AiiDA's daemon for execution.
     - Learn about the different types of `Processes` in AiiDA.
   - **Monitoring and Retrieving Results:**  
     - Understand how to monitor the progress of running workflows using the `verdi` command-line tools.
     - Learn how to query and retrieve the results of completed workflows.

3. **Data Provenance**
   - **Tracking Data Provenance:**  
     - Learn how AiiDA automatically tracks the full provenance of all data within the platform.
     - Understand how to use AiiDA’s querying capabilities to explore data lineage.
   - **Storing and Handling Data:**  
     - Explore how AiiDA stores data in the database and how to manage it efficiently.
     - Learn about the different storage backends and how they integrate with AiiDA.

4. **Plugins**
   - **Developing Plugins:**  
     - Learn the basics of creating AiiDA plugins for custom workflows, data types, and calculation types.
     - Understand the structure of an AiiDA plugin and how to extend the core functionality.
   - **Using Existing Plugins:**  
     - Explore the AiiDA plugin registry to find existing plugins relevant to your work.
     - Understand how to install, configure, and use these plugins within your workflows.


### Python Basics (4 days)
- **[Real Python](https://realpython.com/)**: A comprehensive resource for learning Python programming, suitable for beginners and advanced users alike.

#### 1. **Basic Syntax and Data Structures**
   - **Introduction to Python Syntax**
     - Learn the fundamental syntax rules of Python, including indentation, comments, and basic input/output functions (`print()`, `input()`).
     - Understand the differences between Python 2 and Python 3, and why Python 3 is recommended.

   - **Data Types and Variables**
     - Explore the different data types in Python: integers, floats, strings, and booleans.
     - Learn how to declare and use variables, including naming conventions and dynamic typing.

   - **Lists**
     - Learn how to create, access, modify, and iterate over lists.
     - Understand list methods like `append()`, `remove()`, `pop()`, and `sort()`.
     - Explore list comprehensions for concise and efficient list operations.

   - **Dictionaries**
     - Understand how to create dictionaries with key-value pairs.
     - Learn to access, modify, and iterate over dictionary items.
     - Explore dictionary methods like `get()`, `keys()`, `values()`, and `items()`.

   - **Sets**
     - Learn how to create and use sets, focusing on their unique element property.
     - Understand set operations such as union, intersection, and difference.
     - Explore set methods like `add()`, `remove()`, `union()`, and `intersection()`.

   - **Tuples**
     - Understand the immutability of tuples and how to create them.
     - Learn how to access and unpack tuple elements.
     - Explore the use of tuples in functions and data structures.

#### 2. **Control Structures**
   - **Conditional Statements**
     - Learn to use `if`, `elif`, and `else` statements to control the flow of your program.
     - Understand nested conditions and the importance of logical operators (`and`, `or`, `not`).

   - **Loops**
     - **For Loops**: Learn how to iterate over sequences like lists, dictionaries, and strings using `for` loops.
     - **While Loops**: Understand how to use `while` loops for repeated execution based on a condition.
     - Explore loop control statements like `break`, `continue`, and `else` with loops.

   - **Exception Handling**
     - Learn the importance of handling errors gracefully using `try-except` blocks.
     - Understand how to raise exceptions with `raise`, and use `finally` for cleanup operations.
     - Explore specific exceptions and how to handle them (e.g., `ValueError`, `TypeError`, `IndexError`).

#### 3. **Functions and Modules**
   - **Defining Functions**
     - Learn how to define functions using the `def` keyword.
     - Understand function arguments, return values, and default parameters.
     - Explore the concept of recursive functions and their use cases.

   - **Lambda Functions**
     - Understand what lambda functions are and how to use them for small, anonymous functions.
     - Learn common use cases of lambda functions, especially with functions like `map()`, `filter()`, and `reduce()`.

   - **Modules and Packages**
     - Learn how to import and use standard Python modules like `math`, `os`, and `sys`.
     - Understand how to create your own modules and import them into other Python files.
     - Explore the Python Package Index (PyPI) and how to install external packages using `pip`.

   - **Scopes and Namespaces**
     - Understand the concept of local, global, and nonlocal scopes in Python.
     - Learn how Python resolves variable names using the LEGB (Local, Enclosing, Global, Built-in) rule.
     - Explore how to use the `global` and `nonlocal` keywords to modify variables in different scopes.

#### 4. **Object-Oriented Programming (OOP)**
   - **Introduction to OOP**
     - Understand the core principles of OOP: Encapsulation, Inheritance, Polymorphism, and Abstraction.
     - Learn how OOP is implemented in Python and why it is beneficial for structuring large codebases.

   - **Classes and Objects**
     - Learn how to define classes using the `class` keyword and instantiate objects from them.
     - Understand the `__init__()` method and its role in initializing object attributes.
     - Explore how to add methods to a class and access attributes and methods from an object.

   - **Inheritance**
     - Understand how to create subclasses that inherit attributes and methods from a parent class.
     - Learn how to override methods in a subclass and use the `super()` function to call parent class methods.
     - Explore the concept of multiple inheritance and the method resolution order (MRO).

   - **Polymorphism**
     - Learn how polymorphism allows different classes to be treated as instances of the same class through method overriding.
     - Explore how to use polymorphism in functions and class methods to work with objects of different classes.

   - **Encapsulation and Access Modifiers**
     - Understand the concept of encapsulation and how to protect data using private and protected attributes.
     - Learn how to implement getter and setter methods for controlled access to class attributes.

#### 5. **Error Handling**
   - **Using `try-except` Blocks**
     - Learn how to wrap potentially error-prone code in `try` blocks and handle exceptions with `except`.
     - Understand how to handle multiple exceptions and provide custom error messages.

   - **Raising Exceptions**
     - Learn how to raise exceptions manually using the `raise` keyword.
     - Understand when to use custom exceptions and how to define them.

   - **Finally and Cleanup Actions**
     - Explore the use of the `finally` block to execute cleanup actions, such as closing files or releasing resources, regardless of whether an exception occurred.

   - **Best Practices for Error Handling**
     - Learn best practices for writing robust code, including catching specific exceptions, avoiding bare `except` statements, and logging errors for debugging purposes.


## Scientific Computing

### Scientific Computing (7 days)
- **[SciPy](https://www.scipy.org/)**: An essential library for performing scientific and technical computing in Python.
  
  #### 1. **Understanding Scientific Workflows**
     - **Introduction to Scientific Workflows**
       - Learn what scientific workflows are and how they are used to manage and automate scientific computations.
       - Understand the importance of reproducibility and transparency in scientific research.
       - Explore examples of scientific workflows in computational research.

     - **Components of a Scientific Workflow**
       - Learn about the different components of a scientific workflow, such as data inputs, computational steps, and result outputs.
       - Study how workflows can be broken down into tasks and how these tasks are interconnected.

     - **Workflow Management Tools**
       - Introduction to workflow management systems (WMS) like AiiDA.
       - Learn how AiiDA manages complex workflows, from task scheduling to data provenance tracking.
       - Explore the advantages of using a WMS for large-scale scientific computations.

  #### 2. **Utilizing SciPy for Scientific Calculations and Data Processing**
     - **Basic Operations with SciPy**
       - Learn how to perform basic operations in SciPy, including mathematical functions, linear algebra, and integration.
       - Explore the use of `scipy.optimize` for optimization problems, `scipy.interpolate` for interpolation, and `scipy.integrate` for numerical integration.
       - Study how SciPy can be used to solve ordinary differential equations (ODEs) and perform Fourier transforms.

     - **Data Processing and Analysis**
       - Learn how to use SciPy for data processing tasks such as filtering, smoothing, and fitting data to models.
       - Explore the use of `scipy.stats` for statistical analysis, including hypothesis testing and probability distributions.
       - Understand how to handle large datasets efficiently with SciPy and NumPy.

     - **Advanced SciPy Modules**
       - Dive deeper into advanced SciPy modules like `scipy.ndimage` for image processing and `scipy.spatial` for spatial data analysis.
       - Learn how to work with sparse matrices using `scipy.sparse` and perform scientific computations on them.

     - **Practical Applications in Scientific Computing**
       - Apply the concepts learned by working on practical examples and projects, such as data analysis pipelines or simulation models.
       - Explore case studies where SciPy has been used in scientific research to solve real-world problems.

     - **Integration with AiiDA**
       - Understand how to integrate SciPy-based calculations within AiiDA workflows.
       - Learn how to use AiiDA to automate and manage SciPy computations, ensuring data provenance and reproducibility.


## Version Control

### Git and Version Control (3 days)
- **[Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials)**: Thorough and practical guides on using Git.
  - **Git Basics**
    - Cloning repositories, committing changes, and managing branches.
  - **GitHub/GitLab**
    - Hosting repositories, creating pull requests, and participating in code reviews.

## Documentation and Communication

### Documentation (3 days)
- **[Markdown Guide](https://www.markdownguide.org/)**: Comprehensive guide to writing documentation in Markdown format.
  - **Writing Clear Documentation**
    - Documenting code, APIs, and processes clearly and effectively.
  - **Markdown**
    - Learning Markdown syntax to write documentation for repositories and wikis.


### Team Collaboration (4 days)
- **[Atlassian Agile Tutorial](https://www.atlassian.com/agile)**: The go-to resource for understanding Agile methodologies and practices, essential for effective teamwork in software development.

#### 1. **Agile Methodologies**
   - **Introduction to Agile**
     - Understand the core principles and values of Agile from the Agile Manifesto.
     - Learn why Agile is favored in software development, focusing on flexibility, customer collaboration, and iterative progress.
   
   - **Scrum Framework**
     - **Roles**: Learn about the key roles in Scrum, including Product Owner, Scrum Master, and Development Team.
     - **Artifacts**: Study the essential artifacts in Scrum, such as the Product Backlog, Sprint Backlog, and Increment.
     - **Events**: Understand Scrum events like Sprint Planning, Daily Standups, Sprint Review, and Sprint Retrospective.
     - **Sprint Cycles**: Learn how to plan and execute work in short, iterative cycles called Sprints.
     - **User Stories**: Understand how to write and manage user stories for backlog items, and how to prioritize them.
     - **Burn-down Charts**: Learn how to use burn-down charts to track the team's progress during a sprint.

   - **Kanban Methodology**
     - **Kanban Basics**: Introduction to Kanban, focusing on visualizing work, limiting work in progress (WIP), and managing flow.
     - **Kanban Board**: Learn how to set up and manage a Kanban board, with columns representing stages of work (e.g., To Do, In Progress, Done).
     - **Work-In-Progress (WIP) Limits**: Understand the importance of WIP limits to avoid bottlenecks and improve efficiency.
     - **Continuous Delivery**: Learn how Kanban supports continuous delivery and improvement by focusing on flow and cycle time.
     - **Measuring and Optimizing**: Study how to measure flow with metrics like cycle time and lead time, and how to optimize them.

   - **Choosing Between Scrum and Kanban**
     - Learn the strengths and weaknesses of Scrum and Kanban.
     - Understand scenarios where Scrum or Kanban might be more appropriate.
     - Explore hybrid approaches like Scrumban, which combine elements of both methodologies.

#### 2. **Communication Tools**
   - **Introduction to Communication Tools**
     - Understand the importance of effective communication in Agile teams for coordination, transparency, and quick decision-making.
   
   - **Using Slack for Team Collaboration**
     - **Channels**: Learn how to organize conversations into channels based on projects, teams, or topics.
     - **Direct Messages**: Understand when to use direct messages versus public channels for communication.
     - **Integrations**: Explore how to integrate Slack with tools like GitHub, Jira, and Google Drive to streamline workflows.
     - **Notifications**: Learn how to set up and manage notifications to stay informed without being overwhelmed.
     - **File Sharing**: Understand the best practices for sharing files and documents within Slack.
     - **Slack Apps**: Explore useful Slack apps like polls, reminders, and task management tools to enhance team productivity.

   - **Using Microsoft Teams for Collaboration**
     - **Teams and Channels**: Learn how to set up teams and organize channels by departments, projects, or topics.
     - **Meetings**: Understand how to schedule, conduct, and record virtual meetings, including the use of video, screen sharing, and whiteboards.
     - **Integration with Office 365**: Explore how Teams integrates with Office 365 tools like Word, Excel, and OneNote for seamless collaboration.
     - **Task Management**: Learn how to use the Tasks app (integrated with Planner) within Teams to assign and track tasks.
     - **Security and Compliance**: Understand the security features in Teams, including data encryption, compliance, and managing guest access.
     - **Best Practices**: Study best practices for using Teams efficiently, such as organizing files in OneDrive, setting up notifications, and maintaining a clear communication structure.

   - **Choosing Between Slack and Microsoft Teams**
     - Compare the features, strengths, and weaknesses of Slack and Microsoft Teams.
     - Understand which tool might be better suited to different types of projects or teams.
     - Explore the potential for using both tools in complementary ways, if necessary.



<!--### Web Development Topics

**HTML, CSS, JavaScript**
- **[MDN Web Docs](https://developer.mozilla.org/en-US/)**: The most comprehensive and authoritative resource for learning and referencing HTML, CSS, and JavaScript.

#### Week 1: HTML & CSS
- **HTML (3 days)**
  - [Introduction to HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML)
  - [Getting started with HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started)
  - [What's in the head? Metadata in HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML)
  - [HTML text fundamentals](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/HTML_text_fundamentals)
  - [Creating hyperlinks](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)
  - [Advanced text formatting](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting)
  - [Document and website structure](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)
  - Debugging HTML
  - Marking up a letter
  - Structuring a page of content
  - Multimedia and embedding
  - Images in HTML
  - Video and audio content
  - From object to iframe — other embedding technologies
  - Adding vector graphics to the web
  - Responsive images
  - Mozilla splash page
  - HTML tables
  - HTML table basics
  - HTML table advanced features and accessibility
  - Structuring planet data

- **CSS (4 days)**
  - CSS Syntax and Selectors
  - Colors, Backgrounds, and Borders
  - Margins, Padding, and Box Model
  - Flexbox and Grid Layout
  - Typography (Fonts, Text Alignment, Text Decoration)
  - Positioning (Static, Relative, Absolute, Fixed, Sticky)
  - CSS Animations and Transitions
  - Media Queries and Responsive Design
  - Pseudo-classes and Pseudo-elements
  - CSS Variables and Custom Properties

#### Week 2: JavaScript
- **JavaScript Basics (4 days)**
  - Syntax, Variables, Data Types
  - Operators, Expressions, and Statements
  - Functions and Scope
  - Objects and Arrays

- **JavaScript Advanced (3 days)**
  - DOM Manipulation
  - Event Handling
  - ES6 Features (let, const, arrow functions, template literals, destructuring, spread/rest operators)
  - Promises and Async/Await
  - Error Handling
  - Fetch API and AJAX

**React**
- **[React Official Documentation](https://react.dev/learn)**: The best and most updated resource for learning React, straight from the creators of React.

#### Week 3: React
- **React Basics (4 days)**
  - Introduction to React and JSX
  - Components and Props
  - State and Lifecycle
  - Handling Events
  - Conditional Rendering
  - Lists and Keys
  - Forms and Controlled Components
  - Lifting State Up

- **React Advanced (3 days)**
  - Composition vs. Inheritance
  - React Hooks (useState, useEffect, useContext, useReducer, etc.)
  - Context API
  - React Router
  - Error Boundaries
  - Higher-Order Components
  - Performance Optimization (React.memo, useCallback, useMemo)

**REST API**
- **[Swagger](https://swagger.io/)**: For designing, documenting, and testing REST APIs efficiently.

- **REST API (3 days)**
  - Introduction to RESTful Services
  - HTTP Methods (GET, POST, PUT, DELETE, PATCH)
  - REST API Design Principles
  - CRUD Operations
  - Status Codes and Responses
  - Authentication and Authorization (JWT, OAuth)
  - Versioning
  - Error Handling
  - Pagination, Filtering, and Sorting
  - Rate Limiting and Throttling
  - REST API Documentation (Swagger, Postman)
  - Consuming REST APIs (using Fetch, Axios in JavaScript)
  - CORS (Cross-Origin Resource Sharing)

### Backend Development

**Python**
- **[Real Python](https://realpython.com/)**: In-depth articles and tutorials on Python programming, suitable for all levels.

#### Week 1: Python
- **Python Basics (4 days)**
  - Basic Syntax and Data Structures (Lists, dictionaries, sets, tuples)
  - Control Structures (Loops, conditionals)
  - Functions and Modules (Defining functions, importing modules)
  - Object-Oriented Programming (Classes, inheritance, polymorphism)
  - Error Handling (Try-except blocks)

**Database Management**
- **[SQLBolt](https://sqlbolt.com/)**: Interactive and straightforward lessons on SQL.

#### Week 2: Database Management
- **SQL (4 days)**
  - Writing queries
  - Joins
  - Indexing

- **NoSQL (3 days)**
  - Understanding databases like MongoDB if needed

**Django**
- **[Django Official Documentation](https://docs.djangoproject.com/en/stable/)**: The most comprehensive guide for learning Django.

#### Week 3: Django
- **Django Basics (4 days)**
  - Setup and Configuration (Installing and setting up a Django project)
  - Models (Defining and managing data models)
  - Views and Templates (Creating views and templates for the web application)
  - Forms (Handling forms in Django)

- **Django Advanced (3 days)**
  - Authentication and Authorization (User login, registration, permissions)
  - Django REST Framework (DRF) (Building RESTful APIs)

### DevOps and Deployment

**Version Control**
- **[Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials)**: Thorough and practical guides on using Git.

#### Week 1: Version Control & Containerization
- **Version Control (3 days)**
  - Git (Cloning repositories, committing changes, branching, merging)
  - GitHub/GitLab (Hosting repositories, pull requests, code reviews)

**Containerization**
- **[Docker Official Documentation](https://docs.docker.com/)**: The best resource for learning Docker and containerization.

- **Containerization (4 days)**
  - Docker (Creating Dockerfiles, managing Docker containers)
  - Docker Compose (Managing multi-container Docker applications)

**CI/CD**
- **[GitHub Actions Documentation](https://docs.github.com/en/actions)**: A practical guide for setting up CI/CD pipelines with GitHub Actions.

#### Week 2: CI/CD & Cloud Services
- **CI/CD (3 days)**
  - Continuous Integration/Continuous Deployment (Setting up CI/CD pipelines with tools like GitHub Actions, Travis CI, Jenkins)

**Cloud Services**
- **[AWS Documentation](https://docs.aws.amazon.com/)**: Comprehensive and practical guides for deploying applications on AWS.

- **Cloud Services (4 days)**
  - AWS/GCP/Azure (Basic understanding of deploying applications to cloud platforms)
  - Vercel/Netlify (Deploying frontend applications)

### Testing

**Unit Testing**
- **[PyTest Documentation](https://docs.pytest.org/en/stable/)**: The best resource for learning PyTest for unit testing in Python.

#### Week 1: Unit, Integration, and End-to-End Testing
- **Unit Testing (2 days)**
  - PyTest/Unittest (Writing and running unit tests for Python code)

**Integration Testing**
- **[Postman Learning Center](https://learning.postman.com/)**: The go-to resource for learning API integration testing with Postman.

- **Integration Testing (2 days)**
  - Testing REST APIs (Using tools like Postman, PyTest-Django)

**End-to-End Testing**
- **[Cypress Documentation](https://docs.cypress.io/)**: Comprehensive and modern guide for end-to-end testing of web applications.

- **End-to-End Testing (3 days)**
  - Selenium/Cypress (Writing end-to-end tests for web applications)

### Data Handling and Visualization

**Data Formats**
- **[JSON.org](https://www.json.org/)**: The best resource for understanding and working with JSON.
- **XML**

**Data Visualization**
- **[Plotly](https://plotly.com/)**: Comprehensive guides and tools for creating interactive data visualizations.

#### Week 1: Data Formats & Data Visualization
- **Data Formats (3 days)**
  - JSON (Understanding and working with JSON data)
  - XML (Working with XML data if required)

- **Data Visualization (4 days)**
  - Plotly/D3.js (Visualizing data if AIIDA requires data visualization components)

### AIIDA-Specific Knowledge

**AIIDA Framework**
- **[AIIDA Official Documentation](https://aiida.readthedocs.io/)**: The most comprehensive and authoritative guide for learning and using the AIIDA framework.

#### Week 1: AIIDA Framework
- **AIIDA Framework (7 days)**
  - Installation and Setup (Setting up an AIIDA environment)
  - Managing Workflows (Understanding how to create and manage computational workflows)
  - Data Provenance (Tracking and querying the data provenance)
  - Plugins (Developing and using AIIDA plugins)

### Scientific Computing

**Scientific Computing**
- **[SciPy](https://www.scipy.org/)**: The best resource for learning scientific computing with Python.

#### Week 2: Scientific Computing
- **Scientific Computing (7 days)**
  - Understanding of Scientific Workflows (Basic understanding of how scientific computations are structured and managed)

### Communication and Collaboration

**Documentation**
- **[Markdown Guide](https://www.markdownguide.org/)**: The most comprehensive guide to writing documentation in Markdown format.

#### Week 1: Documentation & Team Collaboration
- **Documentation (3 days)**
  - Writing Clear Documentation (For code and APIs)
  - Markdown (Writing documentation in Markdown format)

**Team Collaboration**
- **[Atlassian Agile Tutorial](https://www.atlassian.com/agile)**: The best resource for understanding Agile methodologies and practices.

#### Week 2: Team Collaboration
- **Team Collaboration (4 days)**
  - Agile Methodologies (Understanding Agile practices like Scrum or Kanban)
  - Communication Tools (Using tools like Slack, Microsoft Teams for team communication)

**NextJS (Not Now)**
- **[Next.js Official Documentation](https://nextjs.org/docs)**: The most comprehensive and up-to-date resource for learning Next.js.

### Next Steps
- **NextJS (4 days)**
  - Introduction to Next.js and Setup
  - Pages and Routing
  - Static Site Generation (SSG)
  - Server-Side Rendering (SSR)
  - API Routes
  - Data Fetching (getStaticProps, getServerSideProps)
  - Dynamic Routing
  - Custom App and Document
  - CSS-in-JS (Styled JSX, CSS Modules)
  - Authentication (using NextAuth.js or other methods)
  - Deployment (Vercel, Netlify)
  - Environment Variables
  - Internationalization (i18n)
  - Incremental Static Regeneration (ISR)-->
