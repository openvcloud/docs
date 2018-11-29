# Create Custom Dashboards

If you are completely new to Grafana, start here: [http://docs.grafana.org/guides/gettingstarted/](http://docs.grafana.org/guides/gettingstarted/)

Following measurements are available:

* disk.iops.read
* disk.iops.write
* disk.throughput.read
* disk.throughput.write
* machine.CPU.utilisation
* network.packages.rx
* network.packages.tx
* network.throughput.incoming
* network.throughput.outgoing
* network.vfw.packets.rx
* network.vfw.packets.tx
* network.vfw.throughput.incoming
* network.vfw.throughput.outgoing

For each of them three variants exist:

* h: values collected per hour
* m: values collected per 5 minutes
* t: total aggregated value 

In what follows all steps are documented in order to create a simple dashboard visualizing the average read and write IOPS of all virtual machines.

The very first step is selecting **+ New** from the **Dashboard** menu:

![](../../.gitbook/assets/newdashboard.png)

You'll get an empty dashboard, with one row.

From the hamburger menu on the left of the row select **Add Panel &gt; Graph**:

![](../../.gitbook/assets/addpanel.png)

On **Metrics** tab of the Graph panel select **Influxdb\_controller** as the value for **Panel data source**:

![](../../.gitbook/assets/paneldatasource.png)

Still in the **Metrics** tab select **disk.iops.read** as the measurement of the first query:

![](../../.gitbook/assets/queryafrommeasurement.png)

Next specify that you only want the values of the virtual disks:

![](../../.gitbook/assets/queryafromtype.png)

Add a second query by clicking **+ Add query**:

![](../../.gitbook/assets/addquery.png)

For the second query select **disk.iops.write** as the measurement, and again for the virtual disks:

![](../../.gitbook/assets/queryb.png)

Change the aliases of both queries:

![](../../.gitbook/assets/changealiases.png)

In the **General** tab change the **Title** to **Average IOPS of Virtual Disks**:

![](../../.gitbook/assets/changepaneltitle.png)

Hit **Save** and see the result:

![](../../.gitbook/assets/result%20%283%29.png)

