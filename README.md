# iEval
[![DOI](https://zenodo.org/badge/515204661.svg)](https://zenodo.org/badge/latestdoi/515204661)

This repo contains data of iEval: Interactive Evaluation Framework for Open-Domain Empathetic Chatbots.

## Introduction
Building an empathetic chatbot is an important objective in dialog generation research, with evaluation being one of the most challenging parts. By empathy, we mean the ability to understand and relate to the speakers’ emotions, and respond to them appropriately. Human evaluation has been considered as the current standard for measuring the performance of open-domain empathetic chatbots. However, existing evaluation procedures suffer from a number of limitations we try to address in our current work. In the cited paper, we describe iEval, a novel interactive evaluation framework where the person chatting with the bots also rates them on different conversational aspects, as well as ranking them, resulting in greater consistency of the scores. We use iEval to benchmark several state-of-the-art empathetic chatbots, allowing us to discover some intricate details in their performance in different emotional contexts. Based on these results, we present key implications for further improvement of such chatbots. To facilitate other researchers using the iEval framework, we release our dataset consisting of collected chat logs and human scores.

## Dataset
The data from our experiment are available in the [ieval_data.json](https://github.com/Sea94/ieval/blob/main/ieval_data.json) file. It contains a list of objects, with each object corresponsing to a single experimental task of the following structure:

- `part` (int): numerical id of the experimantal task
- `elapsed_sec` (int): overall number of seconds elapsed per given task
- `elapsed_min` (float): overall number of minutes elapsed per given task
- `TEQ_raw` (list(int)): worker's responses to the questions of the Toronto Empathy Questionnaire [1] (not used in our analysis)
- `TEQ_agg` (int): worker's total score for Toronto Empathy Questionnaire [1] (not used in our analysis)
- `<VALENCE>` (obj): emotional polarity of the grounding scenario; taken values: `positive`, `negative`
  - `conv_id` (str): id of a conversation from the EmpatheticDialogues dataset [2] that was used for the grounding scenario
  - `emotion` (str): emotion label from the EmpatheticDialogues dataset [2] that was used for the grounding scenario
  - `prompt` (str): situation prompt from the EmpatheticDialogues dataset [2] that was used for the grounding scenario
  - `<COLOR>` (obj): color code of a chatbot; taken values: `Pink`, `Purple`, `Yellow`, `Green`
    - `chat_log` (str): chat log between the worker and the chatbot with the assigned \<COLOR\> for the given emotional \<VALENCE\>
    - `P` (int): worker's Likert-type score assessing the statement: "The chatbot was polite throughout our conversation."
    - `^P` (int): worker's Likert-type score assessing the statement: "Some of the chatbot's responses were insulting."
    - `A` (int): worker's Likert-type score assessing the statement: "The chatbot was paying attention to what I was saying."
    - `^A` (int): worker's Likert-type score assessing the statement: "The chatbot was inattentive to my messages."
    - `EU` (int): worker's Likert-type score assessing the statement: "The chatbot understood my emotions."
    - `ER` (int): worker's Likert-type score assessing the statement: "The chatbot responded to my emotions appropriately."
    - `L` (int): worker's Likert-type score assessing the statement: "The chatbot is likable."
    - `R` (int): worker's Likert-type score assessing the statement: "The chatbot was repetitive."
    - `S` (int): worker's Likert-type score assessing the statement: "The chabot's responses made sense given my inputs."
    - `Rating` (int): overall rating of the chatbot (inverse of the rank, i.e., the higher, the better)
    

[1] R. Nathan Spreng, Margaret C. McKinnon, Raymond A. Mar, and Brian Levine. The Toronto Empathy Questionnaire

[2] H. Rashkin, E. M. Smith, M. Li, Y. Boureau. Towards Empathetic Open-domain Conversation Models: a New Benchmark and Dataset

_Remark: we did not use workers' scores for reserve-worded Likert-type questions in our analysis (marked with "^"). Also, the reported results for "empathetic" and "making sense" dimension are computed as:_
- *empathetic = AVG(EU_\<COLOR\>, ER_\<COLOR\>)*
- *making sense = AVG(A_\<COLOR\>, S_\<COLOR\>)*

_We averaged the scores for these pairs of dimensions as they were highly correlated with each other (Pearson's r > 0.85)._

## References

Please cite [*] if you found the resources in this repository useful.

[*] E. Svikhnushina, A. Filippova, P. Pu. *iEval: Interactive Evaluation Framework for Open-Domain Empathetic Chatbots*

```
@inproceedings{Svikhnushina2022iEval,
  title = {iEval: Interactive Evaluation Framework for Open-Domain Empathetic Chatbots},
  author = {Ekaterina Svikhnushina and Anastasiia Filippova and Pearl Pu},
  booktitle = {SIGDIAL},
  year = {2022},
}
```

## License
See the [LICENSE](LICENSE) file in the root repo folder for more details.
