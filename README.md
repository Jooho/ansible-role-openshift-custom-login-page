Ansible Role: Openshift Custom Login Page
=========

This role help create a custom login page of Openshift.
In detail, it is just changing the logo of default login page.

Requirements
------------


Role Variables
--------------

| Name                      | Default value                         |        Requird       | Description                                                                 |
|---------------------------|---------------------------------------|----------------------|-----------------------------------------------------------------------------|
| openshift_master_conf_dir | /etc/origin/master                    |         yes          | Where openshift configuation dir is                                         |
| master_url                | http://master1.example.com:8443       |         yes          | API Server URL                                                              |
| login_html_dir            | /etc/origin/master                    |         yes          | Where new login html page will locate                                       |
| temp_dir                  | /tmp                                  |         no           | Temp directory                                                              |


Dependencies
------------

Jooho.image-resize 

Example Execute Command
-----------------------
```
ansible-playbook  ./playbook.yaml v  --extra-vars output_img_file=/tmp/sample-openshift-ori.png
```


Example Playbook
----------------
~~~
- name: Example Playbook
  hosts: masters
  gather_facts: false
  
  pre_tasks:
  - name: Shared values in roles
    set_fact:
       output_img_file: /tmp/sample-openshift-ori.png

   roles:
      - { role: resize_image, output_img: "{{output_img_file}}", force: true}
      - { role: configure_login_logo, resized_img: "{{output_img_file}}", master_url: "master1.example.com:8443", login_html_folder: "/etc/origin/master/stylesheet/images" }

~~~

License
-------

BSD/MIT

Author Information
------------------

This role was created in 2016 by [Jooho Lee](http://github.com/jooho).

