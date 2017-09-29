## How to setup a local virtual CAN interface

make install will install to system and require root permissions.
Only tested on linux will not work on windows but might work on mac


```shell
git clone https://github.com/linux-can/can-utils
cd can-utils
./autogen.sh
make
make install
```

from [StackOverflow](https://stackoverflow.com/questions/21022749/how-to-create-virtual-can-port-on-linux-c)

```shell
modprobe can
ip link add dev vcan0 type vcan
ip link set up vcan0
```

If everything worked as intended it is now possible to interact with vcan0 as if it were a can bus using can-utils
like so:

```shell
cangen vcan0 &
candump vcan0
```

## Running CAN dump extracting script

1. Start WIFI hot spot
2. Power on Moped
3. Edit REMOTE variable in getdump.sh so that it is equal to ip leased to Moped
4. Connect to WIFI hot spot
5. Make sure that current directory is src
6. ./getdump.sh
7. Pray
8. Profit!? (can0.dump + can1.dump in src if success)
