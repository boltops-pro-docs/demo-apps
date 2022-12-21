<!-- note marker start -->
**NOTE**: This repo contains only the documentation for the private BoltsOps Pro repo code.
Original file: https://github.com/boltopspro/demo-apps/blob/master/gke/workload-identity/demo-manual/README.md
The docs are publish so they are available for interested customers.
For access to the source code, you must be a paying BoltOps Pro subscriber.
If are interested, you can contact us at contact@boltops.com or https://www.boltops.com

<!-- note marker end -->

# Demo for KSA and GSA: Manual Creation

Shows how to set up Kubernetes Service Account and Google Service Account so that kubernetes pods have IAM permissions to Google cloud resources.

Docs: https://cloud.google.com/kubernetes-engine/docs/how-to/workload-identity#verify_the_setup

## Step-by-step Instructions

**1. Enable Google APIs**

* [Kubernetes API](https://console.cloud.google.com/apis/enableflow?apiid=container.googleapis.com)
* [IAM API](https://console.developers.google.com/apis/api/iam.googleapis.com/overview)

**2. Set GOOGLE_PROJECT**

Form:

    export GOOGLE_PROJECT=project-123456

Example:

    export GOOGLE_PROJECT=boltops-learn

**3. Create an Google IAM service account**

    gcloud iam service-accounts create demo-dev
    gcloud iam service-accounts list | grep " demo-dev@$GOOGLE_PROJECT.iam.gserviceaccount.com"

**4. Add Permissions with IAM roles**

Form:

    gcloud projects add-iam-policy-binding PROJECT_ID --member serviceAccount:GSA_NAME@GSA_PROJECT.iam.gserviceaccount.com --role ROLE_NAME

Example:

    gcloud projects add-iam-policy-binding $GOOGLE_PROJECT --member serviceAccount:demo-dev@$GOOGLE_PROJECT.iam.gserviceaccount.com --role roles/cloudsql.client
    gcloud projects add-iam-policy-binding $GOOGLE_PROJECT --member serviceAccount:demo-dev@$GOOGLE_PROJECT.iam.gserviceaccount.com --role roles/secretmanager.viewer

Note `roles/cloudsql.client` vs `cloudsql.client`

Confirm:

    # Look for demo-dev
    # or roles/cloudsql.client or roles/secretmanager.viewer
    gcloud projects get-iam-policy $GOOGLE_PROJECT --format json > projects-get-iam-policy.json

**5. Allow Kubernetes service account to impersonate the IAM service account with **IAM policy binding**. This enables linking the 2 accounts.**

Form:

    gcloud iam service-accounts add-iam-policy-binding GSA_NAME@GSA_PROJECT.iam.gserviceaccount.com --role roles/iam.workloadIdentityUser --member "serviceAccount:PROJECT_ID.svc.id.goog[NAMESPACE/KSA_NAME]"

Example:

    gcloud iam service-accounts add-iam-policy-binding demo-dev@$GOOGLE_PROJECT.iam.gserviceaccount.com --role roles/iam.workloadIdentityUser --member "serviceAccount:$GOOGLE_PROJECT.svc.id.goog[demo-dev/demo]"

Confirm:

    gcloud iam service-accounts get-iam-policy demo-dev@$GOOGLE_PROJECT.iam.gserviceaccount.com

Note: Believe Google the roles/iam.workloadIdentityUser is like a AWS Service-Linked Role.

**6. Kubernetes Service Account YAML**

Form:

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  annotations:
    iam.gke.io/gcp-service-account: GSA_NAME@PROJECT_ID.iam.gserviceaccount.com
  name: KSA_NAME
  namespace: NAMESPACE
```

Example:

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  annotations:
    iam.gke.io/gcp-service-account: demo-dev@GOOGLE-ID-123.iam.gserviceaccount.com
  name: demo
  namespace: demo-dev
```

**7. Kubernetes Deployment YAML**

Form:

```yaml
spec:
  serviceAccountName: KSA_NAME
  nodeSelector:
    iam.gke.io/gke-metadata-server-enabled: "true"
```

Example:

```yaml
apiVersion: apps/v1
kind: Deployment
# ...
spec:
  template:
    metadata:
      serviceAccountName: demo
      nodeSelector:
        iam.gke.io/gke-metadata-server-enabled: 'true'
```

**8. Deploy: kubectl apply**

    kubectl apply -f namespace.yaml
    kubectl apply -f service_account.yaml
    kubectl apply -f deployment.yaml

**9. Confirm**

    kubens demo-dev
    kubectl exec -ti deploy/web -- bash
    curl -H "Metadata-Flavor: Google" http://169.254.169.254/computeMetadata/v1/instance/service-accounts/default/email ; echo
    gcloud secrets list
