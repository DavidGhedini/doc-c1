************
Installation
************

Installation can be done using the postgis-builder.sh script or via GIT.

Installation
=======================

Use wget to download the application to your public directory:

.. code-block:: console
   :linenos:
   
   wget https://raw.githubusercontent.com/AcuGIS/PostGIS-Builder/master/scripts/postgis-builder.sh
   chmod +x postgis-builder.sh
   ./postgis-builder.sh
    
The above will install all of the components.

Database Creation
===================

Run the install.sql to create the table for forms.

Backend (Optional)
===================

You can use the application with the front end only.  To enable backend to enter and edit resources via UI:

1. Create the user database using createusers.sql
2. Go to applocation/registration.php and register and account.

Via Git or Download
===================

You can use Git to build module for an existing Webmin installation:

.. code-block:: console
   :linenos:

    git clone https://github.com/AcuGIS/PostGIS-Builder
    mv PostGIS-Builder-master postgis
    tar -cvzf postgis.wbm.gz postgis/

    
.. note::
    Following above, you will need to log in to Webmin to complete installation using the install :ref:`wizard-label`.   
    


