Run this project via `docker-compose up --force-recreate`

If you don't use the force-recreate flag on the second run the permissions will be corrected as the generated /etc/fix-attrs.d/01-default-drupal-files-dir will be present and will apply. This reuse of the container is what has helped this issue not get noticed for so long.

## Sample Output From First Run

Note how fix-attrs.d runs and then confd from cont-init.d

```
Creating fixattrs_web ...
Creating fixattrs_web ... done
Attaching to fixattrs_web
fixattrs_web | [s6-init] making user provided files available at /var/run/s6/etc...exited 0.
fixattrs_web | [s6-init] ensuring user provided files have correct perms...exited 0.
fixattrs_web | [fix-attrs.d] applying ownership & permissions fixes...
fixattrs_web | [fix-attrs.d] 00-logs-nobody: applying...
fixattrs_web | [fix-attrs.d] 00-logs-nobody: exited 0.
fixattrs_web | [fix-attrs.d] 01-apache-logs-dir: applying...
fixattrs_web | [fix-attrs.d] 01-apache-logs-dir: exited 0.
fixattrs_web | [fix-attrs.d] done.
fixattrs_web | [cont-init.d] executing container initialization scripts...
fixattrs_web | [cont-init.d] 10-run-confd: executing...
fixattrs_web | => Running confd to write configuration templates
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO Backend set to env
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO Starting confd
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO Backend nodes set to
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO Target config /etc/fix-attrs.d/01-default-drupal-files-dir out of sync
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO Target config /etc/fix-attrs.d/01-default-drupal-files-dir has been updated
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO Target config /etc/httpd/conf.d/99-docker-default.conf out of sync
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO Target config /etc/httpd/conf.d/99-docker-default.conf has been updated
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO /etc/httpd/conf/httpd.conf has md5sum f5e7449c0f17bc856e86011cb5d152ba should be c7467de7725e44244acf4af5f06e2712
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO Target config /etc/httpd/conf/httpd.conf out of sync
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO Target config /etc/httpd/conf/httpd.conf has been updated
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO Target config /var/log/services/README.txt out of sync
fixattrs_web | 2017-07-05T15:20:57Z 1728bc62b731 confd[219]: INFO Target config /var/log/services/README.txt has been updated
fixattrs_web | [cont-init.d] 10-run-confd: exited 0.
fixattrs_web | [cont-init.d] done.
fixattrs_web | [services.d] starting services
fixattrs_web | [services.d] done.