# GA-w03d04-lesson

# Agile Development, MVP, and User Stories

## Objectives
*After this lesson, students will be able to:*

- Explain the basics of Agile methodologies and why it's used
- Describe user stories and how they are different than to-dos
- Understand the concept of MVP
- Practice creating user stories for an example app

## Agile vs. Waterfall

#### Waterfall

_The waterfall model is a sequential design process, used in software development processes, in which progress is seen as flowing steadily downwards (like a waterfall) through the phases of Conception, Initiation, Analysis, Design, Construction, Testing, Production/Implementation and Maintenance._- [Wikipedia](http://en.wikipedia.org/wiki/Waterfall_model)

<p style="text-align:center">
  <img src="https://i.imgur.com/yJMVO91.png">
</p>

Waterfall is a good example of a linear methodology. It has it's own benefits:

- simple,  easy to understand and use.
- easy to manage due to the rigidity of the model – each phase has specific deliverables and a review process
- phases are processed, completed one at a time, and do not overlap
- works well for smaller projects where requirements are very well understood
- inflexible deadlines lead to developer burnout

However, other methodologies have evolved as the need for greater flexibility has arisen.

#### Agile

_Agile software development is a group of software development methods in which requirements and solutions evolve through collaboration between self-organizing, cross-functional teams. It promotes adaptive planning, evolutionary development, early delivery, continuous improvement, and encourages rapid and flexible response to change_- [Wikipedia](http://en.wikipedia.org/wiki/Agile_software_development)

#### The Agile Manifesto

This was a formal "proclamation" of key values and principles for approaching software development that was put together in 2001.  The four key concepts value:

- **Individuals and interactions over processes and tools:** self-organization and motivation are important, as are interactions like co-location and pair programming
- **Working software over comprehensive documentation:** working software is more useful and welcome than just presenting documents to clients in meetings
- **Customer collaboration over contract negotiation:** requirements cannot be fully collected at the beginning of the software development cycle, therefore continuous customer or stakeholder involvement is very important
- **Responding to change over following a plan:** agile methods are focused on quick responses to change and continuous development

The core principles of agile development remain the same:

* Iterative, incremental and evolutionary
* Efficient and face-to-face communication
* Very short feedback loop and adaptation cycle
* Quality focus
* Adaptive vs. predictive
* Iterative vs. waterfall
* Code vs. documentation


#### Agile practices

_Agile development is supported by a bundle of concrete practices suggested by the agile methods, covering areas like requirements, design, modeling, coding, testing, project management, process, quality, etc. Some notable agile practices include_ - Wiki

* **Test-driven development** (TDD) is a software development process that relies on the repetition of a very short development cycle: first the developer writes an (initially failing) automated test case that defines a desired improvement or new function, then produces the minimum amount of code to pass that test, and finally refactors the new code to acceptable standards.

* **Continuous integration** (CI) is the practice of merging all developer working copies with a shared mainline several times a day. It was adopted as part of extreme programming (XP), which did advocate integrating more than once per day, perhaps as many as tens of times per day. The main aim of CI is to prevent integration problems, referred to as "integration hell" in early descriptions of XP. CI isn't universally accepted as an improvement over frequent integration, so it is important to distinguish between the two as there is disagreement about the virtues of each. During WDI we will look at [Travis CI](https://travis-ci.com/) as an example of Continuous Integration.

* **Information radiators** is a generic term for any handwritten, drawn, printed or electronic displays that a team places in a highly visible location to track progress or metrics.  Examples include scrum board, task board, or a burndown chart.

* **Pair programming** (sometimes referred to as peer programming) is an agile software development technique in which two programmers work as a pair together on one workstation. One, the driver, writes code while the other, the observer, pointer or navigator, reviews each line of code as it is typed in. The two programmers switch roles frequently.

* **Refactoring** is the process of restructuring existing computer code – changing the factoring – without changing its external behavior. Refactoring improves nonfunctional attributes of the software.

* **Scrum meetings** are short meetings used to plan, review, and increase accountability and clarity across a team. Examples include sprint planning, daily scrum, sprint review and retrospective, and **STAND UPS**.

* **User personas** are used in user-centered design and marketing. They can be described as fictional characters created to represent the different user types that might use a site, brand, or product in a similar way. Marketers may use personas together with market segmentation, where the qualitative personas are constructed to be representative of specific segments.

* **User story** is a description consisting of one or more sentences in the everyday or business language of the end user or user of a system that captures what a user does or needs to do as part of his or her job function. User stories are used with agile software development methodologies as the basis for defining the functions a business system must provide, and to facilitate requirements management. It captures the 'who', 'what' and 'why' of a requirement in a simple, concise way, often limited in detail by what can be hand-written on a small paper notecard.

* **Velocity tracking** The velocity is calculated by counting the number of units of work completed in a certain interval, the length of which is determined at the start of the project. [Pivotal Tracker](http://www.pivotaltracker.com/)

* **Wireframes** A website wireframe, also known as a **page schematic** or **screen blueprint**, is a visual guide that represents the **skeletal framework** of a **website**.

## User personas 

A user persona is a fictional representation of your ideal customer. 

Example from Pinterest: 

![](https://i.pinimg.com/736x/46/e5/b5/46e5b5b76da8d32c224aa5219ff5d8a7--customer-experience-user-experience.jpg)

The idea is to have a well fleshed out sense of what your users are like before you build your project

## User Stories

Once you have constructed User Personas, to better understand your Users, you must construct User stories to identify each pathway they may want to take through your app or website.

User stories exist in different formats, but this is one that works quite well:

_As a **[role]**, I want to **[goal]** so I can **[benefit/purpose]**_

Here's an example of user stories for TicTacToe:

* As a player 1, I want to be able to place an X in a square
* As a player 2, I want to be able to place an O in a square 
* As a player, I want to know if I have won so I can brag to all of my friends

More concrete example for 'Keep', googles synched notes app
* As an instructor, I want to jot down notes so I can save them for later
* As an instructor, I want my notes to synch accross my decives, so I can see them on my phone


#### Why do we do this?

When we practice **TDD** we will be able to write integration (user acceptance) tests that will match our user stories. This is really cool. If done correctly, our tests will automatically checks that all our functionalities (pathways) are available and working. Check out the example below showing integration specs written in Ruby using a tool called capybara. It reads like plain English:

```ruby
describe "the sign in process", :type => feature do
  before :each do
    User.make(:email => 'user@example.com', :password => 'password')
  end

  it "signs me in" do
    visit '/sessions/new'
    within("#session") do
      fill_in 'Email', :with => 'user@example'
      fill_in 'Password', :with => 'password'
    end
    click_button 'Sign in'
    expect(page).to have_content 'Success'
  end
end
```
&#x1F535; **Activity**
```
- Create 2 user personas for people who might play your game (this is a little bit overkill for this project, but it's good practice)
- Create four user stories that apply to your game
- 10 min
```  

## MVP - minimum viable product

An MVP is the simplest version of an application that still serves the main purpose of the application for users. You should *always* have a clear idea of what your MVP is for any software project, and your MVP should be the first thing you build. A lot of people feel that once that is created, you should ship it to customers strait away, because you will start getting feedback from customers that will inform how and if you build your other desired features. 

#### Example - Facebook

The MVP of Facebook would have included the ability to create a profile, add text content to one's profile, and "friend" others. 

Notice, the feed isn't even a part of it. The purpose of facebook is to have a place for people to share their lives with their friends. These three features (which are substantial) fulfill that purpose. 

Live chat, serving adds, checking in, creating events, etc. are all *well* outside the scope of the MVP

#### Example - Tic Tac Toe

The MVP for tic tac toe would be the ability to place x's and o's, and calculate a winner. 

Notice, playing multiple rounds, keeping score, the ability to name players, the ability to choose a sprite, etc. are all *not* in the MVP for tic tac toe. 


&#x1F535; **Activity**
```
- Write a first draft MVP in the form of user stories. What things do a user *have* to be able to do to get the basic functionality of your game?
- 10 min
```  



&#x1F535; **Activity**
```
- Create a project proposal! It should have:
  - A description of your product
  - Your two User Personas from the earlier activity
  - All of the user stories that make up your MVP
  - All of the user stories that make up your stretch goals
  - A wireframe for your project
- Open ended
```  

## Further Reading

- [Agile web development overview](https://www.keycdn.com/blog/agile-web-development/)
- [From Personas to User Stories](https://www.romanpichler.com/blog/personas-epics-user-stories/)
- [Agile Methodologies.org](http://agilemethodology.org/)
- [Real world examples of MVPs](https://crew.co/how-to-build-an-online-business/mvp-minimum-viable-product-example/)
