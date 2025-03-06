# If you are facing the Py4JJavaError 
# "Cannot run program 'python3': CreateProcess error=2, The system cannot find the file specified" indicates that Spark is unable to find Python3 on your system.

_Step1_: Check the environmental variables and set the 2 new system variable those points to the python.exe files.\
		```Variable name: PYSPARK_PYTHON```
		```Variable path: C:\Users\USER_NAME\anaconda3\python.exe``` (where the python.exe file exists)
		```Variable name: PYSPARK_DRIVER_PYTHON```
		```Variable path: C:\Users\USER_NAME\anaconda3\python.exe``` (where the python.exe file exists)

_Step 2_: Restart the kernal and try running it. If the issue persists, then go to step 3.

_Step 3_: Open/run the command prompt with the admin, as we have to link if there is any missing pieces in the process.\
		
  Enter the following commands:
  
	  ```echo %PYSPARK_PYTHON%``` --------------> This should return the path specified in the environmental variables
	  ```echo %PYSPARK_DRIVER_PYTHON%``` -------> This should return the path specified in the environmental variables
	  ```where python```	--------------------> This should return the path where the python is installed and saved
	  ```where python3```   --------------------> This should return the path where the python is installed and saved
   
  If python works and python3 fails, then the Spark application is trying to find the python3 path.\
  To overcome this issue we have to create a symbolic link using the following command on the command prompt for which we need admin access.\
  mklink C:\Windows\System32\python3.exe C:\Users\USER_NAME\anaconda3\python.exe\
  This must fix your issue.
