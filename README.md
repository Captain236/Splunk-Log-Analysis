# Analyzing DNS Log Files using splunk SIEM
## Introduction
DNS (Domain Name System) logs are crucial for understanding network activity and identifying potential security threats. Splunk SIEM (Security Information and Event Management) provides powerful capabilities for analyzing DNS logs and detecting anomalies or malicious activities.

## Skills Learned 
- Advanced understanding of SIEM concepts and practical application
- Understand the splunk query language and impliment in the project
- Understand the concept of Log Analysis
- Development of critical thinking and problem-solving skills in cybersecurity

## Prerequisites
- Splunk instance is installed and configures
- DNS log data sources are configured to forward logs to Splunk.

## Steps
## prepare a sample DNS Log file
- Obtain sample DNS log file in a suitable format (e.g., text files).
- Nevigate to splunk settings>Add Data
- select upload as data input method
## Upload file
- upload a dns log file.
- Choose the appropriate source type for DNS logs (e.g., dns or a custom source type if applicable).
- Once all settings are configured, click on the Review button.
- Review the settings one final time to ensure accuracy.
- Click Submit to upload the sample DNS log file to Splunk.
-  ![Search _ Splunk 9 2 1 - Google Chrome 7_10_2024 8_11_03 PM](https://github.com/user-attachments/assets/43cfaebd-c8ff-4f4a-85ef-d567659232c0)

## 1 Verify upload 
- After uploading, navigate to the search bar in the Splunk interface.
- Run a search query ## index=<your_dns_index> sourcetype=<your_dns_sourcetype> ##  to verify that the uploaded DNS events are visible.
- ![Search _ Splunk 9 2 1 - Google Chrome 7_10_2024 8_12_38 PM](https://github.com/user-attachments/assets/862607b0-a57c-4821-af9f-8c714e70d5a7)

 ## 2 Search for DNS Events
 - open the splunk interface and nevigate to the search bar
 - Enter ## index=* sourcetype=dns_log ## to retrieve DNS events
 - ![Search _ Splunk 9 2 1 - Google Chrome 7_10_2024 8_14_14 PM](https://github.com/user-attachments/assets/0a85e3c8-f7eb-491e-8ca7-4e1d04afe5de)

## 3 Extracting relevent fields
- Identify key fields in DNS logs such as source IP, destination IP, domain name, query type, response code, etc.
- To do this there is a option on left side down "Extract new fields" click on it.
- select any one log field which you want ...
- ![Search _ Splunk 9 2 1 - Google Chrome 7_10_2024 8_17_11 PM](https://github.com/user-attachments/assets/e69f9b09-3607-4753-8cd3-730e558a70fa)
- click on next
- select "regular expression" on select method..
- ![Search _ Splunk 9 2 1 - Google Chrome 7_10_2024 8_19_44 PM](https://github.com/user-attachments/assets/f491039a-6aa7-4881-a0c7-134029cbbe97)
- now identify the Identify key fields in DNS logs such as source IP, destination IP, domain name, query type, response code, etc.
- ![Search _ Splunk 9 2 1 - Google Chrome 7_10_2024 8_22_35 PM](https://github.com/user-attachments/assets/0cadf769-c935-45fd-90a5-209ad1168137)
- now click on view in search

## 4 Identify Anomalies
- Look for unusual patterns or anomalies in DNS activity.
- Example query to identify spikes ## index=_* OR index=* sourcetype=dns_sample  | stats count by fqdn ##
- ![Search _ Splunk 9 2 1 - Google Chrome 7_10_2024 8_25_17 PM](https://github.com/user-attachments/assets/95d7175c-a6a8-4ceb-9987-3a0c97383105)
  
## 5  Find the top DNS sources
- Use the top command to count the occurrences of each query type:
- ![Search _ Splunk 9 2 1 - Google Chrome 7_10_2024 8_25_17 PM](https://github.com/user-attachments/assets/6bdb1618-3cf6-4e6a-9fe1-f0a3c74fa451)

## 6 Generate data in table formate
- Use table command to generate data in table formate
- exmaple :- index=* sourcetype=dns_log | table src-ip src_port dst_ip dst_port
- ![Search _ Splunk 9 2 1 - Google Chrome 7_10_2024 8_28_49 PM](https://github.com/user-attachments/assets/eab1d8e2-3722-4395-99d3-feaa66d8401f)

## 7 Rename
- rename command is use to rename the perticular field name
- example :- index=* sourcetype=dns_log | rename domain as fullydomain | table fullydomain
- ![Search _ Splunk 9 2 1 - Google Chrome 7_10_2024 8_30_44 PM](https://github.com/user-attachments/assets/2bca3f1e-46e4-4636-b7e3-bebf0c9c7fde)

## 8 Investigate Suspicious Domains
- Search for domains associated with known malicious activity or suspicious behavior.
- Utilize threat intelligence feeds or reputation databases to identify malicious domains such virustotal.com
- Example search for known malicious domains:
- ![Search _ Splunk 9 2 1 - Google Chrome 7_10_2024 8_39_01 PM](https://github.com/user-attachments/assets/3be00c62-e117-48be-864c-b9eff57ad008)

## Conclusion
Analyzing DNS log files using Splunk SIEM enables security professionals to detect and respond to potential security incidents effectively. By understanding DNS activity and identifying anomalies, organizations can enhance their overall security posture and protect against various cyber threats.













