# transfer.sh

Easy and fast file sharing from the command-line. This code contains the server with everything you need to create your own instance.

[![Build Status](https://travis-ci.org/dutchcoders/transfersh.svg?branch=master)](https://travis-ci.org/dutchcoders/transfersh)

## Usage

```
Upload:
$ curl --upload-file ./hello.txt https://transfer.sh/hello.txt

Encrypt & upload:
$ cat /tmp/hello.txt|gpg -ac -o-|curl -X PUT --upload-file "-" https://transfer.sh/test.txt

Download & decrypt:
$ curl https://transfer.sh/1lDau/test.txt|gpg -o- > /tmp/hello.txt

Upload to virustotal:
$ curl -X PUT --upload-file nhgbhhj https://transfer.sh/test.txt/virustotal

Add alias to .bashrc or .zshrc:
===
transfer() {
    # write to output to tmpfile because of progress bar
    tmpfile=$( mktemp -t transfer )
    curl --progress-bar --upload-file $1 https://transfer.sh/$(basename $1) >> $tmpfile;
    cat $tmpfile;
    rm -f $tmpfile;
}

alias transfer=transfer
===
$ transfer test.txt
```

## Development

- grunt serve
- grunt build

- sh transfer-server/run.sh 

## Contributions

Contributions are welcome.

## Creators 

**Remco Verhoef**
- <https://twitter.com/remco_verhoef>
- <https://twitter.com/dutchcoders>

**Uvis Grinfelds**

## Copyright and license

Code and documentation copyright 2011-2014 Remco Verhoef. Code released under [the MIT license](LICENSE). 
