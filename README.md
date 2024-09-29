```markdown
# Tomcat 9 Installation and Configuration on RHEL 7 & 8

This repository contains scripts and instructions for installing and configuring Apache Tomcat 9 on RHEL 7 & 8.

## Prerequisites

Before you begin, ensure you have the following:

- **Java JDK 1.8+**: Tomcat requires Java to run. Ensure Java is installed on your system.
- **Root or Sudo Privileges**: You need administrative privileges to execute the installation and configuration commands.

## Installation Steps

### 1. Set Hostname

Set the hostname of your server to `tomcat` for easier identification.

```bash
sudo hostnamectl set-hostname tomcat
```

### 2. Navigate to the `/opt` Directory

Change your current directory to `/opt`, where we will download and install Tomcat.

```bash
cd /opt
```

### 3. Install Required Packages

Install essential packages such as `git`, `wget`, and `vim`. Also, install Java JDK 1.8.

```bash
sudo yum install git wget vim -y
sudo yum install java-1.8.0-openjdk-devel -y
```

### 4. Download and Extract Tomcat Software

Download the Tomcat 9 tarball from the official Apache website and extract it.

```bash
sudo wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.69/bin/apache-tomcat-9.0.69.tar.gz
sudo tar -xvf apache-tomcat-9.0.69.tar.gz
sudo rm apache-tomcat-9.0.69.tar.gz
sudo mv apache-tomcat-9.0.69 tomcat9
```

- **`wget`**: Downloads the Tomcat tarball.
- **`tar -xvf`**: Extracts the tarball.
- **`rm`**: Removes the tarball after extraction.
- **`mv`**: Renames the extracted directory to `tomcat9`.

### 5. Set Permissions

Set the appropriate permissions for the Tomcat directory to ensure it is accessible.

```bash
sudo chmod 777 -R /opt/tomcat9
```

### 6. Start Tomcat

Start the Tomcat server using the startup script.

```bash
sudo sh /opt/tomcat9/bin/startup.sh
```

### 7. Create Soft Links to Manage Tomcat as a Service

Create symbolic links to the Tomcat startup and shutdown scripts for easier management.

```bash
sudo ln -s /opt/tomcat9/bin/startup.sh /usr/bin/starttomcat
sudo ln -s /opt/tomcat9/bin/shutdown.sh /usr/bin/stoptomcat
sudo starttomcat
```

- **`ln -s`**: Creates symbolic links.
- **`starttomcat`**: Starts the Tomcat server using the symbolic link.

### 8. Switch to `ec2-user`

Switch to the `ec2-user` account if you are using an EC2 instance.

```bash
sudo su - ec2-user
```

## Configuration Files

### server.xml

The main configuration file for the Tomcat server. It contains settings for server ports, connectors, and other server-wide configurations.

### context.xml

Configuration file for web applications. It can be used to define context-specific settings such as database connections and resource links.

### tomcat-users.xml

File to manage Tomcat users and roles. It is used to define user credentials and their associated roles for accessing the Tomcat Manager and Host Manager applications.

## Notes

- Ensure you have the necessary permissions to edit these configuration files.
- Restart Tomcat after making any changes to apply the new configurations.

## Conclusion

You have successfully installed and configured Tomcat 9 on your RHEL 7 & 8 system. You can now start and stop Tomcat using the `starttomcat` and `stoptomcat` commands from anywhere.

## Acknowledgments

- Apache Tomcat documentation
- Community contributions
