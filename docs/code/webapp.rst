**********************
Webapp
**********************

To front end webapp is html with a PHP block for listing maps.

.. code-block:: xml
   :linenos:
 
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
      


 
  



 
  

