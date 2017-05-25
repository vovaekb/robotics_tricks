# Add swap space on Raspberry Pi (Ubuntu 16.04)
Sometimes it is useful to add additional swap memory on Raspberry Pi. It can happen than current RAM memory is not enough and you can get error "virtual memory exhausted: Cannot allocate memory" while compiling from sources. In this case we need to add swap space.

## Check swap information in the system
Firstly let`s check whether the system has swap space configured:

```bash
sudo swapon --show
```
If nothing appears in output, than there is no swap space available. We can also verify that by typing command:
```bash
free -h
```

## Creating swap file
Let`s create a swap file with 1 GB. We will use the tool fallocate, which creates a file of a preallocated size instantly.
```bash
sudo fallocate -l 1G /swapfile
```
We can check that 1G was reserved for swap:
```bash
ls -l /swapfile
```
## Enabling the swap file
For sake of security, we can optionally restrict permissions so only root can read the content of file:
```bash
sudo chmod 600 /swapfile
```
Check the file permissions:
```bash
ls -lh /swapfile
```
Now we will mark the file as swap space:
```bash
sudo mkswap /swapfile
```
Verify that the swap is available:
```bash
sudo swapon --show
```
and using command free:
```bash
free -h
```
Let`s make the change permanent adding the swapfile to /ets/fstab.
Firstly backup the current /etc/fstab:
```bash
sudo cp /etc/fstab /etc/fstab.bak
```
Now add the swap file information to the end of /etc/fstab:
```bash
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```




