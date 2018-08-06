# Running-graphical-applications

Perergrine uses VirtualGL and FastX for remote desktop and visualization capabilities for graphical applications.

VirtualGL is an open-source package that gives any Linux remote display software the ability to run OpenGL applications with full 3D hardware acceleration. The traditional method of displaying graphics applications to a remote X server (indirect rendering) supports 3D hardware acceleration, but this approach causes all of the OpenGL commands and 3D data to be sent over the network to be rendered on the client machine. With VirtualGL, the OpenGL commands and 3D data are redirected to a 3D graphics accelerator on the application server, and only the rendered 3D images are sent to the client machine. VirtualGL "virtualizes" 3D graphics hardware, allowing users to access and share large-memory visualization nodes with high-end graphics processing units (GPUs) from their energy-efficient desktops. For more information, refer to the current documentation or the background article.

FastX provides a means for sharing a graphical desktop. By connecting to a FastX session on a DAV node, users can run graphical applications on a data analysis and visualization (DAV) node with a similar experience to running on their workstation.  Another benefit is that you can disconnect from a FastX connection, go to another location and reconnect to that same session, picking up where you left off.


# Connecting to DAV Nodes Using FastX
To launch a FastX session please follow the instructions [here](https://www.nrel.gov/hpc/software-fastx.html).


# launching OpenGL Applications
You can now run applications in the remote desktop. You can run X applications normally; however, to run hardware-accelerated OpenGL applications, you must run the application prefaced by the vglrun command, For example, to run the vaporgui application, use:


```bash
$ vglrun vaporgui
```
