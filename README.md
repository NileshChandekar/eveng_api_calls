### EVE-NG API CALL's


# Authentication

  ~~~
  root@eve-ng:~# curl -s -b /tmp/cookie -c /tmp/cookie -X POST -d '{"username":"admin","password":"eve"}' http://127.0.0.1/api/auth/login | jq .
  {
    "code": 200,
    "status": "success",
    "message": "User logged in (90013)."
  }
  root@eve-ng:~#
  ~~~

# List Folders

  ~~~
  root@eve-ng:~# curl -s -c /tmp/cookie -b /tmp/cookie -X GET -H 'Content-type: application/json' http://127.0.0.1/api/folders/ | jq .
  {
    "code": 200,
    "status": "success",
    "message": "Successfully listed path (60007).",
    "data": {
      "folders": [
        {
          "name": "ansible",
          "path": "/ansible"
        }
      ],
      "labs": []
    }
  }
  root@eve-ng:~#
  ~~~

# Nested folders

  ~~~
  root@eve-ng:~# curl -s -c /tmp/cookie -b /tmp/cookie -X GET -H 'Content-type: application/json' http://127.0.0.1/api/folders/ansible | jq .
  {
    "code": 200,
    "status": "success",
    "message": "Successfully listed path (60007).",
    "data": {
      "folders": [
        {
          "name": "..",
          "path": "/"
        }
      ],
      "labs": [
        {
          "file": "Lab_1.unl",
          "path": "/ansible/Lab_1.unl",
          "umtime": 1582038693,
          "mtime": "18 Feb 2020  16:11"
        },
        {
          "file": "RHOSP_16.unl",
          "path": "/ansible/RHOSP_16.unl",
          "umtime": 1582038694,
          "mtime": "18 Feb 2020  16:11"
        },
        {
          "file": "RHOSP_16_Cloned_16FEB2020.unl",
          "path": "/ansible/RHOSP_16_Cloned_16FEB2020.unl",
          "umtime": 1582038693,
          "mtime": "18 Feb 2020  16:11"
        }
      ]
    }
  }
  root@eve-ng:~#
  ~~~

# Get Lab Details

  ~~~
  root@eve-ng:~# curl -s -c /tmp/cookie -b /tmp/cookie -X GET -H 'Content-type: application/json' http://127.0.0.1/api/labs/ansible/RHOSP_16.unl | jq .
  {
    "code": 200,
    "status": "success",
    "message": "Lab has been loaded (60020).",
    "data": {
      "author": "",
      "description": "",
      "body": "",
      "filename": "RHOSP_16.unl",
      "id": "74563b1f-43fb-47c6-b331-326508704434",
      "name": "RHOSP_16",
      "version": "1",
      "scripttimeout": 300,
      "lock": 0
    }
  }
  root@eve-ng:~#
  ~~~

# Get topology

  ~~~
  root@eve-ng:~# curl -s -c /tmp/cookie -b /tmp/cookie -X GET -H 'Content-type: application/json' http://127.0.0.1/api/labs/ansible/RHOSP_16.unl/topology | jq .
  {
    "code": "200",
    "status": "success",
    "message": "Topology loaded",
    "data": [
      {
        "type": "ethernet",
        "source": "node1",
        "source_type": "node",
        "source_label": "e0",
        "destination": "network1",
        "destination_type": "network",
        "destination_label": ""
      },
      {
        "type": "ethernet",
        "source": "node2",
        "source_type": "node",
        "source_label": "e0",
        "destination": "network3",
        "destination_type": "network",
        "destination_label": ""
      },
      {
        "type": "ethernet",
        "source": "node2",
        "source_type": "node",
        "source_label": "e1",
        "destination": "node1",
        "destination_type": "node",
        "destination_label": "e1",
        "network_id": 2
      },
      {
        "type": "ethernet",
        "source": "node4",
        "source_type": "node",
        "source_label": "e0",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e12",
        "network_id": 5
      },
      {
        "type": "ethernet",
        "source": "node4",
        "source_type": "node",
        "source_label": "e1",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e3",
        "network_id": 10
      },
      {
        "type": "ethernet",
        "source": "node4",
        "source_type": "node",
        "source_label": "e2",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e21",
        "network_id": 14
      },
      {
        "type": "ethernet",
        "source": "node5",
        "source_type": "node",
        "source_label": "e0",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e13",
        "network_id": 6
      },
      {
        "type": "ethernet",
        "source": "node5",
        "source_type": "node",
        "source_label": "e1",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e4",
        "network_id": 11
      },
      {
        "type": "ethernet",
        "source": "node5",
        "source_type": "node",
        "source_label": "e2",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e22",
        "network_id": 15
      },
      {
        "type": "ethernet",
        "source": "node6",
        "source_type": "node",
        "source_label": "e0",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e14",
        "network_id": 7
      },
      {
        "type": "ethernet",
        "source": "node6",
        "source_type": "node",
        "source_label": "e1",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e5",
        "network_id": 12
      },
      {
        "type": "ethernet",
        "source": "node6",
        "source_type": "node",
        "source_label": "e2",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e23",
        "network_id": 16
      },
      {
        "type": "ethernet",
        "source": "node7",
        "source_type": "node",
        "source_label": "e0",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e15",
        "network_id": 8
      },
      {
        "type": "ethernet",
        "source": "node7",
        "source_type": "node",
        "source_label": "e1",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e6",
        "network_id": 13
      },
      {
        "type": "ethernet",
        "source": "node7",
        "source_type": "node",
        "source_label": "e2",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e24",
        "network_id": 17
      },
      {
        "type": "ethernet",
        "source": "node3",
        "source_type": "node",
        "source_label": "e0",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e11",
        "network_id": 4
      },
      {
        "type": "ethernet",
        "source": "node3",
        "source_type": "node",
        "source_label": "e1",
        "destination": "node2",
        "destination_type": "node",
        "destination_label": "e2",
        "network_id": 9
      }
    ]
  }
  root@eve-ng:~#
  ~~~

# Start **ALL** nodes ``check the syntax carefully``

  ~~~
  root@eve-ng:~# curl -s -c /tmp/cookie -b /tmp/cookie -X GET -H 'Content-type: application/json' http://127.0.0.1/api/labs/ansible/RHOSP_16.unl/nodes/start | jq .
  {
    "code": 200,
    "status": "success",
    "message": "Nodes started (80048)."
  }
  root@eve-ng:~#
  ~~~

#### What happens when we actually run the above command ^^^^^

  ~~~
  Feb 22 07:47:45 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 1 -t "Router" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:01:00 -netdev tap,id=net0,ifname=vunl0_1_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:01:01 -netdev tap,id=net1,ifname=vunl0_1_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:01:02 -netdev tap,id=net2,ifname=vunl0_1_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:01:03 -netdev tap,id=net3,ifname=vunl0_1_3,script=no -device virtio-net-pci,netdev=net4,mac=00:50:00:00:01:04 -netdev tap,id=net4,ifname=vunl0_1_4,script=no -smp 1 -m 2048 -name Router -uuid b3564d2a-789d-4c7f-9e97-8d562b742c65 -vnc :26869 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=dc > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/1/wrapper.txt 2>&1 &

  Feb 22 07:47:48 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 2 -t "Switch" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:02:00 -netdev tap,id=net0,ifname=vunl0_2_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:02:01 -netdev tap,id=net1,ifname=vunl0_2_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:02:02 -netdev tap,id=net2,ifname=vunl0_2_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:02:03 -netdev tap,id=net3,ifname=vunl0_2_3,script=no -device virtio-net-pci,netdev=net4,mac=00:50:00:00:02:04 -netdev tap,id=net4,ifname=vunl0_2_4,script=no -device virtio-net-pci,netdev=net5,mac=00:50:00:00:02:05 -netdev tap,id=net5,ifname=vunl0_2_5,script=no -device virtio-net-pci,netdev=net6,mac=00:50:00:00:02:06 -netdev tap,id=net6,ifname=vunl0_2_6,script=no -device virtio-net-pci,netdev=net7,mac=00:50:00:00:02:07 -netdev tap,id=net7,ifname=vunl0_2_7,script=no -device virtio-net-pci,netdev=net8,mac=00:50:00:00:02:08 -netdev tap,id=net8,ifname=vunl0_2_8,script=no -device virtio-net-pci,netdev=net9,mac=00:50:00:00:02:09 -netdev tap,id=net9,ifname=vunl0_2_9,script=no -device virtio-net-pci,netdev=net10,mac=00:50:00:00:02:0a -netdev tap,id=net10,ifname=vunl0_2_10,script=no -device virtio-net-pci,netdev=net11,mac=00:50:00:00:02:0b -netdev tap,id=net11,ifname=vunl0_2_11,script=no -device virtio-net-pci,netdev=net12,mac=00:50:00:00:02:0c -netdev tap,id=net12,ifname=vunl0_2_12,script=no -device virtio-net-pci,netdev=net13,mac=00:50:00:00:02:0d -netdev tap,id=net13,ifname=vunl0_2_13,script=no -device virtio-net-pci,netdev=net14,mac=00:50:00:00:02:0e -netdev tap,id=net14,ifname=vunl0_2_14,script=no -device virtio-net-pci,netdev=net15,mac=00:50:00:00:02:0f -netdev tap,id=net15,ifname=vunl0_2_15,script=no -device virtio-net-pci,netdev=net16,mac=00:50:00:00:02:10 -netdev tap,id=net16,ifname=vunl0_2_16,script=no -device virtio-net-pci,netdev=net17,mac=00:50:00:00:02:11 -netdev tap,id=net17,ifname=vunl0_2_17,script=no -device virtio-net-pci,netdev=net18,mac=00:50:00:00:02:12 -netdev tap,id=net18,ifname=vunl0_2_18,script=no -device virtio-net-pci,netdev=net19,mac=00:50:00:00:02:13 -netdev tap,id=net19,ifname=vunl0_2_19,script=no -device virtio-net-pci,netdev=net20,mac=00:50:00:00:02:14 -netdev tap,id=net20,ifname=vunl0_2_20,script=no -device virtio-net-pci,netdev=net21,mac=00:50:00:00:02:15 -netdev tap,id=net21,ifname=vunl0_2_21,script=no -device virtio-net-pci,netdev=net22,mac=00:50:00:00:02:16 -netdev tap,id=net22,ifname=vunl0_2_22,script=no -device virtio-net-pci,netdev=net23,mac=00:50:00:00:02:17 -netdev tap,id=net23,ifname=vunl0_2_23,script=no -device virtio-net-pci,netdev=net24,mac=00:50:00:00:02:18 -netdev tap,id=net24,ifname=vunl0_2_24,script=no -device virtio-net-pci,netdev=net25,mac=00:50:00:00:02:19 -netdev tap,id=net25,ifname=vunl0_2_25,script=no -device virtio-net-pci,netdev=net26,mac=00:50:00:00:02:1a -netdev tap,id=net26,ifname=vunl0_2_26,script=no -device virtio-net-pci,netdev=net27,mac=00:50:00:00:02:1b -netdev tap,id=net27,ifname=vunl0_2_27,script=no -device virtio-net-pci,netdev=net28,mac=00:50:00:00:02:1c -netdev tap,id=net28,ifname=vunl0_2_28,script=no -smp 1 -m 2048 -name Switch -uuid b4f13b1d-82fb-4fba-89d3-3373b4de11e6 -vnc :26870 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=dc > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/2/wrapper.txt 2>&1 &

  Feb 22 07:47:48 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 4 -t "Controller_0" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:04:00 -netdev tap,id=net0,ifname=vunl0_4_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:04:01 -netdev tap,id=net1,ifname=vunl0_4_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:04:02 -netdev tap,id=net2,ifname=vunl0_4_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:04:03 -netdev tap,id=net3,ifname=vunl0_4_3,script=no -smp 4 -m 12000 -name Controller_0 -uuid 9c387900-6cf1-4d9a-92ff-f1549bf08e82 -vnc :26872 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=nd > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/4/wrapper.txt 2>&1 &

  Feb 22 07:47:49 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 5 -t "Controller_1" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:05:00 -netdev tap,id=net0,ifname=vunl0_5_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:05:01 -netdev tap,id=net1,ifname=vunl0_5_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:05:02 -netdev tap,id=net2,ifname=vunl0_5_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:05:03 -netdev tap,id=net3,ifname=vunl0_5_3,script=no -smp 4 -m 12000 -name Controller_1 -uuid adbd15cb-2eb8-4bee-b0c1-a753290c38a0 -vnc :26873 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=nd > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/5/wrapper.txt 2>&1 &

  Feb 22 07:47:50 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 6 -t "Controller_2" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:06:00 -netdev tap,id=net0,ifname=vunl0_6_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:06:01 -netdev tap,id=net1,ifname=vunl0_6_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:06:02 -netdev tap,id=net2,ifname=vunl0_6_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:06:03 -netdev tap,id=net3,ifname=vunl0_6_3,script=no -smp 4 -m 12000 -name Controller_2 -uuid 80073afc-a9cf-4a1e-89fb-3d5c7d47dadb -vnc :26874 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=nd > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/6/wrapper.txt 2>&1 &

  Feb 22 07:47:50 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 7 -t "Compute_0" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:07:00 -netdev tap,id=net0,ifname=vunl0_7_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:07:01 -netdev tap,id=net1,ifname=vunl0_7_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:07:02 -netdev tap,id=net2,ifname=vunl0_7_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:07:03 -netdev tap,id=net3,ifname=vunl0_7_3,script=no -smp 4 -m 12000 -name Compute_0 -uuid 799438ac-6b42-42f3-9530-e7c9b7802974 -vnc :26875 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=nd > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/7/wrapper.txt 2>&1 &

  Feb 22 07:47:50 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 3 -t "undercloud_node" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:03:00 -netdev tap,id=net0,ifname=vunl0_3_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:03:01 -netdev tap,id=net1,ifname=vunl0_3_1,script=no -smp 6 -m 16000 -name undercloud_node -uuid da0246d7-839d-473b-be82-b01b550e4ad2 -vnc :26871 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=dc > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/3/wrapper.txt 2>&1 &
  ~~~



# Stop **ALL** nodes ``check the syntax carefully``


~~~
root@eve-ng:~# curl -s -c /tmp/cookie -b /tmp/cookie -X GET -H 'Content-type: application/json' http://127.0.0.1/api/labs/ansible/RHOSP_16.unl/nodes/stop | jq .
{
  "code": 200,
  "status": "success",
  "message": "Nodes stopped (80050)."
}
root@eve-ng:~#
~~~


#### What happens when we actually run the above command ^^^^^


  ~~~
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/1 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/2 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/4 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/5 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/6 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/7 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/3 > /dev/null 2>&1
  ~~~

#### ^^^^ In the backend it's actually running the command `` fuser -k -TERM /opt/unetlab/tmp/0/<prjectUUID>/node_uuid `` where ``0`` is username --> ``0`` default to ``admin``


**NOTE** : While working with API, you will not get access to your GUI, it get auto disconnect if auth via CLI(api call)


## The same can be done via CLI command line - Beauty is you will have access of GUI and you can see the progress.

## The current state, where all the nodes are stopped.

![Image ipa](/home/nchandek/redhat/githubprojects/eveng_api_calls/images/1.png)


#### Lets start the node from CLI

##### Have created this script file to trigger the **START** event.

  ~~~
  root@eve-ng:~# cat  16start.sh
  #!/bin/bash
  /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 1 > /dev/null 2>&1 ; sleep 3
  /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 2 > /dev/null 2>&1 ; sleep 3
  /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 3 > /dev/null 2>&1 ; sleep 3
  /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 4 > /dev/null 2>&1 ; sleep 3
  /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 5 > /dev/null 2>&1 ; sleep 3
  /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 6 > /dev/null 2>&1 ; sleep 3
  /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 7 > /dev/null 2>&1 ; sleep 3

  root@eve-ng:~#
  ~~~

##### Let me run it now.

  ~~~
  root@eve-ng:~# bash -x 16start.sh
  + /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 1
  + sleep 3
  + /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 2
  + sleep 3
  + /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 3
  + sleep 3
  + /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 4
  + sleep 3
  + /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 5
  + sleep 3
  + /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 6
  + sleep 3
  + /opt/unetlab/wrappers/unl_wrapper -a start -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 7
  + sleep 3
  root@eve-ng:~#
  ~~~

##### The node is been **STARTED**.

![Image ipa](/home/nchandek/redhat/githubprojects/eveng_api_calls/images/2.png)

##### Logs Captured, both **CLI** and **API** call are same. [No difference]
### [START]
  ~~~
  Feb 22 07:47:45 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 1 -t "Router" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:01:00 -netdev tap,id=net0,ifname=vunl0_1_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:01:01 -netdev tap,id=net1,ifname=vunl0_1_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:01:02 -netdev tap,id=net2,ifname=vunl0_1_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:01:03 -netdev tap,id=net3,ifname=vunl0_1_3,script=no -device virtio-net-pci,netdev=net4,mac=00:50:00:00:01:04 -netdev tap,id=net4,ifname=vunl0_1_4,script=no -smp 1 -m 2048 -name Router -uuid b3564d2a-789d-4c7f-9e97-8d562b742c65 -vnc :26869 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=dc > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/1/wrapper.txt 2>&1 &
  Feb 22 07:47:48 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 2 -t "Switch" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:02:00 -netdev tap,id=net0,ifname=vunl0_2_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:02:01 -netdev tap,id=net1,ifname=vunl0_2_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:02:02 -netdev tap,id=net2,ifname=vunl0_2_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:02:03 -netdev tap,id=net3,ifname=vunl0_2_3,script=no -device virtio-net-pci,netdev=net4,mac=00:50:00:00:02:04 -netdev tap,id=net4,ifname=vunl0_2_4,script=no -device virtio-net-pci,netdev=net5,mac=00:50:00:00:02:05 -netdev tap,id=net5,ifname=vunl0_2_5,script=no -device virtio-net-pci,netdev=net6,mac=00:50:00:00:02:06 -netdev tap,id=net6,ifname=vunl0_2_6,script=no -device virtio-net-pci,netdev=net7,mac=00:50:00:00:02:07 -netdev tap,id=net7,ifname=vunl0_2_7,script=no -device virtio-net-pci,netdev=net8,mac=00:50:00:00:02:08 -netdev tap,id=net8,ifname=vunl0_2_8,script=no -device virtio-net-pci,netdev=net9,mac=00:50:00:00:02:09 -netdev tap,id=net9,ifname=vunl0_2_9,script=no -device virtio-net-pci,netdev=net10,mac=00:50:00:00:02:0a -netdev tap,id=net10,ifname=vunl0_2_10,script=no -device virtio-net-pci,netdev=net11,mac=00:50:00:00:02:0b -netdev tap,id=net11,ifname=vunl0_2_11,script=no -device virtio-net-pci,netdev=net12,mac=00:50:00:00:02:0c -netdev tap,id=net12,ifname=vunl0_2_12,script=no -device virtio-net-pci,netdev=net13,mac=00:50:00:00:02:0d -netdev tap,id=net13,ifname=vunl0_2_13,script=no -device virtio-net-pci,netdev=net14,mac=00:50:00:00:02:0e -netdev tap,id=net14,ifname=vunl0_2_14,script=no -device virtio-net-pci,netdev=net15,mac=00:50:00:00:02:0f -netdev tap,id=net15,ifname=vunl0_2_15,script=no -device virtio-net-pci,netdev=net16,mac=00:50:00:00:02:10 -netdev tap,id=net16,ifname=vunl0_2_16,script=no -device virtio-net-pci,netdev=net17,mac=00:50:00:00:02:11 -netdev tap,id=net17,ifname=vunl0_2_17,script=no -device virtio-net-pci,netdev=net18,mac=00:50:00:00:02:12 -netdev tap,id=net18,ifname=vunl0_2_18,script=no -device virtio-net-pci,netdev=net19,mac=00:50:00:00:02:13 -netdev tap,id=net19,ifname=vunl0_2_19,script=no -device virtio-net-pci,netdev=net20,mac=00:50:00:00:02:14 -netdev tap,id=net20,ifname=vunl0_2_20,script=no -device virtio-net-pci,netdev=net21,mac=00:50:00:00:02:15 -netdev tap,id=net21,ifname=vunl0_2_21,script=no -device virtio-net-pci,netdev=net22,mac=00:50:00:00:02:16 -netdev tap,id=net22,ifname=vunl0_2_22,script=no -device virtio-net-pci,netdev=net23,mac=00:50:00:00:02:17 -netdev tap,id=net23,ifname=vunl0_2_23,script=no -device virtio-net-pci,netdev=net24,mac=00:50:00:00:02:18 -netdev tap,id=net24,ifname=vunl0_2_24,script=no -device virtio-net-pci,netdev=net25,mac=00:50:00:00:02:19 -netdev tap,id=net25,ifname=vunl0_2_25,script=no -device virtio-net-pci,netdev=net26,mac=00:50:00:00:02:1a -netdev tap,id=net26,ifname=vunl0_2_26,script=no -device virtio-net-pci,netdev=net27,mac=00:50:00:00:02:1b -netdev tap,id=net27,ifname=vunl0_2_27,script=no -device virtio-net-pci,netdev=net28,mac=00:50:00:00:02:1c -netdev tap,id=net28,ifname=vunl0_2_28,script=no -smp 1 -m 2048 -name Switch -uuid b4f13b1d-82fb-4fba-89d3-3373b4de11e6 -vnc :26870 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=dc > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/2/wrapper.txt 2>&1 &
  Feb 22 07:47:48 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 4 -t "Controller_0" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:04:00 -netdev tap,id=net0,ifname=vunl0_4_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:04:01 -netdev tap,id=net1,ifname=vunl0_4_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:04:02 -netdev tap,id=net2,ifname=vunl0_4_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:04:03 -netdev tap,id=net3,ifname=vunl0_4_3,script=no -smp 4 -m 12000 -name Controller_0 -uuid 9c387900-6cf1-4d9a-92ff-f1549bf08e82 -vnc :26872 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=nd > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/4/wrapper.txt 2>&1 &
  Feb 22 07:47:49 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 5 -t "Controller_1" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:05:00 -netdev tap,id=net0,ifname=vunl0_5_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:05:01 -netdev tap,id=net1,ifname=vunl0_5_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:05:02 -netdev tap,id=net2,ifname=vunl0_5_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:05:03 -netdev tap,id=net3,ifname=vunl0_5_3,script=no -smp 4 -m 12000 -name Controller_1 -uuid adbd15cb-2eb8-4bee-b0c1-a753290c38a0 -vnc :26873 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=nd > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/5/wrapper.txt 2>&1 &
  Feb 22 07:47:50 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 6 -t "Controller_2" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:06:00 -netdev tap,id=net0,ifname=vunl0_6_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:06:01 -netdev tap,id=net1,ifname=vunl0_6_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:06:02 -netdev tap,id=net2,ifname=vunl0_6_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:06:03 -netdev tap,id=net3,ifname=vunl0_6_3,script=no -smp 4 -m 12000 -name Controller_2 -uuid 80073afc-a9cf-4a1e-89fb-3d5c7d47dadb -vnc :26874 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=nd > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/6/wrapper.txt 2>&1 &
  Feb 22 07:47:50 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 7 -t "Compute_0" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:07:00 -netdev tap,id=net0,ifname=vunl0_7_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:07:01 -netdev tap,id=net1,ifname=vunl0_7_1,script=no -device virtio-net-pci,netdev=net2,mac=00:50:00:00:07:02 -netdev tap,id=net2,ifname=vunl0_7_2,script=no -device virtio-net-pci,netdev=net3,mac=00:50:00:00:07:03 -netdev tap,id=net3,ifname=vunl0_7_3,script=no -smp 4 -m 12000 -name Compute_0 -uuid 799438ac-6b42-42f3-9530-e7c9b7802974 -vnc :26875 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=nd > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/7/wrapper.txt 2>&1 &
  Feb 22 07:47:50 INFO: starting /opt/unetlab/wrappers/qemu_wrapper -T 0 -D 3 -t "undercloud_node" -F /opt/qemu-2.4.0/bin/qemu-system-x86_64 -d 0 -x -- -device virtio-net-pci,netdev=net0,mac=00:50:00:00:03:00 -netdev tap,id=net0,ifname=vunl0_3_0,script=no -device virtio-net-pci,netdev=net1,mac=00:50:00:00:03:01 -netdev tap,id=net1,ifname=vunl0_3_1,script=no -smp 6 -m 16000 -name undercloud_node -uuid da0246d7-839d-473b-be82-b01b550e4ad2 -vnc :26871 -hda hda.qcow2 -machine type=pc,accel=kvm -vga std -usbdevice tablet -boot order=dc > /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/3/wrapper.txt 2>&1 &
  ~~~

#### Lets stop the node from CLI

##### Have created this script file to trigger the **STOP** event. // I don't want to stop all nodes

  ~~~
  root@eve-ng:~# cat 16stop.sh
  #!/bin/bash
  /opt/unetlab/wrappers/unl_wrapper -a stop -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 4 > /dev/null 2>&1 ; sleep 3
  /opt/unetlab/wrappers/unl_wrapper -a stop -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 5 > /dev/null 2>&1 ; sleep 3
  /opt/unetlab/wrappers/unl_wrapper -a stop -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 6 > /dev/null 2>&1 ; sleep 3
  /opt/unetlab/wrappers/unl_wrapper -a stop -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 7 > /dev/null 2>&1 ; sleep 3

  root@eve-ng:~#
  ~~~


##### Let me run it now.

  ~~~
  root@eve-ng:~# bash -x 16stop.sh
  + /opt/unetlab/wrappers/unl_wrapper -a stop -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 4
  + sleep 3
  + /opt/unetlab/wrappers/unl_wrapper -a stop -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 5
  + sleep 3
  + /opt/unetlab/wrappers/unl_wrapper -a stop -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 6
  + sleep 3
  + /opt/unetlab/wrappers/unl_wrapper -a stop -T 0 -F /opt/unetlab/labs/ansible/RHOSP_16.unl -D 7
  + sleep 3
  root@eve-ng:~#
  ~~~

##### The node is been **STOPPED**.

![Image ipa](/home/nchandek/redhat/githubprojects/eveng_api_calls/images/3.png)

##### Logs Captured, both **CLI** and **API** call are same. [No difference]
### [STOP]

  ~~~
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/1 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/2 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/4 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/5 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/6 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/7 > /dev/null 2>&1
  Feb 22 07:49:58 INFO: stopping fuser -k -TERM /opt/unetlab/tmp/0/74563b1f-43fb-47c6-b331-326508704434/3 > /dev/null 2>&1
  ~~~
