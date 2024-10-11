.. _OpenAIServer:

****************************************************
OpenAI Compatible Server
****************************************************

The ``furiosa-llm`` package includes an OpenAI-compatible server
that can interact with OpenAI clients (and, of course, HTTP clients as well),
supporting the ``/v1/chat/completions`` and ``/v1/completions`` APIs.
In this section, we will explain how to launch the OpenAI-compatible `furiosa-llm` server.

.. tip::

    You can learn more about the OpenAI API at `Completions API <https://platform.openai.com/docs/api-reference/completions>`_
    and `Chat API <https://platform.openai.com/docs/api-reference/chat>`_.

To launch the server, you must prepare: (1) the FuriosaAI LLM Engine artifact and
(2) a chat template for the model. To download the FuriosaAI LLM Engine artifact,
follow the instructions provided through our distribution channels or contact our sales team.
To prepare the chat template, follow the instructions in the following section.

.. warning::

   This document is based on Furiosa SDK 2024.1.0 (alpha) version,
   and the features and APIs described in this document may change in the future.


Preparing Chat Templates
================================================

Furiosa SDK 2024.1.0 (alpha) uses Transformers v4.31.0, which does not support a chat template.
Therefore, to support ``/v1/chat/completions``,
you need to specify your own chat template based on jinja2 template format.

The chat template is a text file that contains the template for the chat prompt.
`Llama-3.1-Instruct.tpl <https://gist.githubusercontent.com/hyunsik/16f1906af7ac2b4db41af9957a66e168/raw/62935b0c24c03669208cf90f3f87b1694521053d/Llama-3.1-Instruct.tpl>`_
is an chat template example for Llama 3.1 Instruct model.

.. note::

    In 2024.2 release, Furiosa LLM will support the chat template and ``chat()`` API
    to support the chat models seamlessly.


Launching the Server
================================================
You can launch the server using the ``furiosa-llm serve`` command
with an artifact path. The following is the command to launch the server:

.. code-block::

    furiosa-llm serve \
    --model {artifact path}

Also, you can specify the chat template path as follows:

.. code-block::

    furiosa-llm serve \
    --model {artifact path}
    --chat-template {chat template path}


By default, the server binds to ``localhost:8000``, and
you can change the host and port using the ``--host`` and ``--port`` options.

The following is the list of options and arguments for the serve command:


.. code-block::

    usage: furiosa-llm serve [-h] --model MODEL [--host HOST] [--port PORT] --chat-template CHAT_TEMPLATE [--response-role RESPONSE_ROLE] [-tp TENSOR_PARALLEL_SIZE] [-pp PIPELINE_PARALLEL_SIZE] [-dp DATA_PARALLEL_SIZE] [--devices DEVICES]

    options:
    -h, --help            show this help message and exit
    --model MODEL         The Hugging Face model id, or path to Furiosa model artifact. Currently only one model is supported per server.
    --host HOST           Host to bind the server to
    --port PORT           Port to bind the server to
    --chat-template CHAT_TEMPLATE
                            Path to chat template file (must be a jinja2 template)
    --response-role RESPONSE_ROLE
                            Response role for /v1/chat/completions API (default: 'assistant')
    -tp TENSOR_PARALLEL_SIZE, --tensor-parallel-size TENSOR_PARALLEL_SIZE
                            Number of tensor parallel replicas. (default: 4)
    -pp PIPELINE_PARALLEL_SIZE, --pipeline-parallel-size PIPELINE_PARALLEL_SIZE
                            Number of pipeline stages. (default: 1)
    -dp DATA_PARALLEL_SIZE, --data-parallel-size DATA_PARALLEL_SIZE
                            Data parallelism size. If not given, it will be inferred from total avaialble PEs and other parallelism degrees.
    --devices DEVICES     Devices to use (e.g. "npu:0:*,npu:1:*"). If unspecified, all available devices from the host will be used.


Using OpenAI API with Furiosa LLM
=====================================================
Once the server is launched, you can interact with the server using HTTP clients and
OpenAI API clients.

You can simply test the server using the following curl command:

.. code-block:: sh

    curl http://localhost:8000/v1/chat/completions \
        -H "Content-Type: application/json" \
        -d '{
        "model": "EMPTY",
        "messages": [{"role": "user", "content": "Say this is a test!"}]
        }' | python -m json.tool


You can also openai client to interact with the server.
To use openai client, you need to install the openai package.

.. code-block:: sh

    pip install openai


OpenAI provides two APIs: ``client.chat.completions`` and ``client.completions``.
If you want to receive a streaming response, you can use the ``client.chat.completions``
API with ``stream=True``. The example is as following:

.. code-block::

    from openai import OpenAI

    # Replace the following with your base URL
    base_url = f"http://localhost:8000/v1"
    api_key = "EMPTY"

    client = OpenAI(api_key=api_key,base_url=base_url)

    stream = client.chat.completions.create(
        model="EMPTY",
        messages=[{"role": "user", "content": "Say this is a test"}],
        stream=True,
    )

    for chunk in stream:
        if chunk.choices[0].delta.content is not None:
            print(chunk.choices[0].delta.content, end="")


The compatibility with OpenAI API
=================================================

Currently, ``furiosa serve`` supports the following OpenAI API parameters:
You can find more about each parameter at `Completions API <https://platform.openai.com/docs/api-reference/completions>`_
and `Chat API <https://platform.openai.com/docs/api-reference/chat>`_.

.. warning::

    Please note that using ``use_beam_search`` with ``stream`` is not allowed
    because the beam search cannot determine the tokens until the end of the sequence.

    In 2024.1 release, ``n`` works only for beam search and it will be fixed in the next release.

* ``n``
* ``temperature``
* ``top_p``
* ``top_k``
* ``early_stopping``
* ``length_penalty``
* ``max_tokens``
* ``min_tokens``
* ``use_beam_search``
* ``best_of``

Launching the OpenAI-Compatible Server Container
================================================================

Furiosa LLM can be launched immedaitely as a containerized server.

.. code-block::

    # Download the chat template for LLama 3.1 Instruct Model if necessary
    wget https://gist.githubusercontent.com/hyunsik/16f1906af7ac2b4db41af9957a66e168/raw/62935b0c24c03669208cf90f3f87b1694521053d/Llama-3.1-Instruct.tpl

    docker run -it --rm --privileged \
        --env HF_TOKEN=$HF_TOKEN \
        -v ./Llama-3.1-8B-Instruct:/model \
        -v ./Llama-3.1-Instruct.tpl:/Llama-3.1-Instruct.tpl \
        -p 8000:8000 \
        furiosaai/furiosa-llm:2024.1.0 \
        serve --model /model --chat-template /Llama-3.1-Instruct.tpl
