# Getting Started with BabelMatcher + Ansible deployment

This project uses the babelnet project (link) to deploy the example or test programs into a remote machine using ansible.

## Configuration

This project uses the **config_data.yml** to be able to get the code source to deploy and the destination location to do so.
You need to generate the rsa id and name it **id_rsa** to be able to use the project or can also be edited to your id_rsa file name.
This is also the case with the ansible_host ip, ansible_user and all configuration related to ansible as such.

There are 5 ansible playbooks that are use to examplify the use and possibilities of the BabelMatcher library. The ansible functionality was implemented
because there is a real risk of running out of babelkeys tokens while running the program, and this keys are renewed every 24 hours, so, if you now you now
you are going to spend all your tokens without finishing the task at hand, deploying the task into a remote machine can be the more realisting and functional way
to do it.

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