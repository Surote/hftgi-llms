# Deploying HuggingFace TGI for Open Source LLMs in Kubernetes / OpenShift with GitOps

The aim of this repository is to easily deploy our OpenSource LLMs in OpenShift or Kubernetes clusters using GitOps: 

![LLM0](/assets/llm0.png)

## Overview

[Text Generation Inference (TGI)](https://huggingface.co/docs/text-generation-inference/index) is a toolkit for deploying and serving Large Language Models (LLMs). TGI enables high-performance text generation for the most popular open-source LLMs, including Llama, Falcon, StarCoder, BLOOM, GPT-NeoX, and T5.

This repo will deploy [HuggingFace Text Generation Inference](https://github.com/huggingface/text-generation-inference) server deployments in K8s/OpenShift with GitOps:

![LLM2](/assets/llm1.png)

With this we can easily deploy different Open Source LLMs such as Llama2, Falcon, Mistral or FlanT5-XL among others in our OpenShift / Kubernetes clusters to be consumed as another application:

![LLM2](/assets/llm4.png)

## Requirements

- ROSA or OpenShift Clusters (can be also deployed in K8s with some tweaks)
- GPU available (24gb vRAM recommended)
- Node Feature Discovery Operator
- NVIDIA GPU Operator
- ArgoCD / OpenShift GitOps

Tested with A10G (g5.2xlarge) with Spot Instances using a ROSA cluster with 4.13 version and RHODS with 2.14.0

## Models available to deploy using GitOps

- [Mistral-7B-Instruct](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.1)

```md
kubectl apply -k gitops/mistral
```

![LLM0](/assets/llm0.png)

- [Flan-T5-XXL](https://huggingface.co/google/flan-t5-xxl)

```md
kubectl apply -k gitops/flant5xxl
```

![LLM0](/assets/llm8.png)

- [Falcon-7B-Instruct](https://huggingface.co/tiiuae/falcon-7b-instruct)

```md
kubectl apply -k gitops/falcon
```

![LLM0](/assets/llm7.png)

- [Llama2-7B-Chat-HF](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf)

```md
kubectl apply -k gitops/llama2
```

- [StarCoder](https://huggingface.co/bigcode/starcoder)

```md
kubectl apply -k gitops/starcoder
```

## Inference to the LLMs

* Check the [Inference Guide](./inference/README.md) to test your LLM deployed with Hugging Face Text Generation Inference 

## FrontEnd Gradio ChatBot powered by HF-TGI

We will deploy alongside the HF-TGI a Gradio ChatBot application with [Memory](https://python.langchain.com/docs/modules/memory/types/buffer) powered by [LangChain](https://python.langchain.com/docs/get_started/introduction).

This FrontEnd will be using the HF-TGI deployed as a backend, powering and fueling the AI NPL Chat capabilities of this FrontEnd Chatbot App.



NOTE: If you want to know more, check the [original source rh-aiservices-bu repository](https://github.com/rh-aiservices-bu/llm-on-openshift/blob/main/examples/ui/gradio/gradio-hftgi-memory/README.md). 

## Extra Notes

- This is just a PoC, not ready for Production!
- Repo is heavily based in the [llm-on-openshift repo](https://github.com/rh-aiservices-bu/llm-on-openshift/tree/main/hf_tgis_deployment). Kudos to the team!