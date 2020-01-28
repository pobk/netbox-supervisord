# Alternative supervisord installation for systems without systemd

For non-Linux distributions where systemd is not available supervisord can be utilised. Either install your OS packages or install using pip:

```no-highlight
# pip install supervisor
```

Once installed you will need to copy the `supervisord.conf` either into to your `supervisor.conf` configuration or add it to a `supervisor.d` directory.   

```no-highlight
# cp contrib/supervisord.conf /usr/local/etc/supervisor.d/
```

Now we'll need to tell supervisor to re-read it's configuration files and update any configurations.

```no-highlight
# supervisorctl reread
# supervisorctl update
```

It may be necessary to update the configuration for your specific setup.

You can use the command `supervisorctl status` to verify that the WSGI service is running:

```
# supervisorctl status
netbox                           RUNNING   pid 906, uptime 2:12:28
netbox-rq                        RUNNING   pid 907, uptime 2:12:28
```

If the services are not running, you can use `supervisorctl start netbox` and `supervisorctl start netbox-rq` to start netbox.

!!! info
    As with the systemd configuration the configurations provided here are bare minimums. You may want to make adjustments to better suit your production environment.
