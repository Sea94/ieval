The `ieval_logs.csv` file contains a dataframe with the logs from our experiment.
Each two consecutive rows comprise data collected within one Human Intelligent Task.
The columns in the dataframe are defined as follows:
- `part` (int): numerical id of the HIT
- `elapsed_sec` (int): overall number of seconds elapsed per given HIT
- `elapsed_min` (float): overall number of minutes elapsed per given HIT
- `TEQ_raw_i` (float): worker's response to the i-th question of the Toronto
	Empathy Questionnaire [1] (not used for analysis in this submission)
- `TEQ_agg` (float): worker's total score for Toronto Empathy Questionnaire
	(not used for analysis in this submission)
- `valence` (str): emotional polarity of the grounding scenario
- `chat_log_<COLOR>` (str): chat log between the worker and the chatbot, which
	was assigned a <COLOR> color
- `P_<COLOR>` (int): worker's Likert-type score assessing the statement:
	"The chatbot was polite throughout our conversation."
- `^P_<COLOR>` (int): worker's Likert-type score assessing the statement:
	"Some of the chatbot's responses were insulting."
- `A_<COLOR>` (int): worker's Likert-type score assessing the statement:
	"The chatbot was paying attention to what I was saying."
- `^A_<COLOR>` (int): worker's Likert-type score assessing the statement:
	"The chatbot was inattentive to my messages."
- `EU_<COLOR>` (int): worker's Likert-type score assessing the statement:
	"The chatbot understood my emotions."
- `ER_<COLOR>` (int): worker's Likert-type score assessing the statement:
	"The chatbot responded to my emotions appropriately."
- `L_<COLOR>` (int): worker's Likert-type score assessing the statement:
	"The chatbot is likable."
- `R_<COLOR>` (int): worker's Likert-type score assessing the statement:
	"The chatbot was repetitive."
- `S_<COLOR>` (int): worker's Likert-type score assessing the statement:
	"The chabot's responses made sense given my inputs."
- `Rank_<COLOR>` (int): overall rating of the chatbot (the higher, the better)


[1] R. Nathan Spreng, Margaret C. McKinnon, Raymond A. Mar, and Brian Levine. The Toronto Empathy Questionnaire

Remark: we did not use workers' scores for reserve-worded Likert-type questions
in our analysis (marked with "^"). Also, the reported results for "empathetic" and
"making sense" dimension are computed as:
	* empathetic = AVG(EU_<COLOR>, ER_<COLOR>)
	* making sense = AVG(A_<COLOR>, S_<COLOR>)
We averaged the scores for these pairs of dimensions as they were highly correlated
with each other (Pearson's r > 0.85).