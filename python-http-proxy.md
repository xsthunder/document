1. install node
2. run `sudo npm i -g http-proxy-to-socks`, npm is from node package
3. run `hpts -s localhost:1086` 1086 as your socks proxy port, set up http proxy tunnel on localhost:8080 on default. hpts is shortened form for http-proxy-to-socks
4. run `export http_proxy=localhost:8080` only vailable for current bash session, urllib will use http_proxy
5. `curl google.com` to find if you are fine to go

6. `python <python_file>`

