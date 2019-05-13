# ATutor-Instructor-Backup-Exploit

- Exploit Title: ATutor 2.2.4 'Backup' Remote Command Execution 
- Google Dork: inurl:/ATutor/login.php
- Date: 5/13/2019
- Exploit Author: Joseph McPeters
- Vendor Homepage: https://atutor.github.io/
- Software Link: https://sourceforge.net/projects/atutor/files/latest/download
- Version: < 2.2.4 (Versions 2.2.4 and prior seem to be affected)
- Tested on: Windows 7 with XAMPP / Linux 3.16.0-4-amd64 with version 2.2.4 and 2.2.1
- Authors Site: http://incidentsecurity.com/atutor-2-2-4-backup-remote-command-execution/

ATutor 2.2.4 is vulnerable to arbitrary file uploads via the backup function that may result in remote command execution.

First login with the instructor account and select a course:

- #1 http://[atutor address]/atutor/bounce.php?course=1

Then navigate to "Manage"

- #2 http://[atutor address]/atutor/tools/index.php

Next select Backups/Upload

- #3 http://[atutor address]/atutor/mods/_core/backups/upload.php

From here a specially crafted backup zip file i.e "pwned_backup.zip" can be uploaded that will result in remote command execution.

The PoC arbitrary file can be found at:
http://[atutor address]/atutor/content/1/pwned/poc.PhP

or

C:\xampp\htdocs\ATutor\content\1\pwned\poc.PhP

Note: The "1" in the address will change based on the course number and the "content" directory may be different.
However by default the installation calls for the dir name to be "content". This has been tested on both linux/windows installations.

- A copy of the PoC zip file (pwned_backup.zip) can be downloaded: https://github.com/fuzzlove/ATutor-Instructor-Backup-Arbitrary-File
