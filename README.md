# PLC Project: Backup Electricity Generator

## Objective
This project uses a PLC unit to control the power of a building, by using 2 generators in the case of a power outage. 

![1](https://user-images.githubusercontent.com/86275885/122983982-eb290a80-d372-11eb-94a7-e7b6a19c83df.jpg)



## Design Control Components
The design consists of 3 discrete inputs:
- I1: Power Grid 
- I2: G1working (available)
- I3: G2 working (available)

The design consists of 3 discrete outputs:
- Q1: Building Electricity indicator
- Q2: Indicates when G1 is functioning
- Q3: Indicates when G2 is functioning

Other technical components: 
- M1: relay to save G1 status if ON or OFF
- M2: relay to save G2 status if ON or OFF
- T1: Timer for G1 to count first 10s after electricity outage
- T2: Timer for G1 to count second 10s after electricity regain
- T3: Timer for G2 to count first 10s after electricity outage
- T4: Timer for G2 to count second 10s after electricity regain

## Design Description
There are 3 switches available, one to control grid electricity status, and 2 others to control generator availability status (working or not working as in broken). Once there is no grid electricity, if there is at least 1 generator available, the corresponding generator (priority given to G1) will turn ON providing power after 10 seconds neglecting the status of grid electricity provided by the government. After these 10 seconds expire, the PLC program will check whether or not grid electricity power is provided and if yes, the generator will stay ON for another 10 seconds before switching OFF, elsewise it will keep powering the building. When generator 1 is broken, the priority will now become G2 which will turn ON after 10 seconds and then the program will check if G1 is back online, if G1 is indeed back and fixed, G1 will wait 10 seconds before switching ON and G2 will be OFF therefore making G1 provide power for the building. 

## Conclusion
This project implemented a state machine which taught us how to create several states and design a mechanism to link all of them. It allowed us to dynamically draw a pattern between the different situations and how to control them efficiently. 
