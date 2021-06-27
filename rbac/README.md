# Create NS admin service account and local user

kubectl apply -f demo-admin-sa.yaml
kubectl apply -f demo-admin-role.yaml
kubectl apply -f demo-admin-rolebinding.yaml

# Get the service account token and generate kubeconfig with it:

kubectl get secret -n demo demo-admin-token-vl9jp -o jsonpath="{.data['token']}" | base64 --decode > token3d

remember to base64 decode the token!

# Create the kubectl config

Quick way is to copy an existing kube-config and add user and token to it.

# Troubleshooting

Check the kube-apiserver logs for auth failures

kubectl logs -f kube-apiserver-cluster1-master1 -n kube-system 
