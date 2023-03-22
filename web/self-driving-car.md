# Perception camera

# Perception LIDAR

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


