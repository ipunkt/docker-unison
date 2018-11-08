# unison
Docker auto build repository to synchronize using unison version 2.40.61

## Usage
Install unison 2.40.61 on the target server. There is a statically compiled
version available at http://unison-binaries.inria.fr/

Mount the directory to be synced to /target and a persistent volume for unison
meta data to /unison

Set SERVERCMD if unison is not in the remote servers' paths or has a name other
thatn `unison`

Set REMOTESERVER to the target. Example //remoteserver/path/from/home

Set UNISONLOCALHOSTNAME if you want to use the meta data volume with more than
one container. Otherwise it will default to `unisoncontainer`

## Strange segfaults
The statically linked unison 2.40.61 executable uses vsyscalls which fail on
recent linux kernels. See https://einsteinathome.org/de/content/vsyscall-now-disabled-latest-linux-distros
how this can be fixed. However I do not recommend doing this.
