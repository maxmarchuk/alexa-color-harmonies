# Alexa Color Harmony Skill
Ask Alexa for color harmonies!
### Description 
The goal of this project is to create an Alexa skill that will allow you to ask Alexa for various color harmonies for colors. An example phrase would be "Alexa, what's the complementary color for hex <some hex color code>".
The color harmonies I plan to add to this skill are:
* Complementary
* Split Complementary
* Triadic
* Tetradic

### Installation Instructions
I used AWS Lambda to make a function for handling the intents and Alexa Skills Kit for defining the user interactions (utterances), so you will need an account on console.aws.amazon.com and on developer.amazon.com. 
1. Download and extract the contents of color_harmonies.zip
2. Create an AWS lambda function with NodeJS 6.10 and paste the contents of lambda.js into the online code editor
3. On developer.amazon.com, click on the Alexa tab at the top of the page and then click on "Get Started" on Alexa Skills Kit.
4. You can now create a new skill, go to the interaction model, and simply paste intents.js into the code editor.
5. There may be further configuration needed to set up, but once you wire your new skill to your lambda function, it should be pretty straight forward.

### Resources
I will be using the Alexa Skills API, AWS Management console, AWS Lambda, and an Amazon Echo for this project. 

[Week 3 of development](https://github.com/maxmarchuk/alexa-color-harmonies/blob/master/week3report.md)


### Contact
###### Name: Max Marchuk
###### Email: maxmarchuk@gmail.com
###### License: MIT

