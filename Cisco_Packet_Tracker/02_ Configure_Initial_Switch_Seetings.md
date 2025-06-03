## Part 1: Verify the Default Switch Configuration

``` 
Switch> enable
Switch# show running-config

! Answers:
! - How many Fast Ethernet interfaces does the switch have?
!   ➜ 24 Fast Ethernet interfaces (FastEthernet0/1 to FastEthernet0/24)
!
! - How many Gigabit Ethernet interfaces does the switch have?
!   ➜ 2 Gigabit Ethernet interfaces (GigabitEthernet0/1 and 0/2)
!
! - What is the range of values shown for the vty lines?
!   ➜ 0 to 4 (line vty 0 4)
!
! - Which command will display the current contents of NVRAM?
!   ➜ show startup-config
!
! - Why does the switch respond with “startup-config is not present?”
!   ➜ Because the configuration has not been saved to NVRAM yet (no startup config exists).
``` 
--- 

## Part 2: Create a Basic Switch Configuration (S1)

``` 
Switch# configure terminal
Switch(config)# hostname S1
S1(config)# exit
S1#

Step 2: Secure console access

S1# configure terminal
S1(config)# line console 0
S1(config-line)# password letmein
S1(config-line)# login
S1(config-line)# exit
S1(config)# exit

! Question:
! - Why is the login command required?
!   ➜ The login command tells the device to prompt for the configured password.

Step 3: Verify console access

S1# exit
[Press Enter]

User Access Verification
Password: letmein
S1>

Step 4: Secure privileged mode access

S1> enable
S1# configure terminal
S1(config)# enable password c1$c0
S1(config)# exit

Step 5: Test the security

S1# exit
[Press Enter]

User Access Verification
Password: letmein
S1> enable
Password: c1$c0
S1# show running-config

! Console and enable passwords are visible in plain text here, which is insecure.

Step 6: Replace enable password with secret

S1# config t
S1(config)# enable secret itsasecret
S1(config)# exit

Step 7: Check secret encryption

S1# show run

! Answers:
! - What is displayed for the enable secret password?
!   ➜ A hashed value (e.g. $1$abcd...).
!
! - Why is the enable secret password displayed differently?
!   ➜ Because it’s encrypted with MD5 hashing, unlike the plain text enable password.

Step 8: Encrypt all plaintext passwords

S1# config t
S1(config)# service password-encryption
S1(config)# exit

! Question:
! - Will newly configured passwords be encrypted?
!   ➜ Yes. The service password-encryption command causes all future (and current) plaintext passwords to be stored encrypted.

``` 
---

## Part 3: Configure MOTD Banner

``` 
S1# config t
S1(config)# banner motd "This is a secure system. Authorized Access Only!"
S1(config)# exit

! Questions:
! - When will this banner be displayed?
!   ➜ It will display before the login prompt when someone accesses the device.
!
! - Why should every switch have a MOTD banner?
!   ➜ To display legal and security warnings to unauthorized users.

``` 
---

## Part 4: Save Config to NVRAM

``` 
S1# show run
S1# copy running-config startup-config
[Enter]
Building configuration...
[OK]

! Questions:
! - What is the shortest version of this command?
!   ➜ copy run start
!
! - Which command shows NVRAM content?
!   ➜ show startup-config
!
! - Are all changes saved?
!   ➜ Yes, if saved using copy run start.
``` 

---

## Part 5: Configure S2 (Same Steps)

``` 
Switch> enable
Switch# config terminal
Switch(config)# hostname S2

! Console password
S2(config)# line console 0
S2(config-line)# password letmein
S2(config-line)# login
S2(config-line)# exit

! Enable password
S2(config)# enable password c1$c0

! Enable secret
S2(config)# enable secret itsasecret

! Encrypt all passwords
S2(config)# service password-encryption

! MOTD Banner
S2(config)# banner motd "This is a secure system. Authorized Access Only!"
S2(config)# exit

! Save configuration
S2# copy running-config startup-config
[Enter]
Building configuration...
[OK]

``` 
