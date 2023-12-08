---
layout: model
title: Turkish bert_qa_loodos_bert_base_uncased_qa_fine_tuned BertForQuestionAnswering from oguzhanolm
author: John Snow Labs
name: bert_qa_loodos_bert_base_uncased_qa_fine_tuned
date: 2023-11-15
tags: [bert, tr, open_source, question_answering, onnx]
task: Question Answering
language: tr
edition: Spark NLP 5.2.0
spark_version: 3.0
supported: true
engine: onnx
annotator: BertForQuestionAnswering
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BertForQuestionAnswering model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP.`bert_qa_loodos_bert_base_uncased_qa_fine_tuned` is a Turkish model originally trained by oguzhanolm.

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/bert_qa_loodos_bert_base_uncased_qa_fine_tuned_tr_5.2.0_3.0_1700008767611.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/bert_qa_loodos_bert_base_uncased_qa_fine_tuned_tr_5.2.0_3.0_1700008767611.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python


document_assembler = MultiDocumentAssembler() \
    .setInputCol(["question", "context"]) \
    .setOutputCol(["document_question", "document_context"])
    
    
spanClassifier = BertForQuestionAnswering.pretrained("bert_qa_loodos_bert_base_uncased_qa_fine_tuned","tr") \
            .setInputCols(["document_question","document_context"]) \
            .setOutputCol("answer")

pipeline = Pipeline().setStages([document_assembler, spanClassifier])

pipelineModel = pipeline.fit(data)

pipelineDF = pipelineModel.transform(data)

```
```scala


val document_assembler = new MultiDocumentAssembler()
    .setInputCol(Array("question", "context")) 
    .setOutputCol(Array("document_question", "document_context"))
    
val spanClassifier = BertForQuestionAnswering  
    .pretrained("bert_qa_loodos_bert_base_uncased_qa_fine_tuned", "tr")
    .setInputCols(Array("document_question","document_context")) 
    .setOutputCol("answer") 

val pipeline = new Pipeline().setStages(Array(document_assembler, spanClassifier))

val pipelineModel = pipeline.fit(data)

val pipelineDF = pipelineModel.transform(data)


```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|bert_qa_loodos_bert_base_uncased_qa_fine_tuned|
|Compatibility:|Spark NLP 5.2.0+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[sentence, token]|
|Output Labels:|[embeddings]|
|Language:|tr|
|Size:|412.0 MB|
|Case sensitive:|false|
|Max sentence length:|512|

## References

https://huggingface.co/oguzhanolm/loodos-bert-base-uncased-QA-fine-tuned