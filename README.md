# Navigating Customer Heterogeneity: Advanced Analytics for a UK-Based E-commerce Retailer

![image](https://github.com/user-attachments/assets/c0a8dfb5-7b65-4372-8d7a-1227874a059e)

## Introduction and Background

In the rapidly changing landscape of e-commerce business especially post covid- 19, understanding and leveraging customer heterogeneity has become a significant factor of competitive advantage in the market. As businesses transition to digital-first models – putting the customer first and making a customer centric strategy, the ability to recognise and cater to the diverse preferences and behaviours of online shoppers is significant (Luo et al., 2023). This report explores into the application of advanced analytics to highlight the complexities of customer diversity within the context of a US-based multinational retailer specializing in unique all-occasion gifts. Mostly serving a broad customer groups, including a significant portion of wholesalers. The retailer operates exclusively online, presenting a rich dataset of transactions and customer records over the period from December 1, 2020, to November 24, 2021.
The challenge of customer heterogeneity lies in the vast grouping of individual customer preferences, purchasing behaviours, and demographic backgrounds (Alves at el., 2023). Traditional marketing approaches often rely on undifferentiated strategies therefor they fall short in addressing the important needs and expectations of distinct customer segments (Taherdoost and Jalaliyoon, 2014). The introduction of analytics offers a solution to this challenge, enabling businesses to divide their customer base into meaningful segments. This analytical segmentation empowers marketers to tailor their strategies effectively, ensuring that the right products and messages reach the most interested audiences, thereby enhancing customer satisfaction and loyalty (Wongand and Wei, 2018).
A wide range of literature highlights the significance of analytics in addressing customer heterogeneity. Research in the fields of marketing and consumer behaviour consistently highlights the effectiveness of segmentation techniques in identifying distinct customer groups based on a variety of criteria, including demographic characteristics, purchasing behaviours, geographical features and psychographic profiles. Studies have shown that businesses that adopt data-driven segmentation strategies enjoy higher customer engagement rates, improved conversion metrics, and increased lifetime value per customer (Luo et al., 2023) (Alves at el., 2023).
Therefor to tackle the heterogeneity issue, this report employs a comprehensive analytics workflow, incorporating statistical methods and machine learning techniques to analyse the retailer's transactional data. Focusing on the principles of data-driven decision-making, methodologies used had been validated through academic research and practical application alike. By applying segmentation models, such as K-means clustering and hierarchical clustering, along with discriminant analysis, this analysis seeks not only to categorize customers into distinct groups but also to understand the defining characteristics of each segment based on the demographics and purchasing patterns.


## Methodology
The methodology section of this report outlines the systematic approach adopted to analyse customer data from an e-commerce multinational US-based retailer, focusing on segmentation, discriminant analysis using LDA model, and RFM analysis to understand and address customer heterogeneity. This section outlines the data preparation, selection of variables for cluster analysis, rationale behind methodological choices, and execution of analyses (Alves Gomes and Meisen, 2023).
Data Preparation and Quality Issues
A comprehensive examination revealed missing values and inconsistencies in variable types. Critical steps undertaken included:
1. Assigning unique identifiers to missing CustomerID entries to preserve record uniqueness.
2. Converting categorical variables (Married, Work, and corrected Education from Edcation) into factor types to accurately represent their categorical nature.
3. Addressing outliers in the ReturnRate variable by excluding records with a ReturnRate greater than 1.
4. Ensuring demographic information consistency for each CustomerID by retaining only the first occurrence of variables (ZipCode, Married, Age, Income, Work, Education), thereby enhancing data integrity.

### Selection of Variables for Cluster Analysis
The cluster analysis incorporated three purchasing behavior variables (Quantity, UnitPrice, ReturnRate) and one descriptive variable (ZipCode). The zipcodes in US follows a predictable incremental pattern in the number, so their centroid can be computed and area near to each other can be assigned to a cluster thus capturing regional characteristics, socio-economic factors, and consumption patterns that are critical for tailoring marketing strategies (Ehsani and Hosseini, 2023).

### Analytical Methods and Rationale

#### Cluster Analysis
Cluster analysis was executed using K-means and hierarchical clustering to identify distinct customer segments. To determine optimal number of clusters fviz_nbclust library was used to compute and visualize the WSS and silhouette plot.

![image](https://github.com/user-attachments/assets/b45d3699-8fdf-4f7f-bcc6-55e02f8ee519)

Figure 1: WSS plot 

![image](https://github.com/user-attachments/assets/e0dd5356-f0a2-44f5-b7e6-6330f7d4da0c)

Figure 2: Silhouette plot

![image](https://github.com/user-attachments/assets/6fa5fd26-5ef2-4818-92b5-edc4cb1e65a0)

Figure 3: Elbow plot

#### Hierarchical Clustering: 
Employing the Ward's method, chosen for its ability to create compact clusters of good distribution, an elbow plot from hierarchical clustering further corroborated the choice of k=3, revealing a natural division in the data that aligns with the silhouette analysis.

![image](https://github.com/user-attachments/assets/d9fde5e8-e57f-4e72-91a0-f27519e7a106)
![image](https://github.com/user-attachments/assets/407a8e1a-8350-4e69-a504-903c1fdc61cb)


**K-means Clustering**: Acting on the methodology from literature (Aslantaş et al.., 2023), The silhouette score, a measure of how similar an object is to its cluster compared to other clusters, indicated the highest average silhouette score at k=3. This finding suggested optimal clustering with three distinct groups, providing a balance of within-cluster similarity and between-cluster distinction with a score of 98.5 %. Suggesting a good separation among clusters.

![image](https://github.com/user-attachments/assets/ae5bab1a-2c14-4d4d-9612-4d7a074525b2)

#### Discriminant Analysis

Linear Discriminant Analysis (LDA) was employed to examine how well the identified segments could be distinguished based on demographic features. The LDA aimed to validate the robustness of the segments identified through clustering and to understand the variables most influential in defining segment boundaries (Xanthopoulos et al., 2013). The LDA model output included coefficients of linear discriminants, indicating the contribution of each predictor to the discriminants, and prior probabilities for each segment, reflecting the initial likelihood of segment before observing the data.

![image](https://github.com/user-attachments/assets/f2e89db5-6b9a-4e98-96c4-1aed8060070f)

![image](https://github.com/user-attachments/assets/cf61899b-b47d-4bc7-b85a-68079870dcae)

The coefficients show the contribution of each predictor to the linear discriminants, which are combinations of the predictors that best separate the segments. For LD1 (which accounts for 99.97% of the variance between groups), predictors like Income and Work2 have positive coefficients, indicating they help distinguish between segments.
Given the high proportion of trace captured by LD1, the analysis suggests that focusing on the predictors with the highest absolute coefficients in LD1 could be most fruitful for understanding the distinctions between segments. The model's effectiveness in distinguishing these groups based on the predictors suggests potential for targeted strategies in marketing, product development, or service offerings tailored to the unique characteristics of each segment.

![image](https://github.com/user-attachments/assets/e07cae3c-2fbe-4672-8e9e-81b51f684f03)

Discriminant model fit from the test set, and cross-validation analysis collectively suggest that the LDA model is highly effective at classifying observations into their correct segments, particularly highlighted by the model's high accuracy of AUC, and other performance metrics.

![image](https://github.com/user-attachments/assets/7107f97f-32eb-4774-93e5-13c3c3828eee)

The slight discrepancy in the ANOVA test of LD1 and LD2 scores. LD1, F value is 1.1402 with a p-value of 0.2856, suggesting that the differences in the LD1 scores across the segments are not statistically significant. This indicates that LD1 may not effectively differentiate between the segments. This highlights the complexity of discriminant analysis but does not detract from the model's overall exceptional performance in classification tasks. The results from the cross-validation further validate the model's strength and its capability to generalize well to unseen data.


### RFM Analysis
RFM analysis was conducted to evaluate customers based on recency, frequency, and monetary value, employing both independent and sequential sorting methods. This dual approach enables significant insights into customer behaviour and provide a deeper understanding of customer engagement levels (Christy et al., 2021).

## Results
The results from the analysis visualized in Tableau present a clear picture of customer segmentation within the US-based multinational e-commerce retailer. These insights, derived from a meticulous analysis using cluster and discriminant analysis techniques, as well as RFM scoring, are crucial in understanding the heterogeneity of customers and crafting tailored marketing strategies (Sarvari et al., 2016).

![image](https://github.com/user-attachments/assets/29623d64-83e3-4ea2-9b77-5abae6d77ad3)

![image](https://github.com/user-attachments/assets/aa0bf21a-397e-4b24-9553-05368197e247)


Segmentation was significant in distinguishing the varied consumer groups. Our findings revealed three distinct segments, each demonstrating unique characteristics:

**Segment 1** represents the 'Traditional Shoppers,' characterized by their median quantity purchases and consistent spending, accounting for the highest total sales volume of 82,214. Their geographical spread is the broadest, indicating a universal appeal of the retailer's products across diverse areas. The high number of married individuals and their age demographic suggest they may prioritize stability and reliability over novelty in their purchasing patterns.

**Segment 2**, the 'Selective Shoppers,' seems to be more calculated in their purchasing frequency but opts for larger quantities per transaction, as suggested by an average quantity of 12 per order. This behaviour might reflect a bulk-buying trend or an affinity for specific occasions that warrant larger purchases. With the highest average age of 61, this group likely represents more mature customers who value quality and quantity and have a higher loyalty potential.

**Segment 3** can be dubbed as the 'Frequent Shoppers,' with the smallest size but the highest order frequency and a young average age of 59, indicating a segment with potential long-term value for the retailer. Their geographic distribution and lower marital ratio hint at a more dynamic and possibly urban customer base, who could be responsive to trend-based and seasonal campaigns.
The geographical distribution analysis illustrated each segment's clustering pattern, suggesting distinct regional market characteristics that could influence tailored marketing and product positioning strategies (Ehsani and Hosseini, 2023).

![image](https://github.com/user-attachments/assets/6cb43cc7-2e74-494e-b6d8-2af977071820)

![image](https://github.com/user-attachments/assets/92960113-a73c-47cc-9be0-8afd944d7886)

Furthermore, the heatmap representing revenue generated from each ZIP code painted a compelling picture of how different regions contribute to the retailer's earnings, emphasizing areas of high engagement within each segment.

![image](https://github.com/user-attachments/assets/8bc5f0c9-c952-47f1-a7de-5e9f082c4f76)


### RFM analysis

![image](https://github.com/user-attachments/assets/4d72ef19-cb5b-4ad1-bb67-5108e9878164)

![image](https://github.com/user-attachments/assets/3ff7c52f-3e1e-4c53-a381-31f68a6ac410)


Recency: Customers are fairly evenly distributed across different recency segments. This suggests a stable inflow of customer engagement over time. No single recency segment dominates, indicating no recent market events or campaigns have disproportionately influenced customer purchases.
Monetary: There is a significant presence of customers in the higher monetary groups in Segment 1, indicating that this segment likely contains your most valuable customers in terms of spending. Segment Group 1 may be seen as the most crucial segment for revenue, with a drop in the count of high-spending customers in Segment Groups 2 and 3.
Frequency: The highest frequency groups are most noticeable in Segment Group 1, suggesting these customers not only spend more but also purchase more often, highlighting a segment of loyal and engaged customers. Segment Groups 2 and 3 have a reduced but still significant presence of frequent buyers.
Overall, Segment Group 1 is the most valuable, showing the highest levels of recent engagement, purchasing frequency, and spending. These customers are prime candidates for loyalty programs and upselling opportunities. Segment Groups 2 and 3 may represent customers with moderate engagement, who could be targeted with re-engagement campaigns and offers to increase their frequency and monetary contribution.
The data implies that efforts should be made to nurture customers in Segment Group 1 to maintain their high engagement and spending levels, while customers in Segment Groups 2 and 3 might need strategic incentives to increase their interaction frequency and spending with the business.

![image](https://github.com/user-attachments/assets/38ea8fc0-fd4a-4963-84fd-3c8d8b7d422c)

The most customers are in the 555 segment are in group 1, indicating a group of best customers who are recent, frequent, and high-spending. While, other noticeable segments are 454 and 355, which show a slightly lower frequency or monetary score but still have a relatively high customer count. Whereas, segments 2 and 3 have a notably lower customer count for the top RFM score (555) compared to Segment Group 1 but in Segment Group 2, the 455 segment seems to be more prevalent than in Segment Group 1.


The business could use this information to tailor specific engagement strategies for each segment.
1. Maintain the loyalty of the 555 customers with exclusive offers.

2. Encourage the 454 and 355 customers to spend more or visit more frequently to move them to the 555 segment.

3. Investigate why Groups 2 and 3 have fewer top-tier customers and develop strategies to increase their RFM scores.

This analysis helps in identifying where to focus marketing efforts and customer service to optimize customer value and loyalty.


## Conclusion 
In conclusion, the comprehensive segmentation analysis conducted for the US-based multinational e-commerce retailer has significantly defined the heterogeneous nature of its customer base. Through the application of advanced statistical techniques and thoughtful interpretation of the resulting data, three distinct customer segments have been identified and characterized by their unique demographic profiles, purchasing behaviours, and geographic distributions.
Segment 1, the 'Traditional Shoppers,' embodies a broad demographic reach with consistent purchasing habits. Segment 2, the 'Selective Shoppers,' shows a preference for bulk purchasing among an older demographic. Segment 3, the 'Frequent Shoppers,' while smaller in size, exhibits a high frequency of purchases and encapsulates a younger, dynamic customer segment. Each of these segments offers unique opportunities for targeted marketing strategies, product offerings, and customer engagement models.
The insights provided by the RFM analysis further emphasize the varying degrees of customer engagement across segments and suggest potential strategies for personalized marketing and customer relationship management. Moreover, the geographic analysis and monthly revenue trends underline the importance of localizing marketing efforts and optimizing them in line with seasonal and temporal purchasing patterns.

### Limitations
However, it is important to acknowledge the limitations of this project. While the analysis provides a strong foundation for understanding customer behaviour, continuous monitoring and re-evaluation are necessary to keep pace with the dynamic nature of e-commerce. Additionally, external factors such as market trends, competitor strategies, and economic conditions were not within the scope of this analysis and could impact customer behaviour (Pynatih et al., 2024).

### Practical implications
The retailer is now equipped with actionable insights to enhance its competitive strategy in the e-commerce landscape. By embracing the detailed understanding of its customer segments, the retailer can follow a path toward sustained growth, market adaptability, and a stronger customer-focused approach to its business model.


## References
Alves Gomes, M. and Meisen, T., 2023. A review on customer segmentation methods for personalized customer targeting in e-commerce use cases. Information Systems and e-Business Management, 21(3), pp.527-570.
Luo, Q., Forscher, T., Shaheen, S., Deakin, E. and Walker, J.L., 2023. Impact of the COVID-19 pandemic and generational heterogeneity on ecommerce shopping styles–A case study of Sacramento, California. Communications in Transportation Research, 3, p.100091.
Ehsani, F. and Hosseini, M., 2023. Consumer segmentation based on location and timing dimensions using big data from business-to-customer retailing marketplaces. Big Data.
Gupta, A., Country Wide E-Commerce Customer Segmentation and Analysis Using Multi Level Clustering. Available at SSRN 4505948.
Nakano, S., 2023. Customer demand concentration in online grocery retailing: Differences between online and physical store shopping baskets. Electronic Commerce Research and Applications, 62, p.101336.
Taherdoost, H. and Jalaliyoon, N., 2014. Marketing vs E-marketing. International Journal of Academic Research in Management, 3(4), pp.335-340.
Wong, E. and Wei, Y., 2018. Customer online shopping experience data analytics: Integrated customer segmentation and customised services prediction model. International Journal of Retail & Distribution Management, 46(4), pp.406-420.
Xanthopoulos, P., Pardalos, P.M., Trafalis, T.B., Xanthopoulos, P., Pardalos, P.M. and Trafalis, T.B., 2013. Linear discriminant analysis. Robust data mining, pp.27-33.
Christy, A.J., Umamakeswari, A., Priyatharsini, L. and Neyaa, A., 2021. RFM ranking–An effective approach to customer segmentation. Journal of King Saud University-Computer and Information Sciences, 33(10), pp.1251-1257
Sarvari, P.A., Ustundag, A. and Takci, H., 2016. Performance evaluation of different customer segmentation approaches based on RFM and demographics analysis. Kybernetes, 45(7), pp.1129-1157.
Aslantaş, G., Gençgül, M., Rumelli, M., Özsaraç, M. and BAKIRLI, G., 2023. Customer segmentation using K-means clustering algorithm and RFM model. Dokuz Eylül Üniversitesi Mühendislik Fakültesi Fen ve Mühendislik Dergisi, 25(74), pp.491-503.
OpenAI (2023) Introducing GPT-4. Available at: https://openai.com/blog/gpt-4 (Accessed: 8 March 2024).
Pynatih, N.M.N., Amrita, N.D.A. and Aripin, Z., 2024. FINANCIAL IMPACT OF BRAND STRATEGY: AN ANALYSIS OF KEY FINDINGS AND FUTURE RESEARCH PROSPECTS. KRIEZ ACADEMY: Journal of development and community service, 1(3), pp.33-46.
