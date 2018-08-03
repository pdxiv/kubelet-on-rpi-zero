# kubelet-on-rpi-zero
Attempts at building kubernetes that works with Raspberry Pi Zero, for use with the Cluster Hat.

Unzip kubelet.zip and move the kubelet binary to /usr/bin.
```
unzip kubelet.zip
sudo mv kubelet /usr/bin/kubelet
```
Move the kubelet.service unit file to the systemd configuration directory.
```
sudo cp kubelet.service /etc/systemd/system/
```
Create configuration and manifests directory.
```
sudo mkdir -p /etc/kubernetes/manifests
```
Move Kubelet config.yaml to /etc/kubernetes directory:
```
sudo cp config.yaml /etc/kubernetes/
```
Start the kubelet service.
```
sudo systemctl daemon-reload

sudo systemctl enable kubelet

sudo systemctl start kubelet
```
Verify that the kubelet is running.
```
sudo systemctl status kubelet
```
