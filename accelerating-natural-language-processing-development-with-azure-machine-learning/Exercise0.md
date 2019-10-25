# Login to your Jupyterhub Portal.
In this exercise you will Log into your **jupyterhub portal** using your labvm username and Password from your Environment details page.
1. Click on Environment Details Tab on this Page to view your Azure Lab credentials details. Use these details to login into the JupyterHub Portal.<br/>
      ![](images/username.png)
### Login to Jupyterhub Portal
1. Copy the **jupyterhub URL** from your Lab credentials details page and navigate it in a new tab.
      ![](images/jupyterurl.png)
1. Enter your Labvm Admin Username and Labvm Admin Password from your Lab credentials details page in the Jupyterhub login page and click on **Sign In** button.

     ![](images/sign1.png)
1. Now you will be able to see your jupyterhub portal home page. Select the **nlp** folder on jupyterhub portal.
     ![](images/nlp.png)
1. Select **examples>>text_classification>>tc_transformers_azureml_pipeline** folder and open this
**tc_transformers_azureml_pipelines.ipynb** file.
     ![](images/pipeline.png)
1. After click on **tc_transformers_azureml_pipelines.ipynb**, a new tab will open and you will see a pop-up to select kernal.
     ![](images/popup.png)
1. Select **npl_gpu** kernal from drop down menu and click on **Set Kernal**.
     ![](images/nplgpu.png)
1. Please make sure **npl_gpu** cluster is selected on your notebook before running any command in notebook.
     ![](images/nplselect.png)   
1.  Fill in the Azure services parameters in the **Define Parameters** section using the corresponding values in the **Environment Details** tab.
1. You can click anywhere in the cell and execute it by entering **shift + enter** on your keyboard.
1. Follow all the steps from notebook to finish the exercise.
## NLP Best Practices Repository
You can find the utils and wrappers used in this lab, in addition to more NLP scenario examples in the GitHub repository: [aka.ms/nlp_ignite](aka.ms/nlp_ignite)
