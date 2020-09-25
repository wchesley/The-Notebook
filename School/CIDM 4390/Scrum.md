# CIDM 4390

## Description:

Prerequisites: CIDM 2315, CIDM 3350, and CIDM4390. A capstone course for the study of software engineering, Emphasis on requirement specifications, logical design, issues in OOP, design pattern, client-server computing, project management. Students construct original and significant projects that synthesize all course experiences to produce well-designed software applications.

### Books:

> Guide to Software Structure and Design By: Bob Martin  
> Essential Scrum: A Practical Guide to the Most Popular Agile Process By: Kenneth S. Rubin

Weekly meeting set for Wednesdays @ 6pm  
Team meeetings set for Mondays @ 6pm

# Scrum Overview:

Scrum is a framework for organizing and managing work.  
Scrum is a refreshingly simple, people-centric framework based on the values of
honesty, openness, courage, respect, focus, trust, empowerment, and collaboration.

## Scrum Roles:

- 1 or more Scrum Teams each consisting of 3 roles:
  1. Product Owner
     - responsible for what will be developed and in what order.
     - central point of product leadership.
     - single authority for deciding which features and functionality to build.
     - obligated to ensure the most valuable work is performed.
  2. Scrum Master
     - responsible for guiding the team in creating and following its own process based on the broader scrum framework.
     - assists eveyrone involved in understanding and embracing Scrum values, principles and practices.
     - acts like a coach, providing process leadership
     - assists development team in thier own high-performance, organization-specific scrum approach.
     - **Scrum master is a leader not a manager.**
  3. Development Team
     - Responsible for determing how to deliver what the product owner has asked for.
     - diverse, cross-functional collecion of all types of developers
       - UI designer, database admin, programmer, architect, ecteria..
     - dev team self organizes to determine the best way to accomplish the goal set out by the product owner.
     - typical team size is 5-9, there can be multiple dev teams on a project.

## Sprint activities and artifacts

![Rubin Scrum Diagram](../../images/school/rubin_scrum.png)

From the top:

- product owner has an idea of what he wants to build
- throught **Grooming** the idea is broken down into sets of features - Overall the activity of creating and refining product backlog items, estimating
  them, and prioritizing them is known as grooming
- this set of features is organized into a prioritized list called the **Product Backlog**
  - On new-product development the product backlog items initially are features
    required to meet the product owner’s vision. For ongoing product development, the
    product backlog might also contain new features, changes to existing features, defects
    needing repair, technical improvements, and so on.
  - The product backlog is a constantly
    evolving artifact. Items can be added, deleted, and revised by the product owner as
    business conditions change, or as the Scrum team’s understanding of the product
    grows (through feedback on the software produced during each sprint).
- Sprints
  - Sprints are timeboxed, there is always a start and ending date, usually no more than a month in length.
  - Sprint Planning involves the Product Owner, Scrum Master and Dev Team.
  - During the meeting a **Sprint Goal** is agreed upon
    - Sprint Goal is what the upcomming sprint is supposed to achieve.
  - Important to work at a sustainable pace!
- Sprints start with **Sprint Planning**
  - the product backlog is too large to be completed within a single sprint. Sprint planning takes features from the product backlog; what the team can build in the timeframe of the sprint, and puts these features into the sprint backlog.
    - **Sprint Backlog**: A set of detailed tasks of how the team plans to design, build, integrate and test the selected subset of features from the product backlog.
    - Dev team will try to estimate (usually in hours) the amount of effort required to complete each task. Breaking product backlog items into tasks is a form of design and just-in-time planning for how to get the features done.
- work done during the sprint is the **Sprint execution**
  - Each day of sprint execution invloves an adaptive planning activity called **Daily Scrum**
    - Team members self organize and help manage the flow of work, daily meetings help prevent putting off issues until they might be too late to fix.
  - Nobody tells the development team in what order or how to do the task-level work in the sprint backlog. Instead, team members define their own task-level work and then self-organize in any manner they feel is best for achieving the sprint goal.
  - Ideally at the end of sprint execution the team has produced a **Potentially shippable product increment** That represents, some but not all of the product owner's vision.
- Daily Scrum
  - Short, ideally daily meeting involving the Dev Team and facilitated by the Scrum master
  - example daily scrum structure: Each team member answers the following:
    1. What did I accomplish since the last daily scrum?
    2. What do I plan to work on by the next daily scrum?
    3. What are the obstacles or impediments that are preventing me from making progress
  - The daily scrum is essential for helping the development team manage the fast, flexible flow of work within a sprint.
  - **The daily scrum is not a problem-solving activity** More of a team status update, to further assist the team inspect, sync and adapt so they might perform better.
- Done?
  - a bare-minimum definition of done should yield a complete slice of product functionality that is designed, built, integrated, tested, and documented.
- Sprints end with **Review and Retrospective**
  - **Sprint Review** stake holders and the scrum team inspect the product being built
    - The Sprint Review is focused on reviewing the just-completedfeatures in the context of the overall development effort.
    - A successful review results in bidirectional information flow. The people who aren’t on the Scrum team get to sync up on the development effort and help guide its direction. At the same time, the Scrum team members gain a deeper appreciation for the business and marketing side of their product by getting frequent feedback on the convergence of the product toward delighted customers or users.
  - **Sprint Retrospective** Scrum team inspects the scrum process being used to create the product.
    - Sprint Retrospective frequently occurs **after** the sprint review and **before** the next sprint planning.
    - During the sprint retrospective the development team, ScrumMaster, and product owner come together to discuss what is and is not working with Scrum and associated technical practices. The focus is on the continuous process improvement necessary to help a good Scrum team become great.
- Once the Retrospecive is complete, the cycle may begin again.

## Chapter 19: Sprint Planning

## Overview

A product backlog may represent many weeks or months of work, which is much
more than can be completed in a single, short sprint. To determine the most important
subset of product backlog items to build in the next sprint, the Scrum team performs
sprint planning. During sprint planning the Scrum team agrees on a goal for
the sprint, and the development team determines the specific product backlog items
that are aligned with that goal and that it can realistically deliver by the end of the
sprint. To acquire confidence in what it can deliver, the development team creates a
plan for how to complete the product backlog items. Together the product backlog
items and the plan form the sprint backlog.

## Timing

Recurring Just-in-time activity taking place at the beginning of each sprint. Meeting shouldn't last more than 8hrs for a month long sprint, 4hrs for a 2-week sprint.

## Participants

Full Scrum team is involved in spring planning. Produt owner, scrum master and Dev Team.

- Product owner shares the sprint goal, presents the prioritized product backlog items.
- Dev team works to determine what it can deliver and makes a realistic commitment at the **end** of each sprint planning.
- Scrum Master observes the planning, asks probing questions adn facilitates to help ensure a successful result. **Scrum Master is not in charge of the dev team** Scum master does not decide on what commitments the dev team makes, rather the scrum master may challenge the team's commitment to ensure it's realistic and appropriate.

## Process

The first and most crucial step is a product backlog that has been groomed prior to sprint planning so that the topmost items meet the scrum teams' definition of ready.

- Typically this means that the topmost items have well-defined acceptance criteria and are appropriately sized estimated, and prioritized.
- Engaged product owners also enter sprint planning having a good idea of what they want the team to deliver by the end of the sprint.
- product owner should communicate his initial sprint goal in a way that doesn’t unduly influence the development team to commit to more than it realistically can deliver. The fact that the product owner knows what he wants, however, does not necessarily mean that the development team is capable of delivering it during that sprint. A realistic commitment is achieved only through collaboration between the product owner and the development team members.
- Dev Team will create a plan for how they will acheive the sprint goal. Most teams break down the target Backlog items in to sets of Tasks
  - Good rule of thumb for Task Planning: A task shouldn't take more than 8 hours of effort to complete.
- At the end of sprint planning the development team’s commitment is communicated through a finalized sprint goal and the sprint backlog.

### Sprint Planning Inputs:

| Input               | Description                                                                                                                                                  |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Product Backlog     | Prior to sprint planning, the topmost product backlog items have been groomed into a _ready_ state.                                                          |
| Team Velocity       | The team’s historical velocity is an indicator of how much work is practical for the team to complete in a sprint.                                           |
| Constraints         | Business or technical constraints that could materially affect what the team can deliver are identified.                                                     |
| Team capabilities   | Capabilities take into account which people are on the team, what skills each team member has, and how available each person will be in the upcoming sprint. |
| Initial Sprint Goal | This is the business goal the product owner would like to see accomplished during the sprint.                                                                |

## Approaches to Sprint planning

### Two-Part Sprint Planning

Part 1: Dev team determines it's capacity to complete work then forecasts the product backlog iteesm that it beleives it can deleiver by the end of the sprint.
Part 2: Acquire Confidence in the teams ability to complete the items forecasted in Part 1. Most teams create this plan by breaking the product backlog items into a set of tasks and then estimating (in hours) the effort required to complete each task. The team then compares the estimate of task hours against its capacity, in terms of hours, to see if its initial commitment was realistic.

![Two Part Planning approach](../../images/school/two-part-sprint-planning.png)

### One-Part Sprint Planning

the development team begins by determining its capacity to complete work. Based on available capacity, the sprint goal may need to be refined. Next the team selects a product backlog item and then acquires confidence that the selected item will reasonably fit within the sprint, given other items already included in the team’s evolving commitment. This cycle is then repeated until the team is out of capacity to do any more work. At that point the commitment is finalized and sprint planning is over.

![One Part Planning Approach](../../images/school/One-part-sprint-planning.png)

## Determining Capactiy

In a two week sprint, we must accept that the team doens't have the full 10 working days to complete the sprint. During the Sprint time must be reserved for Sprint Planning, Sprint Review, Sprint retrospective activities and the Team should reserve at most 10% of it's time to assisting the product owner in grooming the product backlog items.  
The team must also determine how much time it should reserve for work outside the sprint, things like supporting the current product, maintaining another product, or other work unrelated to the current sprint. The team should also remember that in an eight-hour day, team members really don’t have a full eight hours to work on product backlog items. There is some overhead required to be a good citizen of the organization—attending meetings, responding to emails, interruptions, and so on. **Estimation shouldn't be 100% perfect** Things can and probably will go wrong, Planning a buffer against unexpected problems is a good solution.  
How should we measure our sprints capacity?

- same units as product backlog items? usually in story points or ideal days
- same units as the sprint backlog tasks, or effort hours.

## Selecting Product Backlog Items

Selection can be done in several ways. If we have a sprint goal, we would select product backlog items that align with that goal. If there is no formal sprint goal, our default is to select items from the top of the product backlog.  
One of Rubin's rules when selecting product backlog items for a sprint is that we don’t start what we can’t finish. So if the next product backlog item is too big to complete in the sprint given the other items that we have already agreed to complete, we should either try to break down the next item into two or more smaller items, each of which would be valuable to our customers, or consider working on another item that we can complete. Also, having a good definition of ready will prevent product backlog items from being selected that are poorly defined or have unfulfilled resource or dependency constraints that would prevent our finishing them in a sprint.

## Acquiring Confidence

Most Scrum teams gain the necessary level of confidence by breaking the product backlog items down into the tasks that are required to complete them to the Scrum team’s agreed-upon definition of done. These tasks can then be estimated (usually in effort-hours) and subtracted from the team’s capacity. Breaking product backlog items into tasks is a form of design and just-in-time planning for how to get the items done.  
Some teams use velocity however the risk of using velocity as the sole means of establishing confidence is that
even though the numbers look right, the commitment might still be unachievable.

## Refine the Sprint Goal

The sprint goal summarizes the business purpose and value of the sprint. The product owner should come to sprint planning with an initial sprint goal. That initial goal, however, can be refined during the course of sprint planning as the sprint-planning participants work together to determine what can realistically be delivered.

## Finalize the Commitment

At the completion of sprint planning the development team finalizes its commitment to the business value it will deliver by the end of the sprint. The sprint goal and the selected product backlog items embody that commitment.

# Chapter 20: Sprint Execution

Sprint execution is like a mini project unto itself—all of the work necessary to deliver a potentially shippable product increment is performed.

## Timing

Sprint Execution takes up the majority of time during a sprint, beginning just after sprint planning is completed, ending when the sprint review begins. For a two week sprint, the execution would ideally consume 8 of the 10 working days.

## Participants

- Dev Team members self-organize and determine the best way to meet the goal established during sprint planning.
- Scrum Master acts as the coach, facilitator and impediment remover, doing what they can to help the team be successful.
- Product owner must be available to answer clairfying questions, review intermediate work and provide feedback to the team.

## Sprint Execution activity

- Task Planning
- Daily Scrums
- Task Performance
- Communicating
- Flow Management  
  Inputs into the Sprint Execution are:
- Sprint Goal
- Sprint Backlog  
  Outputs:
- Potentially shippable product increment.

## Sprint Execution Planning (Task Planning)

The team produces a plan for how to achieve the sprint goal. Most teams create a sprint backlog, which consists of Product backlog items and their associated tasks with the estimated effort hours.  
The other option is to create a full task-level sprint execution plan, akin to the project plan but at sprint level, however doing so is effort intensive, the economics of creating this are hard to justify.  
A good principle for sprint execution is to approach task-level planning opportunistically rather than trying to lay out up front a complete plan of how to do the work. Allow task planning to occur continuously during sprint execution as the team adapts to the evolving circumstances of the sprint.

## Flow Management

It’s the team’s responsibility to manage the flow of work during sprint execution to meet the sprint goal. It must make decisions such as how much work the team should do in parallel, when work should begin on a specific item, how the task-level work should be organized, what work needs to be done, and who should do the work.

## Parallel Work and Swarming

An important part of managing flow is determining how many product backlog items the team should work on in parallel to maximize the value delivered by the end of the sprint. Working on too many items at once contributes to team member multitasking, which in turn increases the time required to complete individual items and likely reduces their quality.  
Just as working on too many items at the same time is wasteful, working on too few items at a time is also wasteful. It leads to underutilization of team member skills and capacity, resulting in less work being completed and less value being delivered.  
An balance between the two must be found. Rubin recommends that teams work on the number of items that leverages, but does not overburden the T-Shaped skills and available capacity of the team  
![T-Shaped skills](../../images/school/t-shapedskills.png)

This tatic of balancing overworking and underutalization is known as swarming. Where team members with available capacity gather to work to finish items that have already been started, rather than beginning new work items.  
**Teams that still think in terms of individual roles wind up with some members far ahead and others who are mired in
unfinished work. A classic individual-role-focused thought is “The testers might still have ‘their’ work to finish up, but I’m finished coding this feature, so I’m off to start coding the next one.” In a team that swarms, people would understand that it is typically better to stay focused and help get the testing done instead of running ahead to start working on new features.** Traditional role-based thinking plagues many teams. What we need instead is value-delivery-focused thinking, where the team members opportunistically organize the tasks and who will work on them. In doing so, they minimize the amount of time that work sits idle and reduce the size and frequency at which team members must “hand off” work to one another. This might mean, for example, that two people pair up on the first day of sprint execution and work in a highly interleaved fashion, with rapid cycles of test creation, code creation, test execution, and test and code refinement, and then repeat this cycle. This approach keeps work flowing (no blocked work), supports very fast feedback so that issues are identified and resolved quickly, and enables team members with T-shaped skills to swarm on an item to get it done.  
While swarming favors working on fewer items concurrently, it doesn’t necessarily mean working on only one product backlog item at a time. One item at a time might be correct in a given context, but just saying that all team members should collectively focus on a single item at a time is potentially dangerous. A different number of items might be appropriate when we consider the actual work that needs to be done, the skills of the team members, and other conditions that exist at the time a decision to start or not start working on another item needs to be made.

## What work needs to be done and who does it? 
Ultimatly it's up to the dev team to decide this. Various factors will influence the ability to accomplish the work set out for this sprint. 

## Daily Scrum
**Daily Scrum** is a critical, daily inspect-and-adapt activity to help the team achieve faster, more flexible flow toward the solution.
- ideally a daily 15 minute meeting for the team to sync, inspect and adapt planning activity to more effeciently do their job.     
- Daily Scrum helps to avoid waiting. If there is an issue blocking work flow, the team shouldn't have to wait more than a day to discuss it. 

## Task Performance - Technical Practices
Dev teams are expected to be technically good at what they do. The proper technical practices of software engineering, continuous integration, automated testing, refactoring, Test-Driven Development for example, need to be integrated and properly implemented. Without doing so, the build up of technical debt will continously increase, if this is not accounted for the team will likely fail to achieve the level of agility needed to deliver long-term, sustainable business value.  

## Communicating 
Team communication is extrememly important in sprint execution. Hence the daily scrum, comms between the team need not be complex, most teams use a Task board, Burndown and or Burnup chart as a central source of information during the sprint. 

### Task Board
On this task board each product backlog item planned to be worked on during the sprint is shown with the set of tasks necessary to get the item done. All tasks initially start off in the “to do” column. Once the team determines that it is appropriate to work on an item, team members start selecting tasks in the “to do” column for the item and move them into the “in progress” column to indicate that work on those tasks has begun. When a task is completed, it is moved to the “completed” column.  
![Task Board](../../images/school/task-board.png)  

### Sprint Burndown chart
Each day during sprint execution the team updates the estimate of how much effort remains for each uncompleted task, typically in table format, can also be graphed. Sprint burndown charts are useful for tracking progress and can also be sued as a leading indicator, to predict when work will be completed.   
The sprint backlog and the sprint burndown charts always use estimated effort remaining. They do not capture actual effort expended. In Scrum there is no specific need to capture the actuals, unless the organization requires it. 

### Sprint Burnup Chart
A sprint burnup chart is an alternative way to visualize progress through a sprint. In sprint burnup charts the work can be represented in either effort-hours (as in the sprint burndown chart) or in story points. Many people prefer to use story points in their burnup charts, because at the end of the sprint the only thing that really matters to the Scrum team is business-valuable work that was completed during the sprint, and that is measured in story points (or ideal days), not task hours.

## Closing: Sprint Execution
**Sprint Execution** is performed opportunistically, leveraging the skills of the team, feedback from work already completed, and the evolving, unpredictable circumstances of the sprint. This doesn’t mean that sprint execution is chaotic, but rather that it is guided by the application of good flow management principles, which determine how much work to do in parallel, which work to start, how to organize that work, who will do the work, and how much effort to invest in the work.