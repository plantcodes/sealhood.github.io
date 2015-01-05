## Rsyslogd ##

### rsyslog.conf ###

`rsyslog.conf` contains following sections:

1. Global directives
2. Templates
3. Output channels
4. Rules (selector + action)

### selector
selector = facility.priority

* **faclity**
>One of following keywords: auth, authpriv, cron, kern lpr, mail, mark, news, (security),syslog, user, uucp, local0--local7. `security` is deprecated. 

* **priority**
>One of following keywords: debug, info ,notice, warning(warn), err(error), crit, alert, emerg(panic);   The `error, painic and warn` are **deprecated**.

### action ###
Log message content is written to "log-file",the "log-file" may be the following:

* **general file**
>log to a real file specified with full pathname. For example ` *.* /var/log/file.log `

* **terninal an console**
>`/dev/console`

* **remote machine**
>Three way to forward messages to remote machine.
>Tranditonal UDP transport(prepend host with "@"). 
>Plain TCP based transport(prepend host with "@@"). 
>RELP transport(prepend host with ":omrelp:").
>For example, `*.* @102.168.0.1`
