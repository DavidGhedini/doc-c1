.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

***************************
Dashboard
***************************
.. contents:: Table of Contents

Components
===================

The main dahsboard generates a thumbnail link for each row entry in the database.

It also contains a link to the login page (which can be removed if you are not using the backend).
      
 .. image:: ../../_static/frontend.png .

Main Code
===================

The Metric field is the field which will be used for coloring the map.

This field can be a standard data column or a calculated column.

In the demo data (widgets.sql), the Metric column is calculated:

.. code-block:: sql

  alter table public.wardinfo add column widgetsperward numeric GENERATED ALWAYS AS (round(widgets / POWER((perimeter)/4),2))) STORED

.. Warning:: 
   Leaflet generated GeoJson for the map.  You should limit the amount of data and columns to prevent long load times. 








