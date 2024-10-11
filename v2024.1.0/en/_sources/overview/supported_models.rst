.. _SupportedModels:

**********************************
Supported Models
**********************************

FuriosaAI Software Stack supports a variety of Transformer-based models in HuggingFace Hub.
The following is the list of model architectures that are currently supported by Furiosa SDK.
If your model is based on the following architectures,
you can use Furiosa SDK to compile, quantize, and run the model on FuriosaAI RNGD.

Decoder-only Models
====================================

.. list-table:: Decoder-only Models
   :align: center
   :header-rows: 1
   :widths: 130 120 300

   * - Architecture
     - Model Name
     - Example HuggingFace Models
   * - ``LlamaForCausalLM``
     - Llama 2, Llama 3.1
     - ``meta-llama/Llama-2-70b-hf``, ``meta-llama/Llama-3.1-70B``, ``meta-llama/Llama-3.1-70B-Instruct``, ``meta-llama/Llama-3.1-8B``, ``meta-llama/Llama-3.1-8B-Instruct``, ..
   * - ``GPTJForCausalLM``
     - GPT-J
     - ``EleutherAI/gpt-j-6b``


Encoder-only Models
====================================

.. list-table:: Encoder-only Models
   :align: center
   :header-rows: 1
   :widths: 130 120 300

   * - Architecture
     - Model Name
     - Example HuggingFace Models
   * - ``BertForQuestionAnswering``
     - Bert
     - ``google-bert/bert-large-uncased``, ``google-bert/bert-base-uncased``, ..


Model Support Roadmap
====================================

FuriosaAI is actively expanding the support for various models.
The following is the roadmap for the model support:

* 2024.2 (beta 0)
    *

