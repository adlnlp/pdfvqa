# PDFVQA


The GitHub will be released after the conference (ECML PKDD 2023).
The Appendix can be found in the Appendix.pdf 


# [PDF-VQA: A New Dataset for Real-World VQA on PDF Documents](https://arxiv.org/abs/2304.06447)

### <div align="center"> Yihao Ding, Siwen Luo, Hyunsuk Chung, Soyeon Caren Han </div>
### <div align="center"> Accepted by European Conference on Machine Learning and Principles and Practice of Knowledge Discovery in Databases <br> (ECML PKDD 2023) </div>



## PDFVQA Dataset
We introduce **PDFVQA**, a new Document-based Visual Question Answering dataset, to comprehensively examine the document understanding from various aspects, including document element recognition, document layout structural understanding as well as contextual understanding and key information extraction. Our PDF-VQA dataset extends the current scale of document understanding that limits on the single document page to the new scale that asks questions over the full document of multiple pages.

**The dataset contains three tasks:**
- **Task A**: document element recognition and spatial relationship understanding among document elements on the page level. The answers should be predicted from a fixed answer space.
- **Task B**: structural understanding of document elements and answer extraction on the document page level.
- **Task C**: document understanding on the whole document level of multiple consecutive pages.
There are pkl files contains Task C question answer pairs

Data Statistics of Tasks A, B, and C:

<img src="https://github.com/adlnlp/pdfvqa/blob/main/Figures/PDFVQA_DataStats.png" width="50%">
  
## Relational Graph Annotation
Our PDFVQA dataset specifically annotates the hierarchically logical relational graph among the document layout elements to specify the potential affiliation between document elements by identifying the
parent objects and their children’s objects based on the hierarchical structures of document layouts. 

Future works can directly use such relational information as the additional features for document understanding. 

## Dataset files
The dataset consists of three main splits: training, validation, and testing. For each split, we provide two types of files:
- question-answer pkl files: contains questions and their ground truth answers.
- document layout structure pkl file: contains essential document information, including the bounding box coordinates of each document layout component, textual contents inside each bounding box, and parent-child relationships (relational graph annotation). This information is crucial for understanding the structure of the visually-rich documents and identifying relevant Regions of Interest (RoIs) that might contain the answers to the questions.

We also provide the document images for each data split. The pkl files contain the information to locate the document images of each target document.

### Document Image and Layout Structure Pickle Files
Please refer to this [link](https://drive.google.com/drive/folders/1A2cI3uJUU_1ZliOKpHmYa07VfvZCwOo1?usp=drive_link) to get the document images of each split. 

Layout structure information of each data split: [Training](https://drive.google.com/file/d/1SyEptlqqX-frq_1hSQTxUGGptk6OI9aQ/view?usp=drive_link),
[Validation](https://drive.google.com/file/d/1Z9umISob9ar_5n5T-Cbhr4nbHuQCvVGm/view?usp=drive_link),
[Testing](https://drive.google.com/file/d/1knSVmocw4-_FF98bFMdVSvhnUn3mPUvm/view?usp=drive_link)

### Task A Question Answer Pairs:

### Task B Question Answer Pairs:

### Task C Question Answer Pairs
Please refer to those links to get question-answer pairs for [training](https://drive.google.com/file/d/1-8ECkZV5q5i7CBY7U1llmCTSiVJPUNsS/view?usp=drive_link), [validation](https://drive.google.com/file/d/1-WdGXwo_8U7cU8mOh5ZjLm_CDqDDWbxo/view?usp=drive_link) and [testing](https://drive.google.com/file/d/1-F242FFvubAIpjXPItFc_eGUs3dzb6QO/view?usp=drive_link) splits. 

## Experiments
We experimented with several baselines on our PDF-VQA dataset to provide a preliminary view of different models’ performances. 

- Acronym of feature aspects: Q--Question features; B--Bounding box coordinates; V--Visual appearance features; C--Contextual features; R: Relational Information.
- The better performance of VisualBERT than ViLT indicates that object-level visual features are more effective than image patch representations.
- LayoutLM2 used token-level visual and bounding box features, which shows it's ineffective for the whole document element identification.
- Our proposed graph-based model, LoSpa, achieves the highest performance compared to all baselines, which indicates the effectiveness of relational information on this task.
- The comparatively low performances on Task C of all models indicate the difficulty of document-level questions and produce massive room for improvement for future research on this task.
- **Note: the detailed baseline model setup can be found in Appendix C.**


<img src="https://github.com/adlnlp/pdfvqa/blob/main/Figures/Overall_Performance.png" width="70%">

## Contributors
The contributors of the work are:
- [Yihao Ding](https://scholar.google.com/citations?user=A2onD9gAAAAJ&hl=en) (Ph.D. candidate at the University of Sydney)
- [Siwen Luo](https://scholar.google.com/citations?user=32nO4VAAAAAJ&hl=en) (Ph.D. candidate at the University of Sydney)
- Hyunsuk Chung (FortifyEdge, Sydney, Australia)
- [Soyeon Caren Han](https://drcarenhan.github.io/) (Senior lecturer at the University of Western Australia, Honorary senior lecturer at the University of Sydney)


## Citation
If you use the dataset, please cite this our paper [PDF-VQA: A New Dataset for Real-World VQA on PDF Documents](https://link.springer.com/chapter/10.1007/978-3-031-43427-3_35) accepted by [ECML PKDD 2023](https://2023.ecmlpkdd.org/). 
```
@InProceedings{10.1007/978-3-031-43427-3_35,
  author="Ding, Yihao
          and Luo, Siwen
          and Chung, Hyunsuk
          and Han, Soyeon Caren",
  editor="De Francisci Morales, Gianmarco
          and Perlich, Claudia
          and Ruchansky, Natali
          and Kourtellis, Nicolas
          and Baralis, Elena
          and Bonchi, Francesco",
  title="PDF-VQA: A New Dataset for Real-World VQA on PDF Documents",
  booktitle="Machine Learning and Knowledge Discovery in Databases: Applied Data Science and Demo Track",
  year="2023",
  publisher="Springer Nature Switzerland",
  address="Cham",
  pages="585--601",
  abstract="Document-based Visual Question Answering examines the document understanding of document images in conditions of natural language questions. We proposed a new document-based VQA dataset, PDF-VQA, to comprehensively examine the document understanding from various aspects, including document element recognition, document layout structural understanding as well as contextual understanding and key information extraction. Our PDF-VQA dataset extends the current scale of document understanding that limits on the single document page to the new scale that asks questions over the full document of multiple pages. We also propose a new graph-based VQA model that explicitly integrates the spatial and hierarchically structural relationships between different document elements to boost the document structural understanding. The performances are compared with several baselines over different question types and tasks (The full dataset is released in https://github.com/adlnlp/pdfvqa).",
  isbn="978-3-031-43427-3"
}
```






