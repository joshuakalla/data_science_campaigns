# Launching Jupyter Hub Infrastructure

In order to set up the course infrastructure, I followed the procedures described [here](https://the-littlest-jupyterhub.readthedocs.io/en/latest/install/google.html). 

I created an instance with 12 vCPUs, 26 GB memory, and 100 GB standard persistent disk.

Under start-up script, I entered:

```
#!/bin/bash
curl https://raw.githubusercontent.com/jupyterhub/the-littlest-jupyterhub/master/bootstrap/bootstrap.py \
  | sudo python3 - \
    --admin jkalla - \
    --user-requirements-txt-url https://raw.githubusercontent.com/joshuakalla/data_science_campaigns/master/requirements.txt
```

After setting up Jupyter Notebook and logging in as an admin, I navigated to the Terminal and entered:
```
sudo -E pip install nbgitpuller
sudo -E	jupyter serverextension enable  --sys-prefix --py nbgitpuller
sudo -E pip install nbzip==0.1.0
sudo -E jupyter serverextension enable  --sys-prefix --py nbzip
sudo -E jupyter nbextension     install --sys-prefix --py nbzip
sudo -E jupyter nbextension     enable  --sys-prefix --py nbzip
sudo -E apt-get install pandoc
sudo -E apt-get install texlive-xetex
```

To link students directly to labs, I am using nbgitpuller. To use this, I go [here](https://jupyterhub.github.io/nbgitpuller/link). There, I enter in the IP address for JupyterHub. Under URL path, I enter something like `notebooks/data_science_campaigns/Labs/Lab1/lab01.ipynb`. Under Repository URL I enter something like `https://github.com/joshuakalla/data_science_campaigns`. This produces a link that I can then distribute to students.



I am redirecting the Google VM to http://datascience4politics.org. To set-up the redirect, I followed the directions at https://www.bloggerlessons.com/set-up-a-domain-on-google-cloud-server/. 

Thanks!