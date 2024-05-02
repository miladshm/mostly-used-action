# Fix `/EFI/fedora/grubenv` not found

```bash
sudo dnf -y reinstall grub2-common
sudo grub2-editenv create
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
sudo dracut -f --regenerate-all
```
