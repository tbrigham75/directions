Some Normal Containers have Init Containers that need to start up before the container to do a thing.

Init containers run in a series and start by what is listed first in YAML

If you see Init:CrashLoopBackOff its a guarantee that the Init Containers are having an issue.