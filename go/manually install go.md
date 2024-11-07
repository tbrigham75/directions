I was trying to install a GO package and it was complaining about the version of Go that was installed by Apt.  This is how to install manually.

1.  wget https://go.dev/dl/go1.23.3.src.tar.gz
2.  tar -xf go1.23.3.src.tar.gz
3.  sudo chown -R root:root ./go
4.  sudo mv -v go /usr/local
5.  vi ~/.bashrc
    # Golang environment variables
    export GOROOT=/usr/local/go/
    export GOPATH=$HOME/go
    export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin