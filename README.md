# Set up jupyter notebook server on ec2

Set up jupyter notebook on ec2. [Here](https://medium.com/@alexjsanchez/python-3-notebooks-on-aws-ec2-in-15-mostly-easy-steps-2ec5e662c6c6) is a great article.

One thing to notice is that now, when setting up `.jupyter/jupyter_notebook_config.py`, `c.NotebookApp.ip = '*'` should be `c.NotebookApp.ip = '0.0.0.0'`

And we can open the port 8888 later after the runing of the instance.

We can use `nohup linuxcommand &` to run the notebook process at background.

* `&` means run at background

* `nohup` means ignore the hungup signal sent by terminal when we close it.

# s3


