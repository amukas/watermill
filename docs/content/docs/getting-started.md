+++
title = "Getting started"
description = "Up and running in under a minute"
weight = -9999
draft = false
toc = true
bref = "todo"
type = "docs"
+++

### Install

```bash
go get -u github.com/ThreeDotsLabs/watermill/
```

### Subscribing for messages

{{% tabs id="subscribing" tabs="go-channel,kafka" labels="Go Channel,Kafka" %}}

{{% tabs-tab id="go-channel"%}}
{{% load-snippet-partial file="content/docs/getting-started/go-channel/main.go" first_line_contains="import (" last_line_contains="process(messages)" %}}
{{% load-snippet-partial file="content/docs/getting-started/go-channel/main.go" first_line_contains="func process" %}}
{{% /tabs-tab %}}

{{% tabs-tab id="kafka" %}}
{{% message type="success" %}}
Installed `librdkafka` is required to run Kafka subscriber.
{{% /message %}}

{{< collapse id="installing_rdkafka" >}}

{{< collapse-toggle box_id="docker" >}}
Running in Docker
{{% /collapse-toggle %}}
{{% collapse-box id="docker" %}}
Easiest way to run Watermill with Kafka locally is using Docker.

{{% load-snippet file="content/docs/getting-started/kafka/docker-compose.yml" type="yaml" %}}

And running `docker-compose up`.

More detailed explonation of how it is running, and how to add live reload you can find in [our [...] article](todo).

{{% /collapse-box %}}
{{< collapse-toggle box_id="ubuntu" >}}
Installing librdkafka on Ubuntu
{{% /collapse-toggle %}}
{{% collapse-box id="ubuntu" %}}
Newest version of the `librdkafka` for Ubuntu distributions you can find in [Confluent](https://www.confluent.io/)'s repository.

```bash
# install `software-properties-common`, `wget`, or `gnupg` if not installed yet
sudo apt-get install -y software-properties-common wget gnupg

# add a new repository
wget -qO - https://packages.confluent.io/deb/4.1/archive.key | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.confluent.io/deb/4.1 stable main"

# and then you can install newest version of `librdkafka`
sudo apt-get update && sudo apt-get -y install librdkafka1 librdkafka-dev
```
{{% /collapse-box %}}
{{< collapse-toggle box_id="redhat" >}}
Installing librdkafka on CentOS/RedHat/Fedora
{{% /collapse-toggle %}}
{{% collapse-box id="redhat" %}}
We will use [Confluent](https://www.confluent.io/)'s repository to download newest version of `librdkafka`.

```bash
# install `curl` and `which` if not already installed
sudo yum -y install curl which

# install Confluent public key
sudo rpm --import https://packages.confluent.io/rpm/4.1/archive.key

# add repository to /etc/yum.repos.d/confluent.repo
sudo cat > /etc/yum.repos.d/confluent.repo << EOF
[Confluent.dist]
name=Confluent repository (dist)
baseurl=https://packages.confluent.io/rpm/4.1/7
gpgcheck=1
gpgkey=https://packages.confluent.io/rpm/4.1/archive.key
enabled=1

[Confluent]
name=Confluent repository
baseurl=https://packages.confluent.io/rpm/4.1
gpgcheck=1
gpgkey=https://packages.confluent.io/rpm/4.1/archive.key
enabled=1
EOF

# clean YUM cache
sudo yum clean all

# install librdkafka
sudo yum -y install librdkafka1 librdkafka-dev
```

{{% /collapse-box %}}
{{< collapse-toggle box_id="osx" >}}
Installing librdkafka on OSX
{{% /collapse-toggle %}}
{{% collapse-box id="osx" %}}
todo
{{% /collapse-box %}}
{{< collapse-toggle box_id="building" >}}
Building from sources (for other distros)
{{% /collapse-toggle %}}
{{% collapse-box id="building" %}}
Manually compiling from sources:

```bash
wget -O "librdkafka.tar.gz" "https://github.com/edenhill/librdkafka/archive/v0.11.6.tar.gz"

mkdir -p librdkafka
tar --extract --file "librdkafka.tar.gz" --directory "librdkafka" --strip-components 1
cd "librdkafka"

./configure --prefix=/usr && make -j "$(getconf _NPROCESSORS_ONLN)" && make install
```

{{% /collapse-box %}}
{{< /collapse >}}

{{% load-snippet-partial file="content/docs/getting-started/kafka/main.go" first_line_contains="import (" last_line_contains="process(messages)" %}}
{{% load-snippet-partial file="content/docs/getting-started/kafka/main.go" first_line_contains="func process" %}}
{{% /tabs-tab %}}

{{% /tabs %}}

### Ack

???? todo

### Publishing messages

{{% tabs id="publishing" tabs="go-channel,kafka" labels="Go Channel,Kafka" %}}

{{% tabs-tab id="go-channel"%}}
{{% load-snippet-partial file="content/docs/getting-started/go-channel/main.go" first_line_contains="go process(messages)" last_line_contains="func process(messages" %}}
{{% /tabs-tab %}}

{{% tabs-tab id="kafka" %}}
{{% load-snippet-partial file="content/docs/getting-started/kafka/main.go" first_line_contains="go process(messages)" last_line_contains="func process(messages" %}}
{{% /tabs-tab %}}

{{% /tabs %}}


### Using *Messages Router*

### Deployment

### What next?