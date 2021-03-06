DOP: Digital Ocean API Python Wrapper
=====================================

DOP is a MIT licensed Python wrapper for Digital Ocean's API.


Features
--------

Full support for all methods listed `here`_

Installation
------------

To install dop, simply: ::

    $ pip install dop


Example
-------
It is pretty easy to use:

.. code-block:: python

    from dop.client import Client

    client = Client('client_id', 'api_key')
    
    # Print regions.
    regions = client.regions()
    for region in regions:
        print(region.to_json())

    # Print sizes.
    sizes = client.sizes()
    for size in sizes:
        print(size.to_json())

    # Print public global images.
    images = client.images()
    for image in images:
        print(image.to_json())

    # Print your private images.
    images = client.images(filter='my_images')
    for image in images:
        print(image.to_json())

    # Create a droplet
    conf = {
        'name': 'test',
        'size': {'size_slug': '512MB'},
        'image': {'image_slug': 'ubuntu-13-04-x64'},
        'region': {'region_slug': 'nyc1'},
    }
    droplet = client.create_droplet(**conf)

To create a droplet, you can use the data fetched from regions, sizes and images methods to fill the dictionary properly.


Contribute
----------
Pull requests and improvements are welcome.

.. _`here`: https://www.digitalocean.com/api
