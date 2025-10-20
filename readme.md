configurations files linked with my homelab kubernetes cluster management.
use helm and helmfile.
"dev" env run under Kind cluster, "prod" one under k3s, 

no bitnami chart inside.

more details will come after.


kind create cluster -n homelab --config kind/values-kind.yaml

installation en dev : 
helmfile -e default -l env!=prod apply --skip-diff-on-install
installation en prod : 
helmfile -e default -l env!=dev apply --skip-diff-on-install


helmfile -e default --state-values-set test=non build

