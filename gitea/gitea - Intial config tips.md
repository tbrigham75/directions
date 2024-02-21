1.  When prompted for the server domain include the port # for Initial Web Config:
    192.45.2.145:2222
2.  After container deploys, Edit ~/dockervolumes/configs/gitea/gitea/conf/app.ini and add this to [repository] section:
    USE_COMPAT_SSH_URI = true

3. Reboot or stop and start service for Step 2 to take effect.