.. _WhatsNew:

***************
What's New
***************

.. contents:: Table of Contents
  :depth: 1
  :local:
  :backlinks: none


.. _Release2024_2_1:

Furiosa SDK 2024.2.1 Beta0 (2024-01-10)
==============================================

2024.2.1 is the minor release based on 2024.2.0 major release.
This release includes a couple of feature improvements, and 32k context length support in models,
such as LLaMA 3.1, EXAONE.

.. _Release2024_2_1_Highlights:

Highlights
----------------------
* 32k context length support in furiosa-llm for various models, such as LLaMA 3.1, EXAONE
* Artifacts with the same ``tensor_parallelism_size`` is compatible even with any ``pipeline_parallel_size``


.. list-table:: Component version
   :widths: 200 50
   :header-rows: 1

   * - Package name
     - Version
   * - furiosa-compiler
     - 2024.2.0
   * - furiosa-driver-rngd
     - 2024.2.0
   * - furiosa-driver-rngd
     - 2024.2.0
   * - furiosa-firmware-tools-rngd
     - 2024.2.0
   * - furiosa-firmware-image-rngd
     - 2024.2.0
   * - furiosa-pert-rngd
     - 2024.2.1
   * - furiosa-model-compressor
     - 2024.2.0
   * - furiosa-llm
     - 2024.2.1
   * - furiosa-llm-models
     - 2024.2.0
   * - furiosa-mlperf
     - 2024.2.1
   * - furiosa-mlperf-resources
     - 4.1.0
   * - furiosa-native-compiler
     - 2024.2.0
   * - furiosa-native-runtime
     - 2024.2.1
   * - furiosa-feature-discovery
     - 2024.2.0
   * - furiosa-device-plugin
     - 2024.2.0
   * - furiosa-smi
     - 2024.2.0
   * - furiosa-libsmi
     - 2024.2.0

.. raw:: html

   <hr>

.. _Release2024_2_0:

Furiosa SDK 2024.2.0 Beta0 (2024-12-23)
==============================================

2024.2.0 is the second major SDK release for RNGD. This release is beta 0 release,
and the features and APIs described in this document may change in the future.

.. _Release2024_2_0_Highlights:

Highlights
----------------------
* New Model support: Solar, EXAONE-3.0, CodeLLaMA2, Vicuna, ...
* 8k context length support in models, such as LLaMA 3.1
* Tensor Parallelism support (``tensor_parallel_size <= 8``)
* Torch 2.4.1 support
* Transformers 4.44.2 support
* Furiosa LLM
    * ArtifactBuilder API and CLI tools (refer to :ref:`ArtifactBuilder`)
        * Users can build artifacts from Huggingface Hub models with Huggingface Transformers compatible API
    * Huggingface Transformers compatible API support (`furiosa_llm.optimum`)
        * AutoModel, AutoModelForCausalLM, AutoModelForQuestionAnswering API
        * QuantizerForCausalLM API support for calibration and quantization
    * LLMEngine, AsyncLLMEngine API support compatiable with vLLM
* About 20% performance improvements in LLaMA 3.1 models
    * e.g., 3580 tokens/sec in LLaMA 3.1 8B model with a single RNGD card

.. list-table:: Component version
   :widths: 200 50
   :header-rows: 1

   * - Package name
     - Version
   * - furiosa-compiler
     - 2024.2.0
   * - furiosa-driver-rngd
     - 2024.2.0
   * - furiosa-firmware-tools-rngd
     - 2024.2.0
   * - furiosa-firmware-image-rngd
     - 2024.2.0
   * - furiosa-pert-rngd
     - 2024.2.0
   * - furiosa-llm
     - 2024.2.0
   * - furiosa-llm-models
     - 2024.2.0
   * - furiosa-mlperf
     - 2024.2.0
   * - furiosa-mlperf-resources
     - 4.1.0
   * - furiosa-model-compressor
     - 2024.2.0
   * - furiosa-native-compiler
     - 2024.2.0
   * - furiosa-native-runtime
     - 2024.2.0
   * - furiosa-smi
     - 2024.2.0
   * - furiosa-libsmi
     - 2024.2.0
   * - furiosa-device-plugin
     - 2024.2.0
   * - furiosa-feature-discovery
     - 2024.2.0

.. _Release2024_1_0:

.. raw:: html

   <hr>

Furiosa SDK 2024.1.0 Alpha (2024-10-11)
==============================================

2024.1.0 is the first SDK release for RNGD. This release is alpha release,
and the features and APIs described in this document may change in the future.

.. _Release2024_1_0_Highlights:

Highlights
------------------------
* Model Support: LLaMA 3.1 8B/70B, BERT Large, GPT-J 6B
* Furiosa Quantizer supports the following quantization methods:
    * BF16 (W16A16)
    * INT8 Weight-Only (W8A16)
    * FP8 (W8A8)
    * INT8 SmoothQuant (W8A8)
* Furiosa LLM
    * Efficient KV cache management with PagedAttention
    * Continuous batching support in serving
    * OpenAI-compatible API server
    * Greedy search and beam search
    * Pipeline Parallelism and Data Parallelism across multiple NPUs
* ``furiosa-mlperf`` command
    * Server and Offline scenarios
    * BERT, GPT-J, LLaMA 3.1 benchmarks
* System Management Interface
    * System Management Interface Library and CLI for Furiosa NPU family
* Cloud Native Toolkit
    * Kubernetes integration for managing and monitoring the Furiosa NPU family


.. list-table:: Component version
   :widths: 200 50
   :header-rows: 1

   * - Package name
     - Version
   * - furiosa-compiler
     - 2024.2.0
   * - furiosa-device-plugin
     - 2024.2.0
   * - furiosa-driver-rngd
     - 2024.2.0
   * - furiosa-feature-discovery
     - 2024.1.0
   * - furiosa-firmware-tools-rngd
     - 2024.1.0
   * - furiosa-firmware-image-rngd
     - 2024.1.0
   * - furiosa-libsmi
     - 2024.2.0
   * - furiosa-llm
     - 2024.2.0
   * - furiosa-llm-models
     - 2024.2.0
   * - furiosa-mlperf
     - 2024.2.0
   * - furiosa-mlperf-resources
     - 4.1.0
   * - furiosa-model-compressor
     - 2024.1.0
   * - furiosa-native-compiler
     - 2024.2.0
   * - furiosa-native-runtime
     - 2024.2.0
   * - furiosa-smi
     - 2024.1.0

