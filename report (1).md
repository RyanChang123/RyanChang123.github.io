Summary 

The question we attempted to ask was whether positive or negative sentiment in a company's 10-K filing could predict future returns for the stock. The first step for this problem was figuring out which firms to use in the study. In a holistic study, I would have used all the firms currently publicly traded. However, due to computing constraints, this was limited to the 500 firms in the S&P 500. Upon deciding which firms to use, I needed to download the 10-K files. This was done through EDGAR and the SEC website for downloading the most recent 10-Ks for the firms in the S&P based on last year. Collecting the 10-Ks along with the price returns surrounding the filing period, I attempted to understand how these 10-Ks related to returns, primarily focusing on topic areas of Porter's Five Forces, company risk, and company employees. Aggregating the positive and negative sentiment around these areas, I attempted to find a pattern associated with these sentiments and the 10-K returns.

The first step upon downloading the 10-Ks was determining what words to use for sentiment and how to determine the topic being used. In determining what topic areas to use, I focused on the topics of Porter's Five Forces, company risk, and employees. In determining whether the company was describing these areas of the business in the 10-K reports, I focused on keywords given to us by the textbook. In relating to whether the 10-Ks had positive or negative sentiment around these topic areas, I used a count to determine the mentions of positive and negative words from two sentiment databases. These sentiment databases included those from a machine learning program and from a list of words by Tim Loughran and Bill McDonald. The counts of these words, both negative and positive, were created surrounding the words near the topic areas. These positive and negative word counts were then put into a CSV along with the return data. Depending on a weighted average of topic area and how positive the sentiment was within each topic area, firms were categorized into low, medium, and high sentiment values. Correlating these sentiment values with the performance of the stock during the end of the fiscal year and right after the reporting window, I was able to compare how they performed from a sentiment perspective.

In computing results, there were three graphs created throughout this study. They consisted of a positive correlation, negative correlation, and sentiment return graphs. The positive correlation graph pitted the count of ML and LM positive and negative words and related their counts to positive stock returns. The negative correlation graph pitted the count of ML and LM positive and negative words and related their counts to negative stock returns. The sentiment graph took groupings of weighted average sentiment by firm into low, medium, and high categories by LM or ML databases. The graph then created a scatter plot taking the weighted average sentiment by topic area compared to returns and graphed it by each sentiment grouping. The resulting graphs created interesting results and room for further exploration. In general, the ML words and their relation to positive returns were expected. The positive words were positively correlated with positive returns, and the negative words were negatively correlated with positive returns. However, a point of emphasis is the LM relations to positive return. The LM values were flipped where positive returns were positively related to negative words by topic and were negatively related to positive word counts. This difference is fascinating and needs to be explored further. When looking at the negative correlations, most variables related to both positive and negative word count by topic were positively related to negative returns. This excludes the variables related to employees. For both negative and positive mentions in LM employees' topic areas, there were negative correlations with negative return. This could be interpreted as sending a positive signal to returns because employees are being cut and the business is being streamlined or if a new hire could boost potential profitability of the firm. When looking at the sentiment return results, I created a graph grouping the overall weighted sentiment into low, medium, and high groups for both LM and ML variables. I then graphed this weighted average on the x-axis and returns on the y-axis. Surprisingly, many of the graphs seem to be normally distributed. Some points of notice include the high ML positive group. The vast majority of firms had positive returns in relation to the positive sentiment they received. Another point of note is the medium sentiment firms for LM. These firms had vastly negative returns across the group. In summary, the results of the study indicate several instances where further insights could be helpful in determining how sentiment may affect the stock price, and there is much more research that needs to be done.

Data section

The data collected came from a sample of 500 S&P firms and their 10-Ks. I utilized data cleaning techniques, organized spacing, and separated each word of each respective 10-K by word. This allowed me to determine which words matched the topic area words and the matching sentiment words surrounding them. Filtering through each 10-K file allowed for the counts of positive and negative sentiment words to be created surrounding each topic area.

Variables 

ML Positive : list of postive ML words 
LM Positive : list of postive LM words 
ML Negative : list of Negative ML words 
LM Negative : list of Negative LM words 

Porter's 5 : list of words related to Porter's 5 forces 
Risk : list of words related to business risk and litigation
Employee Behavior: list of words related to employee behaviors of the business

Relating to ML
Security : what security is being referenced 
T1P : Topic 1 postive word count 
T1N : Topic 1 negtive word count 
T1T : Topic 1 total related word count = T1P + T1N 
T1P%: % of positive word count = T1P / T1T
T2P : Topic 2 postive word count
T2N : Topic 2 negtive word count 
T2T : Topic 2 total related word count = T2P + T2N 
T2P%: % of positive word count = T2P / T2T
T3P : Topic 3 postive word count
T3N : Topic 3 negtive word count 
T3T : Topic 3 total related word count = T3P + T3N 
T3P%: % of positive word count = T3P / T3T
LM_sentiment : categorical variable
     if 0.8 <= weighted_average <= 1.00:
                sentiment = "High"
            elif 0.7 <= LM_t1_positive_percent < 0.8:
                sentiment = "Medium"
            else:
                sentiment = "Low"
Weighted Average: weighted average of all three topic areas TP% 

Relating to LM
Security_LM : what security is being referenced 
LM_T1P : LM Topic 1 postive word count 
LM_T1N : LM Topic 1 negtive word count 
LM_T1T : LM Topic 1 total related word count = LM_T1P + LM_T1N 
LM_T1P%: LM % of positive word count = LM_T1P / LM_T1T
LM_T2P : LM Topic 2 postive word count
LM_T2N : LM Topic 2 negtive word count 
LM_T2T : LM Topic 2 total related word count = LM_T2P + LM_T2N 
LM_T2P%: LM % of positive word count = LM_T2P / LM_T2T
LM_T3P : LM Topic 3 postive word count
LM_T3N : LM Topic 3 negtive word count
LM_T3T : LM Topic 3 total related word count = LM_T3P + LM_T3N 
LM_T3P%: LM % of positive word count = LM_T3P / LM_T3T
LM_sentiment : categorical variable
     if 0.8 <= weighted_average <= 1.00:
                sentiment = "High"
            elif 0.7 <= LM_t1_positive_percent < 0.8:
                sentiment = "Medium"
            else:
                sentiment = "Low"
Weighted Average: weighted average of all three topic areas LMT% 


Realting to Security prices 
Ticker : outlines what ticker the returns are related to 
date_1 : security price before the end of the fiscal year and reporting period 
date_2 : security price just following the reporting period close
Return: difference between date 1 and date 2 price 

Words used in each dictionary 
LM Positive : 30 
LM Negative : 30
ML Positive : 75
ML Negative : 48

The lists in the ML dictionaries consisted of all the words available in the sample. The words in the LM dictionaries consisted of 30 words in the dictionary based on the central limit theorem. A sample of 30 or more should approximately return a normal curve of returns, justifying the sample size I used.

A CSV was created for three components:

Returns before and after 10-K filing for the 500 S&P stocks.
1. Counts and sentiment categories for each topic by ML words.
2. Counts and sentiment categories for each topic by LM words.
3. A full CSV was created by combining these three CSVs.

The full CSV was then cleaned for missing values in order to perform the correlation and analysis.

The near_regex function is a function that determines if a positive or negative word sentiment is related to the topic being discussed in the 10-K. I did not want to factor in partials into the near_regex function because I believe this would skew the data to having more negative or positive sentiment than there actually is. The maximum distance I used for a topic and its descriptive adjective was 5 words. Based on research that the average sentence is between 15 - 20 words and that there are approximately 2 - 3 adjectives in a sentence, I thought that the length of a maximum of 5 words separating the topic and adjectives was justified.

I chose Porter's Five Forces, Risk, and Employees because it provides a holistic overview of the company. Porter's Five Forces covers the dynamics within the industry. Risk applies to litigations and company-specific issues or potential future hurdles. Employees deal with the specific employee sentiment around the company or how the company may be affected in the future from an employee perspective.

The summary statistics of the final analysis can be seen through the correlation graphs of positive and negative sentiment along with the weighted average sentiment graphed against positive and negative return. These statistics measure low, medium, and high sentiment for ML variables and LM variables as compared to the stock returns before and after the filing period. The graphs provide a holistic overview of general sentiment based on the count of positive and negative variables by topic and how that relates to the change in returns. Some caveats about the sample are that the returns are calculated through the general end of the reporting period. This may be different firm by firm and could affect the results. Additionally, the data does not affect overall market conditions which could affect firm pricing. A strong economy would artificially boost stock prices and returns while a weak one would do the reverse. This may inflate or deflate return data regardless of positive or negative sentiment surrounding the topic.

Results

Tables with the correlation between positive and negative variables by topic and compared to positive and negative returns can be seen in the positive_correlation and negative_correlation PNGs. Further, a scatterplot PNG can be seen through the Sentiment_return PNG. This outlines the weighted average sentiment compared to return for low, medium, and high sentiment. It also separates the data into the ML and LM variable categories.

In comparing the relationship between return variables for LM and ML compared to returns, it is important to look at the correlation graphs. In the positive_correlation graph, the ML variables seem to indicate an "expected" result. In this case, all topic positive words related to positive stock returns while the negative ones had a negative correlation with positive returns. However, when looking at the LM words, these seem to be completely reversed. The positive words surrounding each topic seemed to indicate negative returns while the negative words seemed to be positively correlated with the positive returns of the firm. In particular, the Porter's Five Forces negatives words seem to have a very significant positive correlation with positive return.

In the negative_correlation graph, there is a significant difference in results. The results indicate that nearly all mentions of positive and negative words are positively correlated with negative returns. This could be influenced by the current market environment the data was taken from or the way the negatives were referenced in the 10-K. This was the case for all values except for employee references. For both positive and negative employee mentions, there was a negative correlation with negative returns. The positive word sentiment was slightly negatively correlated, but the negative word sentiment was significantly correlated with negative returns.

Hu and Roher incorporated many more firms, years, and additional controls to attempt to get a more holistic view of the market and how sentiment may affect returns. During my analysis, I only focused on the S&P 500 firms, which are large-cap firms in the US. By incorporating over 3000 firms, the analysis performed in the study gives better insights into firms that do not fall into the S&P 500 and provides a better measure of how sentiment affects all firms. For years, the data compiled for my study only consisted of the returns before and after one year of 10-K filings. In the study, they had data for over a decade and aggregated the results across firm 10-Ks. This allows them to analyze more data and have a better understanding if data may change over time. The additional controls allow the study to get a better analysis of how different reporting forums may influence the wording that is used. For example, earnings reports, 10-Ks, and the WSJ will each utilize adjectives differently, and market sentiment will be different depending on which avenue the sentiment information is received from.

For contextual sentiment, two variables that I would want to investigate further are the positive returns for LM negative sentiment for Porter's Five Forces and LM employee negative sentiment for negative returns. Both these values are significantly more correlated than the other variables. What is fascinating is that they are opposite of what one would think they would be. The negative sentiment for LM Porter's Five Forces had the greatest correlation for positive returns for all variables. This should be investigated further and may affect the interpretation of Porter's Five Forces analysis for analysts. If negative sentiment could indicate positive return, then perhaps the 10-K should be read differently and interpreted differently by those reading and analyzing the security. For LM employee negative sentiment, the negative references had a negative correlation with negative returns. This could affect economic implications for descriptions of HR and how that may affect the stock price and how analysts should interpret the information.

Sign indicates expectation while magnitude indicates the severity of the expectation. In this context, the sign is how each variable and topic relate to the return of the stock after and before filing. The magnitude is the significance positive or negative sentiment by topic area is correlated to the returns of the stock. In this case, there were several instances of unexpected signaling and magnitude of results. The ML and LM data seems to be flipped through several different variables, and the LM negative Porter's sentiment and LM Negative Employees sentiment seem to have opposite effects than expected. Understanding that these variables signal to investors in relation to returns is important to interpreting the movement of the stock. Understanding the magnitude of the effects is important in long-term understanding of the correlation of the variables with return and how impactful they are.
