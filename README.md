# HackLab
An easy-to-deploy virtual Penetration Testing environment.

![external-content duckduckgo com](https://user-images.githubusercontent.com/8818608/91989187-7e377c00-ed30-11ea-8afa-78dc1194a6cf.jpeg)

<hr>

## Introduction
HackLab allows one to easily deploy a local Penetration Testing sandbox environment. The environment consists mainly of the latest Kali Linux box. The user also has the option to deploy several additional boxes to act as the targets. All VM are connected on a private network to provide the user with an enclosed sandbox environment to experiment in.

### Usage

To deploy an instance of Kali Linux,

``` vagrant up ```

To deploy targets, vagrant up [target-name]

``` vagrant up target1 ```

To reset targets,

``` vagrant reload target[n] ```

To shutdown environment,

``` vagrant suspend ```

#### Logging into Kali
The default login credentials for Kali Linux when deployed via Vagrant is:

Username: _vagrant_

Password: _vagrant_

#### [Synched Folders](https://www.vagrantup.com/docs/synced-folders)
 The directory ``` ./public/ ```, found in the root of this repository is shared across the Kali guest VM under ``` /public/ ```.

This is useful for executing ad-hoc scripts inside the sandbox.
