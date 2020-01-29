# pandas-project
Data cleaning Shark attack database

import pandas as pd
import re
data = pd.read_csv('sharkattack.csv', engine = 'python')

These are my imports, I used pandas to wrangle and clean my database easier.

1. I analysed which columns were the ones that contained the greatest number of null values. Out of nearly 6000 rows I considered optimum to erase the columns that had more than 3000 null values (Unnamed.23, Unnamed.22 and TIme. 

2. Then I dropped the columns that I considered irrelevant for general analysis in order to make the database lighter.
I erased ['Name','Case Number','original order','Investigator or Source', 'pdf', 'href formula', 'href', 'Case Number.1', 'Case Number.2'] 

3. Then I realised that there where Countries with null values that coincide with not null Area and location values. So with a deeper analysis and google search we could find out the countries of most of the accidents (except 11 values). We could have a similar approach in the cases where we have null for Area but not null for location. 

4. To clean the fatal column I changed (' N' 'N ' 'n' 'F') to 'N' and the other unidentifiable values or null values to 'UNKNOWN'

5. Then I reordered the columns to have a better idea of the info in the database and renamed the columns to take out spaces that can lead to confusions. 'Species ' to 'Species' 'Sex ' to 'Sex'

6. Then I extracted the month out of the date column and created a new column named month with this info. Also I realised that there were several rows with  Year 0 value but they had the year in the Date column. I used regex to identify this situation and replaced those Year 0 with the new value from DATE. Like this we had around 15 rows without Year. 

7. I got rid of duplicated or nearly duplicated rows (when there were more than one victim in an accident) I grouped by country date type and area and created a new column with "Number of victims" so we can now know how many victims are normally attacked in one shark attack.

8. My intention and next step is to use regex to analyse non fatal accidents to now what body parts shark attack most. I wanted to extract key words from injuries column such as "leg, arm, thigh, hand, toes, fingers..."

9. I analysed the most common shark species that attack nearby the cost. 

10. Last I identified the season of each accident and created a new column with that info, but I didn't consider seasons depending on country/area (That was a next step)

11. I would have liked also to have cleaned and narrow the Activity column and Type column but couldn't because of lack of time.

Extraction 
data = data.to_csv("archive_name", sep='\t', index=False)

Conclusion: 
I have learned the importance of regex, how to extract info from one column in order to put it in other columns. I have also learned how to restrinct values per column, the less possible values there are, the better. 
