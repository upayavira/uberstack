Uberstack
=========

Uberstack is a simple tool that sits on top of Rancher Compose and Docker Compose.

It allows you to create a set of "stacks", and then use them in various 
combinations, providing each combination with its own set of configurations.

Installation
------------
Uberstack is a pretty simple Bash script. Place the `ust` script somewhere on 
your path. Then, define an UBER\_HOME environment variable that points to your
configurations for Uberstack.

Configuration
-------------
UBER\_HOME points to a directory that contains two directories:

 * **stacks**: contains a directory per stack, each stack contains a 
   docker-compose.yml, and optionally a rancher-compose.yml file
 * **uberstacks**: contains a directory per uberstack. Each 
   uberstack contains a stacks.conf file, naming one stack per line,
   and any set of \*.env files. Env files define configurations for
   specific environments, such as `local`, `dev`, `staging`, `prod`.

Usage
-----
To start up a new uberstack called `solrcloud`, on your local setup,
use the `up` action:

    ust up solrcloud local

To remove this setup, do:

    ust rm solrcloud local

Where an environment isn't specified, `local` is assumed.

When removing a stack, you will be asked to confirm the deletion, with
the exception of `local` which will proceed without confirmation.
