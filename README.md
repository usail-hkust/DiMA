# DiMA: An LLM-Powered Ride-Hailing Assistant at DiDi ([PDF](https://arxiv.org/pdf/2503.04768))

<p align="center">

![Testing Status](https://img.shields.io/badge/docs-in_progress-green)
![Testing Status](https://img.shields.io/badge/pypi_package-in_progress-green)
![License: CC BY 4.0](https://img.shields.io/badge/license-CC%20BY%204.0-blue)

</p>

<p align="center">

| **[1 Introduction](#introduction)** 
| **[2 Prompt Tempalte](#requirements)**
| **[3 Case Study](#usage)**
| **[4 Citation](#citation)**

</p>

## 1 Introduction
<div style="display: flex; justify-content: center;">
  <img src="https://github.com/usail-hkust/DiMA/blob/main/Figure1.png" width="500">
</div>

Official project for KDD 2025 paper ["DiMA: An LLM-Powered Ride-Hailing Assistant at DiDi"](https://arxiv.org/pdf/2503.04768).

DiMA is an LLM-powered ride-hailing assistant. Its goal is to provide seamless ride-hailing services and beyond through a natural and efficient conversational interface under dynamic and complex spatiotemporal urban contexts.

## 2 Prompt Template

We present the prompt template of every module in './Prompt'.

#### Spatiotemporal-aware Tool-augmented Order Planning

As mentioned in the methodology, this module conducts spatial mapping, temporal reasoning, and progressive order planning. The entire process is achieved through a function call. In this section, we provide the detailed prompt template in ['./Prompt/Spatiotemporal-aware tool-augmented order planning.md'](https://github.com/usail-hkust/DiMA/blob/main/Prompt/Spatiotemporal-aware%20tool-augmented%20order%20planning.md). As can be seen in the demonstration in the prompt, when the user just inputs an address Hongyuan, DiMA will automatically generate a set of function call, which will be sequentially executed to achieve order planning.

#### Multi-type Dialog Replier Selection

After order planning, the dialog policy will be generated to allocate different dialog replies for response generation. Specifically, we fully utilize all current information for allocating, including the current user query, history dialog, current time, and intermediate executed system results. We provide the prompt template in ['./Prompt/Dialog replier selection mechanism.md'](https://github.com/usail-hkust/DiMA/blob/main/Prompt/Dialog%20replier%20selection%20mechanism.md). As can be seen, we first provide a well-illustrative description of this task, and then we explain the input respectively, including history dialog, current user query, executing results, current time, and order status. Then, we providea  description of each dialog replier scenario to help it understand how to perform response replier allocation. Before controlling output format, we adda  demonstration example in the prompt.

#### Specialized Dialog Relpier

In a specialized response generation pipeline, we will follow a formulaic response style to generate the assistant's response.  The prompt template is provided in [./Prompt/specialized dialog replier.md](https://github.com/usail-hkust/DiMA/blob/main/Prompt/specialized%20dialog%20replier.md).  As can be seen, we provide four illustrative response styles to deal with different response scenarios. To conserve space, we omitted the full prompt and detailed explanation of each component (\ie <historical conversation>, <current user query>, and <current time>) since they are identical to those shown in ['./Prompt/Dialog replier selection mechanism.md'](https://github.com/usail-hkust/DiMA/blob/main/Prompt/Dialog%20replier%20selection%20mechanism.md). The explanations of these items are also shortened for the error-handling and knowledge-enhanced dialog replied.

#### Error-handling Dialog Replier

As discussed in the methodology, the error-handling pipeline aims to politely reject the user's unmet request or further ask the user for more detailed ride-hailing intent. Specifically, we add a few instructions and provide corresponding demonstrations (\ie how to incorporate the system error for a better response) based on the prompt of the specialized dialog replier. The added prompt content is shown in ['./Prompt/error-handling dialog replier.md/'](https://github.com/usail-hkust/DiMA/blob/main/Prompt/error-handling%20dialog%20replier.md). As shown in the prompt, the core is to add the explanation of the contradictions identified and to provide examples of contradictions to help the LLMs know how to reply in these situations.

#### Knowledge-enhanced Dialog Replier

We add retrieved QA pairs into the prompt and explicitly prompt LLMs to follow these similar QA pairs to generate the response. Specifically, we achieve prompt extension (\ie adding a task re-profile and retrieved QA pairs) based on the prompt of the specialized dialog replier. The added prompt template is shown in [./Prompt/knowledge-enhanced dialog replier.md](https://github.com/usail-hkust/DiMA/blob/main/Prompt/knowledge-enhanced%20dialog%20replier.md).  As can be seen, we provide current user query, retrieved assistant response, and corresponding similarity score in the prompt, beginning with an initial task re-profile.

## 3 Case Study

We present a case study of DiMA to illustrate how DiMA creates a ride-hailing order and provides a response given a user query.

The following figure shows the entire dialog session:

![Case Study](https://github.com/usail-hkust/DiMA/blob/main/Case_Study.png)

## 4 Citation

If you find our work is useful for your research, please consider citing:

```
@article{ning2025dima,
  title={DiMA: An LLM-Powered Ride-Hailing Assistant at DiDi},
  author={Ning, Yansong and Cai, Shuowei and Li, Wei and Fang, Jun and Tan, Naiqiang and Chai, Hua and Liu, Hao},
  journal={arXiv preprint arXiv:2503.04768},
  year={2025}
}
```

