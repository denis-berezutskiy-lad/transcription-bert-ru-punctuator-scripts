# About

This project contains scripts and configs for making a Russian punctuation/capitalization dataset based on transcriptions, training a BERT model on that dataset and performing some inference examples on the trained model.

An instance of already collected dataset is located here: https://huggingface.co/datasets/denis-berezutskiy-lad/ru_transcription_punctuation

An instance of already trained model in located here: https://huggingface.co/denis-berezutskiy-lad/lad_transcription_bert_ru_punctuator

The underlying base model is https://huggingface.co/DeepPavlov/rubert-base-cased-conversational

In order to train the model the set of NeMo scripts has to be used: https://github.com/NVIDIA/NeMo

Please note that the NeMo scripts revision was fcfc0ebb23b428a9bee6d847d1e0b37ca0784ba5 at the moment of training, and a later version may not be compatible with the required libraries (and vice versa).

Please also note that torchmetrics is not linked to the latest version, because that version is not compatible with the mentioned NeMo revision.

# Why one more punctuator

The idea behind the project is to use large continous professional transcriptions for training rather than relying on short low-quality samples consisting of 1-2 sentences (which is typical for the most popular datasets in Russian). Our experiments show significant improvements comparing to BERTs trained on the standard Ru datasets (social comments, omnia russica etc.). That's why we mainly use transcriptions published by Russian legislatures (Gosduma, Mosgorduma) with some addition of film subtitles from OpenSubtitles project.

# Supported labels

Please note that some new labels are not supported by NeMo scripts out of the box (-, —, T), so we need to add special handling for them. See the inference notebook for details.

## Punctuation

O
,
.
?
!
:
;
…
⁈
-
—

## Capitalization

O
U
T

(T means abbreviation ("total" uppercase))
