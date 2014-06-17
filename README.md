# Description

'docker-baids' stands for "docker bash aids" and it's just a bunch of general purpose bash aliases that turned into a bunch of general purpose bash functions+aliases for 'docker' project.

You can use them in a standalone way (just copy/paste functions or aliases to your own files) or you can use it with [baids](https://github.com/rcmorano/baids), a project to manage bash functions and aliases.

# Installation

Just clone or link this project under '~/.baids/functions.d' and reload aliases:

```
git clone https://github.com/rcmorano/docker-baids.git ~/.baids/functions.d/docker-baids
baids-reload
```

```bash
~# git clone https://github.com/rcmorano/docker-baids.git ~/.baids/functions.d/docker-baids
Cloning into '/root/.baids/functions.d/docker-baids'...
remote: Reusing existing pack: 69, done.
remote: Total 69 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (69/69), done.
Checking connectivity... done
~# baids-reload
~# docker<TAB>
docker                                   docker-container-ip
docker-autocommit                        docker-container-most-recent
docker-baids-reload                      docker-container-remove-all
docker-baids-remap                       docker-container-remove-all-non-running
docker-baids-upgrade                     docker-image-most-recent
docker-container-diff-most-recent        docker-image-remove-all
docker-container-inspect-most-recent     docker-image-remove-orphan
~# 
```

# Usage

You will usually type 'docker-' and push \<TAB\> to complete the command or remember some of the shortened aliases :]

Here is the current functions list and some info. Although most are self explanatory, some need notes:

* **docker-baids-reload**: reload aliases and functions
* **docker-baids-remap**: recreates alias files from functions in 'functions.d' dir, then reloads them.
It makes acronym-based aliases for each function in a separated file in 'aliases.d'. In e.g.:
```
# contents of $HOME/.docker-baids/aliases.d/00-docker-baids
alias dbr='docker-baids-reload'
alias dbre='docker-baids-remap'
alias dbu='docker-baids-upgrade'
alias dcmr='docker-container-most-recent'
alias dcdmr='docker-container-diff-most-recent'
alias dci='docker-container-ip'
alias dcimr='docker-container-inspect-most-recent'
alias dcra='docker-container-remove-all'
alias dcranr='docker-container-remove-all-non-running'
alias dimr='docker-image-most-recent'
alias dira='docker-image-remove-all'
alias diro='docker-image-remove-orphan'
```
* **docker-baids-upgrade**: pull rebases your docker-baids installation. Be careful :]
* **docker-container-most-recent**: returns the most recently launched container's id
* **docker-container-diff-most-recent**: 'docker diff' the most recently launched container
* **docker-container-ip**: 'docker inspect' the most recently launched container and print its IP.
It admits a container ID as argument also.
* **docker-container-inspect-most-recent**: 'docker inspect' the most recently launched container
* **docker-container-remove-all**: removes every existant container in localhost.
**NOTE:** It tries to kill every running container, then, it tries to remove all of them.
* **docker-container-remove-all-non-running**: removes only the non-running containers
* **docker-image-most-recent**: returns the most recently build image's id
* **docker-image-remove-all**: Are you sure? Tries to remove every image in docker host leaving a clean docker environment.
**NOTE:** It calls 'docker-container-remove-all', then, tries to remove all the images.
* **docker-image-remove-orphan**: It tries to remove every non tagged image.

# Extending/Contributing

1. Fork project
2. Add some bash functions (in e.g. your custom 'docker run' for xexposing port 80 for a determined project)
3. Execute 'baids-remap' and get shortened aliases for your functions
4. Commit your changes
5. Optionally, if you consider that your functions are generic enough to help someone out there, send me a pull request! 

# License and Author                                                             
                                                                                 
Author:: Roberto C. Morano (<rcmova@gmail.com>)                                  
                                                                                 
Copyright:: 2014, Roberto C. Morano (<rcmova@gmail.com>)                         
                                                                                 
Licensed under the Apache License, Version 2.0 (the "License");                  
you may not use this file except in compliance with the License.                 
You may obtain a copy of the License at                                          
                                                                                 
    http://www.apache.org/licenses/LICENSE-2.0                                   
                                                                                 
Unless required by applicable law or agreed to in writing, software              
distributed under the License is distributed on an "AS IS" BASIS,                
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.         
See the License for the specific language governing permissions and              
limitations under the License.
