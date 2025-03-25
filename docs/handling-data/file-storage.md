# File storage

Files are stored on Roar Collab in a central filesystem;

Users have access to four central filesystems:  home, work, group, and scratch.
These have different purposes:

- **home** – for configuration files, and links to work, group, and scratch.
- **work** – for your own work; 
only you have read-write access to your home and work directories.
- **scratch**  – for temporary storage of large files.  scratch is *not backed up*, 
and files with a last modified time stamp older than 30 days will be *automatically deleted*.

PI-owned **group** storage directories are available for purchase. These are designed for collaborative work or group level software.

Files in home, work, and group are backed up by a sequence of daily "snapshots" which are kept for 90 days. 
To have files restored from a snapshot, email Client Support at <icds@psu.edu>. 

!!! warning "No backup is infallible"
     Users are exceptionally strongly encouraged to make an off-ICDS backup plan for critical data such as configuration files
     necessary to replicate their research. Using services such as the 
     [Penn State University Backup Service](https://pennstate.service-now.com/sp?id=it_service_offering_request_forms&offering_id=0d2d68fb37a75f406a0f94c543990eb8) may be a good option.


## Quotas

home, work, group, and scratch directories are subject to limits,
both on the amount of storage space and on the number of inodes. Inodes are data structures that 
store most of the essential information about a file or directory. Files, directories, and 
symlinks all count towards inode limits.

On RC, quota limits are:

| Storage | Path | Size | Inodes | Backup | Purpose |
| :----: | :----: | :----: | :----: | :----: | :----: |
| Home | /storage/home | 16 GB | 500,000 | Daily  | Configuration files |
| Work | /storage/work | 128 GB | 1 million | Daily  | User data |
| Scratch | /scratch | None | 1 million | None | Temporary files |
| Group | /storage/group | Specific to<br>allocation | 1 million<br>per TB | Daily | Shared data |

On Roar Restricted, quota levels are the same, however users do not have access to a scratch 
directory and group storage directories are located in the restricted storage space (/restricted/group).


## Monitoring storage use

Exceeding quotas on home or work directories can result in job errors, incomplete file creation, or even login issues.

The `quota_check` utility reports total usage for all storage locations available, giving you an overview of storage usage.

To see the breakdown of file and directory size, [`du`][du] can be used. Combining this with the ['sort'][sort] command allows 
for quick identification of directories that are using the most storage.
[du]: https://man7.org/linux/man-pages/man1/du.1.html
[sort]: https://man7.org/linux/man-pages/man1/sort.1.html

``
du -sch .[!.]* * | sort -hr
``

### Solution to common quota issues in home

Many user-level configuration files and package libraries are stored in the home directory by default.
Large package libraries can quickly overwhelm the home quota and cause out of space errors. 
This commonly occurs with directories such as

 - `.local` - used by Python to store user installed packages
 - `.comsol` - used by Comsol

These [dot files](https://missing.csail.mit.edu/2019/dotfiles/) are hidden by default. You can view
them via the command line using the `ls -la` command.

To correct the out of space error, it is recommended to move the offending directory to work and create 
symlink pointing to the new location. For example, moving the `.comsol` directory is done with the following commands:

```
mv ~/.comsol $WORK/
ln -s $WORK/.comsol ~/.comsol
```

This can be repeated for any directory in home that is causing the out of space error.


## Archive storage

To store infrequently-used files, low-cost archive storage can be purchased. 
Files in archive cannot be used or accessed in place, so access is neither
quick nor convenient. The [Globus][globus] web interface is the only way
to access these files.

Archive quota limits are:

| Storage | Path | Size | Inodes | Backup | Purpose |
| :----: | :----: | :----: | :----: | :----: | :----: |
| Archive | /storage/archive | Specific to<br>allocation | 200,000<br>per TB | None  | Long-term<br>File Storage |


If you store a directory that contains many files, 
you should pack the directory into a single file with `tar`
(see [Creating File Archives using tar](managing-files/archives.md))
before transferring.
[globus]: transferring-data/globus.md

!!! warning "Archive storage is not suitable for storing protected data."
     If you are working with data or software that must adhere to regulatory requirements
     please contact us or the [Office of Information Security](https://security.psu.edu) 
     to ensure it is being handled appropriately.

