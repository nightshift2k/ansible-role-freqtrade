# Ansible Role: Freqtrade

Installs [Freqtrade](https://www.freqtrade.io) on Debian/Ubuntu based systems.

## Information

This Ansible Role is designed to provide unattened and automated installation for Freqtrade - a crypto-currency algorithmic trading software developed in Python. 

Ansible is an open-source software provisioning, configuration management, and application-deployment tool enabling infrastructure as code. If you are new to Ansible and/or Freqtrade, it is highly recommended to get familiar with the concept of configuration management and infrastructure as code (IaaC). Please see the latest [Ansible documentation](https://docs.ansible.com/ansible/latest/index.html) for further information.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: tradingbots
      roles:
        - role: nightshift2k.freqtrade
          become: yes

## Installation

At the moment, the role has not (yet) bin submitted to the Ansible Galaxy repository, so installation from GitHub is currently the only way.
    
    ansible-galaxy install git+https://github.com/nightshift2k/ansible-role-freqtrade.git

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    freqtrade_installation_directory: "/opt/freqtrade"

The destination directory of Freqtrade

    freqtrade_branch: "stable"
    
The branch in GitHub for the checkout of source files.

    freqtrade_install_dev_deps: false
    
Whether to install development dependencies.

    freqtrade_install_plot_deps: false

Whether to install plotting dependencies (plotly).

    freqtrade_install_hyperopt_deps: true
    
Whether to install hyperopt dependencies.

    freqtrade_install_additional_pips:
      - finta
      - ta
Defines a list of additional python packages, that should be installed in Freqtrade's virtual environment.

## Dependencies

None.

## Example Playbook

    - hosts: tradingbots
      vars_files:
        - vars/freqtrade.yml
      roles:
        - role: nightshift2k.freqtrade
          become: yes

*Inside `vars/freqtrade.yml`*:

    freqtrade_installation_directory: "/opt/freqtrade"
    freqtrade_branch: "develop"
    freqtrade_install_dev_deps: true 
    freqtrade_install_plot_deps: true
    freqtrade_install_hyperopt_deps: true 
    freqtrade_install_additional_pips:
      - finta
      - ta
      - mergedeep
      ...

## License

MIT / BSD