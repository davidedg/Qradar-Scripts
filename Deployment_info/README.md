# Get the deployment information of the QRadar environment

IBM Qradar has been the leading SIEM in the cybersecurity market. 

The format of the scripts is Jupyter Notebook and I will do my best to make the comments appropriate so that they are easy for everyone to understand. 

Everything shown in this repository is for educational purposes, if you want to use them in productive environments you must make sure to do the respective tests before affecting any system.

This script has been made to obtain the info of the deployment of the QRadar environment.

Must check

- [x]  Have an authorized service token with admin privileges. Variable=SEC_TOKEN
- [x]  Network connectivity with the Qradar console through port 433. Variable=URL_base

## Output:

df.columns
```
Index(['eps_rate_hardware_limit', 'components', 'public_ip', 'average_eps',
       'private_ip', 'hostname', 'total_memory', 'eps_allocation', 'id',
       'cpus', 'app_memory', 'peak_eps', 'version', 'encryption_enabled',
       'compression_enabled', 'status', 'appliance.id', 'appliance.type',
       'rol'],
      dtype='object')

```

## API Reference:

Retrieves the list of all deployed hosts:

```https
  GET /config/deployment/hosts
```
| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| fields (optional)     | `string` | Use this parameter to specify which fields you would like to get back in the response. |

## Documentation

- [x] [IBM Documentation](https://www.ibm.com/docs/en/qsip/7.3.3?topic=api-restful-overview)
- [x] [Qradar](https://www.ibm.com/community/qradar/)
- [x] [Pandas](https://pandas.pydata.org/docs/reference/index.html)
- [x] [Logging](https://docs.python.org/3/library/logging.html)
- [x] [Jupyter Notebook](https://jupyter.org/notebook.html)

(Qradar is an IBM product and rights are owned by them.)


## Authors

- [@chmedinap](https://www.github.com/chmedinap)

