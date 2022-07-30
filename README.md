Ansible Vector
=========

Simple role to install Vector

Role Variables
--------------

You can set some variables:
1. Vector version that is going to be installed.
```yaml
vector_version: "0.23.0"
```

2. Directory that vector is going to be installed in
```yaml
vector_install_directory: "/etc"
```

3. Directory where vector is going to store data
```yaml
data_dir: "/etc/vector"
```

4. Content of vector config file
```yaml
config:
  sources:
    test_logs:
      type: demo_logs
      format: json
  transforms:
    test_transform:
      type: dedupe
      inputs:
        - test_logs
  sinks:
    debug_sink:
      type: console
      inputs:
        - test_transform
      target: stdout
      encoding:
        codec: json
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```yaml
- name: Install vector
  hosts: vector
  vars:
    vector_install_dir: /etc
    data_dir: /home/test
    config:
      sources:
        test_logs:
          type: demo_logs
          format: json
      transforms:
        test_transform:
          type: dedupe
          inputs:
            - test_logs
      sinks:
        debug_sink:
          type: console
          inputs:
            - test_transform
          target: stdout
          encoding:
            codec: json
  roles:
    - vector
```

License
-------

BSD

Author Information
------------------

The role is created by Netology Student as a homework by Igor Soldatov.

