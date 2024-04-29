<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/gke/workload-identity/demo-automated/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Demo for KSA and GSA: Automated with Kubes

Shows how to set up Kubernetes Service Account and Google Service Account with Kubes in an automated manner.  It takes a 9+ step process down to 1.

Docs: https://cloud.google.com/kubernetes-engine/docs/how-to/workload-identity#verify_the_setup

## Deploy

    kubes deploy

Or to just skip the Dockerfile building

    kubes apply

## Confirm

    kubens demo-dev
    kubectl exec -ti deploy/web -- bash
    curl -H "Metadata-Flavor: Google" http://169.254.169.254/computeMetadata/v1/instance/service-accounts/default/email ; echo
    gcloud secrets list

## Debugging Tips

Check the **service account** policy binding

    export GOOGLE_PROJECT=project-12345
    gcloud iam service-accounts get-iam-policy demo-dev@$GOOGLE_PROJECT.iam.gserviceaccount.com

Should look something like this:

    $ gcloud iam service-accounts get-iam-policy demo-dev@$GOOGLE_PROJECT.iam.gserviceaccount.com
    bindings:
    - members:
      - serviceAccount:boltops-learn.svc.id.goog[demo-dev/demo]
      role: roles/iam.workloadIdentityUser
    etag: BwXmdqm953o=
    version: 1

Check the **Kubernetes namespace** and **Kubernetes service account name**. This seems to be a common issue.

How to remove **service account** binding

    gcloud iam service-accounts remove-iam-policy-binding demo-dev@tung-275700.iam.gserviceaccount.com --member 'serviceAccount:tung-275700.svc.id.goog[ksa-dev/demo]' --role roles/iam.workloadIdentityUser

Check **project** policy bindings

    gcloud projects get-iam-policy $GOOGLE_PROJECT --format json > projects-get-iam-policy.json

How to remove **project** binding

    gcloud projects remove-iam-policy-binding $GOOGLE_PROJECT --member "serviceAccount:demo-dev@$GOOGLE_PROJECT.iam.gserviceaccount.com" --role roles/cloudsql.client
    # if service account has been deleted
    gcloud projects remove-iam-policy-binding $GOOGLE_PROJECT --member "deleted:serviceAccount:demo-dev@$GOOGLE_PROJECT.iam.gserviceaccount.com?uid=102694669082619371778" --role roles/cloudsql.client
