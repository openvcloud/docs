# Configuration File Details

The configuration file is needed by the [installer script](Installer-script.md) to setup the OpenvCloud system.

The system-config is divided in several sections:
- [Support](#support)
- [Network](#network)
- [Itsyou.online](#itsyouonline)
- [Sending E-Mails](#mailclient)
- [SSH Private Key](#ssh-key)
- [Environment](#environment)
- [Certificates](#certificates)
- [Nodes](#nodes)
- [Others](#others)

<a id="support"></a>
## Support

This section is used by the Teleport application to configure the access to the application.

To access the Teleport application you need to have a github oauth application which is defined in the `github` section as follows:

```yaml
support:
  github:
    client_id: 3216584165816f5v
    client_secret: 3wa651wvefqeffefefsf6514651eswrfgw
    teams:
    - team_name: support_beg84
      org_name: be-g8-4
```

To create a GitHub OAuth application follow the [Creating an OAuth App](https://developer.github.com/apps/building-oauth-apps/creating-an-oauth-app/) documentation.

After creating the application you can get both the `client_id` and the `client_secret` from the application page.

Under the `teams` section it is possible to restrict the access to users belonging to a specific GitHub organization as well as specify a specific team that belongs to this organization.

<a id="network"></a>
## Network
Configuration of switch should be done like following in system-config.yaml and it will be configured automatically during installaion
Note: uplinks will be configured on Cisco or Mellanox based on the production is true or false in the config
```yaml
network:
  backplane:
    network: 10.107.1.0/24
  # cisco config start 
  cisco: 
  # configure-uplinks explains if we should configure uplinks on this switch or not
  - configure-uplinks: true
    hostname: be-g8-3
    name: 50 port switch
    password: cisco
    # define which ports connected to which device
    ports:
      # total number of ports in the switch
      count: 50
      # ports that are connected to the 3 controllers
      controllers:
        # ports that use it though ipmi to reboot, start and ...etc the nodes
        ipmi: 46-48
        # ports that hold internal traffic through management interfaces
        management: 35,37,13
      # ports that are connected to cpunodes
      cpunodes:
        ipmi: 2-5,26-29
        management: 7-10,31-34
      mellanox: 38,14
      # ports that are connected to storage nodes
      stornodes:
        ipmi: 40,20,19,41
        management: 16-18,39
    # provider-port is the port that connects the switch to the internet
    provider-port: 50
    # switch serial number
    serial_number: DNI202500MU
    # switch-ip defines which ip we should configure the switch with inside the network
    switch-ip:
      address: 10.107.2.201
      netmask: 255.255.255.0
    # trunk-port defines trunk connections to the controllers and other switches
    trunk-ports:
      controllers: 11,12,45
      mellanox: 48,49
    username: cisco
  gateway-management:
    network: 10.199.0.0/22
    vlan: 2314
  ipmi:
    network: 10.107.4.0/24
    vlan: 2311
  management:
    gateway: 10.107.2.254
    network: 10.107.2.0/24
    vlan: 2311
  # mellanox config
  mellanox:
  # ports that connects cpu and storage node
  - nodes:
    - ports: 1-4,7-10
      split: false
    - count: 4
      enable: 3-4
      ports: '5'
      split: true
    # the count config here explains the number of ports to split each to port
    - count: 4
      # which ports are enabled after split
      enable: 1-2
      # which ports are we applying this config to
      ports: '6'
      split: true
  - ports:
      # total number of ports in the switch
      count: 12
  # mlag ip of this switch
    mlag-ip: 122.21.21.13
    name: mellanox-1
    password: admin
  # define on which controller the serial cable is connected (typical ctrl-02 and ctrl-03)
    serial: ctrl-02
  # provider config will be used if configure-uplinks on this switch is set
    provider:
      mlag-channel: 17
      port: 46
      vlan: 2300
  # connection between this switch and other switches
    sw-uplinks:
      cisco-mlx: 11
      mlx-mlx: 12
    switch-ip:
      address: 10.107.2.202
      netmask: 255.255.255.0
    username: admin
  # the second mellanox switch
  - nodes:
    - ports: 1-4,7-10
      split: false
    - count: 4
      enable: 3-4
      ports: '5'
      split: true
    - count: 4
      enable: 1-2
      ports: '6'
      split: true
  - ports:
      # total number of ports in the switch
      count: 12
    mlag-ip: 122.21.21.14
    name: mellanox-2
    serial: ctrl-03
    password: admin
    provider:
      mlag-channel: 17
      port: 48
      vlan: 2300
    sw-uplinks:
      cisco-mlx: 11
      mlx-mlx: 12
    switch-ip:
      address: 10.107.2.203
      netmask: 255.255.255.0
    username: admin
  # public network vlan
  public:
    gateway: 10.101.0.1
    vlan: 101
    # public connection type either VRRP or IBPGP
    connection-type: VRRP
  storage:
    network: 10.107.3.0/24
    vlan: 2315
  vxbackend:
    network: 10.240.0.0/16
    vlan: 2313
```


<a id="itsyouonline"></a>
## Itsyou.online

The Itsyou.online section configures the `clientId` / `clientSecret` used for the `oauth` to authenticate with the G8

```yaml
itsyouonline:
  clientSecret: fwegfwefwefw-ALGwzRpSLLf # itsyouonline secret
  clientId: greenitglobe.environments.be-g8-4 # itsyouonline client id
  environment: be-g8-4 #
```

<a id="mailclient"></a>
## Sending E-Mails

To enable to send out emails about certain events user invitation etc. we need to configure smtp settings.

```yaml
mailclient:
  login: support@dummy.com # SMTP login
  passwd: 5jfgf5tjrdsd # SMTP password
  port: 578 # SMTP port
  sender: support@env.com # SMTP server sender
  server: smtp.domain.com # SMTP server address
```

<a id="ssh-key"></a>
## SSH Private Key

When downloading the controller image it will have this private key preconfigured in it's `authorized_keys`.
During the installation of the G8 this key will be replaced with an autogenerated key instead.

```yaml
ssh:
  private-key: |
    -----BEGIN RSA PRIVATE KEY-----
    MIIEpAIBAAKCAQEAvwuJCeHCTrBGvc86KbZdDLywc2HuQmlkYPrh2bk/UU3tkjSG
    ...
    TZafw3e0jbvBW912NPoCmapEJFfQl7Em66V5MpKlE59NTiyl0TszMg==
    -----END RSA PRIVATE KEY----- # key to be used for authorization on the nodes
```

<a id="environment"></a>
## Environment

This sections contains information about the domain where the G8 will be used and references to the [certificates](#certificates) used

```yaml
environment:
  grid:
    id: 109 # unique number between 1 and 65535
  subdomain: be-g8-4 # environement location
  basedomain: gig.tech
  ssl: # certificate references depending on the case can all be the same although all four sections needs to be defined
      root: cert01
      novnc: cert01
      ovs: cert01
      defense: cert01
  password: 'tester'
  type: small
```

<a id="certificates"></a>
## Certificates

In this section we configure the crt and the key of the certificates referenced by the [environment](#environment) section

```yaml
certificates:
  cert01:
    crt: |
      -----BEGIN CERTIFICATE-----
      MIIFaDCCA1CgAwIBAgIJALMPFMTTCLbPMA0GCSqGSIb3DQEBCwUAMEkxCzAJBgNV
      ...
      zAVFDemdh4fNuZBJ5I7lWAqgViyBOi1PWuBvGzo9bGwz7AHu/fIHf3sZfis=
      -----END CERTIFICATE-----
    key: |
      -----BEGIN PRIVATE KEY-----
      MIIJQgIBADANBgkqhkiG9w0BAQEFAASCCSwwggkoAgEAAoICAQDAhPSK90Qeiz8f
      ...
      MJQvhc7hqkGm6SrTbCi7aooAgQsQJw==
      -----END PRIVATE KEY-----
```

<a id="Nodes"></a>
## Nodes

This section contains all the nodes that make up the G8. Typically there are 3 kind of nodes `cpu` `storage` and `controller`
On the `controller` nodes the kubernetes cluster is deployed which runs the OpenvCloud APIs and management software. The `cpu` nodes are used to run the virtual machines. And the `storage` nodes are used to run the OpenvStorage storage software (also partially on cpu nodes).

A node is defined by it's name (hostname) contains certain roles (cpu, storage, controller).
Each node should have `ipmi` and `management` section container the `macaddress` of the node used for `dhcp` to install and manage the nodes.

```yaml
nodes: # Environment nodes info
  - name: ctrl-01
    roles:
      - controller
    ip-lsb: 1 # this defines the offset in the subnets defined in the network section
    fallback:
      ipaddress: 10.101.109.1/16 # defines the public IP used by the controller
      gateway: 10.101.0.1
    ipmi:
      macaddress: 0C:C4:7A:AC:11:36
      username: ADMIN
      password: ADMIN
    management:
      macaddress: 0A:C4:7A:AC:11:36
  - name: cpu-01
    roles:
      - cpu
    ip-lsb: 11
    ipmi:
      macaddress: 0C:C4:7A:AC:11:36
      username: ADMIN
      password: ADMIN
    management:
      macaddress: 0B:C4:7A:AC:11:36
  - name: storage-01
    roles:
      - storage
    ip-lsb: 41
    ipmi:
      macaddress: 2C:60:0C:BC:26:65
      username: admin
      password: admin
    management:
      macaddress: 0C:C4:7A:AC:11:36
```

<a id="others"></a>
## Other various settings

```yaml
timezone: CET
```


        


## Validation 

@TODO
