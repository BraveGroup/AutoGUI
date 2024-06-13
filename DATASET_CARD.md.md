AutoGUI: Scaling GUI Grounding with Autonomous Functionality Annotations from LLMs
# Dataset Card for AutoGUI

## Table of Contents
- [Dataset Card for AutoGUI](#dataset-card-for-autogui)
  - [Table of Contents](#table-of-contents)
  - [Dataset Description](#dataset-description)
    - [Dataset Summary](#dataset-summary)
    - [Supported Tasks and Leaderboards](#supported-tasks-and-leaderboards)
    - [Languages](#languages)
  - [Dataset Structure](#dataset-structure)
    - [Data Instances](#data-instances)
    - [Data Fields](#data-fields)
    - [Data Splits](#data-splits)
  - [Dataset Creation](#dataset-creation)
    - [Curation Rationale](#curation-rationale)
    - [Source Data](#source-data)
      - [Initial Data Collection and Normalization](#initial-data-collection-and-normalization)
      - [Who are the source language producers?](#who-are-the-source-language-producers)
    - [Annotations](#annotations)
      - [Annotation process](#annotation-process)
      - [Who are the annotators?](#who-are-the-annotators)
    - [Personal and Sensitive Information](#personal-and-sensitive-information)
  - [Considerations for Using the Data](#considerations-for-using-the-data)
    - [Social Impact of Dataset](#social-impact-of-dataset)
    - [Discussion of Biases](#discussion-of-biases)
    - [Other Known Limitations](#other-known-limitations)
  - [Additional Information](#additional-information)
    - [Dataset Curators](#dataset-curators)
    - [Licensing Information](#licensing-information)
    - [Citation Information](#citation-information)

## Dataset Description

- **Homepage:** [https://autogui-project.github.io](https://autogui-project.github.io)
- **Repository:** [https://github.com/BraveGroup/AutoGUI](https://github.com/BraveGroup/AutoGUI)
- **Paper:** https://arxiv.org/abs/2304.06939
- **Point of Contact:**  (pass@pass)

### Dataset Summary

We present the AutoGUI-627k dataset, an extensive collection of web UI screenshots paired with precise functionality annotations generated by large language models (LLMs). This dataset enriches UI understanding by providing context-specific descriptions for UI elements across a multitude of scenarios. After rigorous filtering for quality, AutoGUI-627k offers 627k images with rich annotations, fostering advancements in vision-language model training for UI automation and interaction.

### Supported Tasks and Leaderboards

This is a pre-training corpus.

### Languages

English

## Dataset Structure


You can access the dataset through [Hugging Face🤗]().


### Data Instances

Documents are arranged as follows:

- `id`: The unique identifier for the instance in the dataset.
- `image_path`: The file path to the image associated with the instance.
- `conversations` is a key mapping to a list of conversations between the user and the assistant.
  - `from`: Indicates whether the message is from the user or the assistant.
  - `value`: The content of the message.
- `unnormalized_box`: A list of four values representing the bounding box coordinates of an element in the image, in the order [x1, y1, x2, y2], where (x1, y1) is the top-left corner and (x2, y2) is the bottom-right corner. These coordinates are not normalized.

Here's an example:

```
{'id': 'funcpred_ground_4',
 'image_path': 'images/func_pred/24-05-29-11-05-59_01a92f84-01f3-45e1-8842-95defea89c1e_step004_actionE_domaincreativecommons.org.png'  
 'conversations': [{'from': 'user',
   'value': "Picture 1: <img>images/func_pred/24-05-29-11-05-59_01a92f84-01f3-45e1-8842-95defea89c1e_step004_actionE_domaincreativecommons.org.png</img>\nUsing the image of this webpage, can you determine the coordinates of the element I describe (with point)? This element navigates users to the blog section of the Creative Commons website, allowing them to access and engage with the organization's blog content."},
  {'from': 'assistant', 'value': '(83,10)'}],
 'unnormalized_box': [1046.0234375, 66.203125, 1086.0859375, 86.4375]}
```

### Data Fields

See above.

### Data Splits

AutoGUI dataset contains a total of 627k instances, 625k of which constitute the training split while the other 2k are reserved as a test split.

## Dataset Creation

The dataset was created between March and May 2024.

### Curation Rationale

This dataset was created with the purpose of enhancing the understanding of UI by (VLMs). Specifically, it aims to address the limitations of existing datasets, lacking contextual functional descriptions of UI elements. By leveraging large language models (LLMs) to autonomously annotate UI elements based on simulated interactions and subsequent changes in the UI's content, this dataset provides detailed functionality descriptions at scale, facilitating the training and evaluation of VLMs in UI understanding tasks.

### Source Data

#### Initial Data Collection and Normalization

See the paper for more details.

#### Who are the source language producers?

Authors of publicly accessible webpages.

### Annotations

#### Annotation process

See the paper for more details. The corpus, as a whole, is not explicitly annotated.

#### Who are the annotators?

N/A

### Personal and Sensitive Information

N/A

## Considerations for Using the Data

### Social Impact of Dataset

- `Accessibility Enhancements`: VLMs trained with the AutoGUI data can obtain stronger UI grounding capabilities, enabling them to act as UI agents that can help users, including those with disabilities, locate elements on complex UIs. This could lead to the development of more intuitive and accessible software applications.
- `Research Impact`: By reducing the effort required for annotating UI data, the AutoGUI can lower the costs for building UI agents in both industry and academia. This could shift labor demands towards more creative and strategic roles rather than repetitive annotation tasks.
- `Privacy and Security Concerns`: Although precautions are taken to avoid sensitive UI elements, the vast nature of the internet makes it challenging to completely eliminate the risk of personal information leakage. Cybersecurity research will need to devise protective approaches to address this potential issue.

### Discussion of Biases

The bias present in the LLMs used for the AutoGUI annotation pipeline may be reflected in the collected data, leading to a trained UI-VLM that inherits the bias. Mitigating bias in the LLM's annotations will be important for developing fair VLM agents that align with the values of users from diverse cultures.

### Other Known Limitations

The key limitations of the AutoGUI dataset are:
- `Lack of real mobile app data`: The system primarily collects data from webpages, which may not accurately represent the UI of native mobile apps.
- `No task-oriented interaction trajectories`: The randomly generated interactions do not capture high-level task semantics, limiting the instruction-following capabilities of the trained VLMs.
- `Inability to annotate write-only UI elements`: To avoid potential impact on the internet, the system excludes interactions with sensitive elements like posting comments or making purchases, resulting in limited coverage of such functionalities.
These limitations suggest that future work should explore incorporating mobile app data, generating task-oriented interactions, and finding ways to safely annotate a wider range of UI elements.

## Additional Information

### Dataset Curators

This dataset was initially curated by researchers from *New Laboratory of Pattern Recognition (NLPR), CASIA*, *The Hong Kong Polytechnic University*, and *Center for Artificial Intelligence and Robotics, HKISI, CAS*. The author list of v1 of the arxiv paper is an accurate list of specific contributors.

### Licensing Information

- 

### Citation Information

```
@article{li2024autogui,
    title={{AutoGUI:} Scaling GUI Grounding with Autonomous Functionality Annotations from LLMs},
    author={Li, Hongxin and Chen, Jingfan and Su, Jingran and Chen, Yuntao and Li, Qing and Zhang, Zhaoxiang},
    year={2024},
}
```