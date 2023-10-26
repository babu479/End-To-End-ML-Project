###End-To-End-ML-Project
---

##Day1:
***

1) Setup the github repository:

   `Create github repository`

2) Create .gitignore file: [.gitignore](.gitignore)

   ``Create file --> .gitignore --> template python --> commit``
   
3) New environment (.venv): [.venv](.venv)
   

   ```
   <!-- To create new environment check the below python commands -->
   #python3 -m venv .venv
   #source .venv/bin/activate
   ```
4) create setup.py with the below content : [setup.py](setup.py)

   ```
      from setuptools import find_packages,setup
      from typing import List

      def get_requirements(file_name:str)->List[str]:
       '''
       This function will return the list of requirements
       '''
       HYPEN_E_DOT="-e ."
       requirements=[]
       with open(file_name) as file_obj:
           requirements=file_obj.readlines()
           requirements=[req.replace("\n","") for req in requirements]
        
           if HYPEN_E_DOT in requirements:
               requirements.remove(HYPEN_E_DOT)
       return requirements

      setup(
       name='MLProject',
       version='0.0.1',
       author='Vinod',
       author_email='vinod@gmail.com',
       packages=find_packages(),
       install_requires=get_requirements('requirements.txt')
      )
   ```
5) Create requirement.txt with the required packages: [requirement.txt](requirements.txt)

    ```
         pandas
         numpy
         seaborn
        #-e . will help us to trigger the setup.py from the requirement.txt. when we try to install the requirements.txt with pip install -r requirement.txt
         -e .
    ```
    
6) Create src folder with __init__.py: [src](src)
   
