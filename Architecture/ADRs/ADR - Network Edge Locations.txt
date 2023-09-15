#Network Edge Locations

##Status - Accepted

##Context - 
RoadWarrior is a global service. Their customers will also travel to world wide locations and need prompt access to their data from any location. Their travel data will be served from 3 redundant location. Since customers may access the data from any location, it needs to be quickly available to them with fast response times irrespective of their location. < 800ms as specified in requirements

One way to solve this is to cache the next 7 to 14 days of trip information at edge locations (also goes by content delivery network) around the world. Based on the users current location and their predicted location if they have upcoming trips, their data can be pushed to the nearest locations. The cache can have a refresh rate ranging from a few hours upto a day to make sure latest data is available.


##Decision
It has been decided to rollout more edge locations based on growth in user numbers and their geographic locations. This is imperative given the stringent response time requirements of < 800ms.


##Consequences
The system will need to build additionla capabilities to track customer location. Additionally services will need to be built to keep data at edge locations up to date.
