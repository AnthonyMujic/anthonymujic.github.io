---
layout: post
title: Write Better Code, Faster

---


Agile software development has gained significant ground in control systems engineering. It is used extensively in company marketing. Everyone wants to be ‘doing Agile’. It is seen as the opposite of Waterfall development.

<h3>Waterfall Development</h3>
Waterfall development is linear:
1. Requirements
2. Analysis
3. Design
4. Code
5. Test
6. Deploy

When one step is completed, you move onto the next step.
Waterfall has a chance of success in projects where the customer has an extremely clear set of requirements. This is seldom the case. Software is soft and it is expected it can change as the customer alters requirements throughout the project as they gain a better idea of what they actually want the system to do. Each time this happens, in Waterfall, the developer has to cycle back and start the process again. This makes changes later on in the process expensive.

<h3>Agile Development</h3>
Agile development is promoted as the solution to the problems of waterfall. Rather than having a linear process, where it is expensive to deviate from the original plan, Agile proposes short development cycles. Software is developed one feature at a time, checking in with the customer to demonstrate completed features, and prioritise future work. This frequent feedback allows the developers to constantly course correct to allow delivery of software the customer needs and adjust to evolving requirements.

<h3>‘We are doing Agile’</h3>
‘We are doing Agile’ is a slogan used to indicate that a company is using short development cycles to adjust during a project to counter the large costs of change in the Waterfall method. The focus is on project management. It is an incomplete picture of what Agile is and was supposed to be. If you read the Agile Manifesto you will notice it is concerned with values and principles. Shorter delivery cycles are only part of the picture. There is also a concern for individuals, and a desire to produce excellent software which doesn’t necessarily follow from only focusing on altering how projects are delivered.

There are two practices I want to explore in deeper detail in following blog posts that need more prominence in the control systems development world, they are software testing and pair programming. I believe if we start off adopting these two practices control system engineers will write better code, faster and enjoy it more.

<h3>Software Testing</h3>
I am not talking about Factory Acceptance Testing (FAT) or Site Acceptance Testing (SAT) where an engineer typically uses switches or the actual hardware to exercise the PLC. I am referring to Unit Testing, Automated Testing, Test Driven Development and Behaviour Driven Development. These testing methodologies use software simulation to test a section of code. As manual intervention and ticking off a check sheet is not required, the tests execute much faster. The tests become an executable form of documentation. They are by necessity always up to date. Having a comprehensive test suite raises confidence that the code does what it should. It also checks that changes don’t break any existing code. This reduces the anxiety associated with change that many developers feel.

<h3>Pair Programming</h3>
Pair Programming is a development practice where two developers sit in front of one computer. I know it sounds strange, but it's making a big impact in the software development world. Here's why: As one developer codes the other watches and questions the code being produced. Coupled with automated testing, one developer can write a test, then the other can implement a  solution. Two sets of eyes are better than one. Often there will be less bugs in the code, as the bugs are addressed before the code makes it to a formal testing phase, or to production. In general there are less bugs and better code. It also has the side effect of training all team members. Say there are 4 team members on a project. If they work in pairs, and rotate the pairs frequently, all members become familiar with all sections of the code base. There is also a greater sense of team ownership of the code.  

