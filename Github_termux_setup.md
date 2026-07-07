Upload File to GitHub Using Termux on Android
1. Install Required Tool
bash
# Grant storage access (so you can access files from Downloads, etc.)
termux-setup-storage

# Update package list and upgrade existing packages
pkg update && pkg upgrade -y

# Install Git and GitHub CLI
pkg install git gh -y

1. Configure Git and Authenticate with GitHub
Set Git user name and email ( attach to your commit)
bash
git config --global user.name "Your GitHub Username"
git config --global user.email "your-email@example.com"

login GitHub using official CLI:
bash
gh auth login

· Select GitHub.com
· Choose HTTPS
· Follow prompts – you'll be asked to authenticate via your browser or paste a one-time code. This is easiest way and avoid manual token handling.

1. Upload File
if your file is in Downloads folder:
bash
cp /storage/emulated/0/Download/your-file.zip ~/   # copy it to Termux home
cd ~/your-project-folder                           # go to your project folder


bash
# Initialise repo with main branch
git init -b main

# Add all files in the current directory
git add .

# Commit with a message
git commit -m "Initial upload"

# Add the remote repository (create a new empty repo on GitHub first – do NOT add README)
git remote add origin https://github.com/your-username/your-repo.git

# Push to GitHub
git push -u origin main
Common Issue & Fixe
  Your local branch isn't named main. Create it   with:
bash
git checkout -b main

Then push again.

Termux may complain about ownership run
bash
git config --global --add safe.directory /storage/emulated/0/...

· Large file push fails
Increase the HTTP buffer:
bash
git config http.postBuffer 524288000

Then retry  push.

After pushing, refresh your GitHub repository page – your files should be there.

"dubious ownership" error – Git is cautious about repositories in shared storage.

✅ Fix ownership error

Run this inside Ebuy folder :
bash
git config --global --add safe.directory /storage/emulated/0/Ebuy

That tell Git to trust that directory. Now try again:
bash
git add .
git commit -m "Initial commit"

Add remote repository correctly

You missed remote name (origin), Use:
bash
git remote add origin https://github.com/Phurba2/Ebuy.git

IMake sure repository Phurba2/Ebuy already exist on GitHub (create it first if not – and don't add README otherwise you'll get push conflict).

🚀 Push to GitHub
bash
git push -u origin main

🎉 Success! Your files are now on GitHub

push complete :

· 3 files (index.html, script.js, style.css) were committed and pushed to main branch.
· remote origin now linked and your local main branch is tracking origin/main.

 