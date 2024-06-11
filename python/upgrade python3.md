https://www.pythoncentral.io/how-to-update-python/

Either SUDO or #:
1. python3 -V
2. sudo update-alternatives --config python3
3. sudo apt install python3.12
4. Run simple .sh script (update-alts.sh) to update the Alts first:
    #!/bin/bash
    i=0 ; for p in /usr/bin/python*.* ; do
    update-alternatives --install /usr/bin/python python $p $((5 + i))
    i=$((i+1))
    done
4. sudo update-alternatives --config python
5. select version you want to run as default