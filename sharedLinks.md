# Introduction / Commencer avec GCP
Pourquoi choisir Google Cloud Platform ?   https://cloud.google.com/why-google/
Tarification   https://cloud.google.com/pricing/philosophy/
Centres de données   https://www.google.com/about/datacenters/
Présentation des produits Google Cloud Platform   http://cloud.google.com/products/
Solutions Google Cloud Platform   http://cloud.google.com/solutions/
A quoi sert google cloud run? c'est un service serverless dans lequel tu déploie ton app avec un container
API Explorer: https://developers.google.com/apis-explorer
KeyWars : https://medium.com/google-cloud/the-key-wars-story-a65bb9dabe56
Notion de Recovery Plan, un bon article : https://cloud.google.com/blog/products/storage-data-transfer/designing-and-implementing-your-disaster-recovery-plan-using-gcp
Bitnami LAMP  : https://docs.bitnami.com/google/infrastructure/lamp/

Pour la question sur LDAP Sync:
Il y a deux modes de fonctionnement :
- G Suite Password Sync - (Synchro complète des identités) - https://support.google.com/a/answer/6120130
- Fédération Google Cloud / AD (création des identités et délégation de l’auth à l’AD) https://cloud.google.com/solutions/federating-gcp-with-active-directory-synchronizing-user-accounts?hl=fr

# Gestion de VMs et de leur réseau
https://cloud.google.com/vpc/network-pricing
https://cloud.google.com/blog/products/sap-google-cloud/announcing-the-general-availability-of-6-and-12tb-vms-for-sap-hana-instances-on-gcp
Recommandations sur les types de VM : https://cloud.google.com/compute/docs/machine-types#recommendations_for_machine_types

Le maillage réseau google / CDN dans le monde : https://peering.google.com/#/infrastructure

Pour les VPNs, voici quelques liens: 
https://cloud.google.com/solutions/building-high-throughput-vpns?hl=fr
https://cloud.google.com/network-connectivity/docs/vpn/concepts/overview?hl=fr

Compute Engine : https://cloud.google.com/compute/docs/ 
VPC Google Cloud Platform : https://cloud.google.com/compute/docs/vpc/
Google Cloud Stackdriver : https://cloud.google.com/stackdriver/docs/  
gcloud, guide de l'outil : https://cloud.google.com/source-repositories/docs/

# Stockage dans le Cloud
Avoir accès a des objets stockés dans le Cloud Storage d'un projet A depuis un projet B ? Les droits d'accès seront gérés au niveau IAM du projet, mais il est possible d'ajouter des identités de différentes sources: https://cloud.google.com/storage/docs/access-control/iam?hl=fr
Il est également possible d'activer un accès public à ce qui est hébergé sur Cloud Storage

https://cloudplatform.googleblog.com/2017/02/inside-Cloud-Spanner-and-the-CAP-Theorem.html. 
https://cloud.google.com/architecture/elastically-scaling-your-mysql-environment
https://cloud.google.com/community/tutorials/horizontally-scale-mysql-database-backend-with-google-cloud-sql-and-proxysql

La doc de la commande gsutil acl : https://cloud.google.com/storage/docs/gsutil/commands/acl
Il y a une option "recursive":
   -R, -r      Performs acl ch request recursively, to all objects under the specified URL.

# Gestion des conteneurs avec GCP
La bande-passante des interfaces réseaux des VMs dépend de leur CPU: https://cloud.google.com/compute/docs/networking/benchmarking-higher-bandwidth-vms

La liste des outils pré-installés sur Cloud Shell: https://cloud.google.com/shell/docs/how-cloud-shell-works#tools
K9s est un outil en ligne de commande pour visualiser ce qui se passe sur un cluster Kubernetes : https://github.com/derailed/k9s

Ptit moment pub pour Anthos et le multicloud : 
https://gdg.community.dev/events/details/google-gdg-cloud-nantes-presents-from-docker-to-anthos/
https://www.meetup.com/fr-FR/GDG-Cloud-Nantes/events/278297888/

Ressources GKE
Pourquoi choisir Google Cloud Platform ?   https://cloud.google.com/why-google/
Tarification   https://cloud.google.com/pricing/philosophy/
Centres de données   https://www.google.com/about/datacenters/
Présentation des produits Google Cloud Platform   http://cloud.google.com/products/
Solutions Google Cloud Platform   http://cloud.google.com/solutions/

https://cloud.google.com/kubernetes-engine/pricing/?hl=fr#cluster_management_fee_and_free_tier

Est ce qu’il y a un moyen de changer le type de CNI dans GKE ?
Par défaut pas de CNI dans GKE mais un pod-network avec du routage "natif", mais il y a la possibilité d'utiliser Cilium
https://cloud.google.com/blog/products/containers-kubernetes/bringing-ebpf-and-cilium-to-google-kubernetes-engine

https://console.cloud.google.com/gcr/images/google-containers/GLOBAL
c'est le lien de toutes les images de base GCP

il y a une vidéo sur le sujet sur la chaine youtube Zenika : https://www.youtube.com/watch?v=HDWJcSEx6J0 ;)

La vidéo K8S en 3min par Eric et PY: https://www.youtube.com/watch?v=uyiDNcSmwFw

Est ce qu'il y a des recommandations pour gérer la sécurité des pods (securityContext ou OPA ou autre) ?
Il y a le CIS benchmark qui publie un rapport de bonnes pratiques: https://www.cisecurity.org/benchmark/kubernetes/
Elles sont transposées dans un outil qui s'appelle kube-bench : https://github.com/aquasecurity/kube-bench d'Aqua Security

# Déploiement et gestion d'Apps dans le cloud
Les 12 facteurs (en lien avec l'intérêt des Flexible App)
https://12factor.net/

Est-ce qu'il y a des accès/env "Dev" qui ne seraient pas facturés (mais par exemple uniquement à partir de ton staging ?) => Il y a un free tier avec app engine : https://cloud.google.com/free/docs/gcp-free-tier#free-tier-usage-limits donc si les besoins en dev sont limités, ce n'est pas facturé :)

Le lien pour les outils et les variables pré-définies https://cloud.google.com/shell/docs/how-cloud-shell-works#tools

https://github.com/GoogleCloudPlatform/deploymentmanager-samples/tree/master/examples/v2

Cloud Source Repositories   https://cloud.google.com/source-repositories/docs/
Deployment Manager   https://cloud.google.com/deployment-manager/docs/
Google Stackdriver   https://cloud.google.com/stackdriver/docs/  

Rappel: Le nouveau nom de StackDriver et son lien : https://cloud.google.com/products/operations
Google Cloud's operations suite (formerly Stackdriver)

Video Cloud Operations: https://www.youtube.com/watch?v=VL2Ql0cmo4g

Est-ce que pub/sub est compatible JMS ou AMQP ou Kafka ou ce n’est accessible que depuis API propre ?
Il n'est utilisable que depuis API propre (HTTP/GRPC), mais est implémenté dans de nombreux langages avec une client-library
https://cloud.google.com/pubsub/docs/reference/libraries#using_the_client_library

# Big Data et Machine Learning
https://bigquery.cloud.google.com/welcome

Un bon lien avec des flowcharts pour aider aux choix des solutions : https://grumpygrace.dev/posts/gcp-flowcharts/
Lien CAP https://cloud.google.com/blog/products/databases/inside-cloud-spanner-and-the-cap-theorem

# Miscellanées
A propos du Google IO 2021 :
Nouvel console DevTools pour Angular : https://blog.angular.io/introducing-angular-devtools-2d59ff4cf62f
Sortie de Flutter 2.2 : https://medium.com/flutter/announcing-flutter-2-2-at-google-i-o-2021-92f0fcbd7ef9
