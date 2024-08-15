HOWTOs
======

### Github Pages
* ```My site: https://pmp-gh.github.io/```
* ```Theme: https://github.com/pages-themes/minimal```
* ```Preview locally: Run bundle exec jekyll serve to start the preview server```
* ```Load localhost:4000 in browser```

### Linux Commands/Utils
#### Files/Dir
* ```ls -lta```
* ```find <path> -type {f|d} -name <name> // find . -type f -name "*.txt"```
* ```chmod [4|2]rwx <file> // 4 = SUID, 2 = SGID```
* ```head/tail -n <num> <file>```
* ```grep -rn <pattern> <path> // grep -rn "foo" *```
* ```sort [-r] <file>```
* ```cat <file>```
* ```less <file>```
* ```diff <file1> <file2>```
* ```mkdir <dir>```
* ```cd <path>```
* ```rm [-rf] <file/dir> // BE CAREFUL!```
* ```ln -s <file> <link>```
* ```cp <src-file> <dest-file>```
* ```dd if=<input-file> of=<output-file> // dd if=/dev/hda1 of=./hda1.img```
* ```mv <old-file> <new-file>```
* ```tar cvf dir.tar <files|dir> // archive```
* ```tar xvf dir.tar // extract```
* ```rsync -azP --delete src/ dest/```

#### Processes
* ```ps -ef```
* ```nice -<N> <prog> // add N to niceness (default 10; range = [-20,19])```
* ```renice <N> <pid> // change niceness of running process```
* ```kill -<sig> <pid> // send signal (3:coredump, 9:term, 18:resume, 19:stop)```
* ```bg <pid>```
* ```Ctrl + Z // suspend process```
* ```jobs // show suspended processes```
* ```fg <pid>```
* ```systemctl [start|stop|restart] <service> // manage SystemD service```

#### Disk
* ```fdisk -l // to see all partitions (sda2 = sata first drive(a) 2nd partition)``` 
* ```mount <part> /dir // mount /dev/sdb1 /mnt```
* ```umount <part> // unmount /dev/sdb1```
* ```df <part> // free space```

#### Network
* ```ifconfig <if> <ip-addr> netmask <mask> broadcast <broadcast-addr>```   
* ```ifconfig <if> [up|down]```
* ```arp -a // see arp cache```
* ```dhclient <if> // get new IP address from dhcpd```
* ```dig <ip-address> // interrogate DNS```
* ```route -n // see all routes```
* ```route add default gw <gateway-addr>```
* ```route add -net <ip-addr> netmask <mask> gw <gateway-addr>```
* ```Firewall: Chains (INPUT, OUTPUT, FORWARD), Tables (FILTER, NAT, MANGLE), Actions (ACCEPT, DROP)```
  ```Options preceding chain: -L (list), -A (append) -D (delete) -P (set default policy)```  
  ```Rule parameters: -s addr/mask, -d addr/mask, -p protocol, --source-port p, --destination-port p```
* ```iptables -L // see all rules```
* ```iptables -A INPUT -p tcp --destination-port 22 -j ACCEPT // accept ssh connections```
* ```netstat -t|u // show TCP/UDP connections```
* ```netstat -l // listening sockets```
* ```netstat -p // process owning sockets```
* ```tcpdump -i <if|any> -c <N> // show N packets on the interface```
* ```tcpdump -i <if|any> -c N -w <pcap-file> port <port> // save packets```
* ```nmap -p <port-range> -sT <host> // scan + attempt TCP connect on host/port```
* ```nc -l <host> <port> // create a listener on host/port```
* ```nc <host> <port> // connect via tcp```
* ```nc -l -p <port> -e <cmd> // nc -l -p 1234 -e /bin/sh - starts a shell```

#### Security
* ```passwd```
* ```openssl genrsa -out <keypair.pem> 2048 // generate RSA key pair```
* ```openssl rsa -in <keypair.pem> -pubout -out <pubkey.crt> // extract public key```
* ```openssl rsautl -sign -in <file> -inkey <keypair.pem> -out <file.sig>```
* ```openssl rsautl -verify -in <file.sig> -inkey <keypair.pem> // see the signed data```
* ```openssl enc -aes-256-cbc -p -in <file> -out <file.enc> // prompt password, print IV, salt```
* ```openssl enc -aes-256-cbc -p -d -in <file.enc> -out <file>```
* ```openssl dgst -sha256 <file>```
* ```openssl req -x509 -sha256 -key <keypair.pem> -out <cert.pem> // self-signed cert request```
* ```ssh user@host```
* ```scp user1@host1:<file1> user2@host2:<file2>```

#### Environment
* ```env // see all environment variables```
* ```export ENVVAR=value```
* ```unset ENVVAR```

---

### Packages (Ubuntu)
* ```apt-cache search <keyword> // to search for package name```
* ```apt-get install <package>``` 
* ```apt-get remove <package>  // use "purge" instead of remove to get rid of config files``` 
* ```apt-get update // to update list of packages available in the repository```
* ```apt-get upgrade // to upgrade packages to latest version```
* ```Add repos to /etc/apt/sources.list```

---

### Editing (Vim)
* ```<ESC> // command mode```
* ```i, a // insert mode```
* ```:w // save```
* ```:q // quit```
* ```:q! // quit without saving```
* ```h, l, j, k // left, right, down, up```
* ```:line // goto line```
* ```1G, G // first, last line```
* ```^, $ // start, end of line```
* ```w, b // word forward, backward```
* ```^f, ^b // next, previous screen```
* ```nyy, nyw // yank n lines, words```
* ```ndd, ndw // delete n lines, words```
* ```d^, d$ // delete to start, end of line```
* ```d1G, dG // delete to start, end of file```
* ```p, P // puts deleted lines after, before cursor```
* ```[/|?]string // search for string forward, backward```
* ```n, N // repeat search forward, backward```
* ```:x,ys/old/new/flags // substitute, g = global, c = confirm, x,y = range, . = line, % = file```
* ```:shell```
* ```:split, vsplit // windows```
* ```^w^w // move to next window```
* ```:close // close window```
* ```:only // close all except current window```
* ```<ESC>v // select block```
* ```> // indent block```
* ```:set nu // line numbering```
* ```:set textwidth=N // hard wrap (also, visual highlight, gq)```
* ```:set tabstop=N // tab size```

---

### Version Control (Git)
* ```git clone <URL> or git init```
* ```git add <files>```
* ```git checkout -- .  // get rid of unstaged changes```
* ```git status```
* ```git commit -m <commit-message>```
* ```git log```
* ```git checkout <commit-hash>```
* ```git reset --hard <commit hash>  // changes HEAD to previous commit```
* ```git push origin main```
* ```git branch <branch-name>  // create local branch```
* ```git branch // confirm in local branch```
* ```git checkout <branch name>  // update working directory```
* ```git merge <branch-name>  // merge into current branch, resolve conflicts, add + commit```
* ```git branch -D <branch-name>  // delete branch```
* ```git branch <branch-name>; git rebase <other-branch>```  
  ```git will find common ancestor of <branch-name> and <other-branch>```  
  ```git will apply commits from <other-branch> from common ancestor```  
  ```git will apply commits from <branch-name>```  
* ```git push -u origin <branch name> // track branch on remote```
* ```git pull // sync with main branch on remote```
* ```git config --global credential.helper store // enable credential storage```

---

### Build
#### gcc 
* ```gcc -c <src-files> // compile only```
* ```gcc -I <include-dirs> <src-files> -g -D <symbol> -o <exec-file>```

#### cmake
```
Assume a project dir structure as follows
/proj-dir
     CMakeLists.txt 
    /build
    /common
        foo.h
        foo.c
        bar.h
        bar.c
    /qux
        CMakeLists.txt
        quux.c

The top-level CMakeLists.txt might look like this: 
----------------------------------------------------------
cmake_minimum_required (VERSION X.YZ)

project ("qux")
add subdirectory ("qux")
----------------------------------------------------------

The CMakeLists.txt in proj-dir/qux might look like this: 
----------------------------------------------------------
set(CMAKE_PROJECT_TARGET qux)
add_definitions (-DPLATFORM_UNIX)

include_directories(
     ${CMAKE_SOURCE_DIR}/qux
     ${CMAKE_SOURCE_DIR}/common
)

link_directories (
    /usr/lib
    /usr/lib/x86_64-linux-gnu)

add_executable(${CMAKE_PROJECT_TARGET} quux.c
				       ../common/foo.c
				       ../common/bar.c)

target_link_libraries(${CMAKE_PROJECT_TARGET} PRIVATE baz)
----------------------------------------------------------
```
* ```cmake --build ./build -DCMAKE_BUILD_TYPE=Debug```
* ```cd ./build && make``` 

---

### Debug (gdb)
* ```gdb prog [core-dump]```
* ```set args <arglist>```
* ```list <func>```
* ```list line1,line2```
* ```run [< <in-file>] [> <out-file>]```
* ```break [line|func]```
* ```info breakpoints```
* ```delete <bp>```
* ```disable <bp>```
* ```enable <bp>```
* ```set <var>=<value>```
* ```step // step into```
* ```next // step over```
* ```call <func>```
* ```finish // finish executing current function```
* ```continue // resume execution until next bp```
* ```where // shows current call stack```
* ```frame // shows current stack frame```
* ```up // previous stack frame```
* ```down // next stack frame```
* ```attach <pid> // attach to process```
* ```detach // detach from process```

---

### ML 
#### Anaconda
* ```Install from website (download and run shell script)```
* ```conda create -n "env_name"```
* ```conda env list```
* ```source ~/anaconda3/etc/profile.d/conda.sh```
* ```conda activate "env_name"```
* ```conda deactivate```

#### PyTorch
* ```conda activate pytorch_env```
* ```conda install ipykernel```
* ```conda install pytorch=1.11.0 torchvision=0.12 torchaudio=0.11 cudatoolkit=11.3 -c pytorch```
* ```To uninstall: conda uninstall pytorch```

#### Jupyter Notebook
* ```Install in base conda environment```
* ```conda install -c conda-forge notebook```
* ```conda install -c conda-forge nb_conda_kernels```
* ```conda install -c conda-forge jupyter_contrib_nbextensions```
* ```conda install nb_conda_kernels```
* ```Select pytorch_env (from New) at start of session```

---

### Graphics 

#### VNC
* ```Server```  
  ```vncserver -depth d -geometry <resolution> // e.g., d=32, resolution=1920x1080```    
  ```vncserver -kill :<display> // display=2```
* ```Client```  
  ```ssh user@<server-ip> -L 5902:127.0.0.1:5902 // ssh tunnel client to server```     
  ```remmina // connect to 127.0.0.1:5902```

#### NVIDIA GPU
```How to install NVIDIA driver and CUDA```
* ```sudo apt-get install nvidia-driver-470```
* ```Download CUDA 11.4 installer and run shell script, but DO NOT install driver```

```How to find and remove all nvidia packages```
* ```dpkg -l | grep nvidia```
* ```dpkg -l | grep cuda```
* ```dpkg -l | grep libcudnn```
* ```dpkg -l | grep libglvnd0```
* ```sudo apt purge <package>```

#### Recover from post boot black screen
* ```During boot, press ESC and drop to root shell in Recovery Mode```
* ```sudo prime-select intel```
* ```sudo reboot```
* ```sudo apt remove nvidia-*```
* ```sudo ubuntu-drivers devices (to see all available drivers)```
* ```sudo apt-get install nvidia-driver-470 (works for Carla setup)```
* ```sudo prime-select nvidia```
* ```sudo reboot```

#### Recover X 
* ```sudo apt install --reinstall gdm3 ubuntu-desktop gnome-shell```
* ```sudo reboot```

---


