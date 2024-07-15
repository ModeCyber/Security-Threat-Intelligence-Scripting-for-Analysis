# Security-Threat-Intelligence-Scripting-for-Analysis
This repository contains a script for gathering log information, processing the data, and protecting the results with access controls.

## Solution
The following steps outline how to write a script (logtest.sh) to gather log information, process the data, and protect the results with access controls.

# Task 1: Create the Script
Step 1: Create the Script File
This exercise involves writing a script to gather log information, process the data, and protect the results with access controls. We create a script called logtest.sh. The first line is the shebang for /bin/sh:

## #!/bin/sh
We create a file using the date as part of the file name. We type:

DATE=$(date “+%Y-%m-%d”)
This command executes the date command and extracts the current year, month, and day. Here, we create a variable called LOGFILE:

LOGFILE="${DATE}_stuff.log"
And then create the file:

touch $LOGFILE
If the file does not exist, it will be created; if it already exists, it will be updated.

# Task 2: Extract Log Information
Step 1: Extract Syslog Information
The next step is to extract the LOGFILE information and store the results in the file. We extract partial LOGFILE using the tail command:

tail -n 10 /var/log/syslog >> $LOGFILE
Here, we extract the last 10 lines from syslog. The >> symbol is used to redirect the output and append it to LOGFILE. If we want to overwrite, we use a single > symbol. In this case, to preserve the file, we use >>.

# Task 3: Append Additional Log Information
Step 1: Extract Auth Log Information
To append additional log information from a different source file, we type:

tail -n 10 /var/log/auth.log >> $LOGFILE
If we want to put the whole log file, we use the cat command. To extract specific information, we use awk. Here, we extract only the last 10 lines of each log file.

# Task 4: Protect the File with Access Controls
Step 1: Set File Permissions
We protect the file using access controls. In this case, we use chmod:

chmod 600 $LOGFILE
This command gives read and write access to the current user, but no access to the group or others.

## Step 2: Make the Script Executable
Exit out of the text editor to make this file executable:

emacs logtest.sh
Step 3: Set Execute Permission
Next, type:

chmod +x logtest.sh
Step 4: Run the Script
Now, type:

./logtest.sh
Step 5: Verify the Created File
To view the created file, type:

ls
You should see the file YYYY-MM-DD_stuff.log.

# Step 6: View the Content of the Log File
To view the content of the file, type:

cat YYYY-MM-DD_stuff.log
You will see the results extracted using the tail commands appended to the file. This concludes the exercise on scripting for analysis.

