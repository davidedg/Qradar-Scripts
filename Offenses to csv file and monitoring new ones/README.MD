# Offenses to csv file and monitoring for new ones

IBM Qradar has been the leading SIEM in the cybersecurity market. 

The format of the scripts is Jupyter Notebook and I will do my best to make the comments appropriate so that they are easy for everyone to understand. 

Everything shown in this repository is for educational purposes, if you want to use them in productive environments you must make sure to do the respective tests before affecting any system.

This script has been made to obtain the open offenses in Qradar and then monitor the creation of new ones.  Save and/or append it to a file for later use in data analysis software.

If you want you can modify this script in some ways:

- [x] Change the filter in URL_Prefix to obtain the offenses you in the status want.
- [x] Change the output to excel, sql, mysql, etc.
- [x] Divide the script in two parts: one for only get all the offenses and one for monitoring the creation of new ones.

Must check

- [x]  Have an authorized service token with admin privileges. Variable=SEC_TOKEN
- [x]  Network connectivity with the Qradar console through port 433. Variable=URL_base

## API Reference - Functions:

#### get_old_offenses

```https
  GET /siem/offenses/{status}
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| status (optional)     | `string` | The status of the offense. One of "OPEN", "HIDDEN", or "CLOSED". |

#### change_domain_id

```https
  GET - /config/domain_management/domains/{offense_id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| domain_id      | `num` | **Required**. Number - The ID of the domain.|


#### change_offense_type_id

```https
  GET - /siem/offense_types/{offense_type}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| offense_type      | `num` | **Required**. Number - The offense type.|

#### change_rule_id
```https
  GET - /analytics/rules/{rule_id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| rule_id     | `num` | **Required**. Number - The rule ID.|


## Documentation

[IBM Documentation](https://www.ibm.com/docs/en/qsip/7.3.3?topic=api-restful-overview)
[Qradar](https://www.ibm.com/community/qradar/)
[Pandas](https://pandas.pydata.org/docs/reference/index.html)
[Logging](https://docs.python.org/3/library/logging.html)
[Jupyter Notebook](https://jupyter.org/notebook.html)

## Authors

- [@chmedinap](https://www.github.com/chmedinap)

