# SMALL-100 Fine-tune
#### English
This project is a fine-tuning of the SMALL-100 model to improve the ability to translate from English to Thai and from Thai to English.
In this repository will be the model after Fine-tune is completed with data from [scb-mt-en-th-2020](https://airesearch.in.th/releases/machine-translation-datasets/)

#### ภาษาไทย
โปรเจคนี้เป็นการ Fine-tuning ตัวโมเดล SMALL-100 ให้มีความสามารถที่มากขึ้นในการแปลภาษาจากภาษาอังกฤษเป็นภาษาไทย และจากภาษาไทยเป็นภาษาอังกฤษ
ใน repository นี้จะเป็นตัวโมเดลหลังจาก fine-tune เสร็จเรียบร้อยแล้วด้วยข้อมูลจาก [scb-mt-en-th-2020](https://airesearch.in.th/releases/machine-translation-datasets/)

## Installation
All detail in this document.

รายละเอียดทั้งหมดอยู่ในเอกสารฉบับนี้

[huggingface doc](https://huggingface.co/docs/transformers/installation) 

## Usage
```python
from transformers import M2M100ForConditionalGeneration
from tokenization_small100 import SMALL100Tokenizer

model = M2M100ForConditionalGeneration.from_pretrained("you/model/path")
tokenizer = M2M100Tokenizer.from_pretrained("you/model/path", tgt_lang="th") # th = Thai , en = English

text = "Life is like a box of chocolates."

encoded = tokenizer(text, return_tensors="pt")
generated_tokens = model.generate(**encoded)
translate = tokenizer.batch_decode(generated_tokens, skip_special_tokens=True) # output of translate
```
