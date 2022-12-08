# Machine translation for songs (EN-TH)
 
## Introduction
<p>In the present day, Thai people enjoy listening to English songs due to their popularity. However, people are having trouble translating the songs from English to Thai because it requires more knowledge to understand some idioms and hidden meanings of the song. Furthermore, translations in some traditional ways take more time and are sometimes inaccurate so we would like to train Machine Translation that can perform song translation tasks from English to Thai that is much faster than in the traditional way. 

<p>There was some previous work that developed Machine Translation from English to Thai such as ParSit (Paisarn Charoenpornsawat Virach Sornlertlamvanich and Thatsanee Charoenporn,2003) , an English to Thai Machine Translation that uses a rule-based approach in order to perform the task, and SCB-Machine Translation which is a transformer model that trained to perform English to Thai and Thai to English translation task. Disadvantages that the two models have in common is the domain used in training the data. Both use general dataset to train so they would not perform songs translation well as the general dataset usually does not include idioms or any hidden meaning phrases.

<p>Transformer models have been explored and proved that they can perform many tasks well including Machine Translation. In this study, we will train transformer models to perform songs translation task. Subsequently, two transformer models have been chosen to do the task which are a transformer base model, Fairseq, and T5, a pre-trained transformer model which is good at many tasks especially for translation.

<p>T5, the pre-trained transformer model, provided a more accurate result than the vanilla transformer model, Fairseq in terms of BLEU score (chrF) due to the richness of its pre-trained data which increased the ability of the model to understand natural language.

## Approach/Methodology/Model
<p>Transformer is a Sequence-to-Sequence model that not only works effectively in many tasks like some Neural Network models but also the use of self attention made the model even more special because it calculates the amount of attention which word should get. Input that we need to prepare is one sentence of the English lyrics from the song that we want to perform the translation task on. However, the transformer model then tokenizes the input sentences and converts it into embedding so it contains some more meaning than the not embeddning version. Lastly, the machine translation will generate the prediction of the study in text  as output. Here we use the Fairseq transformer base model to train our machine translation.

<p>Furthermore, a pre-trained transformer model has been chosen to help improve the performance of Fairseq. T5 is a pre-trained transformer model which has been pre-trained before on an open-source pre-training dataset, called the Colossal Clean Crawled Corpus (C4).

## Dataset
<p>We use the lyrics and translations from <a href='https://www.aelitaxtranslate.com'>aelitatranslate</a>. The owner of this website is an English tutor. He also has a lot of experience in song translations since he has been active for more than 10 years. We have thoroughly checked the translations on the website and decided to use them as our data sets.

<p>Our data sets contain more than 280,000 sentences including English lyrics and translations in Thai. We cleaned the data by cutting out the punctuations and deleting some sentences that are in other languages. In tokenization, we used attacut to tokenize Thai sentences. After that, we split data sets into train sets, dev sets, and test sets. Train sets contain 284,951 sentences which are 99% of data sets. Dev sets contain 1,438 sentences and Test sets contain 860 sentences. We also deleted repeated lyrics in Test sets that have already appeared in Train sets and Dev sets.

## Experiment Setup
<p>Beside the plain transformer base model, Fairseq. T5, the pre-trained transformer model, has been chosen to help improve the performance of Fairseq. The model has been pre-trained before on an open-source pre-training dataset, called the Colossal Clean Crawled Corpus (C4). 

<p>We hypertuned the Fairseq model with dropout rate at 0.1, both encoder and decoder embedding dimension have been set at 256. The model was training for 10 epochs with learning rate at 5e-4 and batch size at 128. For the Fairseq model, it did not take as much time, just about an hour of training time.
<p>Otherwise, the T5 model took about 7 hours of training time with only one epoch. The pre-trained model has been set in default hyperparameter mode to be easily used. However, the default dropout rate is 0, the learning rate is 4e-5 and the batch size is 8.

## Results
<p>Both Transformer Base Model and T5 perform quite well. Our Transformer Base Model which receives no pre-training outperforms SCB MT. This might be because though SCB MT has larger data sets, their data contains general meaning sentences. While our data sets are contained within a specific domain. However, T5 achieves the highest scores among all of the models when measured by ChrF score. 

<p>After that, we decided to check some random translations from all models and find out that overall, Transformer Base Model translates better than T5. Transformer Base Model generates quite good grammatical sentences and can generate some accurate translations from idioms. T5 somehow generates not very good structural sentences when compared to Transformer Base Model because pre-trained data that was used to train T5 didn’t consist of Thai data. So it might not help the model generate good grammatical sentences in Thai. 
<p>However, when comparing SCB MT to other models, SCB MT generates only general sentences with no hidden meaning. This might be because as we said earlier, their data sets contain general topic sentences.
 
## Model Comparison
| Model | Accuracy |
|-----------| ----------|
|SCB-MT |25.38|
| Fairseq | 39.38|
| **T5** | **39.76** |

### Example Sentences
| English Lyrics |We 40 deep in the lobby.|
|-----------| ----------|
| Gold |เพราะเรามากัน 40 คนในล็อบบี้|
| Fairseq |เราดื่มเหล้ากันในล็อบบี้|
| T5 |เราอยู่ในล็อบบี้|
| SCB-MT |พวกเรา 40 ลึกลงไปในล็อบบี้|
 
| English Lyrics | I do not need no ladder because I stand tall. |
|-----------| ----------|
| Gold |ไม่ต้องการบันไดหรอกเพราะฉันยืนหยัดด้วยตัวเองได้|
| Fairseq |ฉันไม่ต้องการบันไดเพราะฉันยืนหยัดต่อสู้|
| T5 |ฉันไม่ต้องการบันไดเพราะฉันยืนอยู่สูง|
| SCB-MT |ฉันไม่ต้องการบันไดเพราะฉันยืนสูง|
 

| English Lyrics | She said “In honesty he was not fly when I met him”. |
|-----------| ----------|
| Gold |เธอบอกว่า“จริงๆนะตอนฉันเจอเขาเนี่ยไม่เห็นดูดีเลย”|
| Fairseq |เธอบอกว่า“เขาไม่ได้ซื่อสัตย์เลยตอนที่ฉันได้เจอเขา”|
| T5 |เธอบอกว่า”จริงใจนะเขาไม่โบยบิน|
| SCB-MT |หล่อนบอก”ความซื่อสัตย์สุจริตเขาไม่บินเมื่อฉันเจอซาก|
 
## Conclusion
<p>To conclude, the performance of the two transformer models in English to Thai song translations task are quite impressive. 
<p>Overall, Both Transformer Base Model and T5 can generate quite good sentences. They also have better scores when compared to SCB MT. In contrast, while T5 achieves the highest scores when measured by ChrF score, Transformer Base Model still generates more accurate meaning than T5 in the sense of translations. This might be because Transformer Base Model was trained with specific domain data sets so it can be flexible when generating sentences that contain hidden meanings.  However, our models still make some mistakes. They still can’t translate some idioms correctly and they still don’t understand many hidden meanings in lyrics. 

<p>Furthermore, our models have a high possibility of mistranslation when faced with long sentences. But this is a good start and we believe our models can be improved and developed in the future.

