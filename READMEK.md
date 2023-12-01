# Workflow Terraform


Pour modifier notre infra AWS, on passe uniquement par l'IaC de Terraform.
Pour cela on crée 2 branches une main et une test/stage.
Dans la branche test, on apporte nos modifications. Et on teste nos modifs via les commandes terraform valid et terraform plan sur notre infra hébergé dans un EKS.
Une fois que c'est tester et valider, on merge la branche test à main. Ce qui va déclencher un terraform apply sur notre infra.


## Requirements

- Créer un user via IAM service > Attach policies directly > AdministratorAccess (normalement attribuer le minimum de droits). Security credentials > Create access key > CLI.
- Copier dans le Github Secret l'access key, afin que Github puisse upload le code sur EKS.
- Créer un bucket S3, pour stocker les informations Terraform (le state -> bucket_tf_state)
- Copier le nom du bucket dans le Github Secret. (BUCKET_TF_STATE: nom_bucket).

## Goal

Le code Terraform va set up l'infra VPC et EKS.
