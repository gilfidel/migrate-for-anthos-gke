# Assessing your workloads for containerization 

## Assessing your MySQL VM for containerization
Migrate for Anthos and GKE comes with an assessement tool that assesses whether or not a VM is a good candidate for migration. This tool is called [Migration Fit Assessement Tool (mFIT)](https://cloud.google.com/migrate/anthos/docs/fit-assessment) and it is used to collect details about your running VM (collected output is stored on local file system) and then analyze the collected data and assess if the VM is a good candidate for migration.

In order to assess your VM for containerization using the mFIT, you need to ssh into your MySQL VM instance and run the following command:
``` bash
curl -s https://raw.githubusercontent.com/GoogleCloudPlatform/migrate-for-anthos-gke/main/scripts/assess_ldt.sh | bash
```

**Note:** The collection script must run as root user using sudo to allow successful collection of the running VM.

The collection script will leave a file on the running VM, in the directory /var/m4a which will be used be Migrate for Anthos and GKE during the migration phase and will allow automated discovery of services, network ports, etc...  
For the MySQL VM the discovery tool will discover the running MySQL instance and the port that it is using.

## Assessing your Tomcat VM for containerization
In the same manner that you have assessed the MySQL VM you should assess your Tomcat VM.
To assess your VM for containerization using the mFIT, you need to ssh into your Tomcat VM instance and run the following command:
``` bash
curl -s https://raw.githubusercontent.com/GoogleCloudPlatform/migrate-for-anthos-gke/main/scripts/assess_ldt.sh | bash
```

You can view the mFIT analysis report using the Cloud Console UI by following the instructions in the [official documentation](https://cloud.google.com/migrate/anthos/docs/fit-assessment#ldt-console). Note that the JSON file should reside in ~/m4a directory.  

You are now ready to start [migrating](../3-migrate/README.md) your VMs to containers

