# gpt-finetuning

## Libraries
  * pandas
  * openai
  
## How to run
  ### 1. Run the Jupyter Notebook 'finetuning-gpt-example.ipynb'
  
  ### 2. Create an OpenAI account, and generate an API_TOKEN
  - https://openai.com/api/login
  - https://beta.openai.com/account/api-keys
  
  ### 3. Set the API_KEY as an environmental variable:
  ```
  $ export OPENAI_API_KEY=<YOUR-API-KEY>
  ```
  
  ### 4. Run the following command for generate a prepared file for finetuning process:
  ```
  $ openai tools fine_tunes.prepare_data -f <LOCAL_FILE>
  # Example:
    $ openai tools fine_tunes.prepare_data -f 'depression.jsonl'
  ```
  
  ### 5. Create a finetuning with the generated file:
  ```
  $ openai api fine_tunes.create -t <TRAIN_FILE_ID_OR_PATH> -m <BASE_MODEL>
  # Example:
    $ openai api fine_tunes.create -t "depression_prepared.jsonl" -m davinci
  ```
  
  ### 6. Get the state of your finetuning (could be in process or queue)
  ```
  $ openai api fine_tunes.follow -i <YOUR_FINE_TUNE_JOB_ID>
  Example:
    $ openai api fine_tunes.get -i ft-YzSMpfIHEUwanA6JFyPLJJuQ
  ```
  ### You can list all created fine-tunes
  ```
  $ openai api fine_tunes.list
  ```
  
  ### 7. Back to the notebook and test your finetuned model

## References

* OpenAI Fine-Tuning - https://beta.openai.com/docs/guides/fine-tuning
* Fine-tuning GPT-3 Using Python to Create a Virtual Mental Health Assistant Bot - https://betterprogramming.pub/how-to-finetune-gpt-3-finetuning-our-virtual-mental-health-assistant-641c1f3b1ef3
* ¿Funciona GTP-3, súper modelo de inteligencia artificial, en conversaciones en español de clientes de banca? - https://www.bbva.com/es/puede-ayudar-gpt-3-en-conversaciones-con-nuestros-clientes-en-espanol
