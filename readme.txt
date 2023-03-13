---------- Tools needed to Run this app -----------
1. Python
2. Pyenv
3. Poetry

--- Refer Rasa Offical Docs Before Installation to Check which Python Versions Rasa can Run and Install Accordingly ---
website => https://rasa.com/docs/rasa/


--- Set Poetry to create virtualenv in current folder/project ---
--> cmd => poetry config virtualenvs.in-project true

--- Set Poetry to use Current Python version of Pyenv Local using --
--> cmd => poetry config virtualenvs.prefer-active-python true


---------- Rasa Chatbot Installation -------------
1. Make a new Folder 
--> cmd => mkdir chatbot

2. Move Inside the Folder
--> cmd => cd chatbot

3. Install required Python Version using
--> cmd => pyenv install 3.7.9

4. Set the Python Version to use in this project
--> cmd => pyenv local 3.7.9

5. Make a pyproject.toml file using poetry
--> cmd => poetry init
    and set python version to 3.7.9 (Which you is install using pyenv local version_name)

6. Make a virtualenv using poetry
--> cmd => poetry install (It will create new virtualenv)

7. Activate Virtualenv
--> cmd => poetry shell (It will activate virtualenv)
    and if it not activate use 
--> cmd => source virtualenv_name/Scripts/activate [In any cmd, powershell, bash]

8. To check poetry is using correct python version and virtualenv path run
--> cmd => poetry env info

9. Check for outdated python package and update it using
--> cmd => python -m pip list --outdated
--> cmd => python -m pip install --upgrade package_name1 package_name2 ...

10. Install Rasa using poetry
--> cmd => poetry add rasa (It will install lastest version of Rasa)
--> cmd => poetry add rasa=3.x (It will install specficed version of Rasa)
--> cmd => poetry add rasa[full] (To install all needed dependencies for every configuration)

and check rasa version using cmd
--> cmd => rasa --version

11. Install Spacy to install a default trained pipeline package (I think spaCy is optional)
--> cmd => poetry add rasa[spacy]  (This will install Rasa Open Source as well as spaCy.)
    or below cmd if above cmd not work
--> cmd => python -m pip install rasa[spacy]  (This will install Rasa Open Source as well as spaCy.)

--> cmd => python -m spacy download en_core_web_md (Its language model for the English language of "medium" sized models.)

12. To check how many package is install and of Which versions run anyone cmd below
--> cmd => python -m pip list
    or
--> cmd => python freeze
    or
--> cmd => python freeze > requirements.txt (To store Python package and its version)
    or 
    check pyproject.toml and poetry.lock file

13. Create a new Rasa Application using
--> cmd => rasa init  (It will create new rasa app with some prompt to choose from or initial.)

14. Run Rasa Server using
--> cmd => rasa run (It will run rasa server it default port: 127.0.0.1:5005)

or Run Rasa Server with Trained Models and Api it default port: 127.0.0.1:5005
--> cmd => rasa run -m models --enable-api --cors "*"
--> cmd => rasa run --enable-api --cors "*" --debug[Optional] -p {PORT}[optional]


15. To Run Rasa Custom Actions it default port: 127.0.0.1:5055
--> cmd => rasa run actions
--> cmd => rasa run actions -p {PORT}[Optional]

------ Errors -----
1. Rasa Webchat version should be 1.0.0 for rasa versions < 2.5
2. If socket and engine error occur then use below cmd
--> cmd => poetry add python-engineio=3.13.2
--> cmd => poetry add python-socketio=4.6.1

3. To run Rasa Webchat use below versions
--> rasa version = 2.1.2
--> rasa sdk = 2.3.1
--> python version = 3.7.5
