# chroot-setup

## packages
`apt-get install tmux git vim-nox tree silversearcher-ag bzip2`

## single user setup

```
git clone https://github.com/acornejo/dotfiles ~/.dotfiles
git clone https://github.com/acornejo/tips ~/.tips
git config --global genot.directory ~/.tips
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
~/.dotfiles/bin/dot-restore
```

## create more users
```
USERS=(alex patty)
G=$(awk -F: "{ if (\$4 ~ /chronos/) print \$1 }" ORS=',' /etc/group | sed 's/,$//')
for user in ${USERS[@]}; do
  useradd -m ${user}
  echo "${user}:${user}" | chpasswd
  usermod -G $G -a ${user}
done
```

## go
Use tgz
https://golang.org/dl/
```
cat << 'EOF' > /etc/profile.d/golang.sh && chmod 755 /etc/profile.d/golang.sh
export GOROOT=/opt/go
export GOHOME=$HOME/go
export PATH=$PATH:$GOROOT/bin
EOF
```

## node
Use tgz
https://nodejs.org/en/download/current/
```
cat << 'EOF' > /etc/profile.d/node.sh && chmod 755 /etc/profile.d/node.sh
export PATH=$PATH:/opt/node/bin
EOF
```

## java
Use tgz
http://www.oracle.com/technetwork/java/javase/downloads/

```
cat << 'EOF' > /etc/profile.d/java.sh && chmod 755 /etc/profile.d/java.sh
export JAVA_HOME=/opt/jdk
export PATH=$PATH:$JAVA_HOME/bin
EOF
```

## python
Use the anaconda distribution (http://conda.pydata.org/miniconda.html).

```
sh miniconda-version.sh -b -p /opt/python

cat << 'EOF' > /etc/profile.d/python.sh && chmod 755 /etc/profile.d/python.sh
export PATH=$PATH:/opt/python/bin
EOF
```

### from source:
Download from https://www.python.org/downloads/ and build from source
libraries need for python:

```
apt-get install zlib1g-dev libbz2-dev libssl-dev libreadline-dev libncurses5-dev libsqlite3-dev libgdbm-dev libdb-dev libexpat-dev libpcap-dev liblzma-dev libpcre3-dev
./configure --prefix=/opt/python
make && sudo make install
```
