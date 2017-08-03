# Analysis of A/B testing

Companies often run tens, if not hundreds, of A/B tests at the same time. 
In this project, I analyze results from an A/B test and design an algorithm to automate some steps.

For an e-commerce company with localized versions of the site, Spain-based users have a much higher conversion rate than any other Spanish-speaking country. One possible one reason could be translation. All Spanish- speaking countries had the same translation of the site which was written by a Spaniard. 

An A/B test to compare conversion rate of having the same translation for all countries, with that of having local translation for each country. That is, Argentinian users would see a translation written by an Argentinian, Mexican users by a Mexican and so on. Obviously, nothing would change for users from Spain.
The suprising results show that the test is negative. I.e., it appears that the non-localized translation was doing better.

### The goal of this project is to
* Confirm that the test is actually negative. That is, it appears that the old version of the site with just one translation across Spain and LatAm performs better
* Explain why that might be happening. Are the localized translations really worse?
* If you identified what was wrong, design an algorithm that would return FALSE if the same problem is happening in the future and TRUE if everything is good and the results can be trusted.

## Data

###  "test_table" - general information about the test results

Columns:
* user_id : the id of the user. Unique by user. Can be joined to user id in the other table. For each user, we just check whether conversion happens the first time they land on the site since the test started.
* date : when they came to the site for the first time since the test started
* source : marketing channel: Ads, SEO, Direct . Direct means everything except for ads and SEO. Such as directly typing site URL on the browser, downloading the app w/o coming from SEO or Ads, referral friend, etc.
* device : device used by the user. It can be mobile or web
* browser_language : in browser or app settings, the language chosen by the user. It can be EN, ES, Other (Other means any language except for English and Spanish) ads_channel : if marketing channel is ads, this is the site where the ad was displayed. It can be: Google, Facebook, Bing, Yahoo ,Other. If the user didn't come via an ad, this field is NA
* browser : user browser. It can be: IE, Chrome, Android_App, FireFox, Iphone_App, Safari, Opera
* conversion : whether the user converted (1) or not (0). This is our label. A test is considered successful if it increases the proportion of users who convert.
* test : users are randomly split into test (1) and control (0). Test users see the new translation and control the old one. For Spain-based users, this is obviously always 0 since there is no change there.

###  "user_table" - some information about the user

Columns:
* user_id : the id of the user. It can be joined to user id in the other table sex : user sex: Male or Female
* age : user age (self-reported)
* country : user country based on ip address
