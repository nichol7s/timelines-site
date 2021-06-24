---
title: A historical list of infectious disease transmitted in aerosols
nav_order: -1
layout: page
---

<script
  src="https://code.jquery.com/jquery-3.6.0.min.js"
  integrity="sha256-/xUj+3OJU5yExlq6GSYGSHk7tPXikynS7ogEvDej/m4="
  crossorigin="anonymous"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.10.11/js/jquery.dataTables.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/fixedcolumns/3.2.1/js/dataTables.fixedColumns.min.js"></script>
<script src="https://unpkg.com/dayjs@1.8.21/dayjs.min.js"></script>
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.10.25/css/jquery.dataTables.min.css">

The airborne or aerosol nature of infection has been talked about for other diseases over the years, and this list contains many of the major developments on these subjects.  <a href="https://twitter.com/intent/tweet?url=https%3A%2F%2Fits-airborne.org%2Fhistorical-list&via=AerosolizedC19&text=%23COVIDisAirborne%20%23masks4All%20%23bewareOfSharedAir%20%23ventilation. See: " target="_blank">Tweet This Page</a>

For the sake of this timeline, **aerosol** = **airborne** = **droplet nuclei**. These are particles that are less-than-100-μm in diameter, and therefore typically evaporate before gravity pulls them to the ground. As small particles, they float for minutes, or even hours, and can travel some distance in this time. The word aerosol simply means a particle suspended in air.

On the other hand, **droplets**, those particles with diameters larger than 100 μm, typically get pulled by gravity to the ground - said to happen within two meters, usually - before they can evaporate and float.

Note: the medical and science communities are changing to a **100** μm (and above) definition of droplets. This was formerly **5** μm. <a target="_blank" href="https://twitter.com/linseymarr/status/1336318245348003840">See @linseymarr's tweets</a>. Everything smaller than 100 μm are aerosol.  See also, a [timeline](historical-timeline.html) version of this page.

<script>
$(document).ready(function () {
    $.noConflict();

       $.getJSON("../media/aerosol-history-timeline.json", function(tl) {
            for(i=0;i < tl.events.length;i++){
                    var html='';
                    var dt = tl.events[i].start_date.year; 
                    var mt = tl.events[i].start_date.month;
                    var dy = tl.events[i].start_date.day;
                    if (mt > 0) {
                        dt = dt + "-" + mt;     
                        if (dy > 0) {
                            dt = dayjs(dt + "-" + dy).format('MMM D, YYYY');     
                        } else {
                            dt = dayjs(dt + "-1").format('MMM, YYYY');    
                        }
                    }

                    dt = dt.replaceAll("-undefined","");
                    html +='<td>' + dt +'</td>';
                    html +='<td><a href="' + tl.events[i].media.link +'">link</a></td>';
                    html +='<td>' + tl.events[i].text.headline +'</td>';
                    html +='<td>' + tl.events[i].text.text +'</td>';
                    $('#table_id tbody').append('<tr>'+html+'</tr>');
            }
            $('#table_id').DataTable();
       });
});
</script>

<table id="table_id" class="display">
    <thead>
        <tr>
          <th>Date</th>
          <th>Link</th> 
          <th>Headline</th> 
          <th>Text</th>
        </tr>
    </thead>
    <tbody>        
    </tbody>
</table>