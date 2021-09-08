---
title:  รายชื่อสเปรย์โควิด-19
permalink: /th/covid19-list
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

Pertinent events and articles supporting the aerosol nature of infection for COVID-19. The viron is around 0.115 microns in size, and is suspended in aerosolized water-based liquids 0.7 microns and bigger. **If your country has not crushed COVID-19 yet, you should wear a good cloth face covering (or mask) as much as possible when around others indoors and in other poorly ventilated spaces.** #covidIsAirborne #masks4All #bewareOfSharedAir #ventilation. <a href="https://twitter.com/intent/tweet?url=https%3A%2F%2Fits-airborne.org%2Fcovid19-list&via=AerosolizedC19&text=%23COVIDisAirborne%20%23masks4All%20%23bewareOfSharedAir%20%23ventilation. See: " target="_blank">Tweet This Page</a>. See also, a [timeline](covid19-timeline.html) version of this page.

<script>
$(document).ready(function () {
    $.noConflict();

       $.getJSON("../media/aerosol-timeline.json", function(tl) {
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