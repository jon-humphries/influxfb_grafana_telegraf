# influxfb_grafana_telegraf

Run the docker compose file with docker-compose up -d

This will create three containers, influxdb, grafana and telegraf

Telegraf is configured to send pings to three public URLS, then store those responses in InfluxDB. You can then query this data either in InfluxDB or by polling Grafana.

All networking is created locally, to access InfluxDB run http://127.0.0.1:8086 (admin/CiscoDisco123) for Grafana http://127.0.0.1:3000 (admin/admin - then set a new password)

All variables for the docker compose file, telegraf config and any automated provisioning for Grafana are set within the .env file and alled with the syntax ${variable}

The connection between Grafana and influxdb is automated.

There are two folders for Grafana provisioning and their are default.taml files for both provisioning automation and for dashboard config. If you wish to add a default dashboard add it to the grafana/dashboards folder.
 

If you wish to use Telegraf as a collector agent for InfluxDB then following the below, otherwise you can skip this and populate InfluxDB using your own methods.

To create the telegraf config in influxdb this is a manual step and is done via the influxdb container:-

root@
influx telegrafs create \
  -n "Meraki Telegraf config" \
  -d "Meraki Monitor Telegraf configuration." \
  -f /etc/telegraf/telegraf.conf
  

 
