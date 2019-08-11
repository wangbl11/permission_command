==========================
sparrow_permission_command
==========================

sparrow_permission_command提供了一个命令(command),用来把注册API到权限中心。

Quick start
-----------

1. Add "sparrow_permission_command" to your INSTALLED_APPS setting like this::

    INSTALLED_APPS = [
        ...
        'sparrow_permission_command',
    ]

2. Add next parameters in settings.py::

    config={
        ...
        "AUTH_CENTRE": {
           "test": "https://backend5.dongyouliang.com/api/sparrow_permission/i/inspectschema/",
           "pro": "https://backend5.hanguangbaihuo.com/api/sparrow_permission/i/inspectschema/",
           "dev": "http://localhost:8000/api/sparrow_permission/i/inspectschema/",
           "unit": "http://localhost:8000/api/sparrow_permission/i/inspectschema/",
        },
    }
    AUTH_CENTRE = config['AUTH_CENTRE'][RUN_ENV]

3. Run `python manage.py generate_schema` to register APIs into permission center
   or Write this command in dockfile to run automatically before rebuild every time in K8s::

    -d 1|2  [jdango version: 1 means <1.11 , 2 means >1.11
    -l 0|1  [local model: 0 means to call permission rest service to register, 1 means use
             permission model directly to register
