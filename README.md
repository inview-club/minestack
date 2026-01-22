# Minestack

Minestack is a Minecraft mod that links actions in the game world to basic OpenStack VM management. When you play, you are actually controlling real virtual machines in an OpenStack cloud through simple in‑game mechanics.

## Core Idea
* Every “managed pig” in Minecraft represents a VM in OpenStack.
* Creating a pig creates a VM.
* Killing that pig deletes the corresponding VM.

This makes it possible to demonstrate cloud infrastructure concepts using familiar Minecraft gameplay.

## Features
* Login to Keystone from chat
  * Enter credentials `minestack auth <login> <password>`
  * Authenticate against Keystone from Minecraft and store the token for later use.

* Create VM by spawning a pig
    * Use command `minestack vm`
    * The mod calls the OpenStack compute API and creates a VM for that entity.
    * The pig holds the mapping (e.g., instance ID) so the mod knows which VM it controls.

    ![vm](./resources/created_vm.png)
* Delete VM by killing the pig
    * When a managed pig dies, the mod sends a delete request for the corresponding VM.
    * The VM is terminated in OpenStack; in game you just see the pig die as usual.

    ![vm](./resources/deleted_vm.png)
## Requirements
* A reachable OpenStack cloud (Keystone + Nova endpoints) from the Minecraft server.
* Credentials with permission to create and delete instances in a project.
* The correct Minecraft version (1.16.5) and mod loader supported by Minestack.