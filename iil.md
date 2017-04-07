> iil.md for install-issue-linux.md

# Update python on ubuntu

<http://mbless.de/blog/2016/01/09/upgrade-to-python-2711-on-ubuntu-1404-lts.html>

# Install Individual python and pip on Linux

This section is suit for scense to install a specify python edition without touch
the OS relied python. Here I install `python2.7.13` on `debian8`.

    # --- pre-installation ---
    sudo apt-get update && apt-get updgrade
    sudo apt-get install zlib1g-dev libssl-dev

    # --- make install folder and do grant ---
    sudo mkdir /usr/local/lib/python2.7.13
    sudo chmod 777 /usr/local/lib/python2.7.13

    # --- download python source and compile ---
    cd ~
    wget https://www.python.org/ftp/python/2.7.13/Python-2.7.13.tar.xz
    tar Jvxf Python-2.7.13.tar.xz
    cd Python-2.7.13
    ./configure --prefix=/usr/local/lib/python2.7.13 --with-zlib=/usr/include --with-ssl
    make && make install

    # --- add new installed python to syspath ---
    echo 'PATH=/usr/local/lib/python2.7.13/bin:$PATH' >> ~/.bashrc
    source ~/.bashrc
    python -V  # confirm syspath works

    # --- download get-pip.py and install pip ---
    cd ~
    wget https://bootstrap.pypa.io/get-pip.py
    python get-pip.py

    # --- install virtualenv ---
    pip install virtualenvwrapper
    echo 'VIRTUALENVWRAPPER_PYTHON=/usr/local/lib/python2.7.13/bin/python' >> ~/.bashrc
    echo 'source /usr/local/lib/python2.7.13/bin/virtualenvwrapper.sh' >> ~/.bashrc
    source ~/.bashrc
