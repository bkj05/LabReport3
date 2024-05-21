# Lab Report 4 - Vim (Week 7)

## Step 4: Complete the first two lessons of vimtutor

### Screenshot:
![Vimtutor](vimtutor_screenshot.png)

### Keys Pressed:
- `vimtutor<enter>`

### Summary:
Opened vimtutor to begin the tutorial.

## Step 5: Clone the repository

### Screenshot:
![Git Clone](git_clone_screenshot.png)

### Keys Pressed:
- `git clone https://github.com/ucsd-cse15l-s24/lab7<enter>`

### Summary:
Cloned the lab7 repository from GitHub.

## Step 6: Fix the program

### Screenshot:
![Vim Edit](vim_edit_screenshot.png)

### Keys Pressed:
- `cd lab7<enter>`
- `vim ListExamples.java<enter>`
- `/index1<enter>`
- `cw`
- `index2<esc>`
- `:wq<enter>`

### Summary:
- Changed directory to lab7.
- Opened ListExamples.java in vim.
- Searched for "index1".
- Changed "index1" to "index2".
- Saved and exited vim.

## Step 7: Re-run the tests

### Screenshot:
![Run Tests](run_tests_screenshot.png)

### Keys Pressed:
- `./run_tests.sh<enter>`

### Summary:
Ran the shell script to execute the tests.

## Step 8: Commit and push the change

### Screenshot:
![Commit and Push](commit_push_screenshot.png)

### Keys Pressed:
- `git add ListExamples.java<enter>`
- `git commit -m "Fixed index1 to index2 in ListExamples.java"<enter>`
- `git push<enter>`

### Summary:
Staged the modified file for commit, committed the change with a message, and pushed the changes to the GitHub repository.

## Step 9: Adding the Lab Report to Your GitHub Pages Site

### Screenshot:
![GitHub Pages](github_pages_screenshot.png)

### Keys Pressed:
- `cd path_to_your_github_pages_repository<enter>`
- `cp path_to_lab_report/lab_report_4.md .<enter>`
- `git add lab_report_4.md<enter>`
- `git commit -m "Added Lab Report 4"<enter>`
- `git push<enter>`

### Summary:
- Navigated to the GitHub Pages repository.
- Copied the lab report markdown file to the repository.
- Staged the lab report file for commit.
- Committed the change with a message.
- Pushed the changes to the GitHub Pages repository.
