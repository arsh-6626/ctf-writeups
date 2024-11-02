# EHax Writeup Submission

## Music Pages

**Name** – Arsh Abbas Naqvi  
**Roll No.** – 24/A02/028

---

### 1. Investigation Part

The index page indicates that we can navigate to any page or file here, which was a significant hint. I concluded that retrieving other files would follow the same approach as for the webpages showing the music files, which are accessed by the `index.php` file via query.

Example URL:
`http://$ip:$port/index.php?view=<path>`

The next step was to try finding `robots.txt`, but that didn’t yield any results, so I skipped it. I also attempted Local File Inclusion (LFI) by navigating back with `/../..` and trying to find `etc/passwd`, but unfortunately, that didn’t work either.

---

### 2. Exploring .git

The next step involved checking the git logs, as hinted. The `.git` folder contains all the necessary information for a project in version control, such as commit history, remote repository address, and more. This folder includes logs that store commit history, which allows us to roll back changes.

The `.git` folder, present by default in every repository, contains the following folders:

- **hooks/**: Contains client or server-side hook scripts.
- **logs/**: Stores records of all changes made. This may contain information like log details, user name, email, etc., which could include a flag.
- **logs/HEAD**: Stores information about all changes made and may contain the flag.
- **objects/**: Stores all content of the repository.

Example URL:
`http://$ip:$port/index.php?view=%3cpath`

---

### 3. Executing the Final Payload

After navigating to each of the potential candidates, I concluded that the flag is located inside:
`http://$ip:$port/index.php?view=.git/logs/HEAD`
