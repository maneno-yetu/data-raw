# Maneno Yetu Dataset

This datasheet follows the [Datasheets for Datasets](https://arxiv.org/abs/1803.09010) framework proposed by Gebru et al. (2018) to provide transparent documentation for the **Maneno Yetu** corpus — a large-scale, dynamic Swahili-language dataset created to support foundational and applied research in Natural Language Processing (NLP). The goal of this document is to help dataset users understand its origins, composition, intended uses, limitations, and ethical considerations. This README is designed to support reproducible research and promote responsible, community-centered development in African language technologies.

## 1. Motivation

**For what purpose was the dataset created?**  
The Maneno Yetu corpus was created to address the lack of large-scale, diverse, and openly available Swahili language datasets suitable for foundational NLP tasks. It supports the development of transformer-based models like SLFM and enables both practical applications and theoretical linguistic analysis.

**Who created the dataset?**  
The dataset was created by researchers affiliated with the University of Dar es Salaam (Tanzania) and Hanyang University (South Korea):
- Chaddy Anthony Zawuya  
- Alfred Malengo Kondoro
- Diana Rwegasira  
- Juma H. Lungo

**What—if any—licenses apply to the dataset?**  
The dataset is released under an open license and is publicly available via GitHub:  
[https://github.com/maneno-yetu/data-raw](https://github.com/maneno-yetu/data-raw)

**What tasks or research does it support?**  
It supports a wide range of tasks:
- Language modeling  
- Part-of-speech tagging  
- Sentiment and emotion classification  
- Named entity recognition  
- Abusive language detection  
- Longitudinal linguistic analysis

**Has it been used in previous work or publications?**  
The dataset was used to train and evaluate the Swahili Language Foundational Model (SLFM), described and benchmarked in a paper presented at CIKM 2025.

## 2. Composition

**What does each instance represent?**  
Each instance consists of a Swahili-language text unit, such as a sentence or paragraph, sourced from public news articles, blogs, literary works, educational resources, or government reports. These instances capture a range of registers from formal to informal discourse.

**What is the total size of the dataset?**

- **Before deduplication:** ~583 million tokens  
- **After deduplication:** ~276 million tokens  
- **Unique tokens:** ~1.6 million  
- **File size:** 1.68 GB (after cleaning and compression)

**What data fields are present?**  
The dataset contains at minimum the following:
- `text`: the raw Swahili content  
- Additional metadata fields may include domain or source information (e.g., blog, news site), though this is not always consistent.

**Is any information missing or obscured?**  
No essential data is intentionally removed or anonymized at this stage. However, some metadata (e.g., timestamps or source URLs) may be missing depending on the original structure of the scraped content.

**Is there a label taxonomy?**  
Not in the core corpus. However, derived benchmark datasets fine-tuned on top of the corpus include annotated labels for:
- Sentiment classification (positive, negative)
- Emotion categories
- Abusive or toxic language

**Does the dataset contain sensitive information?**  
Since the corpus was built using automated web crawling of public online content, it may contain unintended sensitive or harmful material. While language identification filters (based on fastText) were applied to retain only Swahili content, and crawling was done in compliance with `robots.txt` and domain-level policies, the nature of web-based content introduces ethical risks.

As the authors, we acknowledge that building a large-scale, web-based corpus raises valid concerns regarding privacy, intellectual property, and the inadvertent inclusion of sensitive material. Although we took steps to adhere to ethical data collection standards, we plan to strengthen future updates through stricter data governance, more transparent sourcing guidelines, and improved anonymization techniques to support responsible and community-safe use of the dataset.

## 3. Collection Process

**How was the data collected?**  
We developed a custom web crawler to collect Swahili text from targeted public domains such as news sites, blogs, educational platforms, and literary archives. The crawler adhered to ethical standards via `robots.txt` compliance. To ensure language purity, we applied fastText-based language identification filters to retain only Swahili content.

**Over what time period was the data collected?**  
The initial version of the dataset was collected over the past year. However, since Maneno Yetu is a dynamic corpus, it is designed to be periodically updated as new data becomes available.

**Was the data collected with informed consent?**  
The dataset consists entirely of publicly accessible online content collected using automated tools that respect domain-level access policies. No direct human subject data or participant-provided input was involved.

**If data was sampled, how was this done?**  
Sampling was not used. Instead, we collected a broad set of Swahili content and used deduplication and content filtering techniques to maximize quality and diversity.

**Was the data verified or validated?**  
Yes. We used automated processes to clean and validate the dataset. This included removing HTML artifacts, de-duplicating similar content using MinHash and TF-IDF similarity, and applying Swahili-specific tokenization and POS tagging for downstream compatibility.

## 4. Preprocessing and Cleaning

**Was any preprocessing done?**  
Yes. The pipeline included the following steps:
- HTML tag and script removal  
- Language filtering using fastText  
- Near-duplicate removal  
- Swahili-specific tokenization  
- Part-of-speech tagging using fine-tuned spaCy models for low-resource Bantu languages

**Were duplicate entries removed?**  
Yes. Near-duplicate documents were removed using MinHash and cosine similarity over TF-IDF vectors to ensure lexical diversity.

**Was data balanced (e.g., for classification)?**  
No. The raw corpus was not balanced across specific classes or categories. It is intended to reflect a broad and natural distribution of Swahili usage across domains.

**If so, how was balance ensured?**  
Not applicable to the raw corpus. Balance is considered only during downstream fine-tuning on task-specific labeled datasets.

## 5. Uses

**What are the intended uses of the dataset?**  
- Pretraining Swahili NLP models  
- Linguistic and sociolinguistic analysis  
- Benchmark creation for low-resource language tasks  
- Multimodal and contrastive sentiment analysis  
- Toxicity detection on social platforms

**What are out-of-scope or discouraged uses?**  
- Use in commercial systems without proper attribution  
- Applications that ignore ethical guidelines or propagate harmful stereotypes

**Are there any known failure cases or biases?**  
Yes. Since the dataset is web-scraped, it may contain noisy or biased content. Topical imbalance is also noted, particularly overrepresented domains.

**Are there benchmark tasks or metrics associated with it?**  
Yes. The dataset supports evaluation on multiple downstream tasks:
- Sentiment classification (F1: 87.7%)  
- Emotion classification (F1: 86.6%)  
- Abusive language detection (F1: 96.4%)


## 6. Distribution

**How is the dataset distributed?**  
The dataset is publicly available on GitHub:  
[https://github.com/maneno-yetu/data-raw](https://github.com/maneno-yetu/data-raw)

**What format is the data in?**  
- Plain text (`.txt`) and JSON for the raw corpus  
- CSV/TSV formats for labeled benchmark datasets

**Is access restricted?**  
No. The dataset is openly accessible to the public.

**Under what license is it released?**  
The dataset is released under an open license for academic and research use, in accordance with ACM publication guidelines.

## 7. Maintenance

**Will the dataset be updated or maintained over time?**  
Yes. The dataset is designed to be periodically updated through an automated and extensible pipeline, ensuring continued relevance as new Swahili-language data becomes available.

**Who is the contact person or team for questions or issues?**  
For inquiries or support, please contact the corresponding author:  
**Chaddy Zawuya** - `zawuya@gmail.com`
**Alfred Malengo Kondoro** – `alfr3do@hanyang.ac.kr`

**Are updates versioned?**  
Yes. Version control and changelogs are managed through GitHub to ensure transparency in dataset updates and modifications.

**Is there a changelog?**  
Yes. A changelog is maintained on the GitHub repository alongside each dataset release to track additions, improvements, and structural changes.
