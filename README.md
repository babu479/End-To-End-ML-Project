###End-To-End-ML-Project
---

##Day1:
***

1) Setup the github repository:

   ```markdown
   Create github repository
   ```

3) Create .gitignore file: [.gitignore](.gitignore)

   ```markdown
   Create file --> .gitignore --> template python --> commit
   ```
   
5) New environment (.venv): [.venv](.venv)
   

   ```shell
   <!-- To create new environment check the below python commands -->
   #python3 -m venv .venv
   #source .venv/bin/activate
   ```
6) create setup.py with the below content : [setup.py](setup.py)

   ```python
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
7) Create requirement.txt with the required packages: [requirement.txt](requirements.txt)

    ```python
         pandas
         numpy
         seaborn
        #-e . will help us to trigger the setup.py from the requirement.txt. when we try to install the requirements.txt with pip install -r requirement.txt
         -e .
    ```
    
8) Create src folder with __init__.py: [src](src)

9) Install requirements.txt with pip:

   ```shell
   pip install -r requirements.txt
   
   ```
   
##Day2:
***

8) Create components folder under src : [src/components](src/components)

9) Create __init__.py under components: [src/components/__init__.py](src/components/__init__.py)

10) create data ingestion file under components directory: [src/components/data_ingestion.py](src/components/data_ingestion.py)

11) Create data transformation python file under src --> components directory: [src/components/data_transformation.py](src/components/data_transformation.py)

12) create model trainer python file under src --> components directory: [src/components/model_trainer.py](src/components/model_trainer.py)

13) Create pipeline directory with all the files: [src/pipeline](src/pipeline)

    ```shell
    
    Pipeline
       |
       |__ __init__.py
       |__ predict_pipeline.py
       |__ train_pipeline.py
    
    ```
14) Create logger.py for  log file and the logs: [src/logger.py](src/logger.py)

    ```python
    
    import logging
    import os
    from datetime import datetime
    LOG_FILE=f"{datetime.now().strftime('%m_%d_%Y_%H_%M_%S')}.log"
    log_path=os.path.join(os.getcwd(),"logs",LOG_FILE)
    os.makedirs(log_path,exist_ok=True)

    LOG_FILE_PATH=os.path.join(log_path,LOG_FILE)

    logging.basicConfig(
    filename=LOG_FILE_PATH,
    format="[ %(asctime)s ] %(lineno)d %(name)s - %(levelname)s - %(message)s",
    level=logging.INFO,)

      
    ```

15) Create exception.py for exception handlings : [src/exception.py](src/exception.py)

    ```python
      import sys
      def error_message_detail(error,error_detail:sys):
          _,_,exc_tb=error_detail.exc_info()
          file_name=exc_tb.tb_frame.f_code.co_filename
          error_message="Error occured in python script name [{0}] line number [{1}] error message[{2}]".format(
          file_name,exc_tb.tb_lineno,str(error))

       return error_message

    

      class CustomException(Exception):
          def __init__(self,error_message,error_detail:sys):
              super().__init__(error_message)
              self.error_message=error_message_detail(error_message,error_detail=error_detail)
    
          def __str__(self):
              return self.error_message

    ```

16) create utils.py file in src folder:  [src/utils.py](src/utils.py)

**Day3:
***

17) Created a folder name notebook. it has data folder with student.csv file under notebook we have some other of model tainer and EDA students performance

# notebook folder structure

    .
    ├── ...
    ├── notebook                    # Documentation files (alternatively `doc`)
    │   ├── data
    |    |- # Table of contents
    │   ├── faq.md              # Frequently asked questions
    │   ├── misc.md             # Miscellaneous information
    │   ├── usage.md            # Getting started guide
    │   └── ...                 # etc.
    └── ...
