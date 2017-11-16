# ansible-gce-demo
This is a small demo on how to run Ansible playbooks against Google Cloud instances

# Requirements
You need to create the service account key from Google Cloud Platform. Whithin your GCE project go to: IAM & admin → Service account → Create key. Download the key as JSON and save it locally.

Modify the secrets.py file to use the path to your service account key. Here I use my path as example.

Modify the inventory/gce.ini file to use the *absolute* path to your secrets.py.

You may need to set the environment variable GCE_INI_PATH if the gce.py script doesn't found it by default.

# Test connection
If everything is connected correctly the following calls should work:

$ inventory/gce.py --list

$ ansible all -u <your ssh user> -i inventory/gce.py -m ping

# Run
$ ansible-playbook -i inventory/gce.py monitoring.yml
