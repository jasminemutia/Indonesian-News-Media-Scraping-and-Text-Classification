# Indonesian Media News Text Classification
This project involves scraping news articles from Indonesian media sources, such as Liputan6, Detik, and Kompas, and classifying them into categories such as Politics, Sports, and Entertainment. 
The goal is to create a labeled dataset and build a classification model that achieves high accuracy in categorizing news articles. 
Below are the key steps taken in this project, including data scraping, preprocessing, and model evaluation.

## Project Overview
### Data Collection and Scraping
Using Python libraries such as BeautifulSoup and Requests, news data is scraped from sources like Liputan6, Kompas, and Detik. 
Each article's title, URL, media source, and category label are gathered to create a structured dataset. This data is then stored in a DataFrame and exported as a CSV for further processing.

## Data Concatenation
Once data is collected from Liputan6, similar scraping functions are applied to Kompas and Detik. The scraped data from all sources is merged into a single DataFrame called df_mediaNews, resulting in 399 articles with columns URL, Title, Media Source, and Category Label.

## Data Preprocessing
- Lowercasing: All text is converted to lowercase to ensure uniformity.
- Removing Numbers and URLs: Numbers, URLs, and specific domain names are removed, as they do not contribute semantic value.
- Removing Special Characters: Special characters are stripped to focus on meaningful text content.
- Whitespace Normalization: Extra spaces and newlines are standardized.
- Tokenization and Stemming: Tokenization splits sentences into words, while stemming reduces words to their root forms for a more effective vocabulary.

## Text Representation
- Word2Vec (Skip-gram Model):
  
  A Word2Vec model is trained on the preprocessed text data using a skip-gram approach with the following parameters:
  - vector_size=50: Each word is represented by a 50-dimensional vector.
  - window=5: Considers a window of 5 words around the target word.
  - min_count=3: Ignores words that appear fewer than three times.
  - sg=1: Specifies the use of the skip-gram method.

- FastText
  
A FastText model is also trained on the data, with similar parameters to Word2Vec, except FastText captures subword information.

## Model Training
- SVM (Support Vector Machine)
  - An SVM classifier is trained using both Word2Vec and FastText vector representations.
  - For the Word2Vec representation, the model achieves an accuracy of 91%, with precision, recall, and F1-scores indicating high performance across categories.
  - With FastText, the SVM accuracy is slightly lower at 89%, though the performance across categories remains robust.
- Random Forest
  - A Random Forest classifier is also trained on both Word2Vec and FastText vector data.
  - Using the Word2Vec vectors, Random Forest achieves an accuracy of 94%, outperforming SVM. Similarly, FastText yields a strong performance with 93% accuracy.
 
## Conclusion
The Random Forest classifier with Word2Vec (Skip-gram) yields the highest accuracy (94%), followed closely by FastText (93%). The skip-gram approach proves effective for both SVM and Random Forest models, with Random Forest performing better overall.
