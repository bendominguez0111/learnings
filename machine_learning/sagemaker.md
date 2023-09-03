# Amazon Sagemaker & Hugging Face
## Deep Learning Containers
Sagemaker has deep learning containers that allow you to train models.

Can deploy models for inference straight from the HuggingFace hub or you can pull in a model artifact (Sagemaker handles saving your models to an S3 bucket once you train them).

Python package to install sagemaker:
```bash
pip install sagemaker --upgrade # Additional tooling for Sagemaker
pip install boto3 --upgrade # AWS Python SDK
```

Important AWS CLI commands:
```bash
aws sagemaker list-endpoints
```