# C++ Code Smell Visualization
A tool designed to make code smells (antipatterns) identification and planning easier for Project Management for code bases in C++. 

We were compelled to create this project as a way to improve a company's code base overall. With a visualization such as this, it is easier for a Project Manager or Team to identify what code would benefit from further refactoring, or even which sections of the code need the most work. This could be invaluable to Project Managers as they decide which portions of code to assign to developers, or which developers seem more confident doing high-impact things on architecture critical code.

With a dictionary of known or suspected code smells, it empowers JIRA or Task Oriented Project Managers to create Task Items relating to code maintenance. While a Project Manager is identifying items from the “feature backlog” or their “design-meeting”, they can run our tool to identify high impact areas that the following code smells impact: Large Methods, Long Parameter List, Duplicate Code, Large (God) Class, and Lack of Comments.

 

Main Goals/Objectives:

  Identify Code Smells and Their Locations in Code:

    Large Method
    Methods that are 50% larger than the average method length.

    Long Parameter List
    Methods that contain 5 or more parameters.

    Duplicate Code
    Code segments that contain the same text for 5 or more lines.

    Large Class
    Classes that contain 25% more methods/variables from the average count.

    Lack of Comments
    Identify Classes or Methods that do not have comments.

  Visualize their existence and appearance in a easy to understand overview, such as a city/network diagram. 

  Offer suggestions to developers on how to improve the code base, from a dictionary of already curated solutions (* If Time).

  Create a sort of “Refactoring” backlog to be used in tandem with Agile Processes and “Task Oriented” Softwares like JIRA (* If Time).


Planned to be written with Python using an Agile Iterative Cycle ==> with highlight on refactoring.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)