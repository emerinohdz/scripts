# Scripts
A set of bash scripts that may enhance your reMarkable experience

Scripts are split into a total of 3 categories:

## Host
All scripts that fall under this category are host-sided scripts. In other words, these scripts
are executed on your PC, not your reMarkable. Host scripts will however in most cases require
connection to your reMarkable, either trough USB or Wireless.

### rezone.sh
> [Source](https://github.com/reHackable/scripts/blob/master/host/rezone.sh)

reZone is a small script that can set the timezone on your reMarkable according to the host, or specified timezone.
This is done trough SSH by replacing the environmental `TZ` variable in `/etc/profile`.

#### Usage:
```
Usage: rezone.sh [SSH | -h | -help | --help]

Arguments:
SSH                     Devices SSH address (default 10.11.99.1)
-h -help --help         Displays script usage (this)
```

### repush.sh
> [Source](https://github.com/reHackable/scripts/blob/master/host/repush.sh)

A host sided script that can push one or more provided documents to the reMarkable via the web client. Files can be pushed trough USB, as well as remotely trough the `-r` option

In order for this script to work, the reMarkable web interface must be enabled first under `device settings > storage`

##### Supported document types:

* PDF
* EPUB

#### Usage:
```
Usage: repush.sh [-d] [-r ip] [-p port] doc1 [doc2 ...]

Options:
-d                      Delete file after successful push
-r                      Push remotely via ssh tunneling
-p                      If -r has been given, this option defines port to which the webui will be tunneled (default 9000)
```

#### Example:
The following example pushes test1.pdf and test2.pdf while the device is connected trough USB
```sh
$ bash repush.sh test1.pdf test2.pdf
```

The following example pushes test1.pdf and test2.pdf remotely. This example assumes the devices network ip is `10.0.0.43`.
```sh
$ bash repush.sh -r 10.0.0.43 test1.pdf test2.pdf
```

### repull.sh
> [Source](https://github.com/reHackable/scripts/blob/master/host/repull.sh)

A host sided script that can download one or more documents from the reMarkable via the web client. Files can be downloaded trough USB, as well as remotely trough the `-r` option

In order for this script to work, the reMarkable web interface must be enabled first under `device settings > storage`

#### Usage:
```
Usage: repush.sh [-d] [-r ip] [-p port] doc1 [doc2 ...]

Options:
-d                      Delete file after successful push
-r                      Push remotely via ssh tunneling
-p                      If -r has been given, this option defines port to which the webui will be tunneled (default 9000)
```

#### Example:
The following example downloads a document that goes by the name of test1 while the device is connected trough USB
```sh
$ bash repull.sh test1
```
The output will either be a PDF or a EPUB, depending on the document type

The following example downloads test1 and test2 remotely. This example assumes the devices network ip is `10.0.0.43`.
```sh
$ bash repull.sh -r 10.0.0.43 test1 test2
```

## Client
All scripts that fall under this category are client-sided scripts. In other words, these scripts
are executed on your reMarkable either locally, or trough an SSH connection.

## Common
All scripts that fall under this category can be executed on both host as well as client. Some scripts
provided by this category may require to run on both device simultaneously.
