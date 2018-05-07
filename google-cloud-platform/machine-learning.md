# Machine Learning

## Cloud Machine Learning (ML) Engine

* massively scalable managed service for training ML models & making predictions
* enables apps/devs to use tensorflow on datasets of any size
* integrates with GCS/BQ (storage), cloud datalab (dev), cloud dataflow (preprocessing)
* supports online & batch predictions, prioritizing latency (online) & job time (batch)
* or download models and make predictions anywhere; desktop, mobile, own servers
* hypertune - automatically tunes model hyperparameters to avoid manual tweaking
* training: pay per hour depending on chosen cluster capabilities (ML training units)
* prediciton: pay per provisioned node-hours + by prediction request volume

## Cloud Vision API

* classifies images into categories, detects objects/faces, & finds/reads printed text
* pretrained ML model to analyze images and discover contents
* upload images or point to ones stored in GCS 
* Pay per image, based on detection features requested
    * higher priced for OCR or full documents and finding similar images on the web
    * priced together: labels + SafeSearch, ImgProps + Cropping
    * other features priced individually: text, faces, landmarks, logos

## Cloud Speech API

* Automatic Speech Recognition (ASR) to turn spoken word audio files into text
* pretrained ML model for recognizing speech in 110+ languages/variants
* accepts pre-recorded or real-time audio & stream results back in real-time
* handles noisy source audio
* optionally filters inappropriate content in some languages
* accepts contextual hints: words and names that will likely be spoken
* pay for every 15 seconds of audio processed

## Cloud Natural Language API

* analyzes text for sentiment, intent & content classification, and extracts info
* pre-trained ML model for understanding what text means, so you can act on it
* syntax analysis extracts tokens/sentences, parts of speech & dependency trees
* entity analysis finds people, places, things and label them and link to wikipedia
* analysis for sentiment (overall) and entity sentiment detect (+/-) feelings and strength
* content classification puts each document into one of 700+ predefined categories
* charged per request of 1000 chars

## Cloud Translation API

* translate text between 100+ languages; optionally auto detects source languages
* pre-trained ML model for recognizing and translating semantics, not just syntax
* send plain text or HTML and receive translation in place
* pay per character processed for translation
* pay per character for auto detect

## Dialog Flow

* build conversational interfaces for websites, mobile apps, messaging
* pretrained ML model and service for accepting, parsing, lexing input and responding
* train to indentify custom entity types by providing a small dataset of examples
* free plan has unlimited text interactions and capped voice interactions
* paid plan is unlimited but charges per request: more for voice, less for text

## Cloud Video Intelligence API

* annotates videos in GCS (or directly uploaded) with info about what they contain
* enables search a video catalog the same way we search text documents
* specify a region where processing will take place (for regulatory compliance)
* label detection
* shot change detection
* safesearch detection
* pay per minute of video processed

## Cloud Job Discovery

* helps career sites, company job boards to engagement and conversion
* pre-trained ML model to help job seekers search job posting databases
* integrates with many job/hiring systems
* lots of features, such as commute distance and recognizing abbreviations/jargon

## Prediction API
* deprecated (gone)
* replaced with Cloud ML Engine