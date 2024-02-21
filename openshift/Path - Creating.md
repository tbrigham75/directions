spec
	env:
            - name: POSTGRESQL_USER
              valueFrom:
                secretKeyRef:
                  name: postgresql
                  key: database-user
            - name: POSTGRESQL_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: postgresql
                  key: database-password
            - name: POSTGRESQL_DATABASE
              valueFrom:

The above has dashes (lists) this make this into an array.  When creating a path from above it would be something like:

/spec/env/1/name