
Download the application
------------------------------------------
  
* Clone or download the repository. The updated code is in the develop branch.

.. code-block:: bash

    gridappsd@gridappsd-VirtualBox:~$ git clone https://github.com/shpoudel/WSU-Restoration -b develop
    gridappsd@gridappsd-VirtualBox:~$ cd WSU-Restoration

..

Creating the application container
------------------------------------------

* From the command line execute the following commands to build the wsu-restoration container

.. code-block:: bash

     gridappsd@gridappsd-VirtualBox:~/WSU-Restoration$ docker build --network=host -t wsu-restoration-app .
..



Mount the application
-----------------------------------

* Add following to the docker-compose.yml file. 

.. code-block:: bash

    wsu_res_app:
    image: wsu-restoration-app
    volumes:
      - /opt/ibm/ILOG/CPLEX_Studio129/:/opt/ibm/ILOG/CPLEX_Studio129
    environment:
      GRIDAPPSD_URI: tcp://gridappsd:61613
    depends_on:
      - gridappsd 
      
..
