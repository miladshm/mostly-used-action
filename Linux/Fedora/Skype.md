# Skype

## Installing Skype using the Skype RPM repository

```bash
    sudo curl -o /etc/yum.repos.d/skype-stable.repo https://repo.skype.com/rpm/stable/skype-stable.repo
    sudo dnf install skypeforlinux
```

## Installing Skype using Flatpak

### Install Flatpak using dnf

```bash
    sudo dnf install -y flatpak
```

### Install Skype using Flatpak

```bash
    sudo flatpak install -y --from https://flathub.org/repo/appstream/com.skype.Client.flatpakref
```
