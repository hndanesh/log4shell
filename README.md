# Nuclei template for log4shell (CVE-2021-44228)

## Usage
Generate a new DNS bin at https://requestbin.net/dns


### If you have nuclei installed run

Single url
```
nuclei -duc -ni -vv -t CVE-2021-44228.yaml -u <url_to_test> -var DNS_CALLBACK='<your_dns_bin_id>.requestbin.net'
```

List of urls from file
```
nuclei -duc -ni -vv -t CVE-2021-44228.yaml -l <urls_file> -var DNS_CALLBACK='<your_dns_bin_id>.requestbin.net'
```

### If you want to use my docker image
```
docker build -t log4shell .
docker run log4shell -duc -ni -vv -t /CVE-2021-44228.yaml -u <url_to_test> -var DNS_CALLBACK='<your_dns_bin_id>.requestbin.net'
```

### If a host is vulnerable, it would pop up in https://requestbin.net/dns?master=<dns_bin_id>, the template includes the host name

## Testing
Build and start this docker container

https://github.com/christophetd/log4shell-vulnerable-app

```
docker run log4shell -duc -ni -vv -t /CVE-2021-44228.yaml -u http://localhost:8080 -var DNS_CALLBACK='<your_dns_bin_id>.requestbin.net'
```

## Improvements
* Build an extractor to confirm the results