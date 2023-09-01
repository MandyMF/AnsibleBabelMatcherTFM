# Getting Started with BabelMatcher + Ansible deployment

This project uses the babelnet project (link) to deploy the example or test programs into a remote machine using ansible.

## Configuration

Is important to do:

``` bash
ansible-galaxy install -r requirements.yml
```

to install all dependencies.


This project uses the **config_data.yml** to be able to get the code source to deploy and the destination location to do so. You need to generate the rsa id and name it **id_rsa** to be able to use the project or can also be edited to your id_rsa file name.
This is also the case with the ansible_host ip, ansible_user and all configuration related to Ansible as such.

It also uses a **config.yaml** that is used in the BabelMatcher project, the description of its parameters are on the **https://github.com/MandyMF/BabelMatcherTFM** repository. This project configures, deploys and said such repository.

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

### Parameters in config_data.yml
Next the meaning or function of every paramater in config_data.yml.

* ##### config_path_source

This is the path of the file that should be a **.yaml** or a **.yml**, and contains the configuration of the BabelMatcher project Logic and has to have the structure showed in the **config.yaml** file and should be fill with the corresponding values. 

* #### data_path_source

This is the path of the data file to be processed by the model created by the Logic.

* ##### project_path_destination

This is the path folder to where the code will be stored to next be executed on the remote server.

* ##### result_from_model_destination_local

This is the folder where the result from the model execution will be stored.
* ##### result_file_name_on_local

This is the name that the result json file will have. This file will be contained in the **result_from_model_destination_local** folder inside the folder that is equal to the server name where the data was fetched from.

* ##### result_html_name_on_local

This is the name of the resulting file prepared to be shown as an html. This file will be contained in the **result_from_model_destination_local** folder inside the folder that is equal to the server name where the data was fetched from.

* ##### result_model_name_on_local

This is the name of the resulting model created by running the Logic. This folder will be contained in the **result_from_model_destination_local** folder inside the folder that is equal to the server name where the data was fetched from.

* ##### result_pattern_name_on_local

This is the name of the result pattern file created by running the Logic. This file will be contained in the **result_from_model_destination_local** folder inside the folder that is equal to the server name where the data was fetched from.

* ##### model_folder_location_on_source

This is the path of the model to load, to run the playbook tfm_execute_model_from_saved_model.yml and it will only be required in this case.

* ##### publish_results_path

This is the path where is the result html file will be copied to be publish, in case of apache2 default pass is *"/var/www/html/index.html"*.