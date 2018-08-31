# kubelet-on-rpi-zero

Attempts at building kubernetes that works with Raspberry Pi Zero, for use with the Cluster Hat.

## Mount Cgroup subsystems "memory" and "cpuset"

Add `cgroup_enable=cpuset cgroup_enable=memory` to `/boot/cmdline.txt` and reboot.

```bash
sudo reboot now
```

## Install docker

```bash
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker pi
```

## Unzip kubelet.zip and move the kubelet binary to /usr/bin

```bash
unzip kubelet.zip
sudo mv kubelet /usr/bin/kubelet
```

## Move the kubelet.service unit file to the systemd configuration directory

```bash
sudo cp kubelet.service /etc/systemd/system/
```

## Create configuration and manifests directory

```bash
sudo mkdir -p /etc/kubernetes/manifests
```

## Move Kubelet config.yaml to /etc/kubernetes directory

```bash
sudo cp config.yaml /etc/kubernetes/
```

## Start the kubelet service

```bash
sudo systemctl daemon-reload
sudo systemctl enable kubelet
sudo systemctl start kubelet
```

## Verify that the kubelet is running

```bash
sudo systemctl status kubelet
```
