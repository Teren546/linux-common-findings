# linux-common-findings
A personal repo where i will put solutions to problems that i found in linux (different distros)

# Linux Mint

## Problems found

### Keyboard is not working as expected, making all keys from f1-f12 to work as if the Fn button was pressed. The common "no-lock" solutions don't work. 

- Sometimes fn mode is specified in a file, this file contains one of the following 0,1,2. Where, 0 means disable fn functionality, 1 means use only fn functionality, and 2, use only non-fn functionality. Change as you see fit. 
- The file can be found by any of the following:

```
find /sys /proc/sys -type f -name fnmode 2> /dev/null
```

OR

```
sysctl -a 2> /dev/null | grep 'fnmode'
```

In my case was in 

```
/sys/module/hid_apple/parameters/fnmode
```

No reboot required, should work once edited, requires sudo.