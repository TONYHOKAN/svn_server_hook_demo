# Step to set up docker svn with http access image

install docker

```
mkdir -p /root/container/svn/apache
touch /root/container/svn/apache/passwd
```
then 
```
docker run -d \
    --name svn-server \
    -p 21080:80 \
    -p 3690:3960 \
    --volume ${your_path}/svn/repo:/home/svn \
    --volume ${your_path}/svn/apache/passwd:/etc/subversion/passwd \
    elleflorio/svn-server
```

create http access 

`docker exec -t svn-server htpasswd -b /etc/subversion/passwd ${username} ${userpassword}`

# Ref:

https://www.joycc.cn/p/240.html

https://medium.com/@elle.florio/the-svn-dockerization-84032e11d88d

https://stackoverflow.com/questions/22968225/how-to-add-the-commit-comment-to-a-subversion-post-commit-hook
