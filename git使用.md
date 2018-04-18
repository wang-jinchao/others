Github初始配置:  
    
    ssh-keygen -t rsa -C "your_email@youremail.com"
    ssh -T git@github.com

    git config --global user.name "Your Name"
    git config --global user.email "email@example.com"

    echo "# -" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin "SSH链接"
    git push -u origin master
---
在Github上删除某个Repository中的某个文件夹:  

    git rm -r --cached some-directory
    git commit -m "Remove the now ignored directory some-directory"
    git push -u origin master

