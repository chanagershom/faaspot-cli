.. _executions:

==========
Executions
==========

Overview
--------

When you run some command in Asynchronously way, for example: :ref:`deployment run<run_deployment>`,
the command will create execution that will run in the background,
and the result of the API will be the execution id.
You can then use the executions API to get the execution status or to see which executions are currently running.


.. _get_execution_status:

Get Execution Status
--------------------

To get the status of some execution, you need to use the spots API:


..  admonition:: CLI
    :class: open-toggle

    You can get the status of some execution using the CLI:

    .. code-block:: sh

        $ fas executions get EXECUTION_ID


..  admonition:: Python
    :class: toggle

    You can get the status of some execution sing the python-client:

    .. code-block:: python

       from faaspot import Faaspot
       faaspot = Faaspot()
       faaspot.executions.get(EXECUTION_ID)


..  admonition:: HTTP Request
    :class: toggle

    You can get the status of some execution using the direct HTTP requests:

    .. code-block:: sh

       $ curl -X GET --header "Authorization: Token MY_TOKEN" https://api.faaspot.com/v1/executions/EXECUTION_ID

A result of that api should look like that:

    {
        u'created': u'2017-07-21 15:10:52.537686+00:00',

        u'name': u'tasks.create_spot',

        u'output': None,

        u'status': u'Started',

        u'uuid': u'9cfcd860-9a5d-414f-8d2b-317d59d3f486'

    }


.. note::
    The CLI and the python-client support the ``wait`` argument.

    Meaning, that using ``fas executions get EXECUTION_ID --wait`` or using ``faaspot.executions.get(EXECUTION_ID, wait=True)``,
    will wait until the execution is completed.


Get Executions list
-------------------

To get the current running executions


..  admonition:: CLI
    :class: open-toggle

    You can get the current running executions using the CLI:

    .. code-block:: sh

        $ fas executions list

    The executions status command parameters:

    - (Optional) **--include_completed** Boolean parameter, whether to include completed executions. Default is False.


..  admonition:: Python
    :class: toggle

    You can get the current running executions using the python-client:

    .. code-block:: python

       from faaspot import Faaspot
       faaspot = Faaspot()
       faaspot.executions.list()

    The executions status command parameters:

    - (Optional) **include_completed** Boolean parameter, whether to include completed executions. Default is False.


..  admonition:: HTTP Request
    :class: toggle

    You can get the current running executions using the direct HTTP requests:

    .. code-block:: sh

       $ curl -X GET --header "Authorization: Token MY_TOKEN" https://api.faaspot.com/v1/executions/?include_completed=False

    You can add to the request ``?include_completed=False`` or ``?include_completed=True``,
    To include completed executions or not.