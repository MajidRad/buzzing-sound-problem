sudo vi /usr/local/sbin/my-startup.sh


//my-startup.sh-------------------------------------------
echo 0 | sudo tee /sys/module/snd_hda_intel/parameters/power_save_controller
echo 0 | sudo tee /sys/module/snd_hda_intel/parameters/power_save


sudo chmod +x /usr/local/sbin/my-startup.sh
sudo vi /etc/systemd/system/my-startup.servic


// my-startup.servic--------------------------------------
[Unit]
Description=My Startup
[Service]
ExecStart=/usr/local/sbin/my-startup.sh
[install]
wantedBy=multi-user.target


systemctl  status my-startup.service
