![SABnzbd Logo](https://www.usenet.com/wp-content/uploads/2017/05/Screenshot_2-1.png)

**SABnzbd in container with multiarch support**
===

Image is automatically updated, when a new version of SABnzbd arrives on GitHub.   
Supported architectures are amd64, arm64, arm.

The container is lightweight and based on alpine Linux.   

SABnzbd development-releases are now requiring **Python 3**, so I updated the container.

Versions in the latest image
-----
- [SABnzbd](https://sabnzbd.org "SABnzbd Project Homepage") Version: latest master on GitHub
- PAR2 from [par2cmdline](https://github.com/Parchive/par2cmdline) Version: 0.8.0

Start your container
-----
- For **[/config/location]**, use the folder, where your **sabnzbd.ini** file is stored.
- For **[/complete/folder]**, use the folder, where your completed downloads will be stored.
- For **[/incomplete/folder]**, use the folder, where the temporary files will be stored, until download is finished.

````
docker run -d \
  -v [/config/location]:/config \
  -v [/complete/folder]:/complete \
  -v [/incomplete/folder]:/incomplete \
  -e UID=[Users UID] \
  -e GID=[Users GID] \
  -p 8080:8080 \
  --restart=unless-stopped avpnusr/sabnzbd-dev
