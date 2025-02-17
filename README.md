# My Gentoo Journey: A Barebones Installation Guide 

This repository documents my ongoing adventure in crafting a pristine Gentoo Linux system from scratch.  

## What You'll Find Here:  

- gentoo.yml:   A detailed Ansible playbook outlining the steps I take to build this barebones Gentoo installation. This includes kernel configuration, bootloader setup, essential package management, and more.
- settings.yml: A file to customize this playbook so you do not have to deal with ansible.
- Notes & Reflections:  As I delve deeper into the intricacies of Gentoo, you'll find notes on my experiences, troubleshooting tips, and maybe even some rants about obscure dependencies (it happens to the best of us).

## Who This Is For:  

- Fellow Gentoo Enthusiasts:  If you're fascinated by the power and customization Gentoo offers, peek under the hood and see how I approach a clean installation.
- Linux Beginners:  Don't be intimidated! While this project assumes some familiarity with Linux basics, the detailed playbook can serve as a learning resource for those venturing into Gentoo's world.

**Current Status:**  This repository is actively being developed as I continue my journey. Expect updates as new configurations and tweaks are implemented.  

## Key Features (So Far):  
- Minimalist Approach:  Focused on building a solid foundation with essential packages and a custom kernel.
- Ansible Automation:  Utilizing Ansible for reproducible and efficient system configuration.
- Kernel Customization:   Keywording, genkernel, and meticulous flag settings for optimal performance.
- Neofetch Integration:  Because who doesn't love a good ASCII art representation of their system?
- Ready for logging in: NetworkManager, OpenSSH and your authorized_keys file are installed - awaiting your login.
- BTRFS: Using the power of subvolumes, partitioning is easy as pie.
- Legacy BIOS support: Old hardware? New hardware - I got your back!

## Requirements

To run this playbook successfully, you'll need:


* **Ansible:** Version 2.10 or higher is recommended ([https://docs.ansible.com/](https://docs.ansible.com/)).
* **SSH Access:** You'll need SSH access to your target Gentoo system.  
    - For initial installation, consider using a live Linux distribution like [SystemRescue](https://www.system-rescue.org/) which allows you to boot into a temporary environment and set up SSH access. 
    - Ensure your public SSH key is added to the `~/.ssh/authorized_keys` file on the target machine for passwordless authentication.

## Using The Playbook

This playbook is designed to automate a barebones Gentoo installation. Here's how you can use it:


1. **Get the Code:**
   ```bash
   git clone https://github.com/ToeiRei/ansible-gentoo-install.git
   ```

2. **Jump Into the Action:**  Navigate to your newly cloned repository directory: 
   ```bash
   cd ansible-gentoo-install
   ```


3. **Tweak Your Setup:** Make any changes you need to the variables in `settings.yml`. This lets you customize things like your username, hostname, and SSH key path.

4.  **Create Your Inventory File (inventory.ini):** 
   This file tells Ansible which machines to work with. For a single machine installation:

    ```
    [gentoo]
    your_machine_ip ansible_host=192.168.1.10  # Replace with your target machine's IP address

    ```

5. **Make It Happen:** Run the playbook using Ansible! Remember to replace 'YOUR_MACHINE_IP' with your actual IP address:
   ```bash
   ansible-playbook -i inventory.ini gentoo.yml
   ```



**Need Help?**:

*  If you run into issues, check out the Ansible documentation ([https://docs.ansible.com/](https://docs.ansible.com/)):  They've got tons of resources for troubleshooting and getting started.

## Changes
- **2025-02-16**:  Initial import, lots of swearing and wishing I would have never started


Get Involved:   

Feel free to fork this repository, experiment with different configurations, and share your feedback! Let's build a better Gentoo community together. 
