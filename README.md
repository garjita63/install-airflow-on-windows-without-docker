## Install Apache Airflow on Windows without Docker

Airflow is a platform created by the community to programmatically author, schedule and monitor workflows.

It can be installed within docker ot without docker.

### Requirements:
- Windows Subsystem for Linux (WSL2)
- Windows 10 or higher
- Python 3.8 or higher

### Method 1
#### Steps: (See document file : Install Apache Airflow on Windows without Docker.docx) 
https://github.com/garjita63/install-airflow-on-windows-without-docker/blob/main/Install%20Apache%20Airflow%20on%20Windows%20without%20Docker.docx

1. Install WSL2 (Windows Subsystem for Linux 2) on Windows 10
2. Set Up the Virtual Environment
3. Set Up the Airflow Directory
4. Install Apache Airflow
5. Create an Airflow User
6. Run the Airflow Scheduler & Webserver

### Method 2
#### Steps:
- Open Windows Powershell
- Type bash
- Check pyhton version
  pyhton3
  
  For example: Python 3.10.6 (main, Nov 14 2022, 16:10:14) [GCC 11.3.0] on linux
- Check Airflow latest version in website https://airflow.apache.org/docs/apache-airflow/stable/start.html

  For example : Airflow ver.2.5.1
- Set Airflow home directory 
  For example : export AIRFLOW_HOME=d:\airflow\local
- Install Airflow using the constraints file

  AIRFLOW_VERSION=2.5.1
  
  PYTHON_VERSION="$(python --version | cut -d " " -f 2 | cut -d "." -f 1-2)"
  
  CONSTRAINT_URL="https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt"
  
  ##### For example: https://raw.githubusercontent.com/apache/airflow/constraints-2.5.1/constraints-3.10.txt
  pip install "apache-airflow==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"

- airflow db init

- airflow users create \
    --username admin \
    --firstname Peter \
    --lastname Parker \
    --role Admin \
    --email abc@xyz.com

- airflow webserver --port 8080

- airflow scheduler

Visit localhost:8080 in the browser and use the admin account details shown on the terminal to login.
