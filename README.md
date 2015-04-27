# What is ECMSDK ?

Enterprise Content Management SDK (ECMSDK) is an open source, modern, mature, robust and flexible runtime and development platform for building demanding content management applications. The features and capabilities of EMCSDK are designed to help developers bring enterprise-scalable content management-based applications to market faster and better than with any other platform. ECMSDK provides a set of Java APIs that developers can use to customize or extend the product’s core functionality in numerous ways to build comprehensive content-management and collaboration systems.

> Detailed info on [ecmsdk.com](http://www.ecmsdk.com)

This ECMSDK image includes the ECMSDK software running on Tomcat 8 with openJDK7. The ECMSDK schema is stored in an Oracle Database Express Edition (XE) 11.2 database instance. The underlying OS is Ubuntu Linux 14.

# How to use this image ?

## Pull this Docker image from the Docker repository

```    
docker pull inxire/ecmsdk
```

## Run this Docker image

This image can expose the following ports:

 - 22 for SSH
 - 1521 for the database listener
 -  8088 as the HTTP port for the database admin UI
 - 8080 as the HTTP port for Tomcat 8

```
docker run -d -p 50022:22 -p 51521:1521 -p 58088:8088 -p 58080:8080 --name ecmsdk inxire/ecmsdk
```

To check if all services get started within the image, you can execute:

```
docker logs -f ecmsdk
```

Wait until you see `Tomcat started.` in the log output.

## Connect to your image

### Connect to the database

    hostname: <docker.host.ip>
    port: 51521
    sid: xe
    username: system
    password: oracle

**Password for SYS & SYSTEM:**
```oracle```

**ECMSDK schema owner and password:** ```ECMSDK/ECMSDK```

### Login by SSH

    ssh root@<docker.host.ip> -p 50022
    password: admin

**Username of Oracle XE installation:** ```oracle```

### Access URLs

> [Oracle Database XE Admin UI](http://<docker.host.ip>:58088/apex/f?p=4950)

> [WebDAV against ECMSDK](http://<docker.host.ip>:58080/ecmsdk/content/)

## Start developing
You can now start developing your applications by using the ECMSDK APIs published at [ecmsdk.com](http://www.ecmsdk.com/downloads) against this ready-to-go ECMSDK Docker image.