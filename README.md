# Zabbix template for mariadb maxscale
Monitor maxscale server with Zabbix server with zabbix http agent
___

This template monitors maxscale using zabbix http agent. Tested on zabbix server/proxy version **6.0.X** and maxscale version > **2.5.X**. The OS used was debian 11.

## Macros

* **{$MAXSCALE.HTTP.ADDRESS}**: Mandatory. Maxscale`s rest-api listening ip. It can be a virtual ip if ucarp is used.
* **{$MAXSCALE.HTTP.USER}**: Optional. Defaults to **admin**.
* **{$MAXSCALE.HTTP.PASSWORD}**: Optional. Defaults to **mariadb**.
* **{$MAXSCALE.HTTP.PORT}**: Optional.Defaults to **8989**.
* **{$MAXSCALE.HTTP.SCHEMA}**: Optional. Defaults to **http://**.

___

## Features

* Automatic discovery of maxscale backends.
* Automatic discovery of maxscale monitors.
* Automatic discovery of maxscale services.
* Automatic discovery of maxscale listeners.
* Automatic discovery of maxscale sessions.
* Trigger for maxscale version change and low uptime.
___

## Prerequisites

* Zabbix server/proxy must be initially configured with cURL (libcurl) support for [http agent](https://www.zabbix.com/documentation/6.0/en/manual/config/items/itemtypes/http) to work.
* Maxscale`s [rest-api](https://kb-prod.mariadb.com/kb/en/mariadb-maxscale-6-mariadb-maxscale-configuration-guide/#rest-api-configuration) must be enabled

## How to use

1) Enable and configure maxscale`s http rest-api.
2) Configure the firewall to allow zabbix server or proxy access the maxscale api if firewall is used
3) Import the template on your zabbix server.
4) Create a dummy host with zabbix agent interface as localhost for example. If you assign a proxy , the proxy will be issuing the http requests.
5) Assign the maxscale-vip template to the dummy host.