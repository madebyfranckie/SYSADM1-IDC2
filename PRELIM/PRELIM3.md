![image](https://github.com/user-attachments/assets/22f0850b-47ca-44c7-b4be-4a47374795e4)
# SYSADM1 -- Managing Services in Linux

# Requirement: 

-   A virtual machine running Linux

![](vertopal_d55cbb651c8b41a99c6e4857c4357598/media/image2.png){width="4.135416666666667in"
height="1.8020833333333333in"}

Complete this lab as follows:

1.  Use the service --status-all command to list all active and inactive
    services.

List down active and inactive services in the table below. Provide five
(5) services for each column.

  -----------------------------------------------------------------------
  **Active**                             **Inactive**
  -------------------------------------- --------------------------------
  Alsa-utils                             Anacron

  apparmor                               Bluetooth

  apport                                 Console-setup.sh

  Cron                                   Grub-common

  cups                                   plymouth
  -----------------------------------------------------------------------

SS:
![](vertopal_d55cbb651c8b41a99c6e4857c4357598/media/image3.png){width="5.561909448818898in"
height="3.803028215223097in"}

2.  Start the Bluetooth service using the systemctl command.

Ex. sudo systemctl start httpd

![](vertopal_d55cbb651c8b41a99c6e4857c4357598/media/image4.png){width="4.359946412948381in"
height="1.1875in"}

3.  Check the status of the Bluetooth service. What is its status?

SS:
![](vertopal_d55cbb651c8b41a99c6e4857c4357598/media/image5.png){width="5.719548337707787in"
height="2.8441469816272966in"}

The status of the Bluetooth seems to not be responding because of there
is no dongle present. Which, as a result, No Bluetooth found.

![](vertopal_d55cbb651c8b41a99c6e4857c4357598/media/image6.png){width="1.7859689413823272in"
height="2.2131616360454944in"}

4.  Check the status of the cups services. Since when was it running?

SS:
![](vertopal_d55cbb651c8b41a99c6e4857c4357598/media/image7.png){width="6.717777777777778in"
height="4.771288276465442in"}

-   Cups.service is active and running since THU 2024-09-12 08:58:32
    PST; 35 mins ago

-   Triggered by cups.path and cups.socket.

    1.  Stop cups services.

![](vertopal_d55cbb651c8b41a99c6e4857c4357598/media/image8.png){width="6.7092694663167105in"
height="0.5938331146106737in"}

2.  Verify if the service was stopped.

![](vertopal_d55cbb651c8b41a99c6e4857c4357598/media/image9.png){width="6.770588363954506in"
height="1.1214063867016624in"}

3.  Restart the cups services

![](vertopal_d55cbb651c8b41a99c6e4857c4357598/media/image10.png){width="6.814505686789151in"
height="0.48689413823272093in"}

4.  Verify if the service was restarted.

![](vertopal_d55cbb651c8b41a99c6e4857c4357598/media/image11.png){width="6.8079505686789155in"
height="0.8160925196850394in"}

![](vertopal_d55cbb651c8b41a99c6e4857c4357598/media/image12.png){width="6.924982502187227in"
height="0.3093274278215223in"}
