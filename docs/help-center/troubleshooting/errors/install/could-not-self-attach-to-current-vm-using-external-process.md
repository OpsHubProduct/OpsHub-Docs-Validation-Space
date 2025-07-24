## Description

When OIM is installed on Linux and the OS has NFS (Network File System) based file system, the server start-up might fail.  
Following error occurs:

```
SEVERE [main] org.apache.catalina.core.StandardContext.listenerStart Exception sending context initialized event to listener instance of class [com.opshub.JSON.QuartzIntializationServlet]
 java.lang.IllegalStateException: Could not self-attach to current VM using external process
	at net.bytebuddy.agent.ByteBuddyAgent.installExternal(ByteBuddyAgent.java:459)
	at net.bytebuddy.agent.ByteBuddyAgent.install(ByteBuddyAgent.java:393)
	at net.bytebuddy.agent.ByteBuddyAgent.install(ByteBuddyAgent.java:374)
	at net.bytebuddy.agent.ByteBuddyAgent.install(ByteBuddyAgent.java:342)
	at net.bytebuddy.agent.ByteBuddyAgent.install(ByteBuddyAgent.java:328)
	at com.opshub.eai.core.adapters.common.interceptor.OIMCommonMethodInterceptor.init(OIMCommonMethodInterceptor.java:72)
	at com.opshub.JSON.QuartzIntializationServlet.contextInitialized(QuartzIntializationServlet.java:194)
```

## Cause

* ByteBuddy will try to attach agent to JVM using following socket:  
  * `/proc/<processId>/root/tmp/.java_pid<processId>`
* But in case of NFS-based file system, this socket file would not be created.  
  * Hence, ByteBuddy fails to attach the agent and server start-up will fail.

## Solution

* Add following line at the end in OIM user's `.bashrc` file (`/home/{OIM user}/.bashrc`):  
  * ```bash
    export JAVA_OPTS="$JAVA_OPTS -XX:+StartAttachListener"
    ```
* It will make Java eager load the socket file creation.  
* Hence, the socket file will be available to ByteBuddy as soon as it attaches the agent.
