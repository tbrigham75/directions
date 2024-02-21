From SME:
kubeseal --controller-namespace sealed-secrets --controller-name sealedsecretcontroller-sealed-secrets < secret_to_seal.json > sealed_secret.json

From Other sources and Website Tutorials:
kubectl --namespace default create secret generic mysecret --dry-run=client --from-literal foo=bar --output json
kubeseal --controller-namespace sealed-secrets --controller-name sealedsecretcontroller-sealed-secrets <test.json> sealed_secret.json