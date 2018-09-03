# app-win-template
========= 

This role is a Template for building Ansible roles to deploy Windows applications. 


Requirements
------------

* Ansible control server
* Windows Endpoint

 ## Howto:
 1. Zip all files in 1 file.
 
 2. Upload the file to the web/download server.
 
 3. Edit defaults/main.yml to your needs.
 
 4. Add the role to your playbook.


Role Variables
--------------

Variables could be overridden in playbook.

* pkg_state        : 'present' or 'absent'                                 # Whether the application should be installed or removed (present=install, absent=removed).
* pkg_name         : '7zip1805-x64'                                        # Name of the application.
* pkg_arch         : '32bit' or '64bit'                                    # Whether the application is a 32bit or a 64bit application.
* pkg_repo_local   : '{{ ansible_env.ProgramFiles }}/Ansible/temp/'        # Local path to package.
* pkg_repo_remote  : 'http://dl.example.com/resource/7zip/7z1805-x64.zip'  # Remote url to package (needs to be zip file).
* pkg_product_id   : '{23170F69-40C1-2702-1805-000001000000}'              # Product can be found in "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall" or "HKLM:\SOFTWARE\Wow6432Node\M$
* pkg_installer    : '{{ pkg_repo_local }}\7z1805-x64.msi'                 # Executable for the installation.
* pkg_arguments    : '/qn'                                                 # Additional Arguments for a silent installation.

Dependencies
------------


Example Playbook
----------------

    - hosts: windows-endpoint

      roles:
         - app-win-template


License
-------

GPLv3

Author Information
------------------

E: lrutten@bitfinity.nl

I: https://www.bitfinity.nl
