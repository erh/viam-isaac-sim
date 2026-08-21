# Getting started guide

This guide assumes that you're on linux with the Isaac simulator already installed.

These instructions were tested with:
- nvidia-open driver 580.178.04
- dual RTX 5060 Ti
- isaac sim 5.0.0-rc45 installed at /isaac-sim
- ubuntu 24.04.4

- [Viam setup](#viam-setup)

## Viam setup

1. Go to app.viam.com and follow the account creation flow, or sign in if you already have an account
1. Go to your [fleet page](https://app.viam.com/fleet/) and use the 'Add machine' button on the right to create a machine we'll use to host the simulation
1. If you're on a developer machine, you probably don't want to install the viam daemon. Instead, pick a folder on your computer to download the viam-server binary:
	- `~/viam-isaac` is a good default
	- inside the new folder, download viam-server with `wget https://storage.googleapis.com/packages.viam.com/apps/viam-server/viam-server-stable-$(uname -m) && mv viam-server-stable-$(uname -m) viam-server && chmod +x viam-server && ./viam-server -version`
1. Grab your credentials: back in the web UI, go to the status dropdown on the top menu bar. It's likely in the blue 'awaiting setup' state. Open it, hit the 'Machine cloud credentials' button, then paste the credentials into a `viam.json` file in your `~/viam-isaac` folder.
1. Boot viam: in your terminal, run `./viam-server -config viam.json`. As it comes up, in the web UI, you should see the status dropdown turn to a green 'Online' state.

## Configure

install the fragment

TODO: make the module public https://app.viam.com/module/erh/isaac-sim

TODO: move ISAAC_SIM_PATH to config instead of env -- gui cannot override env vars in a fragment-provided module
