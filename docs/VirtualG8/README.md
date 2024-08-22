Setup virtual G8

Create a g8 account

Specify url of the G8 where teh virtual g8 will be installed
```
python3 -m g8.installer.virtualg8 -v 9.9.9 -u https://be-loc-dc01-003.gig.tech/restmachine -t <Pernal JWT with g8 admin scope> -a <account_id> -n vg8 setup
```
If `JWT` is provided in the environment, can skip `-t` flag.

This command should install everything. 

### Troubleshooting

If vms were created, but rke installation was stuck or failed, you can retry the following steps manually.

Run installing k8s
```
python3 -m g8.installer.virtualg8 -v 9.9.9 -u https://be-loc-dc01-003.gig.tech/restmachine -a  <account_id> -n vg8 deploy-k8
```

To install os on nodes start PXE boot service on the bootstrap VM which imitates the raspberry PI:
```
python3 -m g8.installer.virtualg8 -v 9.9.9 -u https://be-loc-dc01-003.gig.tech/restmachine -s K0iOi71NMi -a 8 -n vg8 bootstrap 
```

Deploy cluster

```
installer --config /etc/cfg/system-config.yaml --url 'https://git.gig.tech/openvcloud/devmanifests/-/raw/master/manifests/9.9.9.yml' cluster deploy
```

Snapshot env
```
jwt=<Personal JWT with g8 admin scope>

python3 -m g8.installer.virtualg8 -v 9.9.9 -u https://be-loc-dc01-004.gig.tech/restmachine -t $jwt -a 11 -n vg8 snapshot --snapshot <name>
```

