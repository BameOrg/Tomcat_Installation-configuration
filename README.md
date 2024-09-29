
# Tomcat Configuration Guide

This guide provides steps to configure the Tomcat server.

## 1. Start of Tomcat Configuration

### Tomcat Server Configuration:

1. **Locate Configuration Files:**
   ```bash
   find / -name server.xml context.xml
   ```

2. **Edit `server.xml`:**
   ```bash
   vim /opt/tomcat9/conf/server.xml
   ```

3. **Edit `context.xml` in Manager Webapp:**
   ```bash
   vi /opt/tomcat9/webapps/manager/META-INF/context.xml
   ```

4. **Edit `tomcat-user.xml` to Add User:**
   ```bash
   vi /opt/tomcat9/conf/tomcat-user.xml
   ```

   Add the following user configuration:
   ```xml
   <user username="landmark" password="admin" roles="manager-gui,admin-gui"/>
   ```

5. **Edit `context.xml` in Tomcat Configuration:**
   ```bash
   vi /opt/tomcat9/conf/context.xml
   ```

6. **Edit `context.xml` in Manager Webapp Again:**
   ```bash
   vi /opt/tomcat9/webapps/manager/META-INF/context.xml
   ```

7. **Edit `tomcat-user.xml` to Add Another User:**
   ```bash
   vi /opt/tomcat9/conf/tomcat-user.xml
   ```

   Add the following user configuration:
   ```xml
   <user username="YourName" password="PassWord" roles="manager-gui"/>
   ```

## Notes:
- Ensure you have the necessary permissions to edit these files.
- Restart Tomcat after making these changes to apply the new configurations.
```
