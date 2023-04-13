# Perception camera
Describe the role of camera in the perception stack of a self driving car <TBD>
+ camera model
+ cheapest sensor
+ object detection
+ object tracking
+ Traffic sign recognition
+ Visual SLAM
+ Visual Odometry
+ Semantic segmentation
+ Structure From Motion
  

# Perception LIDAR
role of LIDAR in perception tasks
* Describe the Role of Lidar in the peception tasks
* and the models used
+ Machine learning approaches
  
# Sensor Fusion
The Sensor Fusion Algorithms You Should Know About
To improve your understanding of exactly what a sensor fusion algorithm is, let’s touch on some that are widely used to give you a concrete sense of use cases.

## Algorithms Based on the Central Limit Theorem
Perhaps a more user-friendly name for the **central limit theorem (CLT)** is the law of large numbers: It states that as the sample size of whatever we are measuring increases, the average value of those samples will tend towards a normal distribution (a bell curve). A common example is rolling a die — the more rolls we measure, the closer the average value will be to 3.5, or the “true” average.

How does this relate to sensor fusion? Say we have two sensors, an ultrasonic sensor and an infrared sensor. The more samples we take of their readings, the more closely the distribution of the sample averages will resemble a bell curve and thus approach the set’s true average value.  The closer we approach an accurate average value, the less noise will factor into sensor fusion algorithms.

## Kalman Filter
A Kalman filter is an algorithm that takes data inputs from multiple sources and estimates unknown values, despite a potentially high level of signal noise. Often used in navigation and control technology, Kalman filters have the advantage of being able to predict unknown values more accurately than individual predictions using single methods of measurement.

Sound familiar? This is exactly what we went over in our car example. Because Kalman-filter algorithms are the most widely used application of sensor fusion and provide the foundation for understanding the concept itself, sensor fusion is often synonymous with Kalman filtering. One of the most common uses for Kalman filters is in navigation and positioning technology. Because Kalman filtering is recursive, we only need to know the car’s last known position and speed to be able to predict its current and future state.

## Algorithms Based on **Bayesian Networks**
Bayes’ rule, which deals with probability, is the basis of the update equation described earlier that combines the motion and measurement models. Bayesian networks, also based on Bayes’ rule, predict the likelihood that any one of several hypotheses is the contributing factor in a given event.  some well-known Bayesian algorithms.
+ K2
+ hill climbing
+ iterative hill climbing
+ simulated annealing

## Convolutional Neural Networks
Convolutional neural-network-based methods can simultaneously process many channels of sensor data. From this fusion of such data, they produce classification results based on image recognition. For example, a robot that uses sensory data to tell faces or traffic signs apart relies on convolutional neural-network-based algorithms.

## Summary
In this article, we talked about sensor fusion algorithms, why they’re useful, and what a few well-known ones look like. We also touched on the equations behind these algorithms, which can be fairly complicated.

# Practice

+ Sense
+ understand
+ Plan 
+ Act

### Real world problems

+ **harder**
+ code must run **faster**
+ safety guarantees must be **stronger**

### Car must be able to

+ Read data from sensors
+ Pre- process data
+ **Detect Objects**
+ Track objects
+ Localize itself
+ Estimate ego-motion
+ Plan path
+ Plan motion
+ Follow the path

## Object detection

+ Challenges
  + Detect non learnable objects (eg flying birds)
  + Small objects lying on the road
  + In Sensor redundancy, how to resolve conflicting information
  + very far objects
  + Deep learning , very hard to predict when they fail
  + Fallback classical geometric approach is needed
  + halloween kind of unusual environment

#### Which sensors for perception
+ no single sensor is enough
  + Cameras hard to work in the dark and dont provide metric information
  + LIDAR does not work well when it is wet, snowy or when objects do not reflect light, detect phantom objects
  + Radar has low resolution but measures speed and sees though fog and rain
  
### Typical Perception setup

+ camera object detection and classification
+  Geometric 3d clustering, object detection and tracking potentially sing RADAR
+ Top down object detection on OGM
+ Deep learning OD on 3D point clouds - latest
+ Free space detection with cameras from 3D
  

## Localization
Maps have different layers  

1. a **3D Layer** created by Lidars
2. **Sematic layer** 
3. Layer with **Dynamic** changes

### 3D map Layer

+ Localization in **given 3D map** is largely solved


### Semantic map layer

+ Road lines, driving directions
+ Traffic lights
+ Speed limits
+ All these are aligned to the 3D map
+ Semantic map creation is labor intensive
+ Car is localized in 3D map. hence gives a good guess of the location of traffic lights

### what to do when world changes

+ dealing with changes is hard
+ Implement change detection algos that allow the whole fleet to update the map

### What if we cant align to a 3d Map

+ Align with HD feature maps
+ HD map is similar to semantic map bit with additional features
+ localization in HD feature maps is still not solved
  
## Tracking Objects

+ use extended **Kalman filter** or **Particle filter**
+ prediction is non trivial and still largely unsolved
+ objects can split and merge as a result of detection errors
+ objects can be hidden behind other objects
+ objects can change direction when unobserved

+ Easy to predict expected behavior
+ very complex to predict unexpected behavior


## Code must run Faster

+ Worst case run time must be guaranteed
+ If a component takes longer than expected it might be killed which imposes additional constraints on system design


## Are we ready to hit the roads

### Safety is extremely important

+ car must be safe for occupants and for the surrounding people
+ safety deals with situations like 
  + Tire blew up
  + sensor is unresponsive
  + sensor sends bogus data
  + car software fails
  + how to deal with random systematic failures
  + Fallback mechanism needed
  
### How  do we know the system is safe?

+ Design system to be safe from the start
+ Audit the system to ensure system matches the design
+ The design is guided by H.A.R.A
+ **H**azard **A**nalysis and **R**isk **A**ssesment

### ISO26262 functional safety standard
+ international standard

* Risk and safety
  * Safety = absence of unreasonable risk
  * Risk = F(f,c,S) 
  * S -severity
  * C - controllability
  * f - frequency of occurrence

* Frequency of occurrence
  * **Exposure** - how often is car in the situation where a safety hazard due to failure can occur
  * **Failure** the probability of a particular piece of hardware/software to fail
  * Every item is assigned to **ASIL** level that mitigates such risk
  * **ASIL** level trickles down to individual components which defines gow reliable they must be

#### **ASIL:Automotive Safety Integrity Level**
+ ASIL is a function of 
  + Severity **S** : from **S0** to **S3**
  + Exposure **E** : from **E0** to **E4**
  + Controllability **C** : from **C0** to **C3**
+ Levels **QM, A, B, C, D**
+ Levels form A to D grow in safety consideration


## V model

Requirement Analysis <-> System Testing

High level design <-> Integration testing

Low-level Design <-> Unit Testing

Coding  
+ MISRA
+ AUTOSAR
+ Static code Analysis
+ Continuous Integration

## Other standards
* UL460
* ISO/DIS 23150


## Certifications 

* Safe software can be formally certified


