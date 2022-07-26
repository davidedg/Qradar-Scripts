# Close open offenses

IBM Qradar has been the leading SIEM in the cybersecurity market. 

The format of the scripts is Jupyter Notebook and I will do my best to make the comments appropriate so that they are easy for everyone to understand. 

Everything shown in this repository is for educational purposes, if you want to use them in productive environments you must make sure to do the respective tests before affecting any system.

This script has been made to obtain the open offenses and close and comment the ones that have been created for certain hours.

Must check

- [x]  Have an authorized service token with admin privileges. Variable=SEC_TOKEN
- [x]  Network connectivity with the Qradar console through port 433. Variable=URL_base

## API Reference - Functions:

#### get_offenses

```https
  GET /siem/offenses
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| status     | `string` | The status of the offense. One of "OPEN", "HIDDEN", or "CLOSED". |

#### close_offense

```https
  POST - /siem/offenses/{offense_id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| offense_id      | `num` | **Required**. Number - The ID of the offense.|
| closing_reason_id      | `num` | **Required**. Number - The ID of a closing reason. |
| status      | `string` | **Required**. Number - The status of the offense. |


#### add_comment

```https
  POST - /siem/offenses/{offense_id}/notes
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| offense_id      | `num` | **Required**. Number - The ID of the offense.|
| notes      | `string` | **Required**. Number - The note text. |


## Documentation

[IBM Documentation](https://www.ibm.com/docs/en/qsip/7.3.3?topic=api-restful-overview)
[Qradar](https://www.ibm.com/community/qradar/)
[Pandas](https://pandas.pydata.org/docs/reference/index.html)
[Logging](https://docs.python.org/3/library/logging.html)
[Jupyter Notebook](https://jupyter.org/notebook.html)


## Authors

- [@chmedinap](https://www.github.com/chmedinap)

