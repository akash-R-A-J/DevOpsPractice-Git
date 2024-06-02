This is just for practice and learning purpose.

# Clone the master repository
git clone https://github.com/yourusername/yourmasterrepo.git
cd yourmasterrepo

# Checkout to the notes branch
git checkout notes

# Move PDFs to the pdf-repo directory
mkdir -p pdf-repo
mv *.pdf pdf-repo/
git add pdf-repo
git commit -m "Moved PDFs to the pdf-repo directory"
git push origin notes

# Create a new repository for PDFs (pdf-repo) on GitHub

# Initialize the pdf-repo directory as a Git repository
cd pdf-repo
git init
git remote add origin https://github.com/yourusername/pdf-repo.git
git add .
git commit -m "Initial commit of PDFs"
git push -u origin master

# Go back to the master repository and add the submodule
cd ..
git submodule add https://github.com/yourusername/pdf-repo.git pdf-repo
git add .gitmodules pdf-repo
git commit -m "Added pdf-repo as a submodule"
git push origin master

# Merge the notes branch back into master (if needed)
git checkout master
git merge notes
git push origin master

# Delete the local notes branch
git branch -d notes

# Delete the remote notes branch
git push origin --delete notes
