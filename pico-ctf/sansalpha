# PicoCTF 2024 SansAlpha Writeup

## Challenge: SansAlpha

In this challenge, the objective is to capture the flag on a shell where alphabetical characters cause an error when used. The solution involves several steps to bypass this limitation.

---

### Step 1: Investigate the Environment

Using `*` in the shell produced an error, which revealed that the shell tried to execute every file and directory in the current directory, a behavior called bash globbing. The shell interpreted `*` as "all files and directories," executing the first file it found (in this case, `blargh`) and passing the rest as arguments.

To explore further, I used the special bash variable `$_`, which retrieves the last argument from the previous command. When entered, this showed another file, but still not the flag.

---

### Step 2: Searching Subdirectories

To search within subdirectories, I ran:

```bash
./*/*
```

This revealed `flag.txt` inside the `blargh` folder.

---

### Step 3: Accessing `flag.txt` Without Using Letters

To read `flag.txt` without typing letters, I leveraged a file called `on-calastran.txt`, which contains the letters required to spell `cat`. Using **Shell Parameter Expansion**, I extracted letters from `on-calastran.txt` to reconstruct `cat`:

- **Getting "c"** with `${_:3:1}` (4th character)
- **Getting "a"** with `${_:4:1}` (5th character)
- **Getting "t"** with `${_:8:1}` (9th character)

Combined, this spells `cat`:

```bash
${_:3:1}${_:4:1}${_:8:1}
```

Running `*` again set `$_` to `on-calastran.txt`. Then, I ran:

```bash
${_:3:1}${_:4:1}${_:8:1} ./*/*
```

This command used `cat` to read every file inside subdirectories, revealing the flag.

---

### Summary

Through shell parameter expansion and bash globbing, I managed to capture the flag without typing alphabetical characters. This approach used special variables and command expansion, showcasing a creative solution for environments with restricted character inputs.
