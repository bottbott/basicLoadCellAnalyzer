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

- Microprocessor
- Load cell sensor
    - https://www.sparkfun.com/products/13879
- Load cell amplifier
- Eye bolts

# Microprocessor vs Microcontroller
This project could likely be implemented with a microcontroller solution using an Arduino, or a microprocessor solution using a Raspberry Pi. Given that there is a large tech stack already at play, using a Raspberry Pi should help remove complexity by having on board WiFi and an operating system. 

- Arduino
    - The Arduino might be a little trickier to use to figure out how to handle the sensor data and serially transmit it via some wifi or bluetooth adaptor.

# Microprocessor
There are so many different options for microcontroller that it's hard to know which one is sufficient for this project.

Options
- Raspberry Pi
    - The build walkthrough by Markus uses a Raspberry Pi Zero with wifi. Might be easiest to copy. The Pi can recieve the data and could also be a web server to server an app. 
- Raspberry Pi Zero W 2
    - https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/
    - https://www.pishop.ca/product-category/raspberry-pi/raspberry-pi-boards/current-pi-boards/



We want a controller that:
- has wifi (will be easier to work with than bluetooth)
- has sufficient sampling rate for the incoming sensor data

# Load cell sensor
Load cells come in many different formats. 

- must be able to accept an eyebolt so that it can be pulled in opposite directions. 
- must be able to handle a sufficient force/weight. 

- https://www.amazon.ca/Pressure-Sensor-Scale-Weighting-500kg/dp/B08DXPVBC9/ref=sr_1_164?crid=38BCGGO1GCMLI&keywords=s-type+load+cell&qid=1641179109&sprefix=s-type+load+cell%2Caps%2C128&sr=8-164
- https://www.aliexpress.com/item/1005002666170876.html?src=google&src=google&albch=shopping&acnt=708-803-3821&slnk=&plac=&mtctp=&albbt=Google_7_shopping&albagn=888888&isSmbAutoCall=false&needSmbHouyi=false&albcp=7989987352&albag=90862527748&trgt=1460897941361&crea=en1005002666170876&netw=u&device=c&albpg=1460897941361&albpd=en1005002666170876&gclid=Cj0KCQiAt8WOBhDbARIsANQLp94a5uxooPlXEMnw2tWiET-HG8wHmZuzLPeB9t2sBxPkKWQCUrjW_ZIaAkBaEALw_wcB&gclsrc=aw.ds&aff_fcid=8cca498ac89748e590302ce9cd4ab223-1641178773327-00494-UneMJZVf&aff_fsk=UneMJZVf&aff_platform=aaf&sk=UneMJZVf&aff_trace_key=8cca498ac89748e590302ce9cd4ab223-1641178773327-00494-UneMJZVf&terminal_id=36a7c99daaa1448e9ec385f11a7523fd
- 

# Local cell amplifier
Not sure what distinguishes these but there seems to be some differences that need to be researched. The circuits I've looked at so far have a different sample rates and they also have the ability to accept an external clock signal that can be used to set the sampling rate. I have seen a 10 SPS and 80 SPS setting for the same circuit, and that should be sufficient for now and if a higher sampling rate is desired then it can be configured later on through the external clock inputs.

HX711 datasheet - https://www.digikey.com/htmldatasheets/production/1836471/0/0/1/hx711.html


# Eye bolts
Should be similiar metals so that the is no galvanic corrosion between them, and to ensure they fit together well with the sensor.

# Microcontroller Programming 
For the microcontroller I was thinking that I would install Node.js and then have a web server running on it that can serve a webpage. There should be an application that can collect the output from the load cell and then display it in a way that is beneficial to the user. 

- See the data.
- Record the data.

The frontend can possibly just be built in vanilla JS, but maybe this would be a fun opportunity to play with a framework? The backend would need to be some sort of database. Could be a NoSQL solution, or maybe something on the microcontroller and have the data stay there? That seems like a bad idea because it becomes a limiting factor as storage space goes down and it also isn't accessible without being near the physical device. Probably should think about how to decouple the application from the microcontroller so that it is only minimally coupled to perform the measurements. 

There are a few libraries built to work with HX711. There's one in Python and another in NodeJS. Could potentially try either.

NodeJS
https://github.com/ataberkylmz/hx711

Python
https://github.com/tatobari/hx711py



# Frontend
HTML
CSS
Javascript

OR 

Some framework for fun, and which might tie together frontend/backend as well. 
React
Angular
Vue
Svelte

Going to experiment with Svelte. 


# Backend
Might need a couple of endpoints to do things?
/save


# Storage
Need to house the data somewhere. Keeping it on the microcontroller is where we'll start. Eventually, will need to sync the changes to an external storage somewhere. It should make it easier to start so that the application doesn't have to fetch data or save data to something off-device. I guess a recording session is cached locally, and then there could be a save function that for now writes it to the device and then later on that could be refactored to a different target. 

MongoDB
https://www.mongodb.com/developer/how-to/mongodb-on-raspberry-pi/

## Resources
Markus Rampp - SlackCellv2 - https://gitlab.com/Grommi/slackcellv2
https://stackoverflow.com/questions/69572201/interfacing-load-cell-and-hx711-with-raspberry-pi-3-using-python-3