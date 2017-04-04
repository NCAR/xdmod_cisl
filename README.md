# xdmod_cisl
## Deployment Configuration for CISL Open XDMoD
#Building images: 
You need the scripts here https://github.com/NCAR/sweg-docker-util 
to build things.  

# Notes on starting XDMOD with systemd on CentOS/7:
Do not run docker-compose in daemon mode, systemd will stop it as soon
as it starts!

Using --abort-on-container-exit in the ExecStart argument, and
Restart=always.  When any one container dies, the whole set of services
will die, and systemd will restart everything for us. 


Setting up: 
cp xdmod.service /etc/systemd/system/xdmod.service
chmod 664 /etc/systemd/system/xdmod.service
sudo systemctl daemon-reload
systemctl enable xdmod.service 
systemctl start xdmod.service


