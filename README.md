```bash
# BridgeName: br0
# Interface1: enp6s0f0
# Interface2: enp7s0f3




# Delete
sudo ip link set br0 down
sudo brctl delbr br0
ip addr flush dev enp6s0f0
ip addr flush dev enp7s0f3


# ADD
sudo ip link set enp6s0f0 down
sudo ip link set enp7s0f3 down

sudo brctl addbr br0
sudo brctl stp br0 off
brctl setageing br0 0

sudo brctl addif br0 enp6s0f0
sudo brctl addif br0 enp7s0f3


sudo ip link set enp6s0f0 up
sudo ip link set enp7s0f3 up
sudo ip link set br0 up

sudo ip link set dev enp6s0f0 promisc on
sudo ip link set dev enp7s0f3 promisc on
sudo ip link set dev br0 promisc on

# Show
brctl show
brctl showstp br0
ip link show enp6s0f0
ip link show enp7s0f3
ip link show br0
```
