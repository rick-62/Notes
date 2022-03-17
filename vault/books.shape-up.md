---
id: vGVFAj6ixl6EVbncNPspj
title: Shape Up
desc: ''
updated: 1647506428602
created: 1641973494458
---

https://basecamp.com/shapeup/shape-up.pdf

- key to project work and software development
- Execution is not everything as things can be executed the wrong way, destroying morale etc
- book explores what executing right looks like
- based around a company called _Basecamp_, who have developed this
- Not waterfall, agile or scrum

## Intro
- guide to how product development is done at _Basecamp_
- and a toolbox of techniques to apply to own process
- for anyone within a business

### Pain points
- projects go on and on
- no time to think strategically about a product
- inability to get things done quickly
- information slipping through the cracks.

> Switched from adhoc project lengths to repeating cycles. Took some experimentation to find the optimal length: 6 weeks.

> **Shaping** used to describe the upfront work to set boundaries and reduce risk on projects before they were committed.

### Six-week cycles
- work in six-week cycles
- long enough to get something meaningful build start to finish
- short enough that the deadline looms from the start, so time used wisely
- majority of features can be built within one six-week cycle
- no micromanagement during this six-week cycle

### Shaping
- work is **shaped** before handing it off to a team or individual
- small senior group works in parallel, who define the key elements of a solution
- projects defined at right level of abstraction
- focus less on estimates and more on appetite: How much time do we want to spend? How much is the idea worth?

> This is the task of shaping: narrowing down the 
problem and designing the outline of a solution that fits within the 
constraints of our appetite.

### Making teams responsible
- full responsiblity given to teams/individuals
- when teams more automomous, senior people can spend less time managing
- with less time managing, more time can be spent **shaping up** better projects
- When projects are better shaped, teams have clearer boundaries and work more autonomously

### Targeting risk
- Risk of: 
    - not shipping on time
    - getting stuck
    - getting bogged down with old projects
    - wasting time on unexpected problems
    - not having future capacity
- Reduce risk in the shaping process by solving open questions before comitting project to a time box 
- Don't give project to a team or individual who is still in a rabbit hole or has tangled interdependencies
- Risk reduced by capping to six weeks
- If project runs over it doesn't get an extension. Artificial cap ensures time is not overly invested on a concept which needs rethinking first.


# Shaping

![](/assets/images/2022-01-13-08-14-04.png)

## Principles of shaping
Do so at right level of abstraction: not too vague, not too concrete

1. It's rough
2. The overall solution is solved: open questions/rabbit holes are already resolved
3. It's bounded: indicates what is out of scope

## Who shapes?
- Requires combining interface ideas, with technical possibilities, with business priorities
- Usually need collaboration
- Also requires strategy: why does it matter? what does success look like? what is the cost?

## Two tracks
- Not possible to schedule _shaping_ work
- Have two tracks: one for shaping, one for building (6 week)
- During 6 week cycles teams are building what has already been shaped and shapers are working on future cycles
- Work on the shaping track is kept private until committed to project/product, to give option to put pause or drop work when it's not working

## Steps to shaping
### 1. Set boundaries
- how much time is the raw idea worth
- how to define the problem

First set boundaries on what is being done. It's important not to go into solution mode before ensuring the scope is set, at least in broad terms.

#### Appetite
Sometimes an idea  gets us excited right away, in which case the excitement needs to be tempered. Should check whether this is something really able to invest time in, before committing resource or hours of long meetings.

Other ideas might be boring. We have been asked to do something we don't particularly want to do. 

Appetite split into two groups:
- Small batch, requiring 1/2 staff 1/2 weeks batched together in 6 week cycles
- Large batch, requiring the entire 6 week cycle

All projects which don't fit into 6 weeks are broken down or problem narrowed first.

#### Fixed time, variable scope
- Appetite used to vary the scope of the project or work
- fixed time determined by the 6 week (or couple week constraint)

This _fixed time, variable scope_ principle is applied at each stage of the process, including the shaping process.

- the _appetite_ defines the overarching solution
- the _fixed time box_ pushes the decision as to what is core to the project

#### Narrowing the problem
- Always important to fully understand the problem
- Appetite can tell us how much research into the problem we should do

The boundary is set once the following three have been achieved:
- [ ] raw idea
- [ ] appetite
- [ ] narrow problem definition


### 2. Rough out the elements
- Sketch out solution at high level
- output is idea which solves the problem, but without fine details worked out
- Get from ideas in words to the elements of a software solution
- Move fast and cover lots of ideas

At this stage it is important that the design choices lead to more refined scope and boundary, and not as the intended design. It is also undecided whether the idea is worth committing resource to at this stage and the outcome of this will help to shape that.

#### Move at the right speed
- Either work alone or with experience/trusted partner who can keep pace
- Avoid wrong level of detail: concrete enough to make progress on a solution, without getting dragged down into the details
- Work by hand and explore the pros and cons quickly

Questions to answer:
- [ ] Where in the current system does the new thing fit?
- [ ] How do you get to it?
- [ ] What are key components or interactions?
- [ ] Where does it take you?

#### Breadboarding
Three main components:
1. Places
2. Affordance
3. Connection lines

![](/assets/images/2022-03-15-08-22-25.png)
In this case _Invoice_ and _Set up autopay_ are the places and _Turn on autopay_ is the affordance.

This allows us ot move quickly through ideas and confront problems we may have not originally thought of, with little distraction.

#### Fat marker sketches
The purpose of this is to use a large pen size to create a rough visual design. The large pen size prevents the ability to go into detail on particular aspects of the design.

This ensures not jumping ahead too much but also encourages us to review problems which haven't initially been thought of.

The output of these sketches is a list of elements, which are specific and narrow.


### 3. Address risks & rabbit holes
> A shaped project should be free as holes as possible, but we only have a limited amount of time to shape the project.

- Amend solution accordingly
- Cut things out
- Specify details at certain tricky spots

Well shaped work should look like a thin-tailed probability distribution, with a slight chance it could take an extra week.
![](/assets/images/2022-03-16-08-32-28.png)

With technical unknowns, unsolved design problems and misunderstanding the project can take multiple times this.
![](/assets/images/2022-03-16-08-34-53.png)

> We want to remove the unknowns and tricky problems from the 
project so that our probability is as thin-tailed as possible. That 
means a project with independent, well-understood parts that 
assemble together in known ways.

#### Look for rabbit holes

1. Walk through the solution in slow motion
2. Question the viability of each part of the solution:
    - Does this require new technical work we have never done before?
    - Are we making any assumptions?
    - Are there technical limitations not been considered?
    - Is there a hard decision we need to settle in advance?
    
#### Declare out of bounds & cut back
- Call out anything which is superfluous to original requirements
- Explicitly state things which are out of scope and should not be worked on 
- Cut back on requirements if beyond core components
- Cutting back as much as possible on additional elements directly reduces risk

#### Present to technical experts
- Present some components to a technical expert or third-party
- Test assumptions and identify whether possible
- Ensure get to bottom of whether possible within 6 weeks
- Hunt for showstoppers which may have been overlooked
- Present as an idea on whiteboard, as they may have idea to simplify or approach problem differently
- Could lead to another round of shaping.


### 4. Write the pitch
At this point we’re ready to make the transition from privately 
shaping and getting feedback from an inner-circle to presenting the 
idea at the betting table.


- Formal write up
- Includes:
    - problem
    - constraints
    - solution
    - rabbit holes
    - limitations
- Pitch is considered
- If chosen can form the basis for that piece of work
















