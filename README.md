<h1 align="center">"Suri the Searcher" — A Disaster Relief Robot</h1>

<p align="center">
  <a href="#about">About</a>&nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="#disaster-environment">Disaster Environment</a>&nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="#improved-disaster-recovery">Improved Disaster Recovery</a>&nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="#architecture">Architecture</a>&nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="#internal-representation-of-the-environment">Internal Representation of the Environment</a>
  <br>
  <a href="#reasoning-knowledge-representation-uncertainty-and-intelligence">Reasoning, Knowledge Representation, Uncertainty, and Intelligence</a>&nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="#further-improvements">Further Improvements</a>
  <br>
  <a href="#robot-code-and-project-file">Robot Code and Project File</a>&nbsp;&nbsp;•&nbsp;&nbsp; 
  <a href="#video-recording">Video Recording</a>&nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="#sources">Sources</a>
</p>

<p align="center">
    <img src="https://user-images.githubusercontent.com/110432500/234924254-7f089508-5f69-46ae-8f26-4d711c42ba35.gif" alt="Demo of robot identifying a natural disaster victim" />
</p>


## About
“Suri the Searcher” is an autonomous robot designed to locate victims after a natural disaster. This robot was designed in CoppeliaSim (previously known as V-REP).

## Disaster Environment

One of the dormitories at the Edison Boarding School is on fire! The fire started on the third floor
and has consumed the stairwell on and above the third floor, potentially leaving students on the
third and fourth floors trapped. Additionally, large sections of the third floor’s hallway are on fire,
meaning that students could be trapped inside their rooms.

The fire department has deemed it inadvisable for any firefighters to enter the structure because
a) part of the roof has collapsed, and b) it is a Wednesday afternoon, meaning that all students
should be in their classes (so it is unlikely that any students are in the dormitory).

However, there is still the chance that a student decided to skip class and stay in the dormitory
for any number of reasons; thus, the fire department decides to deploy their human-finding
autonomous robot — named “Suri the Searcher” — to search for anyone trapped inside the
building. Suri is highly resistant to fire and smoke, making her a perfect fit for the job.

In the specific scenario modeled in CoppeliaSim, Suri has entered a bedroom on the third floor
and is searching for any people. There are **two obstacles** for her to navigate around — a **bed**
(the purple object) as well as an **overturned dresser** (the brown object). Suri is able to
successfully navigate around the obstacles, and she ends up finding a person (the
peach-colored cuboid figure) situated between the bed and the north wall.

Upon discovering the person, Suri sends the message “I found a person!” to the firefighters,
who respond appropriately. This message can be seen in the output section on CoppeliaSim
(once Suri encounters the person).

## Improved Disaster Recovery

A burning building can easily lead to loss of human life, especially when firefighters are unable
to search for potential victims. In such a situation, disaster relief robots like Suri are especially
useful and can lead to improved outcomes (i.e. a decrease in the number of casualties). This is
possible because disaster relief robots can often withstand extreme conditions that humans
cannot.

In the scenario described in section A, Suri is able to replace the firefighters for the task of
searching the burning building for victims; this allows the firefighters to avoid unnecessary risks
while also ensuring that any victims are located. Once any victims are located, the firefighters
can quickly and efficiently extract them from the building. In this manner, the firefighters are able
to avoid spending prolonged amounts of time in unsafe conditions, and any victims can still be
rescued. Thus, Suri improves the casualty rate for both firefighters and victims.

In the simulation shown in CoppeliaSim, two obstacles are present in the bedroom — a bed and
an overturned dresser. The dresser is aflame, which would make an attempted rescue by
human firefighters even more dangerous. However, because Suri is extremely fire-resistant, she
is able to experience close contact with burning objects (for a certain amount of time) without
damage. Additionally, Suri’s proximity sensors enable her to detect and avoid any obstacles in
her path; this generally allows Suri to avoid direct contact with these obstacles.

## Architecture

I decided to include three distinct sensors on Suri the Searcher. These can be seen in
CoppeliaSim as a front-facing red sensor, a rear-facing red sensor, and a front-facing yellow
sensor.

The front-facing red sensor is a navigational proximity sensor; this allows Suri to move around
without crashing into obstacles that are in her forward path. When this sensor detects an object,
Suri reverses course in an arc (for a maximum of four seconds) before continuing to move
forward once again.

The rear-facing red sensor is also a navigational proximity sensor; it prevents Suri from backing
up into objects. When this sensor detects an object, Suri adjusts or reverses course (by moving
in a forward direction) in order to avoid a collision with the detected object.

Both the front-facing and rear-facing navigational sensors are highly advantageous for a
multitude of reasons. For example, both navigational sensors decrease the chances that Suri
will make direct contact with potentially-dangerous objects (for example, objects that are on fire
or are chemically hazardous). This decreases Suri’s chances of becoming damaged, which
allows her to better perform her mission. In addition, both navigational sensors decrease the
chances that Suri will make direct contact with — or even run over — an incapacitated victim.
This is beneficial because a collision with a person could cause further injury or distress.

The third and final sensor on Suri’s body is the front-facing yellow sensor; this sensor is a
proximity sensor used for purposes of human detection. This sensor is arguably the most
important of Suri’s sensors, as it enables her to perform the function that she was designed to
fulfill — detecting human victims in a natural disaster situation.

When the human-detection sensor actively detects a person, the sensor changes from yellow to
green (in CoppeliaSim); this is useful for debugging purposes. Additionally, Suri sends a
message whenever a person is detected — “I found a person!” This can also be observed within
CoppeliaSim (in the output section).

Another design feature that I implemented on Suri the Searcher is the bright green color of her
body. This color directly contrasts with the most common colors involved in a fire (red and orange); as such, this feature makes Suri more easily visible to both victims and firefighters. This is useful for many reasons — for example, this makes Suri less of a tripping hazard, it
makes Suri much easier to locate in case something goes wrong with her location beacon, and
it also makes Suri more easily distinguishable from human victims. Visibility aids (such as bright
colors) are crucial in fire-related situations because the visibility within burning structures is often
relatively low.

## Internal Representation of the Environment

Suri maintains an internal representation of her environment by using her proximity sensors. As
previously discussed, Suri has three of these — a front-facing navigational proximity sensor (the
front-facing red sensor that can be seen in CoppeliaSim), a rear-facing navigational proximity
sensor (the rear-facing red sensor), and a front-facing human-detection proximity sensor
(indicated by the front-facing yellow sensor).

As previously stated, Suri uses the front-facing navigational sensor as well as the rear-facing
navigational sensor to detect objects in front of and behind her. As soon as one of these
sensors detects an object, Suri stops moving and reverses course in order to avoid a collision
with the detected object.

Additionally, Suri is able to identify humans within her environment by using her front-facing
human-detection sensor. When this sensor detects a person, the color of the sensor switches
from yellow to green, indicating that a person has been found. Additionally, when a person is
detected, Suri sends out a message — “I found a person!”

At this time, Suri is unable to store the findings of her sensors in memory — that is, she is
unable to create a “map” of her environment. This means that Suri is unable to retain the
findings of her sensors — she simply moves around until/unless her sensors tell her that there is
an object in the way. This also means that Suri is also unable to determine which parts of her
environment she has already searched.

## Reasoning, Knowledge Representation, Uncertainty, and Intelligence

Suri displays **reasoning** skills by having the capability to make decisions. For example, Suri is
able to decide which direction to move in by using the input from her sensors. Additionally, Suri
is able to decide whether or not an object is human (using her human-detection scanner).

Suri displays **knowledge** by having the ability to collect information about her environment. For
example, Suri can determine if there is an object in front of her or behind her by using her
front-facing and rear-facing navigational sensors. Additionally, Suri can determine whether or
not there are humans in her environment (by using her human-detection sensor).

Suri also possesses the ability to deal with **uncertainty** — this is demonstrated by her ability to
navigate an environment that she previously possessed no knowledge of. Suri is able to do this
because of her navigational sensors, which allow her to learn about the environment
“on-the-fly”. Suri also possesses no prior knowledge regarding the number of people present in
the environment or the whereabouts of any people; however, using her human-detection sensor,
Suri is able to locate victims “on-the-fly” as well.

Suri displays **intelligence** because she is able to act on the knowledge that she accumulates
about her environment. For example, when Suri determines that there is an object in her path,
she acts on that knowledge by stopping and reversing course in order to avoid colliding with the
detected object. Furthermore, when Suri determines that she is looking at a human, she acts on
that knowledge by outputting the message “I found a person!”

## Further Improvements

Reinforced learning refers to a machine learning technique where a computer (or robot, in this
case) learns the best path to take through trial and error. As part of this process, the
computer/robot is given a reward upon doing something favorable, but is given a punishment
upon doing something unfavorable (such as taking a worse path) (Bhatt 2018).

Using reinforced learning would highly accelerate and improve Suri’s learning capabilities, and
these elevated learning capabilities would lead to considerably enhanced searching capabilities.
After being constantly trained using reinforced learning, Suri would be able to quickly determine
the most efficient path for finding victims upon being deployed in a natural disaster situation.
This would likely result in better outcomes — for example, victims would be detected more
quickly on average, resulting in less lives lost and better recovery outcomes for the victims.

Implementing an advanced search algorithm as part of Suri’s design would also improve her
learning capabilities as well as her performance. Instead of blindly searching — which is
essentially what Suri currently does — Suri would be able to methodically examine her
surroundings, thus allowing her to more thoroughly and efficiently search her environment for
victims.

One example of a suitable advanced search algorithm is a grid search. A grid search refers to
searching an area in tight parallel lines, and then searching the same area in a second grouping
of tight parallel lines that perpendicularly intersect the first group of parallel lines (Layton 2021).
This search pattern forms a grid, thus resulting in an extremely thorough search of an area; this
is crucial in Suri’s case, as failing to detect a victim could potentially lead to disastrous
consequences.

## Robot Code and Project File

I have included the child script whose icon sits next to the bubbleRob object (in the directory
within CoppeliaSim); this code file governs Suri the Searcher's behavior. The name of the file is “bubbleRob_child_script.txt”. In the file, I have clearly marked (using comments) which code was written by me and which code came from the course resources; all other code originates from the BubbleRob tutorial.

I have also included the project ZIP file itself; this can be imported into CoppeliaSim in order to view Suri the Searcher performing her duties autonomously at a natural disaster site.

## Video Recording

I recorded a video that describes and demonstrates my disaster recovery robot (Suri the Searcher). This video can be accessed using the following link:

[Suri the Searcher Demonstration](https://www.youtube.com/watch?v=1TGIzCC_Dec)

## Sources

● Bhatt, Shweta. “Reinforcement Learning 101.” Medium, Towards Data Science, 19 Mar.
2018, https://towardsdatascience.com/reinforcement-learning-101-e24b50e1d292.

● Layton, Julia. “How Crime Scene Investigation Works.” HowStuffWorks Science,
HowStuffWorks, 6 Apr. 2021, https://science.howstuffworks.com/csi.htm.
