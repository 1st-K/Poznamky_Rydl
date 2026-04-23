pres prikaz `ssh-keygen` (napriklad `ssh-keygen -t ed25519` ) si vygenerujeme dvojici klicu, soukromy a verejny. Pote verejny zkopirujeme do `~/.ssh/authorized_keys`.

nasledne
``` bash
chmod 600 /home/ukol2/.ssh/authorized_keys
chown -R ukol2:ukol2 /home/ukol2/.ssh
```

prihlasujeme se pomoci

``` bash
ssh -i <path_to_key> <user>@<IP>
```


# konifgurace serveru

``` bash
sudo nano /etc/ssh/sshd_config
```

``` mathematica
Port <port name>
MaxAuthTries <max auth tries>
AllowUsers <users>
PubkeyAuthentication <yes / no>
AuthorizedKeysFile <path to .ssh/authorized_keys>
```

``` bash
sudo systemctl restart ssh
```

[[analyza sitoveho provozu]]

