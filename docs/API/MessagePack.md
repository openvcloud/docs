# Message pack

The `openvcloud` API supports returning output in [message-pack](https://msgpack.org/index.html) format.
This is particulary usefull when retreiving a lot data like statistics and billing information.


All API that normally return their data in json format can be requested to return output data in msgpack format. This can be acheived by passing the `accept` headers as `application/msgpack`

## Python Example:

```python
import requests
import msgpack

headers = {"Accept": "application/msgpack", "authorization": "bearer <your jwt>"}
response = requests.post("https://be-g8-3.gig.tech/restmachine/system/usermanager/whoami", headers=headers)
print(msgpack.loads(response.content))
# {'admin': True, 'name': 'admin'}

```
