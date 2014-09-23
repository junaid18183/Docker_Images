==How to Build==
docker build -t="junaid18183/dashing" .

==How to start==
docker run --hostname="dashing"  --name="dashing" -d -p 83030:3030 junaid18183/dashing

