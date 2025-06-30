# some you may delete some file by `rm -rf`(when you hand is smarter than your brain...), so please do something below:

# 1. alias the `rm` to `rm -i` 
In your `~/.bashrc` or `~/.zshrc`, add
```
alias rm='rm -i'
``` 
This will request you to confirm before deleting

# 2. install the `trash-cli` and alias with rm
## 2.1 install package
```
sudo apt install trash-cli
```
## 2.2 alias `rm` to `trash-put` in your `~/.bashrc` or `~/.zshrc`
```
alias rm='trash-put'
```
## 2.3 recover the deleted files by `trash-list` and `trash-restore`
### 2.3.1 find the files `ID` by `trash-list`
```
trash -list
```

Example output:
```
Date        Time            Size  #  Path
2025-05-22  16:50:30        1.2M  0  /home/user/Documents/old_report.pdf
2025-05-22  16:55:15        3.5K  1  /home/user/project/temp_data/junk_folder/
```

### 2.3.2 recover the file by `ID`
For example the `old_report.pdf`
```
trash-restore 0
```

### 2.3.3 if the filename is distinguished
```
trash-restore old_report.pdf
```
