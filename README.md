# Set up jupyter notebook server on ec2

Set up jupyter notebook on ec2. [Here](https://medium.com/@alexjsanchez/python-3-notebooks-on-aws-ec2-in-15-mostly-easy-steps-2ec5e662c6c6) is a great article.

One thing to notice is that now, when setting up `.jupyter/jupyter_notebook_config.py`, `c.NotebookApp.ip = '*'` should be `c.NotebookApp.ip = '0.0.0.0'`

The other thing is that, when create ssl certificate, use this command `openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout "cert.key" -out "cert.pem" -batch`, so you do not need to enter specific questions.
And doing this without `sudo` will get rid of the `PermissionError`.

> If we use sudo to generate the certificate, only root user can use this certificate. While our anacaconda is for user `ubuntu`

If we generate `cert.key` and `cert.pem` separately, we need edit the `.jupyter\jupyter_notebook_config.py` like this:
```
c = get_config()  # Get the config object.
c.NotebookApp.certfile = u'/home/ubuntu/ssl/cert.pem' # path to the certificate we generated
c.NotebookApp.keyfile = u'/home/ubuntu/ssl/cert.key' # path to the certificate key we generated
c.NotebookApp.ip = '0.0.0.0'  # Serve notebooks locally.
c.NotebookApp.open_browser = False  # Do not open a browser window by default when using notebooks.
c.NotebookApp.password = 'sha1:fc216:3a35a98ed980b9...'   # your own password hash just generated
```

And we can open the port 8888 later after the runing of the instance.

We can use `nohup linuxcommand &` to run the notebook process at background.

* `&` means run at background

* `nohup` means ignore the hungup signal sent by terminal when we close it.

# s3


