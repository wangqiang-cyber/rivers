

    title: "ETCD"
    date: 2019-11-11T14:45+08:00
    keywords: ["ETCD","linux"]
    description: "ETCD"
    tags: ["ETCD","linux"]
    categories: ["linux"]
    author: "mpli@iflytek.com"

**1、yum安装etcd**

yum -y install etcd



**2、配置**

**etcd1配置如下：**



 # grep -vE "^#|^$" /etc/etcd/etcd.conf 

 # [member]

ETCD_NAME="etcd1"

ETCD_DATA_DIR="/var/lib/etcd/default.etcd"

ETCD_LISTEN_PEER_URLS="http://192.168.1.8:2380"

ETCD_LISTEN_CLIENT_URLS="http://192.168.1.8:2379,http://127.0.0.1:2379"

 #[cluster]

ETCD_INITIAL_ADVERTISE_PEER_URLS="http://192.168.1.8:2380"

ETCD_ADVERTISE_CLIENT_URLS="http://192.168.1.8:2379"

ETCD_INITIAL_CLUSTER="etcd1=http://192.168.1.8:2380,etcd2=http://192.168.1.9:2380,etcd3=http://192.168.1.10:2380"

ETCD_INITIAL_CLUSTER_TOKEN="etcd-cluster"

ETCD_INITIAL_CLUSTER_STATE="new"



**etcd2配置如下：**

 #[cluster]

ETCD_NAME="etcd2"

ETCD_DATA_DIR="/var/lib/etcd/default.etcd"

ETCD_LISTEN_PEER_URLS="http://192.168.1.9:2380"

ETCD_LISTEN_CLIENT_URLS="http://192.168.1.9:2379,http://127.0.0.1:2379"

 #[cluster]

ETCD_INITIAL_ADVERTISE_PEER_URLS="http://192.168.1.9:2380"

ETCD_ADVERTISE_CLIENT_URLS="http://192.168.1.9:2379"

ETCD_INITIAL_CLUSTER="etcd1=http://192.168.1.8:2380,etcd2=http://192.168.1.9:2380,etcd3=http://192.168.1.10:2380"

ETCD_INITIAL_CLUSTER_TOKEN="etcd-cluster"

ETCD_INITIAL_CLUSTER_STATE="new"



**etcd3配置如下：**

 #[cluster]

ETCD_NAME="etcd2"

ETCD_DATA_DIR="/var/lib/etcd/default.etcd"

ETCD_LISTEN_PEER_URLS="http://192.168.1.10:2380"

ETCD_LISTEN_CLIENT_URLS="http://192.168.1.10:2379,http://127.0.0.1:2379"

 #[cluster]

ETCD_INITIAL_ADVERTISE_PEER_URLS="http://192.168.1.10:2380"

ETCD_ADVERTISE_CLIENT_URLS="http://192.168.1.10:2379"

ETCD_INITIAL_CLUSTER="etcd1=http://192.168.1.8:2380,etcd2=http://192.168.1.9:2380,etcd3=http://192.168.1.10:2380"

ETCD_INITIAL_CLUSTER_TOKEN="etcd-cluster"

ETCD_INITIAL_CLUSTER_STATE="new"



**3、启动etcd**

systemctl start etcd

systemctl enable etcd

