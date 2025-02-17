# Cloud-Monitoring

## Objective

Cloud Monitoring provides dashboards and alerts so you can review performance metrics for cloud services, virtual machines, and common open source servers such as MongoDB, Apache, Nginx, Elasticsearch, and more. You configure Cloud Monitoring in the Console.

### Skills Learned

- Create a Cloud Monitoring account that has two Google Cloud projects.
- Monitor across both projects from the single Cloud Monitoring account.

### Tools Used
- Google Cloud Monitoring
- Google Cloud Logging
- Custom Dashboards
- Alerting Policies
- Instances
- VM


## Steps

At the top of the screen, click on the dropdown arrow next to Project 1's name.
Dropdown arrow
Make sure that you're on the All tab, then click on the name of Project 2 to go into it. All tab
Select Navigation menu > Compute Engine > VM instances to open the VM instances window.
Click Create Instance to create a new instance.
In the Machine configuration:
Enter the values for the following fields:
Field	Value (type or select)
Name	instance2
Region	REGION
Zone	ZONE
Leave all of the options at the default settings.
Click Create.
![Screenshot 2025-02-17 113858](https://github.com/user-attachments/assets/7edba3ac-74e7-4d22-9a2f-2343e5f27496)
![Screenshot 2025-02-17 114004](https://github.com/user-attachments/assets/7005e503-35d7-468a-9116-d35deac23c72)
![Screenshot 2025-02-17 114423](https://github.com/user-attachments/assets/c6b2fb64-7e2b-4cde-8e76-a0b37ff97317)
![Screenshot 2025-02-17 114516](https://github.com/user-attachments/assets/c370eb2a-af23-4e94-8e3c-f1c4a694d38f)
![Screenshot 2025-02-17 114753](https://github.com/user-attachments/assets/90c85cdc-24c1-4bc5-8977-524ec83ecf58)
![Screenshot 2025-02-17 115711](https://github.com/user-attachments/assets/07234630-31ed-4beb-91cb-0712de11fde0)

Step 2Create a Cloud Monitoring group
In the left menu, click Groups, then click +Create group.
Name your group DemoGroup.
The Criteria is a set of rules that will dynamically evaluate which resources should be part of this group.
Cloud Monitoring dynamically determines which resources belong to your group based on the filter criteria that you set up.
In the first dropdown field (Type), Name is selected by default.
In the second dropdown (Operator), Contains is selected by default.
In the third field (Value), type in "instance" since both of the instance names in both of your projects start with the word instance.
Click Done, then click Create.
![Screenshot 2025-02-17 120013](https://github.com/user-attachments/assets/1d3f06ef-0c6f-45b8-9c3d-28a036f60bcd)

![Screenshot 2025-02-17 120643](https://github.com/user-attachments/assets/f7ddf548-2ae9-401c-b6bd-eaa02126cffd)

![Screenshot 2025-02-17 121141](https://github.com/user-attachments/assets/28a97cfd-561c-42c2-a83e-ead7974d5f42)

![Screenshot 2025-02-17 121225](https://github.com/user-attachments/assets/75da5d8e-1c60-4d64-8ae0-29fa378062b4)

Step 3. Uptime check for your group
Uptime checks let you quickly verify the health of any web page, instance, or group of resources. Each configured check is regularly contacted from a variety of locations around the world. Uptime checks can be used as conditions in alerting policy definitions.
In the left menu, click Uptime checks, then click +Create uptime check.
Create your uptime check with the following information:
Protocol: TCP
Resource Type: Instance
Applies To: Group, and then select DemoGroup.
Port: 22
Check frequency: 1 minute, then click Continue.
Click Continue again.
Leave the slider ON state for Create an alert option in Alert & notification section, then click Continue.
For Title: enter DemoGroup uptime check.
Click TEST to verify that your uptime check can connect to the resource.
When you see a green check mark everything can connect, click Create.
![Screenshot 2025-02-17 121427](https://github.com/user-attachments/assets/aa7bdfd5-647b-441d-851c-e0b28f59d17e)
![Screenshot 2025-02-17 121538](https://github.com/user-attachments/assets/53807e7e-c371-4aa7-a691-82364a54883c)
![Screenshot 2025-02-17 121556](https://github.com/user-attachments/assets/987e9473-e739-40c2-94b7-97da859ba74e)

Step 4: Create an Alerting Policy for the Group
In Cloud Monitoring, go to Uptime checks.
Click the More menu icon (three dots) next to your Display Name and select Add alert policy.
Add a new condition:
Click +Add alert condition.
Search for check_passed in the Select a metric field.
Choose VM Instance > Uptime_check > Check passed and click Apply.
Add a filter: Set Filter to check_id and select demogroup-uptime-check-id as the value.
Configure the trigger:
Click the arrow next to VM Instance-Check passed and select Configure trigger.
Set Condition type to Metric absence.
Name the policy Uptime Check Policy, skip notifications, and click Create policy

![Screenshot 2025-02-17 122058](https://github.com/user-attachments/assets/387b7e3f-873f-4e84-9f00-73249c646f02)
![Screenshot 2025-02-17 122141](https://github.com/user-attachments/assets/7604468d-a969-4491-8585-262d9e41c766)
![Screenshot 2025-02-17 122247](https://github.com/user-attachments/assets/b3d57be4-6fbe-4007-939a-a9c8785c003a)
![Screenshot 2025-02-17 122511](https://github.com/user-attachments/assets/2f94d696-a964-45ed-ba10-7f34d5f7c85e)
![Screenshot 2025-02-17 122704](https://github.com/user-attachments/assets/f2b60a09-2657-4b9d-99b8-ed80013dbc26)
![Screenshot 2025-02-17 122838](https://github.com/user-attachments/assets/fb38049b-c564-41d7-9601-51002201dfe6)

Step 20:  
Remove one instance to cause a problem
In the console, select Navigation menu > Compute Engine.
Check the box next to instance2, then click on the 3 vertical dots More icon at the top of the page and click Stop. Click Stop again to turn off the machine.
Wait a minute or 2 for the instance to stop and violate the uptime check you just set up. After a couple of minutes, turn your machine back on by clicking Start/Resume, then Start.
Click Navigation menu > Monitoring > Alerting and refresh your browser. It may take a few more minutes to show that you have issues in the Summary section. Refresh until you see an Incident similar to this:
![Screenshot 2025-02-17 123041](https://github.com/user-attachments/assets/a00aa287-e696-4145-b763-86594a6f3ac8)

![Screenshot 2025-02-17 123453](https://github.com/user-attachments/assets/6b95f4f0-f0b4-40b8-832d-e2084c4032a5)

![Screenshot 2025-02-17 123516](https://github.com/user-attachments/assets/2379ab27-27c1-4bd7-a863-83a4a7ea5871)
