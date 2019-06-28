# orangi_pi_i2c_touchscreen
How to connect GT911 Goodix touchscreen to OrangePI with H3Droid

You need:

1. Touchscreen Goodix GT911

2. Orange Pi

3. H3Droid

Fisrt stage its correct connection touchscreen to OrangePI


Pinout

OrangePI:          Goodix GT911:


1	3.3V              VCC

3	PA12              SDA

5	PA11              SDL

7	PA06              RST

9	GND               GND

11 PA01             INT


addtional information: https://linux-sunxi.org/Touchscreen


Second stage - configure FEX (script.bin), please load you H3Droid to H3resc

and choose "edit fex" mode.

Next add this lines to end of fex file:


[ctp_para]

ctp_used = 1

ctp_twi_id = 0

ctp_name = "Goodix-TS"

ctp_twi_addr = 0x14

ctp1_used = 1

ctp1_twi_id = 0

ctp1_name = "Goodix-TS"

ctp1_twi_addr = 0x5d

ctp_screen_max_x = 1024                                             #X Settings

ctp_screen_max_y = 600                                              #Y Settings

ctp_revert_x_flag = 0                                               #Set this and ctp_revert_y_flag to 1 to flip x and y axis

ctp_revert_y_flag = 0

ctp_exchange_x_y_flag = 0 

ctp_int_port = port:PA01<6><default><default><default>              #INT port settings

ctp_wakeup = port:PA11<1><default><default><1>                      #Wakeup port settings

ctp_io_port = port:PA12<0><default><default><default>               #IO Port Settings

rst_port = port:PA06<1><default><default><default>                  #RST port settings


[ctp_list_para]

ctp_det_user = 1

gt8xx = 1

gt911 = 1

gt911_ts = 1

gt9xx_ts = 1

gt9xxf_ts = 1

gt818_ts = 1


save and reboot to h3droid system.

Next step, you need install terminal app to you system, and start it.

in terminal you need do it:

@: vi /data/rc.local

in vi editor you need enadle insert text mode - press "insert" key in you keyboard

and add this lines:


modprobe gt9xx_ts

modprobe gt9xxf_ts


next twice press "esc", next press "shift and :" to change vi mode to "conmmand mode", then press key w and key q, and press enter.

after you need reboot you system.


Enjoy ! your touchscreen is working ! =)
