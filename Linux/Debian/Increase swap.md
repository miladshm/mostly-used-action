# Increasing swap memory

## Creating a Swap File

```bash
sudo fallocate -l 2G /swapfile
```

We can verify that the correct amount of space was reserved by typing:

```bash
ls -lh /swapfile
```

## Enabling the Swap File

```bash
sudo chmod 600 /swapfile
```

Verify the permissions change by typing:

```bash
ls -lh /swapfile
```

We can now mark the file as swap space by typing:

```bash
sudo mkswap /swapfile
```

After marking the file, we can enable the swap file, allowing our system to start using it:

```bash
sudo swapon /swapfile
```

Verify that the swap is available by typing:

```bash
sudo swapon --show
```

We can check the output of the `free` utility again to corroborate our findings:

```bash
free -h
```

## Making the Swap File Permanent

Back up the `/etc/fstab` file in case anything goes wrong:

```bash
sudo cp /etc/fstab /etc/fstab.bak
```

Add the swap file information to the end of your `/etc/fstab` file by typing:

```bash
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```
