# Queuing mechanism

`ObjectQueue` is a class responsible to handle queued actions.

The **queuer** implements:
* `queue()` - create queue for given OVC object if doesn't exist.
* `chain()` - chain action in case of success of the parent shackle.
* `chainOnError()` - chain action in case of failure of the parent shackle.
* `stop()` - graceful termination of a single queue, waits for all queued actions to be executed and then deletes the queue.
* `terminate()` - graceful termination for all OVC objects, every object waits for all queued actions to be executed and then deletes the queue.

``` py
# create first shackle
A = ObjectQueue.get_instance().queue(method=action_A, **kwargs)

# add rollback action if action_A fails
A.chainOnError(method=rollback_A, **kwargs)

# chain next shackle
B = A.chain(method=action_B, **kwargs)

# add rollback action if action_B fails
B.chainOnError(method=rollback_B, **kwargs)

# get result
result_A = A.get_result()
result_B = B.get_result()
```

![](https://docs.google.com/drawings/d/e/2PACX-1vTdxIg_zzchzgWYBu4u9lnyXnty44Z8s18xW83qoNoktNqk6shZXZYsp90fz-GwWxmnLw99VitjZLAL/pub?w=754&h=1226)