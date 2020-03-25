- docker-ce
  
  - CentOS/RedHat
  
    ```shell
    curl -o /etc/yum.repos.d/docker-ce.repo https://mirrors.ustc.edu.cn/docker-ce/linux/centos/docker-ce.repo
    sed -i 's#download.docker.com#mirrors.ustc.edu.cn/docker-ce#g' /etc/yum.repos.d/docker-ce.repo
    ```
  
  - Ubuntu

    ```shell
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository \
       "deb [arch=amd64] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu \
       $(lsb_release -cs) \
       stable"
    sudo apt-get update
    sudo apt-get install docker-ce
    ```
    
  - Debian

    ```shell
    curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
    sudo add-apt-repository \
       "deb [arch=amd64] http://mirrors.ustc.edu.cn/docker-ce/linux/debian \
       $(lsb_release -cs) \
       stable"
    sudo apt-get update
    sudo apt-get install docker-ce
    ```
  
 
- docker 客户端

  ```shell
  cp  /etc/docker/daemon.json{,-bak}
  curl -sSL https://url.cn/5p1qhXo > etc/docker/daemon.json
  ```

- 镜像站点测速

  ```shell
  curl -sSL https://url.cn/5bHkKgq | bash
  ```

- docker.io 镜像加速
  
  ```shell
  docker pull dockerhub.azk8s.cn/library/centos
  ```

- gcr.io 镜像加速

	```shell
  docker pull gcr.azk8s.cn/google_containers/kube-apiserver:v1.16.3
  docker pull registry.cn-hangzhou.aliyuncs.com/google_containers/kube-apiserver:v1.16.3
  ```
  
- quay.io 镜像加速

  ```shell
  docker pull quay.azk8s.cn/coreos/kube-state-metrics:v1.7.2
  ```
  
- 下载gcr镜像

	```shell
  curl -sSL https://url.cn/5aLmxqd | bash -s gcr.io/google_containers/kube-apiserver:v1.16.3
  ```
  
- 下载k8s镜像

  ```shell
  curl -sSL https://url.cn/5aLmxqd | bash -s k8s.gcr.io/pause-amd64:3.1
  ```
  
- 指定k8s版本，下载全套件

  ```shell
  curl -sSL https://url.cn/5aLmxqd | bash -s - -t v1.16.3
  ```
  
- 下载quay.io镜像

  ```shell
  curl -sSL https://url.cn/5aLmxqd | bash -s quay.io/coreos/kube-state-metrics:v1.7.2
  ```
  
- docker HTTP/HTTPS 代理

  ```shell
  mkdir /etc/systemd/system/docker.service.d/
  cat << 'EOF' > /etc/systemd/system/docker.service.d/http-proxy.conf
  [Service]
  Environment="HTTP_PROXY=http://127.0.0.1:7890/"
  Environment="HTTPS_PROXY=https://127.0.0.1:7890/"
  EOF

  systemctl daemon-reload
  systemctl restart docker
  ```


  