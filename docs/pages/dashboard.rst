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
      
 .. image:: ../../docs/_static/frontend.png .

Main Code
===================

The main code block for generating the map links is below:

.. code-block:: php

  <?PHP foreach($rows as $row) { ?>
            <?PHP
                $image = file_exists("assets/maps/{$row['id']}.png") ? "assets/maps/{$row['id']}.png" : "assets/maps/default.png";
            ?>
            <a href="map.php?id=<?=$row['id']?>" style="text-decoration:none; color: #6c757d!important; font-size: 1.25rem; font-weight: 300;">
                <div class="col">
                    <img src="<?=$image?>" height="225" width="100%">
                    
                    <div class="card-body">
                        <p class="card-text text-center"><?=$row['name']?></p>
                    </div>
                </div>
            </a>
        <?PHP } ?>


 








