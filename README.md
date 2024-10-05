# openlane-flow

Follow the instructions in Nix-based Installation to install Nix and set up Cachix.

You will need curl to install Nix.

To install curl on Ubuntu, simply type in the following in your terminal:
```
sudo apt-get install -y curl
```
After that, simply run this command:
```
curl --proto '=https' --tlsv1.2 -sSf -L https://install.determinate.systems/nix/pr/1145 | sh -s --install --no-confirm --extra-conf " extra-substituters = https://openlane.cachix.org extra-trusted-public-keys = openlane.cachix.org-1:qqdwh+QMNGmZAuyeQJTH9ErW57OWSvdtuwfBKdS254E= "
```