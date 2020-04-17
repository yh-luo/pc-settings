# Setting up Fedora (28+)

## dnf configuration
`/etc/dnf/dnf.conf`

```
[main]
gpgcheck=1
installonly_limit=3
clean_requirements_on_remove=True
fastestmirror=True
deltarpm=True
```

## Update & Cleanup

+ Update packages
    ```bash
    sudo dnf update
    ```
+ Remove caches
    ```bash
    sudo dnf clean all  # all cache
    ```

+ Remove logs
    ```bash
    sudo journalctl --vacuum-size=500M  # keep 500M logs
    ```

## Setting up dependencies

1. Gstreamer for PsychoPy: Install `gstreamermm` . [source](https://groups.google.com/forum/#!topic/wxPython-dev/ixWHYaLw62g)

2. Install dependencies for Tobii Pro SDK to worl. [source](https://www.tobiipro.com/learn-and-support/faqs/my-computer-cannot-connect-to-the-eye-tracker-using-linux-sdk/)
    ```bash
    sudo dnf install libssh2
    sudo dnf install avahi-libs
    sudo dnf install python3-devel
    ```

3. LaTex environment

   + Basic texlive
       ```bash
       sudo dnf install texlive-scheme-basic
       ```
   + Other pacakges that I need
       ```bash
       sudo dnf install texlive-collection-bibtexextra # for bibtex
       sudo dnf install texlive-collection-fontsrecommended
       sudo dnf install texlive-collection-fontsextra
       # for fonts
       sudo dnf install texlive-collection-latexrecommended
       sudo dnf install texlive-collection-latexextra
       ```
