# My Gentoo Journey: A Barebones Installation Guide 

This repository documents my ongoing adventure in crafting a pristine Gentoo Linux system from scratch.  

## What You'll Find Here:  

- gentoo.yml:   A detailed Ansible playbook outlining the steps I take to build this barebones Gentoo installation. This includes kernel configuration, bootloader setup, essential package management, and more.
- settings.yml: A file to customize this playbook so you do not have to deal with ansible.
- Notes & Reflections:  As I delve deeper into the intricacies of Gentoo, you'll find notes on my experiences, troubleshooting tips, and maybe even some rants about obscure dependencies (it happens to the best of us).

## Who This Is For:  

- Fellow Gentoo Enthusiasts:  If you're fascinated by the power and customization Gentoo offers, peek under the hood and see how I approach a clean installation.
- Linux Beginners:  Don't be intimidated! While this project assumes some familiarity with Linux basics, the detailed playbook can serve as a learning resource for those venturing into Gentoo's world.

### Current Status:  This repository is actively being developed as I continue my journey. Expect updates as new configurations and tweaks are implemented.  

## Key Features (So Far):  
- Minimalist Approach:  Focused on building a solid foundation with essential packages and a custom kernel.
- Ansible Automation:  Utilizing Ansible for reproducible and efficient system configuration.
- Kernel Customization:   Keywording, genkernel, and meticulous flag settings for optimal performance.
- Neofetch Integration:  Because who doesn't love a good ASCII art representation of their system?
- Ready for logging in: NetworkManager, OpenSSH and your authorized_keys file are installed - awaiting your login.
- BTRFS: Using the power of subvolumes, partitioning is easy as pie.
- Legacy BIOS support: Old hardware? New hardware - I got your back!

Get Involved:   

Feel free to fork this repository, experiment with different configurations, and share your feedback! Let's build a better Gentoo community together. 
