nethserver_install_packages
=========

Role for install lists of rpm packages, with ability of disabling or enabling repositories for each list.

Example Playbook
----------------

Install a package with default repositories enabled/disabled:

    - hosts: servers
      roles:
        - role: amygos.nethserver_install_packages
          vars:
            packages_lists:
              - pkgs:
                  - sl

Install multiple packages:

    - hosts: servers
      roles:
        - role: amygos.nethserver_install_packages
          vars:
            packages_lists:
              - pkgs:
                  - sl
                  - bc

Install package with `epel-testing` disabled and `epel` enabled:

    - hosts: servers
      roles:
        - role: amygos.nethserver_install_packages
          vars:
            packages_lists:
              - enablerepo:
                  - epel
                disablerepo:
                  - epel-testing
                pkgs:
                  - caddy

Install package with `epel` enabled and reinstall after with `epel-testing` enabled, can be useful for testing an upgrade:

    - hosts: servers
      roles:
        - role: amygos.nethserver_install_packages
          vars:
            packages_lists:
              - enablerepo:
                  - epel
                pkgs:
                  - caddy
              - enablerepo:
                  - epel-testing
                pkgs:
                  - caddy


License
-------

MIT
