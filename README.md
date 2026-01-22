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
    
    https://github.com/ch4t5ky/2023_2024-openstack-teamwork/assets/28315102/7d855930-a67d-4d61-a8b0-cac974b8615e.mp4
* Create VM by spawning a pig
    * Use command `minestack vm`
    * The mod calls the OpenStack compute API and creates a VM for that entity.
    * The pig holds the mapping (e.g., instance ID) so the mod knows which VM it controls.
      
     https://github.com/ch4t5ky/2023_2024-openstack-teamwork/assets/28315102/a57a9a45-96ee-4495-a492-ca44840e4ffb.mp4
  
    ![vm](./resources/created_vm.png)
* Delete VM by killing the pig
    * When a managed pig dies, the mod sends a delete request for the corresponding VM.
    * The VM is terminated in OpenStack; in game you just see the pig die as usual.
      
    https://github.com/ch4t5ky/2023_2024-openstack-teamwork/assets/28315102/8d08284c-47b0-41b9-96c3-017ffcbf7093.mp4

    ![vm](./resources/deleted_vm.png)
## Requirements
* A reachable OpenStack cloud (Keystone + Nova endpoints) from the Minecraft server.
* Credentials with permission to create and delete instances in a project.
* The correct Minecraft version (1.16.5) and mod loader supported by Minestack.
