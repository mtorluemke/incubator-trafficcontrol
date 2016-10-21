# Traffic Ops v2 Installation

### 1. Build w/ Docker

* Download Traffic Control repo

    ```
    $ git clone https://github.com/apache/incubator-trafficcontrol.git
    ```

* Build the RPM

    ```
    $ cd incubator-trafficcontrol/traffic_ops/experimental/ui/build
    $ docker build -t tov2-image .
    $ docker run -v $(pwd)/artifacts:/artifacts -e GITREPO=https://github.com/apache/incubator-trafficcontrol.git -e BRANCH=master tov2-image
    ```

    The rpm will be created the `artifacts` directory.

### 2. Install

* Install the Node.js JavaScript runtime

    ```
    $ curl --silent --location https://rpm.nodesource.com/setup_6.x | sudo bash -
    $ sudo yum install -y nodejs
    ```

* Install the Traffic Ops v2 RPM

    ```
    $ sudo yum install -y ./artifacts/traffic_ops_v2-[version]-[commits].[sha].x86_64.rpm
    ```

### 3. Configure

* Configure Traffic Ops v2

    ```
    $ cd /etc/traffic_ops_v2/conf
    $ sudo cp config-template.js config.js
    $ sudo vi config.js (read the inline comments)
    ```

### 4. Run

* Start Traffic Ops v2

    ```
    $ sudo service traffic_ops_v2 start
    ```

* Navigate to Traffic Ops v2

    ```
    $ http://localhost:8080
    ```

#### Notes

    - Traffic Ops v2 consumes the Traffic Ops API, therefore, an instance of Traffic Ops must be running.
    - This is known to work with CentOS 6.7 and Centos 7 as the host environment.
