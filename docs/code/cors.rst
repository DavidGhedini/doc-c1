**********************
Enable CORS
**********************

To enable CORS for your Tomcat instance, you can use our included file.

This file is located under /scripts/cors.txt

The contents should be added to the line just before </web-app> in your /home/tomcat/apache-tomcat-{version}/conf/web.xml

.. warning::
      Be sure to create a backup of your web.xml file before making any changes.
      

The file Contents are below

.. code-block:: xml
   :linenos:
   
   
            <script>
            const queryString = window.location.search;
            const urlParams = new URLSearchParams(queryString);
            
            var Lat = <?=($map_row['lat'] ? $map_row['lat'] : 0)?>;
            var Lon = <?=($map_row['lon'] ? $map_row['lon'] : 0)?>;
            var Zoom = <?=($map_row['zoom'] ? $map_row['zoom'] : 0)?>;
    	
    	
    	    $(document).ready(function() {
                var map = L.map('map').setView([Lat, Lon], Zoom)
                
                // Add basemap
                L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
                  maxZoom: 18,
                  attribution: ''
                }).addTo(map)
                
                
                var featurecollection = <?=$geom_row['featurecollection']?>;
                
                var choroplethLayer = L.choropleth(featurecollection, {
                    <?PHP if($map_row['metric']) { ?>
                    valueProperty: '<?=$map_row['metric']?>',
                    <?PHP } ?>
                    scale: ['#fbfad4', 'green'],
                    steps: 5,
                    mode: 'q',
                    style: {
                      color: '#fff',
                      weight: 2,
                      fillOpacity: 0.8
                    },
                    onEachFeature: function (feature, layer) {
                        var properties = feature.properties;
                        
                        var html = '<table style="text-align: left; font-size: 100%;">';
                        for (const key in properties) {
                            html += '<tr><th>'+ key +"</th> <td>"+ properties[key] + "</td></tr>";
                        }
                        html += '</table>';
                        
                        layer.bindPopup(html)
                    }
                }).addTo(map)
                
                <?PHP if($map_row['metric']) { ?>
                  // Add legend (don't forget to add the CSS from index.html)
                  var legend = L.control({ position: 'topright' })
                  legend.onAdd = function (map) {
                        var div = L.DomUtil.create('div', 'info legend')
                        var limits = choroplethLayer.options.limits
                        var colors = choroplethLayer.options.colors
                        var labels = [] 
                    
                        // Add min & max
                        div.innerHTML = `
                            <div class="labels">
                                <div class="quarter1">` + limits[0] + `</div>
                                <div class="quarter2">` + Math.round(((limits[limits.length - 1]-limits[0])*.25)+limits[0]) + `</div>
                                <div class="quarter3">` + Math.round(((limits[limits.length - 1]-limits[0])*.75)+limits[0]) + `</div>
                    			<div class="quarter4">` + limits[limits.length - 1] + `</div>
                    		</div>`
                    
                        limits.forEach(function (limit, index) {
                          labels.push('<li style="background-color: ' + colors[index] + '"></li>')
                        })
                    
                        div.innerHTML += '<ul>' + labels.join('') + '</ul> <span><?=ucwords(str_replace("_", " ", $map_row['metric']))?></span>'



                        
                        return div
                   }
                   legend.addTo(map)
                  
                <?PHP } ?>
            });
        </script>
      
You must restart Tomcat for the changes to register.
 
.. note:: The above script is very permissive.  You should refine your CORS filter to reflect usage.
