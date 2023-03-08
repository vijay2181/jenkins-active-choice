# jenkins-active-choice


- Created  a folder structure for jobs in jenkins, where core is the main job which triggers the downstream jobs on selection

![image](https://user-images.githubusercontent.com/86955368/223640009-ef7015e5-9181-427d-8db1-317412d14f00.png)

for example user builds the core job and selects  'Refresh' option along with 'Environment', then Refresh downstream job will be triggered

![image](https://user-images.githubusercontent.com/86955368/223640288-ad7077af-b80a-4559-9d6d-a81b8bc6c844.png)

![image](https://user-images.githubusercontent.com/86955368/223640377-10197928-a89c-4c8f-9651-c9c754863a5d.png)

- it will prompt for user input to select the services, services will be populated by service_list.py file

![image](https://user-images.githubusercontent.com/86955368/223641243-858bcdfd-7d25-4d8e-9e14-88d919062df6.png)


- when user selects 'input requested', then all the running servcies will be prompted where user can select multiple services of his choice 

![image](https://user-images.githubusercontent.com/66196388/223668981-0193a31d-4e2c-4a20-aecc-ed374196021e.png)

- Then selected services will be redirected to a file where we can manuplate to a yaml file

![image](https://user-images.githubusercontent.com/66196388/223669304-d6e6d654-b33b-4598-beb6-dcb499fa6aed.png)


