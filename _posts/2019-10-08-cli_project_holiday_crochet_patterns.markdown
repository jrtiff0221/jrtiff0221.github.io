---
layout: post
title:      "CLI Project Holiday_Crochet_Patterns "
date:       2019-10-08 23:59:41 -0400
permalink:  cli_project_holiday_crochet_patterns
---

 

 
	When I hear the word software developer the first thing that comes to mind is a nerdy person with their head zoned into their computer tapping away at random keys.  It wasn't until my first CLI project that I came to the conclusion that Software developers are essentially artist, but not in the traditional manner rather a coding sense.  Similar to an artist a Developer has to get inspired to create something useful to themselves and/or others.   My obligated inspiration was to create an interactive Holiday Crochet Pattern (HCP) Program. The HCP program would allow a user to initialize the program by typing bin/console + enter in the terminal brief pause.  Then in the terminal appears the content 
	
	Welcome to your Holiday crochet pattern program!
	
	1. Silly Monster Trick or Treat Bag
	2. Fabulous Fall Table Runner
	3. Five Minute Hearts
	4. Beer Mug Bottle Cozy
	5. Cute Turkey Crochet Wreath
	6. Lucky Leprechaun Hat
	7. Rustic Stars
	8. Hanging Crochet Skeleton
	9. Snowflake
	10. Candy Corn Wreath
	11. Crochet Candy Bar Clutch
	12. Super Ghoster Coasters

	Please choose a pattern number(1-12) from the list.

	The user selects the number 10 from the list, again brief pause occurs then more text appears in the command line
 	Title: Candy Corn Wreath

	Description: This easy crochet wreath pattern is the perfect piece of fall decor. With autumn-shaded crochet flowers and little crochet candy corn bits, this festive little wreath will help usher in the changing seasons. 

	From the Blogger: "This fun holiday wreath features crochet candy corn and candy corn colored flowers. Made on a 12" Styrofoam wreath, it is first wrapped with worsted weight yarn (I used corn meal, a dusty yellow color) and then wrapped with 1/4" wide brown ribbon. The candy corn and flowers are then crochet and added to the wreath with the aid of florist pins. Florist pins are found in most craft stores in the floral department. They are wire, U shaped pins that are inserted into the wreath and hold the candy corn and flowers in place."

	Rating: Easy

	Link: http://donnascrochetdesigns.com/more/free-crochet-pattern-candy-corn-flower-wreath.html

	Crochet hook: H/8 or 5 mm hook

	Yarn weight: (4) Medium Weight/Worsted Weight and Aran (16-20 stitches to 4 inches)

	Crochet gauge: candy corn 1" wide
flower 2" wide
Finished size: 12" wreath

Im not going to get into depth about all the methods within my two class. I am only going to describe the last method built in my CrochetScraper class. 
	The final instance method defined in my CrochetScraper class is the self.scrape_holiday_pattern_by_path with an argument of url_path.  
This method begins grabbing select properties about the pattern. First off doc = CrochetScraper.get_doc_from_url(BASE_PATH + url_path). This is variable is similar to the parsing method described in the previous method, however the url_path is different for each pattern within the ‘/Holiday-Crochet-Pattern slug.  I set a variable called attributes = doc.css(‘.articleAttrSection p’). .articleAttrSection is a class and within that class is an array paragraph of elements = p. A second variable called description takes the first element in the attributes array, which is an html paragraph element(i.e description of the pattern), and gets the text from it.  A third variable called rating takes the second element in the attributes array which is an ‘img’ with an ALT tag = Beginner. 
	It was the anchor tags within the .articleAttrSection class where I had to do a lot of refactoring in my project.  Some of the websites had and anchor with the href link to obtain the pattern. A couple pattern websites didn’t have an anchor tag in the .articleAtrrSection class itself but under another class called .stepByStepInstructionsDiv. which had anchor tag and href link to the yarn used for the pattern. I created a variable called instructions = doc.at_css(‘.stepByStepInstructionsDiv’) then used a condition with instructions and  set instructions.content = nil. This allows my programs to ignore the content in the .stepByStepInstructionsDiv class. 
	The final attribute variable I created was the link = anchor ? anchor[:href] : BASE_PATH + url_path. This variable states that if an anchor element exists with a href link then use the link for the pattern directions other wise use the BASE_PATHS + url_path (for the websites that have directions on the website). Some of the websites had other attributes about the patterns that we wanted to include in the  attribute properties of the pattern. In order to extract these attributes local variables are set the key (attr_hash), and value (attribute). Key = attribute.at_css(‘.attrLabels’) this takes the first element in the .attrLabels class. 

Vaule= attribute.css(‘span’).length == 2 ? Attribute.css(‘span’).last : attribute. This means that any element(s) within span element of the .attrLabels class is pulled. A condition is then set to select only the last element within the span length ie the attribute value. 	
	For example Crochet gauge: 16 sc = 4 [10 cm]; 14 rows = 4 [10 cm] in single crochet. CHECK YOUR GAUGE. Use any size hook to obtain the gauge. 
Crochet gauge is the first element in the span tag of the . attrLabels class. Secondary element within span tag of the attrLabels class is describes the key ie making it the value.  .last takes the last element within the span tag of the attrLabels class. A finally condition is set and where the inner text of all the elements with in the span tag are returned. .Capitalize makes the first letter in the inner text Capitalize. .gsub replaces text.  attr_hash is returned .compact loops over the condition and getting rid of keys with empty values.
That is the conclusion of my CrochetScraper class and methods. I can say I am proud of MY masterpiece. One project under my belt many more to come. 
