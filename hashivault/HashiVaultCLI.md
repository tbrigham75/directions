1.  vault version
2.  vault -h #Help
3.  vault read -h #Note:  gives examples
#Set env vars for logging in
4.  export VAULT_ADDR='http://IP2Server:8200' 
5.  export VAULT_TOKEN='setPassHere'
6.  vault login
7.  vault status
#Work with secrets
8.  vault kv put secret/foo bar=baz
9.  vault kv put secret/foo bar=baz hello=world #Sometimes need to put single quotes for special chars such as $'s
10.  vault kv get secret/foo
11.  vault kv delete secret /foo
12.  vault kv undelete -versions=3 secret/foo
#Create user and assign it to a policy
13.  vault write auth/userpass/users/ansible password=password policies=grant-all-policy-on-secrets
