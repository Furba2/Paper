Upload File to GitHub Using Termux on Android

# Grant storage access (so you can access files from Downloads, etc.)
termux-setup-storage

pkg install git

# Configure Git 
git config --global user.name "Your GitHub Username"
git config --global user.email "your-email@example.com"

cd ~/your-project-folder

git init 

git branch -M main

git add .

git commit -m "Initial upload"

git remote add origin https://github.com/your-username/your-repo.git

git push -u origin main

# Common Issue & Fix Termux may complain about ownership run
> git config --global --add safe.directory /storage/emulated/0/... 
