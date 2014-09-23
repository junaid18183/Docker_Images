==How to Build==
docker build -t="junaid18183/dashing" .

==How to start==
docker run -v /plugins_scripts/Git_repos/dashing-demo:/root/dashing-demo --hostname="dashing"  --name="dashing" -d -p 43030:3030 junaid18183/dashing

or docker run  -p 43031:3030 -i -t  junaid18183/dashing:latest /bin/bash -l

==Attach local volume in Container
docker run -v /plugins_scripts/Git_repos/dashing-demo:/root/dashing-demo -i -t  junaid18183/dashing:latest /bin/bash -l

