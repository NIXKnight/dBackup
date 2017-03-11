# dBackup
dBackup (Data Backup) is a backup script for Linux systems.

The script, at the moment, has only been tested on the following Linux distributions.

* Debian
* Ubuntu
* Gentoo
* Fedora
* CentOS (Partial)

## Dependencies
By default, the script uses `gzip` and `bzip2` to compress backups which use a single processing core. You need to install `pigz` and `pbzip2` if you want to use all available processing cores for compression.
### Debian/Ubuntu
    apt-get install pigz pbzip2
### Gentoo
    emerge app-arch/pigz app-arch/pbzip2
### Fedora
    dnf install pigz pbzip2
### CentOS
    yum install pigz
**Note:** CentOS doesn't have `pbzip2` in its repositories. You may have to install it via a 3rd party repository.

## Usage
The script supports the following parameters, which should be specified on the command line:
>
  >   **`-h`** or **`--help`**
  >   
  >   Print this help.
  >   
  >   -----
  >   
  >  **`-d`** or **`--directory`**` [/path/to/target/directory]`
  >  
  >  Target directory to be included in a backup. Provide this parameter multiple times to backup multiple directories.
  >  
  >  **Example:** `./dBackup -d /opt/foo --directory /home/bar`
  >  
  >  -----
  >
  >  **`-c`** or **`--compression-format`**` [gzip|gz|bzip2|bz2]`
  >  
  >  The compression format to use. If this parameter is not provided, compression will not be performed.
  >  
  >  **Example:** `./dBackup -d /opt/foo --directory /home/bar -D /backup -c bzip2`
  >  
  >  -----
  >  
  >  **`--parallel-compression`**
  >  
  >  By default, this script uses gzip and bzip2 utilities to compress data which use a single processing core for compression. By providing this parameter the script will use pigz and pbzip2 utilities which use all processing cores for compression.
  >  
  >  **Note:** This parameter must be give before `-c` or `--compression-format` parameter.
  >  
  >  **Example:** `./dBackup -d /opt/foo --directory /home/bar -D /backup --parallel-compression -c bzip2`
  >  
  >  -----
  >  
  >  **`--strftime`**`[date format]`
  >  
  >  Change date format of backup directory name. By default the date format is %Y%m%d.
  >  
  >  **Example:** `./dBackup -d /opt/foo --directory /home/bar -D /backup -c bzip2 --strftime %d_%B_%Y`

## Features

  &#10004; Backup of local directories.

  &#10006; Pull files and/or directories from remote systems to create a backup.

  &#10006; Backup rotation.

  &#10006; MySQL database backups.

  &#10006; PostgreSQL database backups.

  &#10006; MongoDB backups.

  &#10006; Email notification of backups.

  &#10006; Hash calculation of backups.

  &#10006; Push backups to a central backup server.

## License
This script is licensed under MIT License.
## Author
[Saad Ali](https://github.com/nixknight)
