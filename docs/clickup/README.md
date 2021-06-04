# Clickup

We use Clickup for managing research projects. This tool is similar to Trello, in the sense that it allows for the creation of Kanban-style lists  of cards that can be grouped based on a customizable set of statuses. It does, however, provide many other handy features that would only be available on Trello via Add-ons. In fact, it is so rich in features that one can get easily overwhelmed. In order to mitigate this problem, we try to follow an opinionated set of practices meant for minimizing overhead and allowing for smooth collaboration between team members. 

> [!WARNING] If you find that these practices are not providing any benefit, or are instead making your life more difficult than it should be, feel free to create an issue, and/or submit a PR suggesting alternatives.

# Statuses

### Backlog
Cards High-level requirements or ideas that are not necessarily well defined. New cards can be added to the backlog at any time, but *one must be careful not to interpret this list as a to-do list*. Rather, it is a way to keep track of ideas and help the team prioritize tasks when planning what should be added to the "To do" list.

### To do
Updated once per week, with new cards being created only after a thoughtful discussion based on the backlog and the team's capacity. All new cards added to this status should be well specified, with their expected output clearly defined. In addition, they have to be assigned to specific team meambers. As an example, we could have a task: "Review the state-of-the-art of X", whose outcome could be a summary of the most relevant papers read. Super broad tasks such as "Write paper" should be avoided here, as they make more sense in the backlog.

### In progress
Tasks that are currently being executed by the team members.

### Waiting for review
Tasks that have been completed but have not yet been reviewed. By the end of the week, all tasks in this list are reviewed and moved either marked as complete or moved back to the backlog.

### Blocked
Tasks that have been started but whose execution was blocked due to technical or communication difficulties (e.g., major bug in a library, or waiting for a quote from the supplier) that cannot be controlled by the assignee.

### Complete
Tasks that have been through the review process, and have been approved.

# Task naming

Task descriptions should be in the infinitive, as they represent something that needs to be done. in addition, they should have clear definitions to avoid ambiguities and provide as much information as possible for their completion. If a task description is too lenghty, it is usually because it's not clearly understood, or not very well scoped. If that is not the case, try moving non essential details to the description box within the task modal.

> [!INFO] Note that while useful, these naming conventions are not so important for cards in the backlog.

# Flow

The only allowed flows are:

1. Backlog -> To do -> In progress -> Waiting for review -> Complete
2. Backlog -> To do -> In progress -> Blocked -> Backlog

Tasks should not "jump" from the backlog to the Waiting for Review or Complete list. 

# Estimates

Estimating how long it will take to perform a specific task can be a daunting task, especially when working on something new or when uncertainty is involved. In some situations it may be better to use a different approach. Instead of estimating duration directly, one can assign tasks with a number that represents their complexity as well as the uncertainty involved.

This number, which is commonly referred to as a task's story points are assigned based on:

• The amount of work involved
• The complexity of the required work
• The risk or uncertainty involved
• The estimated duration of the task

> [!INFO] This section is just a guideline. You don't need to use any of these if it doesn't make sense to you or to your project.

For the sake of standardization, the following guidelines should be followed:

(1) Extremely simple tasks that require almost no thinking, meaning you already know what to do and how to do it.

(2) Intermediate between 1 and 3

(3) Tasks that you know how to perform, and do not require much work.

(5) Tasks that you know how to perform, and do require some work.

(8) Tasks that you know how to perform, and require a substantial amount of work.

(13) Tasks that you don't know exactly how to perform/are insecure about, but have an idea of how to start. In other words, tasks you know are doable but that will require some research.

(21) Tasks you have no idea how to start, and that involves extensive testing, thorough validation of the results, or might lead to breaking changes which are difficult to measure. If a task falls into this category, it usually means that it must be further broken down into smaller increments.

As a general advice, tasks should not go to the To Do status if they have (21) story points.

Here are few reasons to use story points (adapted from [here](https://www.atlassian.com/agile/project-management/estimation)):

- Dates don’t account for the non-project related work that inevitably creeps into our days: emails, meetings, and interviews that a team member may be involved in.
- Dates have an emotional attachment to them. Relative estimation removes the emotional attachment.
- One guarantees that they don't waste time on tasks that are not clear enough.
- Each team will estimate work on a slightly different scale, which means their velocity (measured in points) will naturally be different. This, in turn, makes it impossible to play politics using velocity as a weapon.
- Once you agree on the relative effort of each story point value, you can assign points quickly without much debate. 
- Story points reward team members for solving problems based on difficulty, not time spent. This keeps team members focused on shipping value, not spending time.
- Over time one can obtain a good understanding of what's the relationship between the amount of story points that can be burned by the team in a given time interval. This can be used to determine the team's capacity and, therefore, plan the next iterations. In other words, it can help one prioritize and allocate tasks more efficiently.

Unfortunately, story points are often misused. Story points go wrong when they’re used to judge people, assign detailed timelines and resources, and when they’re mistaken for a measure of productivity. Instead, teams should use story points to understand the size of the work and the prioritization of the work. 
