<code class="expression">space.vars.SITENAME</code> is by default deployed with 4 GB memory, but if that needs to be changed then refer to the section below.

# Memory Configuration File

From version 7.4 onwards, there is a configuration file **OIM_Config.properties** added in <code class="expression">space.vars.SITENAME</code>.

You can find this configuration file under the `<code class="expression">space.vars.SITENAME</code> Installation Path>/AppData/OpsHubData` directory.

**OIM_Config.properties** file contains the server memory parameters that can be configured.

# How to Increase Server Memory

1. From `services.msc`, stop the `Opshub Server Service`.
2. Open the command prompt with administrator privileges, and:  
   1. Navigate to `<code class="expression">space.vars.SITENAME</code> Installation Path>/OpsHubServer/bin` directory.  
   2. Run `unregisterservice.bat`. This will remove the `Opshub Server Service`.  
3. From Windows Explorer, go to `<code class="expression">space.vars.SITENAME</code> Installation Path>/AppData/OpsHubData` directory and open `OIM_Config.properties` file using any text editor.  
   In this file, there will be default memory settings for the server as `Xms=1024m` and `Xmx=4096m`.  
   Minimum recommended memory parameter configuration is `Xms=1024m` and `Xmx=4096m` but depending on <code class="expression">space.vars.SITENAME</code> instance load/configuration, these parameters may need to be increased.
   - Format for memory parameter is like, `Xms=<Memory parameter>m`
   - Update `OIM_Config.properties` file based on the required parameters and click **Save**.
4. Now switch back to the previously opened command prompt in step #2.  
   If it is closed, you can reopen it with administrator privileges and navigate to `<code class="expression">space.vars.SITENAME</code> Installation Path>/OpsHubServer/bin` directory.
   1. Run `registerservice.bat`. This will register the `Opshub Server Service` with configured parameters in `OIM_Config.properties` file.
5. From `services.msc`, start the `Opshub Server Service`.
