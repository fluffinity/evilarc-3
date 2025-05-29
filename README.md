# evilarc-3

This is a fork of [evilarc](https://github.com/ptoomey3/evilarc).

## Purpose
evilarc lets you create a zip file that contains files with directory traversal characters in their embedded path.
Most commercial zip program (winzip, etc) will prevent extraction of zip files whose embedded files contain paths with directory traversal characters.
However, many software development libraries do not include these same protection mechanisms (ex. Java, PHP, etc).  
If a program and/or library does not prevent directory traversal characters then evilarc can be used to generate zip files that,
once extracted, will place a file at an arbitrary location on the target system.

## Example
Assuming you have a file `notes.txt` in the same directory as evilarc, the following command will create `evil.zip`,
which attempts to place the file in the unix directory `/etc` when extracted.

```sh
./evilarc.py -f evil.zip -o unix notes.txt -p /etc
```

You can add additional files afterwards by invoking evilarc on the same archive with additional files
```sh
./evilarc.py -f evil.zip -o unix jobs -p /etc/cron.daily/
```
