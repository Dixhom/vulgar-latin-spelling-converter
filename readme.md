# Vulgar Latin spelling converter

This project aims to convert Vulgar Latin words into their corresponding Italian counterparts without the use of a dictionary. Given that Italian is a direct descendant of Vulgar Latin, there should be a pattern that governs how words from the former language evolve into the latter. To achieve this, we trained a Natural Language Processing (NLP) model called Transformer to learn the relationship between Vulgar Latin and Italian spellings. By doing so, the model is capable of accurately converting a Vulgar Latin word into its corresponding Italian word without relying on any external sources.

# Dataset

The dataset was taken from a Swadesh list of Romance languages.  
https://en.wiktionary.org/wiki/Appendix:Romance_Swadesh_lists

Swadesh lists are word lists of body parts, verbs, natural phenomena, in order to compute the relationships of languages. Romance languages are a group of languages that evolved from Vulgar Latin, the common language spoken by the Romans. From this list, we picked up pairs of corresponding words from different languages. We chose Vulgar Latin and Italian because the latter is considered to be closest to the former among the other Romance languages.

![image](https://user-images.githubusercontent.com/7886660/230810783-59e59363-f262-42ec-9123-6c5eb058cc86.png)

I searched for cognate words from the Swadesh list, but for words that were clearly not cognates, I checked their etymology on Wiktionary. Since the Vulgar Latin words on the Swadesh list included those with different grammatical cases, I sometimes got confused along the way, but I tried to match them as closely as possible.

All the non-ascii characters in the words were replaced with the ascii ones.

Below are example records. The number of records is 803.

| italian      | vulgar_latin |
| ------------ | ------------ |
| abbacchiare  | abbaclare    |
| abbattere    | abbatto      |
| abbeverare   | abbiberare   |
| abbracciare  | adbracchiare |
| abbrustolire | brustulare   |

# Training

## Parameters

- BATCH_SIZE = 64
- num_layers = 4
- d_model = 128
- dff = 512
- num_heads = 8
- dropout_rate = 0.1
- N_EPOCHS = 80

# Evaluation

The 10 records unseen by the training data are used for evaluation. Here is the result.

| input          | prediction | ground_truth |
| -------------- | ---------- | ------------ |
| lusciniolus    | loscinolo  | lusignolo    |
| jeniperus      | genvero    | ginepro      |
| artefacto      | arteffare  | artefatto    |
| speclum        | specchio   | specchio     |
| torsus         | torso      | trozza       |
| tiro           | tiro       | tirare       |
| manum gemellam | manoglio   | giumella     |
| exseperare     | sceverare  | sceverare    |
| stantia        | stanza     | stanza       |
| vela           | vela       | vela         |

For 4 out of 10 words, the prediction was correct.

# Conclusion

A NLP model was built to convert Vulgar Latin words to an Italian counterparts. For 4 out of 10 words, the prediction was correct.
