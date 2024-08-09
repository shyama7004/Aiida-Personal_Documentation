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

The sequence of the topics is logically structured based on the typical workflow of setting up and using PostgreSQL, especially for a beginner:

### 1. **Installation and Configuration**:
   - **[Installation from Binaries](https://www.postgresql.org/docs/current/installation.html)**: Setting up PostgreSQL.
   - **[Server Configuration](https://www.postgresql.org/docs/current/runtime-config.html)**: Configuring your server for optimal performance. 

### 2. **SQL Language Basics**:
   - **[Data Definition Language (DDL)](https://www.postgresql.org/docs/current/sql-createtable.html)**: Creating tables, indexes, views.
   - **[Data Manipulation Language (DML)](https://www.postgresql.org/docs/current/sql-insert.html)**: Inserting, updating, deleting data.
   - **[Queries](https://www.postgresql.org/docs/current/tutorial-join.html)**: Selecting and retrieving data.

### 3. **Database Design**:
   - **[Indexes](https://www.postgresql.org/docs/current/indexes.html)**: Efficiently accessing data.
   - **[Performance Optimization](https://www.postgresql.org/docs/current/performance-tips.html)**: Techniques to improve query speed.

### 4. **Transactions and Concurrency**:
   - **[Transactions](https://www.postgresql.org/docs/current/tutorial-transactions.html)**: Ensuring reliable transactions.
   - **[Concurrency Control](https://www.postgresql.org/docs/current/mvcc.html)**: Handling concurrent data access.

### 5. **Backup and Restore**:
   - **[Backup and Restore](https://www.postgresql.org/docs/current/backup.html)**: Essential for data recovery.

### Python Basics (4 days)
- **[Real Python](https://realpython.com/)**: A comprehensive resource for learning Python programming.

#### 1. **Basic Syntax and Data Structures**
   - **[Introduction to Python Syntax](https://docs.python.org/3/reference/lexical_analysis.html)**: Learn the fundamental syntax rules of Python.
   - **[Data Types and Variables](https://realpython.com/python-data-types/)**: Explore different data types in Python and how to use variables.
   - **[Lists](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)**: Creating, accessing, and modifying lists, and understanding list comprehensions.
   - **[Dictionaries](https://realpython.com/python-dicts/)**: Creating and using dictionaries in Python.
   - **[Sets](https://realpython.com/python-sets/)**: Learn about sets and how to use them effectively.
   - **[Tuples](https://realpython.com/python-tuples/)**: Understanding tuples and their usage.

#### 2. **Control Structures**
   - **[Conditional Statements](https://realpython.com/python-conditional-statements/)**: Using `if`, `elif`, and `else` for conditional logic.
   - **[Loops](https://docs.python.org/3/tutorial/controlflow.html#for-statements)**: Understanding `for` and `while` loops in Python.
   - **[Exception Handling](https://realpython.com/python-exceptions/)**: Using `try`, `except`, and `finally` to handle errors effectively.

#### 3. **Functions and Modules**
   - **[Defining Functions](https://realpython.com/defining-your-own-python-function/)**: How to define and use functions in Python.
   - **[Lambda Functions](https://realpython.com/python-lambda/)**: Introduction to lambda functions for concise function definitions.
   - **[Modules and Packages](https://realpython.com/python-modules-packages/)**: Working with modules and packages in Python.
   - **[Scopes and Namespaces](https://realpython.com/python-scope-legb-rule/)**: Understanding variable scopes and namespaces in Python.

#### 4. **Object-Oriented Programming (OOP)**
   - **[Introduction to OOP](https://realpython.com/python3-object-oriented-programming/)**: Core principles of Object-Oriented Programming in Python.
   - **[Classes and Objects](https://realpython.com/python-classes/)**: Creating and using classes and objects in Python.
   - **[Inheritance](https://docs.python.org/3/tutorial/classes.html#inheritance)**: Using inheritance to extend classes in Python.
   - **[Polymorphism](https://docs.python.org/3/glossary.html#term-polymorphism)**: Applying polymorphism in Python programming.
   - **[Encapsulation and Access Modifiers](https://docs.python.org/3/tutorial/classes.html#private-variables)**: Implementing encapsulation and access control in Python classes.

#### 5. **Error Handling**
   - **[Using `try-except` Blocks](https://realpython.com/python-exceptions/)**: Handling errors with `try` and `except`.
   - **[Raising Exceptions](https://docs.python.org/3/tutorial/errors.html#raising-exceptions)**: Manually raising exceptions in Python.
   - **[Finally and Cleanup Actions](https://docs.python.org/3/tutorial/errors.html#defining-clean-up-actions)**: Using `finally` to ensure cleanup actions.
   - **[Best Practices for Error Handling](https://docs.python.org/3/tutorial/errors.html#handling-exceptions)**: foundation for contributing to projects like AiiDA.

## Scientific Computing

I apologize for the confusion earlier. Here are updated, correctly working links to resources that will help you prepare for contributing to AiiDA using SciPy:

### 1. **Basic SciPy Operations**
   - **[Mathematical Functions](https://docs.python.org/3/library/math.html)**: Learn how to use SciPy's special mathematical functions.
   - **[Linear Algebra](hhttps://www.geeksforgeeks.org/scipy-linear-algebra-scipy-linalg/)**: Understand matrix operations, decompositions, and linear algebra functions in SciPy.
   - **[Integration](https://www.geeksforgeeks.org/scipy-integration/)**: Familiarize yourself with numerical integration methods in SciPy, including ODE solvers.
   - **[Optimization](https://www.geeksforgeeks.org/optimization-in-scipy/)**: Study how to use SciPy’s optimization techniques, including minimization, curve fitting, and root finding.
   - **[Interpolation](https://www.geeksforgeeks.org/scipy-interpolation/)**: Learn about different interpolation methods in SciPy and their applications to data.

### 2. **Data Processing and Analysis**
   - **[Signal Processing](https://docs.scipy.org/doc/scipy/tutorial/signal.html)**: Explore SciPy’s signal processing tools, such as filtering, Fourier transforms, and convolution operations.
   - **[Statistical Analysis](https://www.geeksforgeeks.org/scipy-stats/)**: Understand SciPy’s statistical functions, including hypothesis testing, probability distributions, and statistical analysis.
   - **[Handling Large Datasets](https://www.geeksforgeeks.org/handling-large-datasets-in-python/)**: Learn how to efficiently manipulate large datasets using SciPy along with NumPy.

### 3. **Advanced SciPy Modules**
   - **[Sparse Matrices](https://docs.scipy.org/doc/scipy/reference/sparse.html)**: Work with sparse matrices in SciPy and understand their applications in large-scale computations.
   - **[Spatial Data Analysis](https://docs.scipy.org/doc/scipy/reference/spatial.html)**: Study how to handle spatial data, perform distance computations, and use KD-trees with SciPy’s spatial module.
   - **[Image Processing](https://docs.scipy.org/doc/scipy/reference/ndimage.html)**: Learn about image processing techniques using SciPy’s ndimage module, including filtering and morphological operations.

### 4. **Workflow Integration**
   - **[Understanding Workflows](https://aiida.readthedocs.io/projects/aiida-core/en/latest/)**: Learn the concepts of scientific workflows and how to design them.
   - **[Workflow Management Systems](https://aiida.readthedocs.io/projects/aiida-core/en/latest/howto/workflows/)**: Get familiar with AiiDA’s workflow management, task scheduling, data provenance, and automation.
   - **[Integration with AiiDA](https://aiida.readthedocs.io/projects/aiida-core/en/latest/)**: Understand how to integrate SciPy computations within AiiDA workflows, ensuring reproducibility and data provenance.

### 5. **Practical Applications and Case Studies**
   - **[Practical Examples](https://aiida.readthedocs.io/projects/aiida-core/en/latest/howto/index.html)**: Work on real-world examples where SciPy and AiiDA are used together, such as setting up simulations or optimizing scientific experiments.
   - **[AiiDA Plugins](https://aiida.readthedocs.io/projects/aiida-core/en/latest/howto/plugins.html)**: Learn how to write and use AiiDA plugins that require SciPy for their calculations.

### 6. **Documentation and Best Practices**
   - **[SciPy Documentation](https://docs.scipy.org/doc/scipy/)**: Get familiar with the official SciPy documentation for quick reference on functions and their usage.
   - **[AiiDA Contribution Guidelines](https://aiida.readthedocs.io/projects/aiida-core/en/latest/contributing/index.html)**: Study AiiDA’s contribution guidelines and documentation to ensure your work aligns with the project’s standards.

These links should now correctly direct you to the resources you need.


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
     - [Roles](https://www.atlassian.com/agile/scrum/roles): Learn about the key roles in Scrum, including Product Owner, Scrum Master, and Development Team.
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
