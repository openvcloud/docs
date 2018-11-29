# Advanced Configuration

In certain situations it is required to tweak some of our default values. This can be changed on a per grid basis.

This section will explain how to set those configuration and which ones exist.

Here below we discuss how to:

* [Setting advanced configuration values](./#set)
* [Getting advanced configuration values](./#get)

This can be applied to the following configuration settings:

* [Log Archive](https://github.com/openvcloud/docs/tree/6e9bf0cd755ed9fcfd39b1e52ec5e2fbda4125cb/docs/Sysadmin/AdvancedConfiguration/LogArchive.md)
* [Open vStorage settings](https://github.com/openvcloud/docs/tree/6e9bf0cd755ed9fcfd39b1e52ec5e2fbda4125cb/docs/Sysadmin/AdvancedConfiguration/OpenvStorage.md)
* [Reservation of Host Memory](https://github.com/openvcloud/docs/tree/6e9bf0cd755ed9fcfd39b1e52ec5e2fbda4125cb/docs/Sysadmin/AdvancedConfiguration/ReservedHostMemory.md)
* [Virtual machines retention period](https://github.com/openvcloud/docs/tree/6e9bf0cd755ed9fcfd39b1e52ec5e2fbda4125cb/docs/Sysadmin/AdvancedConfiguration/vmretention.md)

## Setting values <a id="set"></a>

Open `jsshell` on any node that is part of the grid you want to configure, and type:

```python
from CloudscalerLibcloud.utils.gridconfig import GridConfig
config = GridConfig()
config.set('<config key>', <config value>)
```

A config file can be any valid Python object structure \(simple types + list and dict\) that is serializable as JSON.

## Getting values <a id="get"></a>

Open `jsshell` on any node that is part of the grid you want to configure, and type:

```python
from CloudscalerLibcloud.utils.gridconfig import GridConfig
config = gridconfig()
configvalue = config.get('<config key>')
```

