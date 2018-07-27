# Repro for PyMesos 0.3.4

See <https://github.com/douban/pymesos/issues/104>

## With 0.3.4

```sh
docker-compose up -d --build && docker-compose logs -f scheduler operator
```

Log output:

```
operator_1       | DEBUG:root:{u'get_health': {u'healthy': True}, u'type': u'GET_HEALTH'}
scheduler_1      | DEBUG:root:registered
scheduler_1      | DEBUG:root:Status update TID aa0ddd62-e81f-483f-93cc-6ce46ed148cd TASK_FAILED
scheduler_1      | DEBUG:root:Status update TID f38c25ae-f045-4ea0-baa4-1060d3dcccb2 TASK_FAILED
scheduler_1      | DEBUG:root:Status update TID a4839244-2971-43d9-9e11-1455d27d3a00 TASK_FAILED
scheduler_1      | DEBUG:root:Status update TID ef222629-aab4-4b94-abc3-837745c4a8c8 TASK_FAILED
scheduler_1      | DEBUG:root:Status update TID b9682fc0-f040-4648-bbef-24f630fe32e3 TASK_FAILED
scheduler_1      | DEBUG:root:Status update TID 2533869a-a6ae-4b1d-96b0-5b836bcbd356 TASK_FAILED
scheduler_1      | DEBUG:root:Status update TID df5276a1-6160-4bc1-b0a6-feb91c1202d5 TASK_FAILED
scheduler_1      | DEBUG:root:Status update TID 4316585a-2c13-46f3-afaf-108dd8a01a1e TASK_FAILED
...
```

## With 0.3.3

Change `requirements.txt` to install `pymesos==0.3.3` instead, then do the following again:

```sh
docker-compose up -d --build && docker-compose logs -f scheduler operator
```

Log output:

```
operator_1       | DEBUG:root:{u'get_health': {u'healthy': True}, u'type': u'GET_HEALTH'}
operator_1       | INFO:pymesos.operator_v1:Operator client subscribed with cluster state: ......
scheduler_1      | DEBUG:root:registered
operator_1       | DEBUG:root:Framework added
operator_1       | DEBUG:root:{u'connected': True, u'active': True, u'framework_info': {u'name': u'MinimalFramework', u'hostname': u'8948746e68d7', u'capabilities': [{u'type': u'GPU_RESOURCES'}], u'checkpoint':False, u'failover_timeout': 100.0, u'user': u'root', u'id': {u'value': u'5567dc35-f10e-4db9-9736-2883e4d36279-0001'}}, u'unregistered_time': {u'nanoseconds': 0}, u'registered_time': {u'nanoseconds': 1532693399293652992}, u'reregistered_time': {u'nanoseconds': 1532693399293652992}, u'recovered': False}
operator_1       | DEBUG:root:Task added
operator_1       | DEBUG:root:{u'executor_id': {u'value': u'MinimalExecutor'}, u'name': u'task 8a129509-8608-4103-9e13-fd9b3fd6cb4c', u'task_id': {u'value': u'8a129509-8608-4103-9e13-fd9b3fd6cb4c'}, u'framework_id': {u'value': u'5567dc35-f10e-4db9-9736-2883e4d36279-0001'}, u'state': u'TASK_STAGING', u'resources': [{u'scalar': {u'value': 0.1}, u'type': u'SCALAR', u'name': u'cpus', u'allocation_info': {u'role': u'*'}}, {u'scalar': {u'value': 32.0}, u'type': u'SCALAR', u'name': u'mem', u'allocation_info': {u'role': u'*'}}], u'agent_id': {u'value': u'5567dc35-f10e-4db9-9736-2883e4d36279-S0'}}
scheduler_1      | DEBUG:root:Status update TID 8a129509-8608-4103-9e13-fd9b3fd6cb4c TASK_FAILED
operator_1       | DEBUG:root:Task updated
operator_1       | DEBUG:root:{u'status': {u'executor_id': {u'value': u'MinimalExecutor'}, u'uuid': u'xXt0s89CSP2jJ/YKWomA1g==', u'task_id': {u'value': u'8a129509-8608-4103-9e13-fd9b3fd6cb4c'}, u'timestamp': 1532693399.30614, u'state': u'TASK_FAILED', u'source': u'SOURCE_AGENT', u'reason': u'REASON_EXECUTOR_TERMINATED', u'agent_id': {u'value': u'5567dc35-f10e-4db9-9736-2883e4d36279-S0'}, u'message': u'Abnormal executor termination: unknown container'}, u'state': u'TASK_FAILED', u'framework_id': {u'value': u'5567dc35-f10e-4db9-9736-2883e4d36279-0001'}}
operator_1       | DEBUG:root:Task added
operator_1       | DEBUG:root:{u'executor_id': {u'value': u'MinimalExecutor'}, u'name': u'task 36732e22-04c5-4a7f-b835-16dbb010ec74', u'task_id': {u'value': u'36732e22-04c5-4a7f-b835-16dbb010ec74'}, u'framework_id': {u'value': u'5567dc35-f10e-4db9-9736-2883e4d36279-0001'}, u'state': u'TASK_STAGING', u'resources': [{u'scalar': {u'value': 0.1}, u'type': u'SCALAR', u'name': u'cpus', u'allocation_info': {u'role': u'*'}}, {u'scalar': {u'value': 32.0}, u'type': u'SCALAR', u'name': u'mem', u'allocation_info': {u'role': u'*'}}], u'agent_id': {u'value': u'5567dc35-f10e-4db9-9736-2883e4d36279-S0'}}
scheduler_1      | DEBUG:root:Status update TID 36732e22-04c5-4a7f-b835-16dbb010ec74 TASK_FAILED
operator_1       | DEBUG:root:Task updated
...
```
