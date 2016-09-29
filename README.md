Regular Expression Examples
===========================

The goal of this script is to provide examples for regular expression.

Learn regular expression from `Automate the Boring Stuff with Python <https://automatetheboringstuff.com/chapter7/>`_

Use `Regexr Tool <http://regexr.com/>`_ to build your regular expression pattern.

Overview
--------

Sub-Section of Running Configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The below example pulls the management interface configuration from the show run.

First use the regexr online tool to build the regular expression pattern. Copy and paste the show running-config in the text section. Type the regular expression pattern in the expression field. You can use the cheat sheet for reference.

.. image:: images/section.png

..

  import re

  with open("switch_config.txt") as read_file:
      config = read_file.read()

  pattern = re.compile(r'!\ninterface Management(0|1)\n((?:.|\n)*?)!')
  mgmt_config = pattern.search(config).group()

  print mgmt_config

Retrieve IP Address
^^^^^^^^^^^^^^^^^^^

From the management interface configuration, retrieve the IP address.

.. image:: images/subsection.png

..

  import re

  with open("switch_config.txt") as read_file:
      config = read_file.read()

  pattern = re.compile(r'!\ninterface Management(0|1)\n((?:.|\n)*?)!')
  mgmt_config = pattern.search(config).group()

  pattern_ip = re.compile(r'((([0-9]){1,3})\.){3}([0-9]){1,3}')
  ip_address = pattern_ip.search(mgmt_config).group()

  print ip_address
