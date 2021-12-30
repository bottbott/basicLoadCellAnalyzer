# basicLoadCellAnalyzer

I've been excited by the visualizations of real world force data that is being used by climbers and coaches to help
understand the power and strength produced by climbers and apply the data gathered to tune training regimes. 

This project relies heavily on the existing design by Markus Rampp for his SlackCellv2. https://gitlab.com/Grommi/slackcellv2

There are several options available on the market. 
GSTRENGTH By EXSURGO TECHNOLOGIES. https://exsurgo.tech/products/gstrength?variant=36100656332967 - $649 USD
Progressor by tindez - https://tindeq.com/product/progressor/ - 140 USD
Force Plate by Entralpi - https://entralpi.com/ - $199 CAD

Rather than buy a product, I want to try to create one so that I can practice and develop my own skills. 

## Materials

There are several components that will be used for this project. 

- Microcontroller
- Load cell sensor
    - https://www.sparkfun.com/products/13879
- Load cell amplifier
- Eye bolts

# Microcontroller
There are so many different options for microcontroller that it's hard to know which one is sufficient for this project.

We want a controller that:
- has wifi (will be easier to work with than bluetooth)
- has sufficient sampling rate for the incoming sensor data

# Load cell sensor
Load cells come in many different formats. 

- must be able to accept an eyebolt so that it can be pulled in opposite directions. 
- must be able to handle a sufficient force/weight. 

# Local cell amplifier
Not sure what distinguishes these but there seems to be some differences that need to be researched. The circuits I've looked at so far have a different sample rates and they also have the ability to accept an external clock signal that can be used to set the sampling rate. I have seen a 10 SPS and 80 SPS setting for the same circuit, and that should be sufficient for now and if a higher sampling rate is desired then it can be configured later on through the external clock inputs.


# Eye bolts
Should be similiar metals so that the is no galvanic corrosion between them, and to ensure they fit together well with the sensor.

# Microcontroller Programming 
For the microcontroller I was thinking that I would install Node.js and then have a web server running on it that can serve a webpage. There should be an application that can collect the output from the load cell and then display it in a way that is beneficial to the user. 

- See the data.
- Record the data.

The frontend can possibly just be built in vanilla JS, but maybe this would be a fun opportunity to play with a framework? The backend would need to be some sort of database. Could be a NoSQL solution, or maybe something on the microcontroller and have the data stay there? That seems like a bad idea because it becomes a limiting factor as storage space goes down and it also isn't accessible without being near the physical device. Probably should think about how to decouple the application from the microcontroller so that it is only minimally coupled to perform the measurements. 

# Frontend
HTML
CSS
Javascript

OR 

Some framework for fun, and which might tie together frontend/backend as well. 


# Backend
Might need a couple of endpoints to do things?
/save


# Storage
Need to house the data somewhere. Keeping it on the microcontroller is where we'll start. Eventually, will need to sync the changes to an external storage somewhere. It should make it easier to start so that the application doesn't have to fetch data or save data to something off-device. I guess a recording session is cached locally, and then there could be a save function that for now writes it to the device and then later on that could be refactored to a different target. 


## Resources
Markus Rampp - SlackCellv2 - https://gitlab.com/Grommi/slackcellv2
