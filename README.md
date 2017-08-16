# Alexa Color Harmony Skill
Ask Alexa for color harmonies!
### Description 
The goal of this project is to create an Alexa skill that will allow you to ask Alexa for various color harmonies for colors. An example phrase would be "Alexa, what's the complementary color for hex <some hex color code>".
The color harmonies I plan to add to this skill are:
* Complementary
* Split Complementary
* Triadic
* Tetradic
### Resources
I will be using the Alexa Skills API, AWS Management console, AWS Lambda, and an Amazon Echo for this project. 

### Contact
###### Name: Max Marchuk
###### Email: maxmarchuk@gmail.com
###### License: MIT

## Week 3 Report
All of the work I'm doing is in Amazon's various web services including the Lambda management console. I've been doing mostly experimental work but at this point I have a working prototype that I can test in the Amazon Alexa developer app by sending text commands to the alexa skill in the cloud. Here are the things I've got working:

#### Alexa Interaction Model
This is what the user will be interacting with, using their voice. The idea here is to offer many different ways to set your color or get harmonies for your color, because otherwise the user would have to look at the documentation each time, and I want this to be somewhat intuitive. Feel free to open an issue on this repo if you believe there should be something else added.

  * Handling setting the current color you're working with
    * Can be done with either 3 or 6 hexadecimal characters. I am using hex codes for colors because calculation seems to be easiest with these. 
    * Must be spoken in one the following ways: 
      * "set color to {first} {second} {third}",
      * "set color to {first} {second} {third} {fourth} {fifth} {sixth}"
  * Handling for the different color harmonies (complementary, split-complementary, triadic, tetradic). I am not a designer, so many of these may be grammatically incorrect
    * Must be spoken in one the following ways: 
      * "What are the {harmonyType} colors",
      * "What is the complement?"
    
This is the gist of the interaction model, and this is what the alexa skills development kit runs against my lambda function through various "Intents". I defined the above phrases to work with various intents that are then handled in my lambda function. That's where the actual coding comes in and I can do some math on the hex color codes to get the right harmonies.

#### AWS Lambda Function
As mentioned above, the AWS lambda function will handle the various intents and their payloads. The request payloads consist of the type of intent (setColorIntent or getColorsIntent) and some data, like the color that's being set in the session, or the color harmony you want to get for the current color in the session.
To calculate the harmonies, I will need to convert the hex codes into a form called HSL (Hue, Saturation and Lightness) which is much easier to perform calculations on, especially for harmonies.
Here are some of the formulas I will need to calculate the different harmonies:

###### Complementary:(Currently the only harmony implemented)
* formula: H1 = |(H0 + 180 degrees) - 360 degrees|

###### Split Complementary:
* formula: H1 = |(H0 + 150 degrees) - 360 degrees|
* formula: H2 = |(H0 + 210 degrees) - 360 degrees|

###### Triadic
* formula: H1 = |(H0 + 120 degrees) - 360 degrees|
* formula: H2 = |(H0 + 240 degrees) - 360 degrees|

###### Tetradic
* formula: H1 = |(H0 + 90 degrees) - 360 degrees|
* formula: H2 = |(H0 + 180 degrees) - 360 degrees|
* formula: H3 = |(H0 + 270 degrees) - 360 degrees|

I hope to find a node library that does the HEX -> HSL conversion work for me, but I wouldn't know how to implement that in the AWS lambda if I did. It shouldn't be too hard to do anyways, but I think it'd be a good experience to attempt to use another node module
