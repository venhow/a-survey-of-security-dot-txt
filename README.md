# ssdt - Survey security.txt files

A program to quickly survey [security.txt](https://tools.ietf.org/html/draft-foudil-securitytxt-10) files found on the Alexa Top 1 Million websites. The program takes about 15 hours to run over a 1.5Mbit residential DSL connection.

```bash
$ ps -p 165199 -o etime
	ELAPSED
	15:06:42
```

## Sample output

```bash
{"website" ["contacts"] "expires"}
{"github.com" ["https://hackerone.com/github"] ""}
{"google.com" ["https://g.co/vulnz" "mailto:security@google.com"] ""}
{"facebook.com" ["https://www.facebook.com/whitehat/report/"] ""}
{"linkedin.com" ["mailto:security@linkedin.com" "https://www.linkedin.com/help/linkedin/answer/62924"] ""}
{"cloudflare.com" ["https://hackerone.com/cloudflare" "mailto:security@cloudflare.com" "https://www.cloudflare.com/abuse/"] "sat, 20 mar 2021 13:24:05 -0700"}
```

## Build the program

```bash
$ make
```

## Run the program

```bash
$ ./ssdt -hosts top-1m-alexa.csv 2> err.txt > out.txt
```

## Remove invalid security.txt entries

```bash
$ grep -v "\[\]" out.txt
```

## Count results

```bash
$ grep -v "\[\]" out.txt | wc -l
```
## Notes

  * You may need to adjust the nofile limit in /etc/security/limits.conf before running ssdt. Otherwise, you may exceed the open file limit.
  * Read my [blog post](https://www.go350.com/posts/a-survey-of-security-dot-txt/) about why I wrote this program.
