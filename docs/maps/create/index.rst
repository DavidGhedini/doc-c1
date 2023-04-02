.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

***************************
Add Map Entry
***************************
.. contents:: Table of Contents

Field Values
===================
      
The values for the database fields are shown below

1. **ID** - Map id (pk, shown only, cannot be updated)
2. **name** - Map name
3. **Host** - hostname or IP of PostGIS database
4. **Database** - database name
5. **Schema** - schema
6. **Username** - database username
7. **Password** - database username
8. **Geom** - database geom column
9. **Metric** - field to render colors (see below)
10. **Table** - database table
11. **Lat** - initial lat
12. **Lon** - initial lon
13. **Zoom** - initial zoom

Metric Field
===================

The Metric field is the field which will be used for coloring the map.

This field can be a standard data column or a calculated column.

In the demo data (widgets.sql), the Metric column is calculated:

.. code-block:: sql
   :linenos:
   alter table public.wardinfo add column widgetsperward numeric GENERATED ALWAYS AS (round(widgets / POWER((perimeter)/4),2))) STORED
```

Input New Entry
===================

To add a new entry, click the "Add New" button as shown below.

      .. image:: _static/add-new.png

      
Populate the fields as shown below.  


      .. image:: _static/add-new-2.png
      
  
Click the Save icon as shown below.  


      .. image:: _static/add-new-3.png   







