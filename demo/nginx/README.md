<!-- note marker start -->
**NOTE**: This repo contains only the documentation for the private BoltsOps Pro repo code.
Original file: https://github.com/boltopspro/demo-apps/blob/master/demo/nginx/README.md
The docs are publish so they are available for interested customers.
For access to the source code, you must be a paying BoltOps Pro subscriber.
If are interested, you can contact us at contact@boltops.com or https://www.boltops.com

<!-- note marker end -->

# Demo Nginx App

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

This Dockerfile just runs nginx. It's useful for debugging. There's some tools also installed to help with debugging.

## Deploy

    kubes deploy

## Debug

    kubens demo-dev # switch to namespace
    kubectl exec -ti deploy/web -- bash # hop into container to debug
