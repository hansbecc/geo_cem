# GeoCEM

GeoNode template project. Generates a django project with GeoNode support.
## Description
This repository contains a Django application based on Geonode project that provide metadata and geospatial data from the Metropolitan Study Center (CEM) of São Paulo.

This information is shared with everybody.
## Live Demo
The demo version it is at the CEM website of Interactive Systems, and you can see [here](http://200.144.244.238)
## Development setup
This section covers the necessary steps to get the application running on a
local development machine. It assumes you're using Ubuntu, so you may need
to adapt some of the commands if this is not true.
### Dependencies
- Docker
- Docker-compose

### Dependencies installation and setup

#### Docker
##### Installation
  ```bash
    sudo add-apt-repository universe
    sudo apt-get update -y
    sudo apt-get install -y git-core git-buildpackage debhelper devscripts
    sudo apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

    sudo apt-get update -y
    sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-compose
    sudo apt autoremove --purge

    sudo adduser geonode
    sudo usermod -aG sudo geonode
    sudo usermod -aG docker geonode
    su geonode
  ```
#### Deploy an instance of a geonode-project Django template 3.1.x with Docker on localhost
Prepare the environment
  ```bash
  sudo mkdir -p /opt/geonode_custom/
  sudo usermod -a -G www-data geonode
  sudo chown -Rf geonode:www-data /opt/geonode_custom/
  sudo chmod -Rf 775 /opt/geonode_custom/
  ```
Clone the source code
  ```bash
  cd /opt/geonode_custom/
  git clone https://github.com/GeoNode/geonode-project.git -b 3.2.x
  ```
Make an instance out of the Django Template
** Note: ** We will call our instance geo_cem. You can change the name at your convenience.
   ```bash
   source /usr/share/virtualenvwrapper/virtualenvwrapper.sh
   mkvirtualenv --python=/usr/bin/python3 geo_cem

   Alterantively you can also create the virtual env like below
   python3.8 -m venv /home/geonode/dev/.venvs/geo_cem
   source /home/geonode/dev/.venvs/geo_cem/bin/activate

   pip install Django==2.2.12

   django-admin startproject --template=./geonode-project -e py,sh,md,rst,json,yml,ini,env,sample,properties -n monitoring-cron -n Dockerfile geo_cem
   cd /opt/geonode_custom/geo_cem
   ```
Modify the code and the templates and rebuild the Docker Containers
   ```bash
   docker-compose -f docker-compose.yml build --no-cache
   ```
Finally, run the containers
   ```bash
   docker-compose -f docker-compose.yml up -d
   ```
[Installation reference](https://docs.geonode.org/en/master/install/advanced/project/index.html#deploy-an-instance-of-a-geonode-project-django-template-3-2-0-with-docker-on-localhost)

#### Recommended: Track your changes

Step 1. Install Git (for Linux, Mac or Windows).

Step 2. Init git locally and do the first commit:

```bash
git init
git add *
git commit -m "Initial Commit"
git branch -M main
git remote add origin https://github.com/repo_demo/demo.git
git push -u origin main
```

Step 3. Set up a free account on github or bitbucket and make a copy of the repo there.



### Project setup

## Testing

## Project Phases

## Wiki
