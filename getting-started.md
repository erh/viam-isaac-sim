# Getting started guide

This guide assumes that you're on linux with the Isaac simulator already installed.

These instructions were tested with:
- nvidia-open driver 580.178.04
- dual RTX 5060 Ti
- isaac sim 5.0.0-rc45 installed at /isaac-sim
- ubuntu 24.04.4

## Viam setup

1. Go to app.viam.com and follow the account creation flow, or sign in if you already have an account
1. Go to your [fleet page](https://app.viam.com/fleet/) and use the 'Add machine' button on the right to create a machine we'll use to host the simulation
1. If you're on your personal dev computer, you probably don't want to install the viam daemon. Instead, pick a folder on your computer to download the viam-server binary:
	- `~/viam-isaac` is a good default
	- inside the new folder, download viam-server with `wget https://storage.googleapis.com/packages.viam.com/apps/viam-server/viam-server-stable-$(uname -m) && mv viam-server-stable-$(uname -m) viam-server && chmod +x viam-server && ./viam-server -version`
1. Grab your credentials: back in the web UI, go to the status dropdown on the top menu bar. It's likely in the blue 'awaiting setup' state. Open it, hit the 'Machine cloud credentials' button, then paste the credentials into a `viam.json` file in your `~/viam-isaac` folder.
1. Boot viam: in your terminal, run `ISAAC_SIM_PATH=/isaac-sim ./viam-server -config viam.json`. As it comes up, in the web UI, you should see the status dropdown turn to a green 'Online' state.

## Start Isaac in Viam

In the 'configure' tab of the web UI, hit the '+' button or tap 'A', then tap 'B' for blocks, then find the `isaac-sim-pick-and-place` fragment from `erh` and install it. Click 'Save' in the top right.

Switch to the 'logs' tab to watch the installed components start up. On the test machine this takes around 15 seconds. You'll see an 'event=complete' event from the rdk.activity logger when this is done.

Now switch to the 'control' tab to interact with the cameras and arm.

If something goes wrong, the place to debug is the logs tab; to cut down on noise, find the components list on the left-side menu bar and click the `erh_isaac-sim` module to filter down the output.
