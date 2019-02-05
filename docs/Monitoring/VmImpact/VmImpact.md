# Virtual machine impact alert

These alerts will notify the users when one of the following scenarios happen:

- A virtual machine loses its disk connections

- The machine stopping due to node being put in maintenance.

- The machine restarting when moving from a node in maintenance

The alarm will be sent if the virtual machine has `alertHook` configured only. This hook can either be a callback url which will receive a post request from the system containing the relevant information, or an email address.

## Configuring the hook alert

Use the api `cloudapi/machines/configureAlertCallBack` to set the callback per virtual machine.

When set the address/url specified will recieve notifications when the described scenarios described above occur.