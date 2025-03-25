# Challenges-Of-Healthcare-Accessibility-In-Africa
This project analyzes healthcare facility data from selected afrcian communities, to identify disparities in access to healthcare between rural and urban regions, 
and evaluate the efficiency of healthcare funding. The analysis uses power BI (power query, Dax, visualizations) to genrate insights.
### Project Overview
This project aims to analyze the challenges of healthcare accessibilty in Africa, using data gathered from selected communities to:
- Identify key disparities in healthcare access between rural and urban regions.
- Analyze the efficiency of healthcare funding and resource allocation across different facilities.
- Provide data-driven insights to improve emergency response times and patient satisfaction.
- Develop strategic recommendations for policymakers to ensure equitable healthcare access.
- To communicate findings effectively using visualization techniques.
![rec](https://github.com/user-attachments/assets/96df4922-8f9f-4859-94b0-65b8f7a0c7ff)
### Dataset

The dataset used for this analysis is the [challenges of healthcare accessiblity in Africa ](https://github.com/timiols/Challenges-Of-Healthcare-Accessibility-In-Africa/blob/main/Healthcare_Access_Africa.csv) dataset consisting of 15 columns and 2001 rows.
### Tools
- **Power query**
- **Power Bi**
### Data Cleaning
The dataset was properly structured and didn’t require complex cleaning. However, the following steps were taken to improve the dataset.
- **Urban_rural_area** column was created to categorize the regions into their respective area type. To achieve this, the custom column function in power query was used, using data from *population* and *facility type* columns.
- **Funding per patient visit** column was created and added to the dataset using average function in Dax to derive average funding per patient visit. This was achieved using data from *funding received (USD)]*  and *annual Patient visits* columns.
- Measure was created using DAX  and added to the dataset to calculate the Pearson correlation coefficient between *funding received (USD)* and *emergency response time (minutes)* columns.
### Exploratory Data Analysis
- How does the distribution of healthcare facilities compare between rural and urban regions?

  ![Screenshot 2025-03-25 133652](https://github.com/user-attachments/assets/9a3007dd-8eae-427c-b8e7-336df6cb943c)
- Are urban healthcare facilities receiving more funding than rural ones?

   ![Screenshot 2025-03-25 133703](https://github.com/user-attachments/assets/c9fa1ddf-9def-45ee-8dc6-a99f97a0620f)
- Are healthcare facilities with higher funding more likely to have shorter emergency response times?

  ![Screenshot 2025-03-25 133722](https://github.com/user-attachments/assets/ba92d887-3f6a-4271-9f35-debf4a51b926)

- Which facility types (hospitals, clinics, health centres) show the highest efficiency in terms of funding per patient visit?

  ![Screenshot 2025-03-25 133734](https://github.com/user-attachments/assets/55ade1f7-0713-4bae-8b8b-dd562db7bb92)

 ### Data analysis
 


