# Setting up Fedora 28

## Update

```bash
sudo dnf update
sudo dnf upgrade
```

## Setting up some packages

```bash
sudo dnf install gcc-c++
```

## Setting up Python

1. Install `python-virtualenv`
    ```bash
    sudo dnf install python-virtualenv
    ```
2. Install multiple Python interpreters
    ```bash
    sudo dnf install python35 # for tobii-research to work
    sudo dnf install python36 # for PsychoPy3 testing
    ```
3. Create a virtual environment for running PsychoPy

    1. Get the dependencies for Linux
        1. Get `wxPython`
            1. [Prerequisites](https://github.com/wxWidgets/Phoenix/blob/master/README.rst#prerequisites)
            2. Gstremer is a fucking headache.
                1. The problem
                    - Soulution: install `gstreamermm` [source](https://groups.google.com/forum/#!topic/wxPython-dev/ixWHYaLw62g)
            3. [Get wxPython wheels](https://wxpython.org/pages/downloads/)
        2. Get `PyQt5`
    2. Create the environment from `psychopy-env.txt` (thanks past me!)
        ```bash
        virtualenv psypy3 --python=python35
        source psypy3/bin/activate
        ```
        ```bash
        (psypy3)$ pip install -r psychopy-env.txt
        ```
        - psychopy-env.txt
        ```text
        asn1crypto==0.24.0
        astroid==2.0.1
        certifi==2018.4.16
        cffi==1.11.5
        chardet==3.0.4
        configobj==5.0.6
        cryptography==2.3
        cycler==0.10.0
        decorator==4.3.0
        et-xmlfile==1.0.1
        ffmpeg-python==0.1.16
        future==0.16.0
        gevent==1.3.5
        greenlet==0.4.14
        idna==2.7
        imageio==2.3.0
        intel-openmp==2018.0.3
        isort==4.3.4
        jdcal==1.4
        json-tricks==3.12.2
        kiwisolver==1.0.1
        lazy-object-proxy==1.3.1
        matplotlib==2.2.2
        mccabe==0.6.1
        moviepy==0.2.3.5
        msgpack-python==0.5.6
        numexpr==2.6.6
        numpy==1.15.0
        opencv-python==3.4.2.17
        openpyxl==2.5.4
        pandas==0.23.3
        patsy==0.5.0
        Pillow==5.2.0
        psutil==5.4.6
        pycparser==2.18
        pygame==1.9.4
        pyglet==1.3.2
        pylint==2.0.1
        PyOpenGL==3.1.0
        pyOpenSSL==18.0.0
        pyosf==1.0.5
        pyparallel==0.2.2
        pyparsing==2.2.0
        Pypubsub==4.0.0
        PyQt5==5.11.2
        PyQt5-sip==4.19.12
        pyserial==3.4
        python-bidi==0.4.0
        python-dateutil==2.7.3
        pytz==2018.5
        PyYAML==3.13
        pyzmq==17.1.0
        requests==2.19.1
        scipy==1.1.0
        six==1.11.0
        sounddevice==0.3.11
        SoundFile==0.10.2
        tables==3.4.4
        tobii-research==1.5.0
        tqdm==4.24.0
        typed-ast==1.1.0
        urllib3==1.23
        wrapt==1.10.11
        wxPython==4.0.3
        xlrd==1.1.0
        zmq==0.0.0
        ```
    3. Download and install PsychoPy
        - My current experiment use [v1.90.3](https://github.com/psychopy/psychopy/releases/tag/1.90.3)
    4. Additional package for eyetracking experiments
        1. tobii_research
            ```bash
            pip install tobii_research
            ```
        2. [psychopy_tobii_controller](https://github.com/hsogo/psychopy_tobii_controller)
        3. [psychopy_tobii_infant](https://github.com/yh-luo/psychopy_tobii_infant) in case that I don't have a local repository.
        4. Install dependencies for Tobii Pro SDK to work
            - [source](https://www.tobiipro.com/learn-and-support/faqs/my-computer-cannot-connect-to-the-eye-tracker-using-linux-sdk/)
            ```bash
            sudo dnf install libssh2
            sudo dnf install avahi-libs
            sudo dnf install python3-devel
            ```

## Setting up R

1. Install R (it takes some time)
    ```bash
    sudo dnf install R
    ```
2. Install RStudio
    1. Download the [rpm](https://www.rstudio.com/products/rstudio/download/#download)
    2. use `dnf` to install it

## Setting up Foxit Reader for pdf reading

1. [Download it](https://www.foxitsoftware.com/pdf-reader/)
2. Extract the file and make it executable to run
    ```bash
    tar zxf file.tar.gz
    chmod a+x FoxitReader.enu.setup.2.4.1.0609(r08f07f8).x64.run
    ./FoxitReader.enu.setup.2.4.1.0609(r08f07f8).x64.run
    ```
3. Install it with the wizard
4. Make it "acutally" run
    - [source](https://gist.github.com/kostyay/dfbdb0d16b2cb256b67bf9176541b1fc)
    ```bash
    cd ~/opt/foxitsoftware/foxitreader
    ln -s /lib64/libssl.so.10 lib/libssl.so.1.0.0
    ln -s /lib64/libcrypto.so.10 lib/libcrypto.so.1.0.0
    ```

## Setting up LaTex environment

1. Install the basic texlive
    ```bash
    sudo dnf install texlive-scheme-basic
    ```
2. Other pacakges that I need to live
    ```bash
    sudo dnf install texlive-collection-bibtexextra # for bibtex
    sudo dnf install texlive-collection-fontsrecommended
    sudo dnf install texlive-collection-fontsextra
    # for fonts
    sudo dnf install texlive-collection-latexrecommended
    sudo dnf install texlive-collection-latexextra
    # I don't know what it's actually for but it won't hurt.
    sudo dnf install texlive-apa6 # for apa6 class
    sudo dnf install latexmk # for LaTex Workshop to work
    ```

## Install other softwares that I used

I'm too lazy to list them. Good luck future me.
