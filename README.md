# Packet-Tracer - Configure-Initial-Switch-Settings

**TOPOLOGI**

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/9613b96f-9726-477d-8fa6-2dbc98fca4da)

**Part 1: Verify the Default Switch Configuration**  

*Step 1: Enter privileged EXEC mode.*   

  A. Click S1 and then the CLI tab. Press Enter.   
  
  ![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/0f52bfbb-0fdc-461e-8a38-b332cc6cf227)
  
  B. Enter privileged EXEC mode by entering the enable command:  `enable`
  
  ![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/776000d5-9b34-4a46-9b2f-a94540a8191e)


*Step 2: Examine the current switch configuration.*
  A. Enter the show running-config command. `show running-config`

  ![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/39aba85e-d2ad-4f8b-b957-7309250d70c8)

  
**Part 2: Create a Basic Switch Configuration**

*Step 1: Assign a name to a switch.*

  ![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/37c9e463-bf7a-4321-b77b-bb59e3cf8622)

*Step 2: Secure access to the console line.*  

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/fa749356-79c5-4786-9202-a050f49490d8)


*Step 3: Verify that console access is secured.*

Exit privileged mode to verify that the console port password is in effect.

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/2e65b5cd-0dfd-49e2-a18b-84c2a36dd1c0)

*Step 4: Secure privileged mode access.*

Set the enable password to c1$c0. This password protects access to privileged mode.
Note: The 0 in c1$c0 is a zero, not a capital O. This password will not grade as correct until after you encrypt it in Step 8.

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/c0d03567-1d1b-44b4-8ddb-b37c1b58b78c)


*Step 5: Verify that privileged mode access is secure.*

  A. Enter the exit command again to log out of the switch.  
  B. Press <Enter> and you will now be asked for a password :  
  User Access Verification  
  Password:  
  C. The first password is the console password you configured for line con 0. Enter this password to return to user EXEC mode.  
  D. Enter the command to access privileged mode.  
  E. Enter the second password you configured to protect privileged EXEC mode.  
  F. Verify your configuration by examining the contents of the running-configuration file:  
  S1# show running-config  
  Notice that the console and enable passwords are both in plain text. This could pose a security risk if someone is looking over your shoulder or obtains access to config files stored in a backup location.

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/c647634d-e7d0-4a5f-a1ed-ae87a69696df)

*Step 6: Configure an encrypted password to secure access to privileged mode.*

The enable password should be replaced with the newer encrypted secret password using the enable secret command. Set the enable secret password to itsasecret.

S1# config t  
S1(config)# enable secret itsasecret  
S1(config)# exit  
S1#   
Note: The enable secret password overrides the enable password. If both are configured on the switch, you must enter the enable secret password to enter privileged EXEC mode. 

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/bb2b4641-7117-4509-87d0-abdc74e6b51f)

*Step 7: Verify that the enable secret password is added to the configuration file.*

Enter the show running-config command again to verify the new enable secret password is configured.
Note: You can abbreviate show running-config as
S1# show run  

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/073c9ce4-17de-484b-a80e-d5dbbb881b84)

*Step 8: Encrypt the enable and console passwords.*

As you noticed in Step 7, the enable secret password was encrypted, but the enable and console passwords were still in plain text. We will now encrypt these plain text passwords using the service password-encryption command.

S1# config t  
S1(config)# service password-encryption  
S1(config)# exit  

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/f7acae2b-b30a-491d-b8b9-511c4f1fe547)

**Part 3: Configure a MOTD Banner**

*Step 1: Configure a message of the day (MOTD) banner.*

The Cisco IOS command set includes a feature that allows you to configure messages that anyone logging onto the switch sees. These messages are called message of the day, or MOTD banners. Enclose the banner text in quotations or use a delimiter different from any character appearing in the MOTD string.

S1# config t  
S1(config)# banner motd "This is a secure system. Authorized Access Only!"  
S1(config)# exit  
%SYS-5-CONFIG_I: Configured from console by console  
S1#  

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/4c34693d-84f3-4061-ac11-29548e347e40)

**Part 4: Save and Verify Configuration Files to NVRAM**

*Step 1: Verify that the configuration is accurate using the show run command.*

Save the configuration file. You have completed the basic configuration of the switch. Now back up the running configuration file to NVRAM to ensure that the changes made are not lost if the system is rebooted or loses power.  
S1# copy running-config startup-config  
Destination filename [startup-config]?[Enter]
Building configuration...
[OK]
Close Configuration Window for S1

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/71c07526-04a0-4598-aff2-7568cdb4670c)

**Part 5: Configure S2**  
You have completed the configuration on S1. You will now configure S2. If you cannot remember the commands, refer to Parts 1 to 4 for assistance. 
Configure S2 with the following parameters : 
Open Configuration Window for S2   

  A. Device name: S2

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/157d27da-c1d1-4691-9668-9ac1c76c81fa)

  B. Protect access to the console using the letmein password.

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/c6c8189e-587c-4c6c-aff3-ad37d3cf80a8)

  C. Configure an enable password of c1$c0 and an enable secret password of itsasecret.

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/04bee7a6-c379-4323-9e76-96b800596a1b)

  D. Configure an appropriate message to those logging into the switch.

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/5aa07c26-b803-4c1f-95de-5f592b89f076)

  E. Encrypt all plain text passwords.

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/6f4dcc51-e25a-4bf4-b139-d84927ad39d3)

  F. Ensure that the configuration is correct.

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/83912d3a-9e57-42a2-9bdb-e01f57419065)

  G. Save the configuration file to avoid loss if the switch is powered down.

![image](https://github.com/eopaleto/Packet-Tracer---Configure-Initial-Switch-Settings/assets/126212773/c32fa32a-91c4-4733-bfd9-85a0f30e9f77)
