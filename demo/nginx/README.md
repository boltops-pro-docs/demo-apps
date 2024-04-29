<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/demo/nginx/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Demo Nginx App

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

This Dockerfile just runs nginx. It's useful for debugging. There's some tools also installed to help with debugging.

## Deploy

    kubes deploy

## Debug

    kubens demo-dev # switch to namespace
    kubectl exec -ti deploy/web -- bash # hop into container to debug
