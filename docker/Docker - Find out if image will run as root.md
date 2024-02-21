2 ways:

#1:
1.  docker inspect tbrigham/gitea_rootless
2.  Look for:  "User": "1000:1000",
3.  If it is "User": "0,0"  <<--That is root.  Anything else is not

#2:
1.  Boot up image
2.  Go to terminal
3.  Notice prompt $ or #
4.  Type CMD id to confirm