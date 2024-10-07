# Tested on IR809

## Steps to reset the router


To erase the current startup configuration on a Cisco IR809 router, you can use the write erase command:

- Log in to the router and enter privileged EXEC mode by entering enable and then entering the enable password command
- Enter into config terminal mode 
- Enter config-register 0x2102
- Enter write erase to erase the NVRAM file system and remove all files
- Confirm that you want to erase all files
- Enter reload
- When prompted whether to save the configuration, enter no
- Confirm that you want to reload the switch 

You can also reset the router to factory defaults by pressing and holding the reset button while powering up the router.

```
IR800>en
IR800#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
IR800(config)#config-register 0x2102
IR800(config)#end
IR800#write erase 
Erasing the nvram filesystem will remove all configuration files! Continue? [confirm]
Oct  7 01:34:42.164: %PNP-6-PNP_SAVING_TECH_SUMMARY: Saving PnP tech summary (/pnp-tech/pnp-tech-error-summary)... Please wait. Do not interrupt.
Oct  7 01:34:42.618: Bootstrap Emulator called with code 62
Oct  7 01:34:42.618: Bootstrap Emulator called with code 61
[OK]
Erase of nvram: complete
IR800#
IR800#
IR800#
IR800#
Oct  7 01:34:42.620: %SYS-5-CONFIG_I: Configured from console by console
Oct  7 01:34:43.088: %SYS-7-NV_BLOCK_INIT: Initialized the geometry of nvram
Oct  7 01:34:43.250: %PNP-6-PNP_TECH_SUMMARY_SAVED_OK: PnP tech summary (/pnp-tech/pnp-tech-error-summary) saved successfully (elapsed time: 1 seconds).
Oct  7 01:34:44.995: %PKI-4-NOCONFIGAUTOSAVE: Configuration was modified.  Issue "write memory" to save new IOS PKI configuration
IR800#
IR800#
IR800#
IR800#reload
```
