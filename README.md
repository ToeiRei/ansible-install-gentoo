# My Gentoo Journey: A Barebones Installation using Ansible

This repository is my ongoing adventure in crafting a pristine Gentoo Linux system from scratch using Ansible

## What You'll Find Here:  

- gentoo.yml:   A detailed Ansible playbook outlining the steps I take to build this barebones Gentoo installation. This includes kernel configuration, bootloader setup, essential package management, and more.
- settings.yml: A file to customize this playbook so you do not have to deal with ansible.
- Notes & Reflections:  As I delve deeper into the intricacies of Gentoo, you'll find notes on my experiences, troubleshooting tips, and maybe even some rants about obscure dependencies (it happens to the best of us).
- Sarcasm & Copium: Let's be real, diving deep into Ansible was less of a controlled learning experience and more of a "I don't know what I'm doing but I'll figure it out (eventually)" freefall. Expect copious amounts of both sarcasm and copium as I navigate the labyrinthine world of YAML, modules, and templating.

## Who This Is For:  

- Fellow Gentoo Enthusiasts:  If you're fascinated by the power and customization Gentoo offers, peek under the hood and see how I approach a clean installation.
- Linux Beginners:  Don't be intimidated! While this project assumes some familiarity with Linux basics, the detailed playbook can serve as a learning resource for those venturing into Gentoo's world.

**Current Status:**  This repository is actively being developed as I continue my journey. Expect updates as new configurations and tweaks are implemented.  

## Key Features (So Far):  
- Minimalist Approach:  Focused on building a solid foundation with essential packages and a custom kernel.
- Ansible Automation:  Utilizing Ansible for reproducible and efficient system configuration.
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


## settings.yml (Configuration)

This file lets you customize the installation process to your specific needs. Modify the variables below according to your setup:

```yaml
# This is the config for the playbook

# Disk Configuration 
main_disk: "/dev/sda"  # The device where Gentoo will be installed.

# Gentoo Configuration
gentoo_mirror: "http://mirror.init7.net/gentoo/releases/amd64/autobuilds/current-stage3-amd64-systemd" # Gentoo Stage 3 mirror URL
gentoo_profile: "default/linux/amd64/23.0/systemd"  # The Gentoo profile to use

# Your Custom Settings
pem_file_path: "ucs-root-ca.pem"   # Path to your root CA certificate file (e.g., for SSL verification) 
authorized_keys_url: "https://go.stargazer.at/authorized_keys" # URL pointing to a file containing your public SSH keys
nfs_portage_host: "nfs-server.local"  # If using NFS for Portage, specify the host name or IP address. (Example)
nfs_portage_path: "/path/to/Portage"  # The path to Portage on the NFS server
```

## Frequently Asked Questions (FAQs)

**Why on earth would you automate a Gentoo install?**
> Look, sometimes even we tech wizards get tired of the same old grind. A vanilla Gentoo base install can be _so_ tedious! This playbook is all about efficiency and letting you skip those boring steps while still having control over the core setup.

**Why Ansible? Why not something else?** 
> Ansible's like the organized friend who always has a plan (and knows how to execute it). It's structured, easy to read, and lets me manage the installation in a clean, repeatable way. Plus,  it doesn't require an agent on the target machine – just SSH access! That means no extra software to install or configure. Sharing this playbook means others can benefit from the same sanity!

**Are you weird?**
> Meow.  (Just kidding - sort of.)

 **How long does it take?**
> On a VM with 4 cores and 8 GB of RAM (AMD EPYC 7282, KVM hypervisor), the entire process took roughly 2 hours. Keep in mind that runtime can vary depending on your hardware and network conditions.   

**What exactly gets installed?**
> This playbook sets up a bare-bones Gentoo base system with essential tools like `htop`, `hyfetch`, `systemd`, and `network-manager`. It doesn't include any user accounts, giving you a completely clean slate to work with.

 **WARNING:** The installation process will erase EVERYTHING on the target disk!  Make absolutely sure there is nothing important you want to keep on that drive before running the playbook. 

**How do I update the playbook?**
> Simply use `git pull` in the directory where you cloned the repository. This will download any changes made to the playbook. Review the updated `settings.yml` file to see what's new!


 **What should I do after the playbook finishes?**
> Once the playbook has run successfully, you have a fresh Gentoo base system ready for customization! Set your hostname, emerge additional software packages using `emerge`, or explore other specialized playbooks (we might add some later!)

 **Do I need any special tools besides Ansible?**
> Yes, Git is required to clone and manage the playbook repository. You also may want to have a text editor like vi, vim, nano, pico,... 

## Need Help?

You're bound to run into the occasional hiccup – we all do!  Here's how you can get back on track:

* **Ansible Docs:** Your best friend when things go sideways:  [https://docs.ansible.com/](https://docs.ansible.com/). They have a treasure trove of troubleshooting tips and guides for Ansible beginners and pros alike.


* **Open an Issue (this repo):** Found something that's not working as expected or spotted a typo? Let me know by opening an issue in this repository!  
* **Pull Requests:** Wanna see some cool new features or have an idea to make things even better?  Send a pull request – I love collaborating and making this playbook the best it can be.

## Changes
- **2025-02-16**:  Initial import, lots of swearing and instant regret
- **2025-02-17**:  Implemented validation for settings, smart NFS server handling, made rootcert optional, implemented hostname, wrote new To Dos

##  To Do 

I'm constantly working to improve this playbook. Here are some things I plan to be tackling soon:

* **Encryption:** Implement LUKS FDE for covering portable devices
* **GPG Token support:** Get support for GPG HW Token like Nitrokey to be used for ssh key storage

Get Involved:   

Feel free to fork this repository, experiment with different configurations, and share your feedback! Let's build a better Gentoo community together. 
