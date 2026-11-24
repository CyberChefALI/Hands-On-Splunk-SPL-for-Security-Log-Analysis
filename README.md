# Hands-On-Splunk-SPL-for-Security-Log-Analysis
Splunk is a powerful Security Information and Event Management (SIEM) platform used to collect, monitor, search, and analyze machine-generated data, including system logs, network traffic, and security events.

## 	Project Objective 

This project focuses on understanding essential SPL commands and performing practical log analysis to detect security events, investigate failed login attempts, identify unusual activities, and develop basic SOC monitoring skills.

## 	Lab Environment Setup

	Install Splunk Enterprise or configure a suitable Splunk environment.

## Practical - 1

## Practice core Splunk SPL queries

## TASK - 1  Starting a SPLUNK session:

Log in to your Splunk instance in a web browser & upload a sample SSH log file to invistigate for practical purpose .
<img width="1920" height="1020" alt="Add Data and 1 more page - Personal - Microsoft​ Edge 22_11_2026 06_42_41" src="https://github.com/user-attachments/assets/4d5a496f-1e9e-45ad-b845-f233b5d683d7" /> 
<img width="1920" height="1020" alt="Screenshot 22_11_2026 06_35_53" src="https://github.com/user-attachments/assets/e9571e65-12b1-4cdb-a96b-1560994e94f6" />
<img width="1920" height="1020" alt="Add Data and 1 more page - Personal - Microsoft​ Edge 22_11_2026 06_39_20" src="https://github.com/user-attachments/assets/ee1c608c-b4e9-4229-bee8-3650099a10ff" />
<img width="1920" height="1020" alt="Add Data and 1 more page - Personal - Microsoft​ Edge 22_11_2026 06_37_12" src="https://github.com/user-attachments/assets/ff7939c4-06e6-4447-9fd0-c49cc0b64893" />

## TASK - 2  stats Command - Gives summary (count, sum, average)

  Total SSH attempts
	
<img width="1920" height="1020" alt="1" src="https://github.com/user-attachments/assets/d0899be2-e733-42be-9265-ba80daa6adba" />



## TASK - 3 SEARCH COMMAND - •	Filters logs & •	Starting point of investigation 

Filter only failed SSH login events.
<img width="1920" height="1020" alt="A" src="https://github.com/user-attachments/assets/e4b6a6df-574d-460a-869b-78f31f7f98c9" />

## TASK - 4  TABLE COMMAND - 

Show only the important fields.
<img width="1920" height="1020" alt="b" src="https://github.com/user-attachments/assets/97dce25c-738d-46eb-b11f-9916c6be25c8" />

## TASK - 5  SORT COMMAND 

Sort the count from highest to lowest.
<img width="1920" height="1020" alt="Captures - File Explorer 23_11_2026 13_41_20" src="https://github.com/user-attachments/assets/356ce3a6-6215-4b10-b23e-9603453bb424" />

## TASK -6  EVAL COMMAND 

Create a readable login_status field.
<img width="1920" height="1020" alt="Captures - File Explorer 23_11_2026 13_41_20" src="https://github.com/user-attachments/assets/582f3b11-8a89-4f88-ad24-e45221154eb3" />

## TASK - 7 TIMECHART COMMAND 

Visualize event counts over time.
<img width="1920" height="1020" alt="Search _ Splunk 10 6 1 1 and 3 more pages - Personal - Microsoft​ Edge 23_11_2026 13_52_05" src="https://github.com/user-attachments/assets/8e46c069-56be-4a02-8d2c-797f56000ce1" />

## Practical - 2 

## SSH Log Analysis

## TASK - 1 ( stats count by event_type )

It is Splunk search command that groups your log events by the event_type field and counts how many times each unique type occurs.
<img width="1920" height="1020" alt="1" src="https://github.com/user-attachments/assets/1f1cae42-748f-40eb-91bd-2e3c115f1fcb" />

## TASK - 2 ( event_type="Successful SSH Login" | stats count by id.orig_h, username | sort -count )

This command  groups your successful events by source IP address and username, counts how many events occurred for each pair, and ranks the results from highest count to lowest.
<img width="1920" height="1020" alt="2" src="https://github.com/user-attachments/assets/35e12baa-c39b-4c51-bab7-2ba9748a37c3" />

## TASK - 3 (  event_type="Failed SSH Login" | stats count by id.orig_h, username | sort -count )

This command  groups your Failed events by source IP address and username, counts how many events occurred for each pair, and ranks the results from highest count to lowest.
<img width="1920" height="1020" alt="3" src="https://github.com/user-attachments/assets/e5699fb4-b922-4e04-b5fb-dac435cfa114" />

## TASK - 4 ( event_type="Multiple Failed Authentication Attempts" | stats count by id.orig_h, username | sort -count )

it filters out normal traffic so Splunk only analyzes alerts or logs flagging repeated failed logins , events by source IP address and username, counts how many events occurred for each pair, and ranks the results from highest count to lowest.
<img width="1920" height="1020" alt="4" src="https://github.com/user-attachments/assets/713ddb75-0f53-455b-bdc7-214d237f752e" />

## TASK - 5 ( 
