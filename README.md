# KFServing example for Serving a ML-Recommender 
This repository builds a Session Based Recommender. The trained ML Model will be served by KFServing. The Metadata will be tracked by MLflow.
The Dataset can be found here: https://www.kaggle.com/mkechinov/ecommerce-behavior-data-from-multi-category-store <br>
Related Blog Post: [https://www.novatec-gmbh.de/blog/ausrollen-und-betreiben-von-ml-modellen-in-produktion-mit-kfserving/](https://www.novatec-gmbh.de/blog/ausrollen-und-betreiben-von-ml-modellen-in-produktion-mit-kfserving/)
## Requirements
- Installation of KFServing as part of Kubeflow or Standalone
- Install Requirements from [requirements](requirements.txt)
- Start a MLflow-Server. If you are new to MLflow: https://github.com/felix-exel/mlflow
- Train the session based recommender model by running the notebook [session_based_recommender_with_mlflow](session_based_recommender_with_mlflow.ipynb)
- If your MLflow Artifact Storage does not point to a Cloud Store, you need to upload your model files manually for an easy deployment with KFServing.
- Alternatively you can mount your model by using Persistent Volumes which isn't covered by this repository
## Quick Start
- Write your Credentials in [aws-secret_serviceaccount](aws-secret_serviceaccount.yaml)
- ```kubectl apply -f aws-secret_serviceaccount.yaml``` <br>
- Change the StorageUri in [tf-deployment-recommender](tf-deployment-recommender.yaml) to your Cloud Path
- ```kubectl apply -f tf-deployment-recommender.yaml``` <br>
- or deploy through the notebook [deploy-kfserving-recommender-service](deploy-kfserving-recommender-service.ipynb)