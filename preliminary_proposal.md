# Capstone-Project
# High level description of project.

    The Global Database of Events, Language and Tone is a project which "monitors print, broadcast, and web news media in over 100 languages from every country in the world. [link](https://www.gdeltproject.org/#intro). The strength of GDELT and the reason that I want to use it for this project is that it does much more than catalog the word content of the articles. It performs a great deal of processing of the articles, data which is largely placed in two databases, the Event Database and the Global Knowledge Graph. (For 15 languages, this is done in the native language. For the others, the analysis is done after the text is machine translated to English).
    
    The Event Database places the event into one of over 300 categories. Nearly 60 attributes are recorded about the event, like the location and who was involved.
    
    The [Global Knowledge Graph](https://www.gdeltproject.org/#computing) "compiles a list of every person, organization, company, location and thousands of emotions from every news report". To assess the emotions/ tone of the article, they use 24 emotional measurement packages that assess 2300 emotions and themes. 
    
    I want to see, for a given type of event, how a region is likely to respond to it. I want to start by looking at one type of event, finding all of its occurences, and creating a "Region Response" for that region and that event. I want to see if I can use unsupervised learning techniques like PCA to then classify Region Responses into different classes. 
    
    Example: An event occurs, namely a "Government Corruption Scandal, reported on by at least 1% of its country's media, and their tone in reporting on it is at least x somber". We go to every country where this event occurred, and get a baseline of the country situation the week before it. We then calculate how all these statistics change over the upcoming week in response to the story, the "Region Response". We finally look at whether any statistics about the country at the time of the event can predict what type of region response they had. 

    `pseudocode:
    for event in event_categories:
        find all occurences of said event in history
        for occurence in occurences:
            get a baseline of that region at that time before the event. Maybe go back one week and get an average baseline of relevant features. This may be a good timeline depending on the length of the news cycle (more research needed?)
            Calculate the percent change in each of the features after the event over different timespans (day, week, month).
            Save this percent change in all features as db entry, associated with region and date. 
    Perform Principle Component Analysis. This will be the "Region Response" to event.
    Join PCA database with other database with statistics on regions at those given dates. I will need to find reputable and long-lasting datasets with many indicators.
    Use these features to predict which class a country will fall into.

    Once the countries are in different classes, we can look at the specific features that went into the PCA to see which are most correlated with the event. Some may be correlated for countries in all classes, otheres just for countries in that specific class. We will thus be able to say, "Event 1 has a high likelihood of causing x, y, and z in countries of this class, but not a high likelihood for countries of this class."    


#What question or problem are you trying to solve?

    The question I want to solve is whether we can predict future events based off of current ones. I would like to be able to say, given a country's current situation, our model has shown us that if it adopts this type of policy, or suffers a political riot, these events are made more likely. So we need a baseline for each country, which may require a different data source. But then we can ask, why did this event lead to this other event in some countries, but not in others? 
    
    So it's almost two questions: 
    We take one category of event, say extremely somber mass shooting. We then find what other events are more likely after this event. We then classify different countries as yes/ no, their likelihood did go up, or didn't go up, so then add that if any factors can predict that.

    Features: An event occurs in a region. IDK. A mass shooting in the US. What other events go up or down after? Then, can we use features about that region, general statistics, to predict how it will respond to an event. 
    
    Maybe we use some form of unsupervised learning to classify different countries responses. With PCA. So the same event happens in one country. These are the things that go up and the things that go down.The extent to which they change is noted. This is a huge number of features, so we use PCA to reduce this. We then have a characterization of a country's or region's response to an event, maybe we use unsupervised learning to place these responses in different classes. Finally, we use statistics about that country at the time of the event to predict which class it will fall into. 
#How will you present your work?

    I would like to make an interactive web app, where you can play around with the predictive model. Take a country and give it an event, and the model will tell you what it predicts to happen after. 
    
    I also imagine that I may use boosted decision trees. While I know these are difficult to visualize, I hope to find a method to present how the model made its decisions. 
#What are your data sources?
#What’s your next step towards making this your project.