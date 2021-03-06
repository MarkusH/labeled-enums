labeled-enums
=============

A Django-friendly iterable Enum type with labels.

Example
-------

.. code-block:: python

    >>> from lenum import LabeledEnum
    >>> class STATE_CHOICES(LabeledEnum):
    ...     NEW = 0
    ...     IN_PROGRESS = 1
    ...     REVIEW = 2, 'In Review'
    ...
    >>>
    >>> STATE_CHOICES.NEW
    0
    >>> STATE_CHOICES.IN_PROGRESS
    1
    >>> STATE_CHOICES[2]
    'In Review'
    >>> list(STATE_CHOICES)
    [(0, 'New'), (1, 'In Progress'), (2, 'In Review')]
    ```

Usage in Django:

.. code-block:: python

    class MyModel(models.Model):
        class STATUS(LabeledEnum):
            CLOSED = 0
            NEW = 1
            PENDING = 2, 'Process Pending'
            FAILED = -1, 'Processing Failed'

        status = models.IntegerField(choices=list(STATUS), default=STATUS.NEW)
