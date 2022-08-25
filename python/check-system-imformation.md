# Check system information

## Check CPU usage

```python
psutil.cpu_percent()
```

- [What is psutil.cpu_percent in Python](https://www.educative.io/answers/what-is-psutilcpupercent-in-python)

## Check disk usage

```python
disk = shutil.disk_usage("/")
disk_free_space_percent = disk.free / disk.total
```

## Check memory usage

```python
psutil.virtual_memory().available >> 20) #MB
```

- [psutil virtual memory units of measurement?](https://stackoverflow.com/questions/21792655/psutil-virtual-memory-units-of-measurement)
- [BitwiseOperators](https://wiki.python.org/moin/BitwiseOperators)

## Check host available

```python
socket.gethostbyname('localhost')
```

- [python: check if a hostname is resolved](https://stackoverflow.com/questions/11618118/python-check-if-a-hostname-is-resolved)
