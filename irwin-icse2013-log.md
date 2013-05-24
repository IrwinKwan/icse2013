Irwin's ICSE 2013 Log
=====================

__2013-05-21	21:44:16__	Initial revision! Starting a git repository just for ICSE 2013 notes. Later, I'll go through these and see if I can transfer them to my blog or another location that's a little more permanent and visible.

__2013-05-22	16:21:20__	Comparative Causality: Explaining the Differences between Executions
William N. Sumner and Xiangyu Zhang (Purdue University, USA). This paper might have some applications to compare different executions between two different Gidget traces to give a sense of what control flow paths different programs could look like.

__2013-05-22	16:24:21__	Explanations are shorter for this approach.

__2013-05-22	16:28:44__	They go back to the last known good execution, find the common point right before the bug, and then compare the executions.

__2013-05-22	16:30:26__	This technique depends on the correct run - which we will have in a Gidget game. (roots in delta debugging). Can be used perhaps as a way to explain why your current bug is different from the correct game to the end user.

__2013-05-22	17:02:33__	Automatic Testing of Sequential and Concurrent Substitutability. Michael Pradel and Thomas R. Gross: mentioned in the questions that overriding methods might actually be a problem because they cause problems that are identified with this method.

__2013-05-22	17:04:52__	Felienne Hermans. Clone Detection in Spreadsheets. 2 slides for motivation - punchy style. One bullet each, with full-sized pictures. Mapping from the bad things to the real things in the spreadsheet domain.

Motivates it with newspaper articles as well.

Overview of dataflow diagrams in spreadsheets. (ICSE11. This is probably worth looking at for Gidget control flow diagrams).

__2013-05-22	17:08:37__	Links the "dependency" diagram to show clones instead of dependencies. What clones do we look for?

__2013-05-22	17:09:55__	Look specifically for data clones: areas of spreadsheet where the same values appear but the results are the same.

__2013-05-22	17:10:58__	"Fingerprint algorithms" from clone detection in source code. Make a lookup table, remove single values, find and match clusters.

__2013-05-22	17:11:26__	Evaluated on EUSES and found 86 spreadsheets (5% of the corpus) with clones - in source code we have 5-30%). Precision 82%.

__2013-05-22	17:15:01__	Also did a case study on the South-Dutch foodbank. They run the entire operation with spreadsheets. visualization really helped. 61 near misses, of which 25 were actual errors. **Visualizations of bugs/clones/potential problems are important.**

__2013-05-22	17:19:20__	From the case study: the foodbank started small, they got bigger, no one wants to touch the spreadsheets anymore. Work on impact calculations to understand where things might fall over as a result of change. Two vacancies for postdoc/Ph.D student.

Keynote: Movie making as Software Engineering, Tony DeRose, Pixar.
=======

These are notes from my notebook I made during the talk.

* "Movie making"
## Act 1: STORYMAKING

* Verbal pitch
* Story boards
	* iterate, story reel. (drawings & demo voices)
	* really get things tight enough so that you're not bored.
* concept art after story is created
	* "Art of Pixar"
	* "Science of Pixar" 2015
* personality poses
* 3D art in sculpts of clay
* Environments, concept art.
* Rigging: add controls for the animator to change character's movements
	* some controls are coarse: "degree of elbow"
	* some controls are fine: "degree to which the jaw is open"
	* some are very fine: "amount the eyebrow is raised"
	* 300 controls in the face - compared to 30 nerves in the human face physiologically!
* Animator: times the execution of animations, of these controls
	* they are actors in the human space - human in the loop! "I wouldn't want to get rid of the animator".
	* System has no idea of volume consistency for the character, of gravity
* Animation "dailies": daily meeting w/ director and animators to show off what has been done and get feedback
* Shading: add lighting to models.
	* every single object, need to place them all, add details. "There's a story behind this pot".
* Lighting: lighting artists. as schedules slip, the lighting department takes the brunt of it.

* "It's not a pipeline at all, lots of feedback loops".

* (complex diagram that contains nodes for layout department, animation, lighting and redndering, mastering, etc.)
	
---

* Progression Reel

	* Takes about 4 years to create a movie. 2 years story/art/design, 2 years implementation/editing

---

## Making Software Like Movies

* Tools: photoshop, maya, sketchup (google), final cut pro/premiere
* MenV: legacy system of Pixar from 1984, about 2m lines of code
	* No coherent architecture
	* 8 different langs
	* different UX paradigms
	* Steve Jobs really wanted to see architecture
	
* Reqs include "Coherent UX" (later we also learn, "Flexibility")

* Attempt 1: they went into a hole, did design, but failed. Attempt 2 also failed.

* Potential problem: we approached it as an engineering problem rather than as a story. To fix this: adapt process from moving-making to engineering.

	* Appointed: a "director". "Producer", "Supervising technical director". Used terms that everyone understood from the movie making business.
	* Mocked up user workflows as scripts (literally, movie scripts)
	* storyboarded (4x8)
		* had a story team
		* user workflows
	* Story Reels: a low fidelity movie illustrating a feature: "Appropriate Fidelity, Appropriate Attention". --> Paper prototyping principles!
	* examples: using sketch frames, not labelling everything in the edit menu, showing only things that are relevant to the current workflow example.
	
* "Real users really resonate with the movies".
	* Show real people doing real problems
	* Focus on workflow, not user interface
	* Iterate
	
* Tony said: "Lessons to us not coming from the SE world."
* Used Story boards for the object model.
* Walkthrough. Director does a 1 on 1 or 2 on 1 to review a process (that is, a workflow story)
* "Engineering Weeklies"
	* when something is ready to show
	* sharing early
	
* What didn't work?
	* Movies have 2 stages: story/art/design and implementation which relies on production tracking, quotas, accurate bids, schedules.
	* This didn't work.
	* Instead, they used agile.
	
## Act 3: Delivery, "Giving Birth"

* Things were bloody. High learning curve. (Later we learn that there was an edict from the top).

* Used physical simulators (cloth, hair)

## Question Period.

* Regarding backwards compatibility: Steve Jobs: "We're not backwards-compatible".
	* working off the digital backlog.
* Book: "Computers as Theatre".
* They stay abreast of physical simulations work, but they aren't bound to reality: "We have to be faithful to the director".
* Most of the sound work is outsourced (sound design, compositions)
* They try to isolate some users (ex: animators) from the technical info. Others are more technical artists and know plugin API, scripts
* These teams in Attempt #2 were domain-knowledgable, so it was bad engineering approach (not lack of knowledge) that was the problem

* Person-power: "We brought in more software engineers only after a lot of the initial design".

* Can we use these tools? "Photoshop and Final Cut."

* Can we use this approach to writing papers? Story-writing tops: try making the movie of the paper before writing the paper.

* The transition from legacy system to new system: was an Edict from the top. Social engineering needed. Very stressful. To help, they embedded engineers with users to sit with the production team.

Technical Sessions
========


__2013-05-23	10:34:45__	Pair Programming Driver/Observer: the oppressive regime. Understand _how_ pairs program. They built a metal model to identify role-related phenomena. 

__2013-05-23	10:35:48__	Role has facets: mission/intention/responsibility

__2013-05-23	10:39:15__	The driver/observer model may not help: adding roles/facets will help understand and guide pair programming practices. Need to use qualitative methods rather than quantitative methods.

__2013-05-23	10:44:53__	Crowdsourcing Software Development Tasks.

__2013-05-23	10:49:04__	COCOMO estimation for costs - overestimates the price for crowdsourced development. Inappropriate prices lead to task starvation (no one wants to do the tasks).

__2013-05-23	10:50:13__	Used web crawling (on what?) and identified 16 price drivers. I can't really see the table from where I am.  (1. ??? 2. quality of input, 3. input complexity, 4. Previous phase decision.) Linear regression model, and 8 other machine learning and statistical models. answer 3 RQs: baseline: naive and COCOMO.

__2013-05-23	10:52:29__	Data from TopCoder, 2003 - 2012. 490 top SW projects, 5910 sw dev tasks.

__2013-05-23	10:53:21__	Top factors (significance analysis): 

__2013-05-23	11:03:28__	Crowdsourcing unit tests

__2013-05-23	11:03:41__	Developers rely highly on existing test cases to write new test cases

__2013-05-23	11:03:56__	Interviewed github developers. "Drive-by commit" on github projects.

Process
=======

Papers were Prem's papers, Dana's paper

## Process Metrics/Code Metrics

Irwin

## Domain Knowledge

woo hoo!

## Dual Ecological Measures

David

Requirements Engineering
======

## Nan's IFT talk


## LDA on Comments and Requirements



Empirical Studies (Analysis)
=================

## [Why Don't Software Developers Use Static Analysis Tools to Find Bugs? Brittany Johnson, Yoonki Song, Emerson Murphy-Hill, and Robert Bowdidge](http://2013.icse-conferences.org/content/why-dont-software-developers-use-static-analysis-tools-find-bugs)

May be of interest to Faezeh regarding how to design features in a development environment.

- Used interview question/short response, gave them a computer and asked them to run FindBugs, and used Participatory Design.
- Coded to "tool output", "user input", "teamwork", "understandability", "workflow", and "tool design".
- Found issues with every aspect, by her assessment the biggest problems were understandability 1st and lack of quick fixes 2nd. 
- Some developers didn't like the output
- **My takeaway:** Developers don't like lists, developers want instant feedback, developers want ways to audit or vet bugs, and developers want to monitor/control automated fixes. Evidence that developers want to be kept "in the loop".

## [Exploring the Impact of Inter-smell Relations on Software Maintainability: An Empirical Study
Aiko Yamashita and Leon Moonen](http://2013.icse-conferences.org/content/exploring-impact-inter-smell-relations-software-maintainability-empirical-study)

Something to look at for me to identify potential relationships between code modules in a case study.

- Big case study at Simula systems
- Apparently everything can end up as a "Wide Interface". 

- Only 46% of observed problems related to code (part of these covered by detectable code smells)
- Not enough data to analyze severity intersmell vs. direct severity
- **My takeaway:** Dependenecies are a problem! Need MORE awareness among relationships in code.


## [An Empirical Study on the Developers' Perception of Software Coupling
Gabriele Bavota, Bogdan Dit, Rocco Oliveto, Massimiliano Di Penta, Denys Poshyvanyk, and Andrea De Lucia](http://2013.icse-conferences.org/content/technical-research)

David may want to read this. 

- Structural (static analysis), Dynamic (execution), Semantic (word similarity), Logical (files-changed-together). 
- How does this align with perceptions of developers on coupling? 76 developers. What kind of coupling aligns best with developer's perceptions? Choose ArgoUML, jEdit and JHotDraw.
- Method: data mining, manually executed functionality to attain code coverage. (66%, but also a lot of abstract and interfaces)
- Asked the original developers about coupling. 6, 3, 3 developers. Also contacted academics to get 64 responses. Original developers were asked to evaluate only their own system but externals examined all systems.
- Semantic, Structural align well with developer's perceptions.
	- ActionVisibilityPrivate/ActionVisibilityProtected. Even though the two classes aren't clearly structural dependent, developers found that they were highly related.
- **My Takeaway:** This work highlights the benefits and usefulness of SEMANTICS (words) for identifying relatedness between classes.
- Questions related to: "The common definition of coupling is pretty highly related to words... so you're asking them to confirm a definition."