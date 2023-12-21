# HackLab
An easy-to-deploy virtual Penetration Testing environment.

![external-content duckduckgo com](https://user-images.githubusercontent.com/8818608/91989187-7e377c00-ed30-11ea-8afa-78dc1194a6cf.jpeg)

<hr>

## Introduction
HackLab allows one to easily deploy a local Penetration Testing sandbox environment. The environment consists mainly of the latest Kali Linux box. The user also has the option to deploy several additional boxes to act as the targets. All VM are connected on a private network to provide the user with an enclosed sandbox environment to experiment in.

## Usage

To deploy an instance of Kali Linux,

``` vagrant up ```


### Logging into Kali
The default login credentials for Kali Linux when deployed via Vagrant is:

Username: _vagrant_

Password: _vagrant_

### [Synched Folders](https://www.vagrantup.com/docs/synced-folders)
 The directory ``` ./public/ ```, found in the root of this repository is shared across the Kali guest VM under ``` /public/ ```.

This is useful for executing ad-hoc scripts inside the sandbox.


## Targets

### OWASP's vulnerable-container-hub
If you need some target practice, OWASP's [vulnerable-container-hub](https://github.com/OWASP/vulnerable-container-hub) offers a factitious environment that is riddled with vulnerabilities. It is good for learning and applying the OWASP framework, and is easily deployable via a multitude of containerization and scripted methods.

To get started, execute the following command in your local filesystem:

``` git clone git@github.com:OWASP/vulnerable-container-hub.git ```

#### Juice Shop

[OWASP Juice Shop](https://owasp-juice.shop/) is probably the most modern and sophisticated insecure web application! It can be used in security trainings, awareness demos, CTFs and as a guinea pig for security tools! Juice Shop encompasses vulnerabilities from the entire [OWASP Top Ten](https://owasp.org/www-project-top-ten) along with many other security flaws found in real-world applications!

The reccomended way to use the Juice Shop with the HackLab is via it's [vagrant](https://github.com/juice-shop/juice-shop/tree/9a0789b5ecb4ee76fe528b1860095e945f6302ac#vagrant) script.

1. Init and update submodules (a submodule is a link to the original repository). 

```bash
$ git submodule init
$ git submodule update
```

2.  Provision vagrant box

``` cd vagrant && vagrant up ```

3. Open Juice Shop endpoint

In your browser, open http://192.168.56.110/

4. Your first mission (should you choose to accept it) is to find the ellusive [scoreboard](https://pwning.owasp-juice.shop/companion-guide/latest/part2/score-board.html). [Happy hunting](https://pwning.owasp-juice.shop/companion-guide/latest/part1/happy-path.html)!