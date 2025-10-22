# CrossNews-UA
CrossNews-UA: A Cross-lingual News Semantic Similarity Benchmark for Ukrainian, Polish, Russian, and English

## Requirements

To fully replicate the pipeline, you'll need the following accounts and API tokens:

- [Toloka Self-Service platform](https://toloka.ai/)
- [HuggingFace API token](https://huggingface.co/docs/api-inference/en/quicktour#get-your-api-token)
- [DeepL API token](https://developers.deepl.com/docs/getting-started/auth)
- [Cohere AI API token](https://docs.cohere.com/docs/chat-api)

## Files in this Repository

- **Sampling_based_on_SemEval.ipynb**: Initial pre-sampling of news pairs from the SemEval22 Task8 Challenge in Russian, English, and Polish.
- **Searching_for_news.ipynb**: Scraping news from Google News and summarizing them.
- **Acceptance_rejection_script.ipynb**: Automated LLM-based quality control for the crowdsourcing solution.
- **main_project_config.json**: Configuration file for the main crowdsourcing project.
- **crossnews-ua.cs**: the final dataset.

## Dataset Description

### Annotation Labels

- **label_1**: \
  &emsp; - **labeler**: An anonymized labeler (№X ∈ [1, 30]). \
  &emsp; - **who_same**: "Do the main characters in the news match?" (*yes* / *partly* / *no* / *incomparable*). \
  &emsp; - **when_same**: "Do the times of the events coincide?" (*yes* / *partly* / *no* / *incomparable*). \
  &emsp; - **where_same**: "Do the places where the events occur match?" (*yes* / *partly* / *no* / *incomparable*). \
  &emsp; - **what_same**: "How do news topics/events relate to each other?" (*similar* / *somewhat_related* / *different*). \
  &emsp; - **what_comment**: Labeler’s justification for their answer to the *what_same* question. \
  &emsp; - **what_comment_translated**: All comments are translated to Ukrainian via DeepL to maintain consistency. \
  &emsp; - **comment_is_good**: Whether the comment was evaluated as good by an LLM-based script or an expert (*True* / *False*). \
  &emsp; - **processed_automatically**: Whether the annotation was processed automatically via majority vote & LLM scripts, or manually by an expert (*True* / *False*). \
  &emsp; - **verdict**: Acceptance or rejection of the annotation (*+* / *-*). \
  &emsp; - **comment**: Reason for rejection if the annotation was rejected; otherwise, empty.

- **label_2**: Same as **label_1**. 
- **label_3**: Same as **label_1**.

### News Articles

- **text1**: Full text of the first news article, parsed by the Newspaper3k library. 
- **text2**: Full text of the second news article, parsed by the Newspaper3k library. 
- **source1**: Link to the source of the first news article. 
- **source2**: Link to the source of the second news article. 
- **url_lang1**: Language of the first news article (*uk* / *en* / *pl* / *ru*). 
- **url_lang2**: Language of the second news article (*uk* / *en* / *pl* / *ru*). 
- **language_of_pair**: Language pair of the news articles (*ukr-ukr* / *ukr-en* / *ukr-pl* / *ukr-ru*).

### Summarizations

- **summ_text1**: First summarization (using Command R) of the first news article. 
- **summ_text2**: First summarization (using Command R) of the second news article. 
- **summ_with_documents_text1**: Second summarization (Command R with "documents") of the first news article. 
- **summ_with_documents_text2**: Second summarization (Command R with "documents") of the second news article.

### Aggregated Labels

- **aggregated_who**: Majority vote answer to "Do the main characters in the news match?" (*yes* / *partly* / *no* / *incomparable* / *disagreement*). 
- **aggregated_where**: Majority vote answer to "Do the places where the events occur match?" (*yes* / *partly* / *no* / *incomparable* / *disagreement*). 
- **aggregated_when**: Majority vote answer to "Do the times of the events coincide?" (*yes* / *partly* / *no* / *incomparable* / *disagreement*). 
- **aggregated_what**: Majority vote answer to "How do news topics/events relate to each other?" (*similar* / *somewhat_related* / *different* / *disagreement*).
