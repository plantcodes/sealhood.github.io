## daemon process ##
* live for a long time
* are started when system is bootstrapped
* terminate when system is shut down
* don't have a controlling terminal (run in the background)

### Error logging ###
A central daemon error-logging facility: BSD syslog. There are 
**three way to generate log messages**:

1. `log` function,read/write `/dev/klog` device, for kernel routines
2. `syslog` function, send messages to UNIX domain datagram socket `/dev/log`, for user process
3. send log messages to udp port 514, for user process local or remote

		#include <syslog.h>
		void openlog(const char *ident, int option, int facility); 	#optional
		void syslog(int priority, const char *format, ...);			#
		void closelog(void);										#optional
		int setlogmask(int maskpri);
		Returns: previous log priority mask value

### Single Instance Daemons ###
Only one copy of the daemon running on the system.
`File-/record-locking mechanism` ensure only one copye of the daemon running.
Each daemon create a file with a fixed name and place a write lock on it. Then the successive attempts to create write lock will fail.

### Daemon conventions ###
* If the daemon a lock file , store it in `/var/run`. The file name is `name.pid`.
* If the daemon supports configuration options, they are usually stored in /etc. The file is named `name.conf`.
*  They are usually started from one of the system initialization scripts. `/etc/rc*` or `/etc/init.d/*`
*  If a daemon has a configuration file, the daemon reads the file *when it starts*, but usually won’t look at it again. If an administrator **changes the configuration**, the daemon would need to be **stopped and restarted** to account for the configuration changes. 

### Client-Server model ###
Server process is a daemon process. It uses `fork` and `exec` anther program to provide service to a client. These servers manage multiple file descriptors: `communication endpoints`, `configuration files`, `log files`, and the like. Leaving this files open in the child, is somewhat dangerous. **An easy solution** to this problem is to set the `close-on-exec` flag for all file descriptors that the executed program won’t need.