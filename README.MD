# Getting Started with BabelMatcher + Ansible deployment

This project uses the babelnet project (link) to deploy the example or test programs into a remote machine using ansible.

## Configuration

Is important to do:

**$ ansible-galaxy install -r requirements.yml**

to install dependencies.


This project uses the **config_data.yml** to be able to get the code source to deploy and the destination location to do so. You need to generate the rsa id and name it **id_rsa** to be able to use the project or can also be edited to your id_rsa file name.
This is also the case with the ansible_host ip, ansible_user and all configuration related to Ansible as such.

There are 5 Ansible playbooks that are used to exemplify the use and possibilities of the BabelMatcher library. The ansible functionality was implemented because there is a real risk of running out of babelkeys tokens while running the program, and this key is renewed every 24 hours, so, if you know you are going to spend all your tokens without finishing the task at hand, deploying the task into a remote machine can be the more realistic and functional way to do it.

* ##### tfm_create_model_from_all_lemmas_found

Process the text with all the data that can be extracted from Babelnet, this mean, using all lemmas found, without disambiguation.

* ##### tfm_create_model_from_first_lemma_found

Process the text with the first lemma found by babelnet using lemmas as query.

* ##### tfm_create_model_from_id_and_tag_list

Process the text with a list of ids and tags, this marks the results with the tags but the meaning or process is related to the ids data.

* ##### tfm_create_model_from_id_list

Process the text with a list of ids and the first lemma found by the id is the tag to match in the result.

* ##### tfm_execute_model_from_saved_model

Process the text using a previously saved model.

### Parameters in config.yml
Next the meaning or function of every paramater in config.yml.

* ##### data_path_source

This is the path to the code with the data folder where the logic of the project is stored.

* ##### data_path_destination

This is the path folder to where the code will be stored to next be executed on the remote server.

* ##### result_from_model_destination_local

This is the folder where the result from the model execution will be stored.
* ##### result_file_name_on_local

This is the name which the result file will have. This file will be contained in the **result_from_model_destination_local** folder inside the folder that is equal to the server name where the data was fetched from.

* ##### result_html_name_on_local

This is the name of the result file prepared to be shown as an html. This file will be contained in the **result_from_model_destination_local** folder inside the folder that is equal to the server name where the data was fetched from.
