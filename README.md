# Article-Theme-Identifier
Program that identifies the theme of the news article from its URL, through supervised machine learning

## RATIONALE
For building a news aggregator, one needs a tool to categorize articles based on their theme. Different news websites use different tags/names for their categories, so the aggregator has to define its own categories and associate the articles from different websites to these categories. Using supervised machine learning with the Wolfram language, I have created a program that can handle this categorization.

## HOW IT WORKS

I have used the NaiveBayes classifier as it works well for categorical variables which is what we need. I created the training set by importing the text from the URL's of politics and sports news articles from various news outlets and labeling them. After training the classifier on this dataset, its performance was very low (48%): \
![Снимокэкрана2016-08-19в12 38 10](https://user-images.githubusercontent.com/52777539/89296545-88a02080-d673-11ea-88f9-6e78505acd32.png)

The reason was from the noise in the training data coming from the ads and unrelated content in the webpages of the news articles I imported. To extract only the main body of the articles from these webpages I created the function getBody displayed below. 

<img width="728" alt="Screen Shot 2020-08-04 at 6 07 35 PM" src="https://user-images.githubusercontent.com/52777539/89303541-63181480-d67d-11ea-89d0-f7b0b412fa00.png">

It detects the text of the article through a 600-character moving window which counts the number of non-whitespace characters and extracts the densest segment of the text (above the pre-specified threshold) as presented on the graph:

![Снимокэкрана2016-08-19в16 11 47](https://user-images.githubusercontent.com/52777539/89297037-504d1200-d674-11ea-8b64-420b8b348913.png)

With this new way of data extraction the training set did not contain any noise and the performance of the classifier improved from 48% to 80%:

![Снимокэкрана2016-08-19в14 59 06](https://user-images.githubusercontent.com/52777539/89303763-ab373700-d67d-11ea-8f16-11ac5fc89649.png)

## FUTURE PLANS
With this methodology, the classifier can be further trained on datasets with other news category types and the program can be integrated into a news aggregator.
