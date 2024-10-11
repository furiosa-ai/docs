****************************************************
FuriosaAI Developer Center
****************************************************

Welcome to the FuriosaAI Developer Center.
FuriosaAI provides an streamlined software stack for deep learning model inference on FuriosaAI NPUs.
This document provides a guide to easily perform the entire workflow of writing inference applications,
from starting with PyTorch model to model quantization, serving, and production deployment.

.. warning::

   This document is based on Furiosa SDK 2024.1.0 (alpha) version,
   and the features and APIs described in this document may change in the future.


Overview
-------------------------------------------------
* :ref:`RNGD`: RNGD Hardware Specification, and features
* :ref:`SoftwareStack`: An overview of the FuriosaAI software stack
* :ref:`SupportedModels`: A list of supported models
* :ref:`WhatsNew`: New features and changes in the latest release
* :ref:`RoadMap`: The future roadmap of FuriosaAI Software Stack

Getting Started
-------------------------------------------------
* :ref:`InstallingPrerequisites`: How to install the prerequisites for FuriosaAI Software Stack
* :ref:`GettingStartedFuriosaLLM`
* :ref:`GettingStartedFuriosaMLPerf`

Cloud Native Toolkit
-------------------------------------------------
* :ref:`CloudNativeToolkit`: An overview of the Cloud Native Toolkit
* :ref:`Kubernetes`: An overview of the Kubernetes Support

Device Management
-------------------------------------------------
* :ref:`FuriosaSMI`: A command line utility for managing FuriosaAI NPUs

Customer Support
--------------------------------------------------
* `FuriosaAI Homepage <https://furiosa.ai>`_
* `FuriosaAI Forum <https://furiosa-ai.discourse.group/>`_
* `FuriosaAI Customer Portal <https://furiosa-ai.atlassian.net/servicedesk/customer/portals/>`_
* `FuriosaAI Warboy SDK Document <https://furiosa-ai.github.io/docs/latest/en/>`_


.. toctree::
   :maxdepth: 1
   :hidden:
   :caption: Overview

   /overview/rngd
   /overview/software_stack
   /overview/supported_models
   /whatsnew/index
   /overview/roadmap


.. toctree::
   :maxdepth: 1
   :hidden:
   :caption: Getting Started

   /getting_started/prerequisites
   /getting_started/furiosa_llm
   /getting_started/furiosa_mlperf

.. toctree::
   :maxdepth: 1
   :hidden:
   :caption: Furiosa LLM

   /furiosa_llm/intro
   /furiosa_llm/furiosa-llm-serve
   /furiosa_llm/references

.. toctree::
   :maxdepth: 1
   :hidden:
   :caption: Cloud Native Toolkit

   /cloud_native_toolkit/intro
   /cloud_native_toolkit/kubernetes

.. toctree::
   :maxdepth: 1
   :hidden:
   :caption: Device Management

   /device_management/furiosa_smi


.. toctree::
   :maxdepth: 1
   :hidden:
   :caption: Customer Support

   FuriosaAI Homepage <https://furiosa.ai>
   FuriosaAI Forum <https://furiosa-ai.discourse.group/>
   FuriosaAI Customer Portal <https://furiosa-ai.atlassian.net/servicedesk/customer/portals/>
   FuriosaAI Warboy SDK Document <https://furiosa-ai.github.io/docs/latest/en/>
