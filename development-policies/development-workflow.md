# Development Workflow

1. ### SCRUM Process {#scrum-process}

Hardware development, unlike software development, often involves physical components and manufacturing processes, which can make it seem less compatible with agile Frameworks like Scrum. However, it's entirely possible to adapt Scrum principles to hardware development with some modifications which the eCozy team incorporated into the development process. Here's how the process was adapted using elements of Scrum in terms of Hardware Development:

* **Product Backlog:** a product backlog was initially created containing most of the features, components, and tasks required to develop the hardware products such as Thermostat, Central Unit and Thermosensor. The backlog was prioritized based on the value they provide to the end-use and was permanently maintained by the Product Owner,  
* **Sprints:** the development process was divided into fixed 2 weeks sprints, time periods during which the team worked to complete a set of tasks from the product backlog. As per vanilla Scrum each sprint should result in a potentially shippable increment of the product (hardware in this case), even if it's just a prototype or part of the final product. However, for the complex deliverables such as eCozy 2.0 devices the result increments were provided in a few iterations with the feedback from the stakeholders to assist in applying better approaches for the future stages,  
* **Sprint Planning:** At the beginning of each sprint, the team conducted a sprint planning meeting to select the tasks from the product backlog that they were working on during the sprint. They broke down these tasks into smaller, more manageable sub-tasks and estimated the effort required to complete them.  
* **Daily Stand-ups:** The team held daily stand-up meetings where team members briefly discussed what they worked on the previous day, what they plan to work on that day, and any obstacles or dependencies they're facing which might have been a blocker to achieve Sprint goal. This kept everyone aligned and helped to identify and address issues at the early stages.  
* **Sprint Review:** At the end of each sprint, the team held a sprint review meeting to demonstrate the work completed during the sprint to stakeholders and other team members. This involved showcasing scheme  prototypes, discussing design iterations, or presenting test results.  
* **Product Backlog refinement:** The main purpose of Product Backlog refinement sessions is to ensure that the Product Backlog, which contains a prioritized list of all desired product features, enhancements, and fixes, is updated, prioritized, and well-understood by the development team. These sessions typically involve collaborative discussions among stakeholders, including the product owner, development team, to clarify requirements, refine user stories, estimate effort, and adjust priorities as needed. Ultimately, the goal is to keep the Product Backlog in a state where it is ready for sprint planning and execution, enabling the development team to deliver valuable increments of the product with each iteration.  
* **Jour Fix:** By bringing together stakeholders from different areas of expertise such as technical solution, business areas, marketing, these meetings of this nature facilitate comprehensive discussions and ensure that all aspects of the project are considered, ultimately driving towards its successful completion.

**![][image10]**

2. ### Maintenance and Support {#maintenance-and-support}

**Text:** Post-launch, products enter the Maintenance and Support phase, governed by the following process:

1. **Bug Triage:** All issues reported by customers or QA are logged in Jira. The Project Manager and Team Lead triage these bugs weekly, assigning a priority (Blocker, Critical, Major, Minor).  
2. **Hotfixes:** `Blocker` or `Critical` bugs that impact production users are addressed immediately. A `hotfix/*` branch is created from `main`, the fix is implemented and tested, and then merged directly into `main` (for immediate release) and `develop` (to prevent regression).  
3. **Maintenance Sprints:** `Major` and `Minor` bugs, along with small enhancements, are batched and prioritized. They are worked on during regular sprints alongside feature development or in dedicated "maintenance" sprints, following the standard `feature/*` branch workflow.
