# ssdt - Survey security.txt files

A survey of [security.txt](https://tools.ietf.org/html/draft-foudil-securitytxt-10) files found on the Alexa Top 1 Million websites.

## Build the program

```bash
$ make
```

## Run the program

```bash
$ ./ssdt -hosts top-1m-alexa.csv 2> err.txt > out.txt
```

## Remove false positives

```bash
$ grep -v "\[\]" out.txt
```

## Count valid results

```bash
$ grep -v "\[\]" out.txt | wc -l
```
## Notes

  * You may need to adjust the nofile limit in /etc/security/limits.conf
