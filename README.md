# openlane-flow

For beginner friendly method we will follow the instructions in Nix-based Installation to install Nix and set up Cachix.

You will need curl to install Nix.

To install curl on Ubuntu, simply type in the following in your terminal:
```
sudo apt-get install -y curl
```
After that, simply run this command:
```
curl --proto '=https' --tlsv1.2 -sSf -L https://install.determinate.systems/nix/pr/1145 | sh -s --install --no-confirm --extra-conf " extra-substituters = https://openlane.cachix.org extra-trusted-public-keys = openlane.cachix.org-1:qqdwh+QMNGmZAuyeQJTH9ErW57OWSvdtuwfBKdS254E= "
```
Make sure to close all terminals after you’re done with this step.

If you already have Nix set up…

You will need to enable OpenLane’s Binary Cache manually.

We use a service called Cachix, which allows the reproducible Nix builds to be stored on a cloud server so you do not have to build OpenLane’s dependencies from scratch on every computer, which will take a long time.

First, need to install Cachix by running the following in your terminal:

```
nix-env -f "<nixpkgs>" -iA cachix
```
Then set up the OpenLane binary cache as follows:
```
sudo env PATH="$PATH" cachix use openlane
```
…and restart the Nix daemon.
```
sudo pkill nix-daemon
```
try updating in this /etc/nix/nix.conf the below lines: 
```
extra-substituters = https://openlane.cachix.org
extra-trusted-public-keys = openlane.cachix.org-1:qqdwh+QMNGmZAuyeQJTH9ErW57OWSvdtuwfBKdS254E=
```
Make sure to restart nix-daemon after updating /etc/nix/nix.conf.
```
sudo pkill nix-daemon
```
Cloning OpenLane, With git installed, just run the following:
```
git clone https://github.com/efabless/openlane2
```
That’s it. Whenever you want to use OpenLane, nix-shell in the repository root directory and you’ll have a full OpenLane environment. The first time might take around 10 minutes while binaries are pulled from the cache.

To quickly test your installation, simply run 
```
openlane --smoke-test
``` 
in the nix shell.