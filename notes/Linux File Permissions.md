# Linux File Permissions

## What are Linux File Permissions?

Linux file permissions define who can **read**, **write**, or
**execute** a file for the **owner**, **group**, and **others**.

They are displayed with the command:

    ls -l

Permissions can be modified using:

-   `chmod`
-   `chown`
-   `chgrp`

This system ensures **security** and prevents **unauthorized changes**.

------------------------------------------------------------------------

## The 3 Permission Types

-   **Read (r)** → Can view the file's contents\
-   **Write (w)** → Can modify or delete the file\
-   **Execute (x)** → Can run the file as a program or script

------------------------------------------------------------------------

## The 3 User Groups

-   **Owner (u)** = The person who created the file\
-   **Group (g)** = Team members who belong to the same group\
-   **Others (o)** = Everyone else on the system

------------------------------------------------------------------------

## Permission Format

When you run:

    ls -l

Example output:

    -rwxr-xr--

### Breakdown

-   `-` → File type (`-` = file, `d` = directory)
-   `rwx` → Owner permissions (read, write, execute)
-   `r-x` → Group permissions (read, execute)
-   `r--` → Others permissions (read only)

------------------------------------------------------------------------

## Changing Permissions

### Numeric Method (Faster)

Permissions are represented as numbers:

-   **4 = Read (r)**
-   **2 = Write (w)**
-   **1 = Execute (x)**

Example:

    chmod 755 script.sh

Meaning:

-   Owner: **7 (4+2+1 → rwx)**
-   Group: **5 (4+0+1 → r-x)**
-   Others: **5 (4+0+1 → r-x)**

------------------------------------------------------------------------

## Common Permission Examples

  Permission   Meaning
  ------------ ----------------------------------------------------
  **777**      `rwxrwxrwx` → Dangerous (everyone has full access)
  **755**      `rwxr-xr-x` → Common for scripts
  **644**      `rw-r--r--` → Config files
  **600**      `rw-------` → Private files

------------------------------------------------------------------------

## Important Commands

### chmod -- Change permissions

    chmod +x /scripts/backup.sh

### chown -- Change owner

    sudo chown ubuntu:developers app.log
    sudo chown newowner file.txt
    sudo chown newowner:newgroup file.txt

### chgrp -- Change group

    sudo chgrp newgroup file.txt
