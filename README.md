## from archiso

```bash
pacman -Sy --noconfirm && \
    pacman -S --noconfirm ansible git jq
```

```bash
umount /mnt/boot && \
    umount /mnt && \
    swapoff /dev/sda2 && \
    ansible-pull \
        -i inventory \
        --url https://github.com/scraswell/ansible-pull-test.git \
        -e '{"init":true}' \
        -e '{"network_ip_address": { "type": "dhcp" }}' \
        --skip-tags complete_installation
```