
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
- agile uses 2 week sprints which are not long enough and too much planning overhead
- 2 week cool-down follows, where project teams are free to work on what they want.

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

#### Ingredients
1. **Problem:** the raw idea
2. **Appetite:** how much time we want to spend & constraints
3. **Solution:** presentation of core elements
4. **Rabbit holes:** call out potential areas of solution to avoid problems
5. **No-gos:** Anything specifically excluded (what the solution won't be)

#### Possible delivery
1. Post proposal so individuals on the betting table can view the proposal
2. Give time for stakeholders to comment on the pitch
3. Amend and present the pitch formally


# Betting

## Bets, not backlogs

### No Backlogs
Don't have backlogs, as these can stack up and we know in some cases we will never have time for. Reduce time having to look at the same thing over and over again, and want to focus on projects right now **- could use time sector system here**.

### A few potential bets
- Prior to 6-week cycle a _betting meeting_ is held where stakeholders decided what to do at the next cycle
- They look at pitches from the last 6 weeks, only 
- There are no backlogs to review or giant list of ideas
- They should only be reviewing shaped proposals which are potential bets
- If proposal rejected, no matter the reason, this DOES NOT get added to a backlog
- Proposals can be lobbied again 6 weeks later.

### Decentralised lists
Everyone (including separate teams) can individually track items/projects, without the need for a central backlog or list. This can include pitches, bugs, requests, or anything they want to pursue independently. None of these should form an input into the better process.

This approach spreads out responsibility of tracking what to do next and regular infrequent 121s between teams can help cross-pollinate ideas for future proposals. This allows different departments  to advocate for what they think is important. 

The overall advantage is everything reviewed is always relevant, timely and of the moment.

### Important ideas come back
- It's easy to overvalue ideas, but in truth, they are cheap
- Really important ideas come back
- Hearing something multiple times will bring it to the surface as important
- This includes bugs or other software issues

## The betting table
_Which projects to schedule_

### Resource & constraints
- must be able to determine who is available and for how long
- **When people are available at different times due to overlapping projects, project planning turns into a frustrating game of Calendar Tetris**
- Working in cycles drastically reduces this problem
- Must also consider the types of project and who is involved
- Also needs to include QA within cycle
- Up to allocated team to decide how to juggle time.

### The betting table
- Meeting held during cool-down, to decide what to work on during next cycle
- Potential bets are either new from past 6 weeks, or someone specifically revived
- No backlog; just a few good options
- Betting table small e.g. CEO, senior programming and product strategist
- Everyone seen and had chance to review proposals beforehand
- 1-2 hours at most considering the proposals
- Output of the call is cycle plan, with no two step process to get approval
- Decisions are based on:
    - who's available
    - business priorities
    - kind of work been on with lately
- Once complete the output cannot be changed and is final
- Buy in from the top is essential to making this process work

### Meaning of a bet
> Bets have a payout

- Output should be something meaningful, with the pitch defining the payout
- Bets are commitments exclusively to work on that thing with no interruptions
- Most that can be lost is 6 weeks time

### Uninterrupted time
> It’s not really a bet if we say we’re dedicating six weeks but then allow a team to get pulled away to work on something else

- Bet must be honoured
- Team must **not** be interrupted or pulled away on other things
- if something comes up, the maximum wait time is 6 weeks - team is not disrupted!
- If that thing is important it can be bet on for the next cycle
- Worst case it's a real crisis, but **true** crisis are rare.

#### Resonates very strongly
> When people ask for “just a few hours” or “just one day,” don’t be fooled. Momentum and progress are second-order things, like growth or acceleration. You can’t describe them with one point. You need an uninterrupted curve of points. When you pull someone away for one day to fix a bug or help a different team, you don’t just lose a day. You lose the momentum they built up and the time it will take to gain it back. **Losing the wrong hour can kill a day. Losing a day can kill a week**

### Circuit breaker
- If the team does not finish the work within the 6 weeks period, there is no extension
- Removes risk of runaway project
- The original bet was on 6 weeks and no more
- Helps to reframe proposals better in the future
- Motivates teams to take more ownership over projects

### Bugs?
Bugs are no different to other pieces of work and rarely present a crisis.

Either,
1. Optionally fix a bug during 2 week cool-down period
2. Propose large fixes at better table for 6 week sprint
3. Have a bug smashing week once a year

### Keeping the slate clean
- Must have clean slate with each cycle, with no scraps of old work
- It is crucial to maximise options in the future
- Road map remains in our heads
- No downside to keeping options open, and massive upside to being able to act on the unexpected
- This includes projects which need to span multiple cycles.

## Place your bets
There are two distinct types of bet:
1. Improvement to an existing product
2. Building a new product

### Existing products
- Following standard Shape Up process
- Expect finished and shipped by end of 6-week cycle
- analogous to crafting a piece of furniture for a house already built

### New products
- analogous to build the house around the furniture
- Can be split into 3 main phases of work:
    1. R&D mode
    2. Production mode
    3. Clean-up mode

#### R&D mode
> We have to learn what we want by building it

Adjust for this in 3 ways:
1. Instead of betting on well-shaped pitch, bet on time of clarifying key pieces of new idea
2. Senior staff make up the design team - cannot delegate if don't know what want yourself & architectural designs will determine what's possible and large decisions may be required in real-time
3. There is nothing to deliver at the end of the 6-week cycle, except possibly foundations to help shape future work

#### Production mode
Once R&D cycles have sufficiently refined architecture and those decisions are settled, the structure is in place to bring in other teams to contribute.

In production mode:
1. Shaping is deliberate again
2. Any team can be given the work
3. Completing features is the goal

At this point, the product is not launched, but is getting refined.

#### Clean-up mode
> In final phases before launching new product all structure goes out of window

In this stage all remaining bits need to be completed and finalised:
1. There is no shaping, with leadership at the helm cutting away distractions and bringing focus to what's important
2. There aren't clear team boundaries
3. Work is released in small chunks

Clean-up should not last longer than two cycles.

### Questions to ask at the betting table

1. Does the problem matter?
2. Is the appetite right?
3. Is the solution attractive?
4. Is it the right time?
5. Are the right people available?

### Kick-off message
Once complete the projects being worked on in the next cycle are communicated to everyone.

# Building

## Hand over responsibility
> The way to really figure out what needs to be done is to start doing real work.

- Hand over the project and not tasks
- Full responsibility passed over to the team or individual carrying out the work
- First few days the teams get acquainted with what has been asked
- Team starts off with some imagined tasks, and begin exploring the problem
- New tasks are created as the developers try to figure things out
- QA/testing needs to be done within the cycle
- Communication usually handled after deployment of project/work

## Get one piece done


































