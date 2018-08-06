# connecting-to-nrel-hpc

*Learn how to connect to NREL's high-performance computing (HPC) systems.*

A supported set of instructions for logging into NREL HPC systems is provided on the [HPC NREL Website](https://www.nrel.gov/hpc/system-connection.html).

## NREL Employee on NREL Device

If you are an NREL employee using an NREL device and you are on the NREL network, then you can use SSH to get a shell on NREL HPC systems in the NREL HPC Data Center.

### Windows

If you are on a Windows system, you will need to install an SSH client.  We recommend [PuTTY](https://www.nrel.gov/hpc/putty-ssh-gateway.html), [Cygwin](https://cygwin.com/install.html), or [Git Bash](https://git-scm.com/downloads).

### Mac or Linux

For Mac and Linux systems, you can ssh to the HPC system in your terminal window with the following command:

```bash
$ ssh username@peregrine.hpc.nrel.gov
```

## Not an NREL Employee or Not on NREL Device

If you are not an NREL employee or not on an NREL device, you need to use one of the following methods, which use multi-factor authentication.

First, you will need to set up your account for multi-factor authentication. See [One-Time Password Token Set Up](https://www.nrel.gov/hpc/one-time-password-tokens.html).

### Command Line Access

If you just need access to a command line on an HPC system, use the [Peregrine SSH server](https://www.nrel.gov/hpc/peregrine-ssh.html).

#### Windows

If you are on a Windows system, you will need to install an SSH client. See [recommended clients](#windows).

#### Mac or Linux

For Mac and Linux systems, you can ssh in your terminal window using the following commands:

```bash
$ ssh username@peregrine-ssh.nrel.gov
```

### Non-Command Line Access

For non-command line access (for example, visualization and web apps), you should use the [HPC VPN](https://www.nrel.gov/hpc/vpn-system-connection.html).
