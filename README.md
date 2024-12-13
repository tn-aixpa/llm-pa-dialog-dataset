# AIxPA_dialogues
AIxPA_dialogues

# Repository content description

## Data
Directory containing the data.

`annotation` and `documents` subdirectory are further divided into `AmiciFamiglia` and `Comune`, containing the data entries matching the source.

### annotation
Each file in this folder is a  JSON representing an annotation task. 

A JSON contains the following elements:
- `task_id` unique identifier of the annotation;
- `doc_src` filename of the document used for the annotation;
- `edited_turns` the list of turns of related to this task;
- `user` the entity the annotator is simulating to be when interrogating the assistant;
- `dial_style` writing style of the dialogue. Either "Tu" (Informal) or "Lei" (Formal);
- `category` main data source pool. Either "AmiciFamiglia" or "Comune";
- `subcategory` subcategory of `category`.

Each turn is structured as follows:
- `id` turn identifier;
- `speaker` entity related to this turn;
- `message` what the entity says;
- `ground` one or more portion of texts taken from the document used to give references to the message. 

### Documents
Documents used during the annotation.

### summaries

Each file is a table that summarises the content of each annotation task.

`all_dialogues_summary.tsv` collects all annotation entries, while `AmiciFamiglia_dialogues_summary.tsv` and `Comune_dialogues_summary.tsv` collects ones only of the matching data source.


Each summary table has the following columns:
- `task_id` unique identifier of the annotation;
- `annotation_type` manual, dynamic, etc;
- `turn_n` amount of turns the post-edited dialogue has;
- `user_type` the entity the annotator is simulating to be when interrogating the assistant;
- `interaction_style` writing style of the dialogue. Either "Tu" (Informal) or "Lei" (Formal);
- `proactive` if true, the dialogue has been annotated so that the assistant is proactive towards the user, asking for details and if they have any queries;
- `ext_knowledge` if true, there are pieces of knowledge that have been picked outside of the document's scope;
- `doc_filename` filename of the document used for the annotation;
- `category` main data source pool. Either "AmiciFamiglia" or "Comune";
- `subcategory` subcategory of `category`.

# Usage
Create a file `config.yaml` in `code` directory and write in it the following

```
hf_token: "HUGGINGFACE_TOKEN"
wandb_token: "WANDB_TOKEN"
```

Replace `HUGGINGFACE_TOKEN` with your Meta Llama 3.1B Instruct's token claimed [in the following HuggingFace page](https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct)
Replace `WANDB_TOKEN` with your token for WanDB. This allows to see the progress of the finetuning


