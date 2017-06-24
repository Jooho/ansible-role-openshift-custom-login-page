Ansible Role: Openshift Custom Login Page
=========

This role help create a custom login page of Openshift.
In detail, it is just changing the logo of default login page.

Requirements
------------
None

Role Variables
--------------

| Name                      | Default value                         |        Requird       | Description                                                                 |
|---------------------------|---------------------------------------|----------------------|-----------------------------------------------------------------------------|
| openshift_master_conf_dir | /etc/origin/master                    |         yes          | Where openshift configuation dir is                                         |
| master_url                | http://master1.example.com:8443       |         yes          | API Server URL                                                              |
| login_html_dir            | /etc/origin/master                    |         yes          | Where new login html page will locate                                       |
| logo_image                | /tmp/sample-openshift-ori.png         |         yes          | Logo image path                                                             |
| temp_dir                  | /tmp                                  |         no           | Temp directory                                                              |


Dependencies
------------

None



Example Playbook
----------------
~~~
- name: Example Playbook
  hosts: masters
  gather_facts: false

   roles:
      - { role: configure_login_logo, logo_img: "/tmp/sample-openshift-ori.png", master_url: "master1.example.com:8443", login_html_dir: "/etc/origin/master/stylesheet/images" }

~~~

License
-------

BSD/MIT

Author Information
------------------

This role was created in 2016 by [Jooho Lee](http://github.com/jooho).

