# EPS by domain in Qradar

IBM Qradar has been the leading SIEM in the cybersecurity market.

The format of the scripts is Jupyter Notebook and I will do my best to make the comments appropriate so that they are easy for everyone to understand.

Everything shown in this repository is for educational purposes, if you want to use them in productive environments you must make sure to do the respective tests before affecting any system.

There are situations where an MSSP contains a different number of clients. In this type of environment there may be several Event Collectors for the clients, but there may also be one that is shared among several others and the logical separation is done by Domains.

For this type of cases, I have created this small script which, with previously defined queries, can extract the EPS by domain.

The steps to create the queries are:

DomainID : It must be clear what the domain id is for each client. This can be obtained using GET - /config/domain_management/domains

processorId: It must be clear to which EP the search will point. This can be obtained using GET - /config/deployment/hosts

The queries must be created in the following way:

"SELECT logsourcename(logSourceId) AS 'Log Source', SUM("eventCount") AS 'Number of Events in Interval', SUM
(eventcount) / 300 AS "EPS in Interval",DOMAINNAME(domainid) AS 'Domain name' from events where ( "domainId"='PUT 
YOUR DOMAIN ID IN HERE' 
AND 
"processorId"='PUT
YOUR EP ID IN HERE' ) GROUP BY logSourceId order by "EPS in Interval" desc LIMIT 1000 last 5 minutes"

This query will be used to obtain the EPS by domain and is a modification of the query that IBM shares in the 
following link: https://www.ibm.com/support/pages/qradar-determining-events-second-rate-each-log-source-qradar

After this, you can export the dataframe to a csv file or save it in a database and create a dashboard to visualize 
the data as you wish. In this example, I will create a simple chart to visualize the data


Must check

- [x]  Have an authorized service token with admin privileges. Variable=SEC_TOKEN
- [x]  Network connectivity with the Qradar console through port 433. Variable=URL_base

## API Reference - Functions:

#### get_searches

```https
  GET - /ariel/searches/{search_id}
```

| Parameter | Type     | Description          |
| :-------- | :------- |:---------------------|
| search_id    | `string` | The ID of the search |

#### get_search_results

```https
  GET - /ariel/searches/{search_id}/results
```
| Parameter | Type     | Description          |
| :-------- | :------- |:---------------------|
| search_id    | `string` | The ID of the search |

```https
  POST - /ariel/searches
```
| Parameter | Type     | Description |
| :-------- | :------- |:------------|
| query_expression    | `string` | query       |

#### get_search_status

```https
  GET - /ariel/searches/{search_id}/status
```
| Parameter | Type     | Description          |
| :-------- | :------- |:---------------------|
| search_id    | `string` | The ID of the search |


## Documentation

- [x] [IBM Documentation](https://www.ibm.com/docs/en/qsip/7.3.3?topic=api-restful-overview)
- [x] [Qradar](https://www.ibm.com/community/qradar/)
- [x] [Pandas](https://pandas.pydata.org/docs/reference/index.html)
- [x] [Logging](https://docs.python.org/3/library/logging.html)
- [x] [Jupyter Notebook](https://jupyter.org/notebook.html)

(Qradar is an IBM product and rights are owned by them.)


## Authors

- [@chmedinap](https://www.github.com/chmedinap)

